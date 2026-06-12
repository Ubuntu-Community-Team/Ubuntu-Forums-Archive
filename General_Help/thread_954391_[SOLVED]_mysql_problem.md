---
title: "[SOLVED] mysql problem"
date: 2008-10-21
forum: General Help
---

### Post by francisc1701 on 2008-10-21
hi everyone!

I'm running Apache 2.2.8-1ubuntu0.3, php 5.2.4-2ubuntu5.3 and mysql server 5.0.51a-3ubuntu5.1 on Kubuntu Hardy.
This bit of php:
```
$lista_procese = mysql_list_processes($conexiune);
$rand= mysql_fetch_assoc($lista_procese);
foreach($rand as $cheie => $valoare)
{
   echo "$cheie = $valoare<br />";
}
```

works fine when I access the page using localhost. This is what it outputs:
```
Id = 10
User = root
Host = localhost
db = 
Command = Processlist
Time = 0
State = 
Info = 
```
However when I access the page from another computer on my local network, the output changes to this:
```
Warning: mysql_list_processes() [function.mysql-list-processes]: Unable to save MySQL query result in /var/www/page.php on line 498
 
 Warning: mysql_fetch_assoc(): supplied argument is not a valid MySQL result resource in /var/www/page.php on line 499
 
 Warning: Invalid argument supplied for foreach() in /var/www/page.php on line 500
```

I googled the first warning (as the others are just a consequence of mysql_list_processes not succeeding) but I did not find anything useful.

What should I do to fix this?

---

### Post by francisc1701 on 2008-10-24
The problem was not caused by Ubuntu, but by my own script. My mistake. ](*,)

Just in case someone else makes the same stupid mistake: the parameters passed to mysql_connect() where incorrect. (they were empty strings).

---

