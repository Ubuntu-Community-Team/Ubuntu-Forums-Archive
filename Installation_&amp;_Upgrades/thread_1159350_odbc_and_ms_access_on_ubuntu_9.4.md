---
title: "odbc and ms access on ubuntu 9.4"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by snake_eyes on 2009-05-14
Hello,

I just prepared the server installed odbc, I configured the the required files as well , and here is the result:
> 
+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL> select * from table;


now I made some small php code:

```

$conn = odbc_connect("DSN","","");
$select = "SELECT * FROM TABLE";
$result = odbc_exec($conn, $select);
while ($row = odbc_fetch_array($result))
{
    $rowid = $row['name1'];
    $pwd = $row['password'];
}
echo "Row id :".$rowid;
echo "password : ".$pwd;

```

now I'm facing a problem with I browse the file it download and ask me to save or open it, although the other projects with php and mysql are working fine.

Any idea gentleman?

Cheers,

---

### Post by snake_eyes on 2009-05-15
anybody there gentleman?

---

