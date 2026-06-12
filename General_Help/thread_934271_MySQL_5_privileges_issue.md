---
title: "MySQL 5 privileges issue"
date: 2008-09-30
forum: General Help
---

### Post by retrovertigo on 2008-09-30
I'm trying to install OneOrZero helpdesk on a test environment, and I'm trying to create a database and user for the software to use.  I am using Ubuntu Server 8.04.1 and I have installed MySQL 5.

As the root database user I have run the following commands.  Password has been removed for security.

```
mysql> create database oneorzero;
Query OK, 1 row affected (0.00 sec)

mysql> create user oneorzero identified by '********';
Query OK, 0 rows affected (0.00 sec)

mysql> grant all on oneorzero.* to oneorzero;
Query OK, 0 rows affected (0.00 sec)
```

Now, when I go to login, this is what happens:

```
ej@helpdesk:~$ mysql -u oneorzero -p oneorzero
Enter password:
ERROR 1045 (28000): Access denied for user 'oneorzero'@'localhost' (using password: YES)
```

The odd thing is that MySQL will let me in if I leave off the password, but when I try switching databases it's as if I haven't specified a user (note the ''@'localhost' in the "access denied" error below):

```
ej@helpdesk:~$ mysql -u oneorzero
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 46
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use oneorzero;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'oneorzero'
mysql>
```

Did I do something wrong in creating this user?

---

### Post by ianhaycox on 2008-09-30
I think you need to,

grant all privileges on oneorzero.* to 'oneorzero'@'localhost';

or 

grant all privileges on oneorzero.* to 'oneorzero'@'%';

---

### Post by retrovertigo on 2008-09-30
> **ianhaycox said:**
> I think you need to,

grant all privileges on oneorzero.* to 'oneorzero'@'localhost';

or 

grant all privileges on oneorzero.* to 'oneorzero'@'%';

I've done that, but I'm still not getting in.  Here is the user's record from the db table:

```
mysql> select * from db where User = 'oneorzero';
+------+-----------+-----------+-------------+-------------+-------------+-------------+-------------+-----------+------------+-----------------+------------+------------+-----------------------+------------------+------------------+----------------+---------------------+--------------------+--------------+
| Host | Db        | User      | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Create_tmp_table_priv | Lock_tables_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Execute_priv |
+------+-----------+-----------+-------------+-------------+-------------+-------------+-------------+-----------+------------+-----------------+------------+------------+-----------------------+------------------+------------------+----------------+---------------------+--------------------+--------------+
| %    | oneorzero | oneorzero | Y           | Y           | Y           | Y           | Y           | Y         | N          | Y               | Y          | Y          | Y                     | Y                | Y                | Y              | Y                   | Y                  | Y            |
+------+-----------+-----------+-------------+-------------+-------------+-------------+-------------+-----------+------------+-----------------+------------+------------+-----------------------+------------------+------------------+----------------+---------------------+--------------------+--------------+
```

---

### Post by ianhaycox on 2008-09-30
That should have been AND not OR as you need the localhost entry as well I think.

It is necessary to have both accounts for oneorzero to be able to connect from anywhere as oneorzero. Without the localhost account, the anonymous-user account for localhost that is created by mysql_install_db would take precedence when oneorzero connects from the local host. As a result, oneorzero would be treated as an anonymous user. The reason for this is that the anonymous-user account has a more specific Host column value than the 'oneorzero'@'%' account and thus comes earlier in the user table sort order.

---

### Post by retrovertigo on 2008-09-30
I added the localhost entry to the db table.  This also added an entry for host "localhost" to the user table, however it did not specify a password so I still could not login.

```
mysql> select * from user where User = 'oneorzero';
+-----------+-----------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| Host      | User      | Password                                  | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections | max_user_connections |
+-----------+-----------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| %         | oneorzero | *FF1252E0BB83843578D1B9C58C2119103A7A4200 | N           | N           | N           | N           | N           | N         | N           | N             | N            | N         | N          | N               | N          | N          | N            | N          | N                     | N                | N            | N               | N                | N                | N              | N                   | N                  | N                |          |            |             |              |             0 |           0 |               0 |                    0 |
| localhost | oneorzero |                                           | N           | N           | N           | N           | N           | N         | N           | N             | N            | N         | N          | N               | N          | N          | N            | N          | N                     | N                | N            | N               | N                | N                | N              | N                   | N                  | N                |          |            |             |              |             0 |           0 |               0 |                    0 |
+-----------+-----------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
2 rows in set (0.00 sec)
```

I updated the user table, copying the password hash from the oneorzero user's "%" entry in the user table to the "localhost" entry, and that ended up doing the trick.


Thanks much for pointing me in the right direction!

---

