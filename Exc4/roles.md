Роли сервера авторизации

| Роль  | Права роли | Пользователи |
| --- | --- | --- |
| УмныйСобственник | Доступ к части АПИ сервиса tenant-core-app, которая отвечает за работу с умными устройствами. | Все собственники |


Роли кластера kubernetes

Предполагается, что все сервисы развернуты в кластере, а все СУБД, active directory и брокеры - вне его.

Для исключения необходимости создания общекластерных ролей (ClusterRole) сервис аутентификации/авторизации лучше развернуть в каждом пространстве имен отдельно, но БД будет одна и таже

Т.к. БД общие для всех реплик сервисов, то разделать кластер на пространства имен по принзнаку номера дома смысла особого нет, т.к. любой экзепляр в каком угодно пространстве имен без контроля внутри приложения сможет получить доступ к чужим данным

## Сервсиные учетки 

| Роль  | Права роли | Пользователи | Простарнство | Тип |
| --- | --- | --- | --- | --- |
| monitoring-role | Доступ на чтение | пользователь для сбора метрик | все | ClusterRole |
| developer-role | Доступ на чтение | разработчики | для каждого пространства свой | Role |