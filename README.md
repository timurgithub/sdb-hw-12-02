
# Домашнее задание к занятию «Работа с данными (DDL/DML)» - `Акаев Тимур`

### Задание 1

1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.
```sql
docker run --name mysql-instance -e MYSQL_ROOT_PASSWORD=root -p 3333:3306 -d mysql:8.4
docker exec -it mysql-instance mysql -u root -p
```

1.2. Создайте учётную запись sys_temp.
```sql
CREATE USER 'sys_temp'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%' WITH GRANT OPTION;
```
1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)
![Скриншот-1](https://github.com/timurgithub/sdb-hw-12-02/blob/main/img/1.png)

1.4. Дайте все права для пользователя sys_temp. 
```sql
CREATE USER 'sys_temp'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%' WITH GRANT OPTION;
```

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)
![Скриншот-2](https://github.com/timurgithub/sdb-hw-12-02/blob/main/img/2.png)

1.6. Переподключитесь к базе данных от имени sys_temp.
```sql
docker exec -it mysql-instance mysql -u sys_temp -p
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.
1.7. Восстановите дамп в базу данных.
1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)
![Скриншот-3](https://github.com/timurgithub/sdb-hw-12-02/blob/main/img/3.png)
![Скриншот-4](https://github.com/timurgithub/sdb-hw-12-02/blob/main/img/4.png)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*



### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```
```sql
SELECT 
    TABLE_NAME, 
    COLUMN_NAME AS PRIMARY_KEY
FROM 
    INFORMATION_SCHEMA.KEY_COLUMN_USAGE
WHERE 
    TABLE_SCHEMA = 'sakila' 
    AND CONSTRAINT_NAME = 'PRIMARY';

```
![Скриншот-5](https://github.com/timurgithub/sdb-hw-12-02/blob/main/img/5.png)
