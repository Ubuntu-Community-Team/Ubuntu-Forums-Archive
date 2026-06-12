---
title: "PHP Cron Help"
date: 2008-08-13
forum: General Help
---

### Post by QBD on 2008-08-13
I have tried looking everywhere for a cron code that would allow me to run a php file but i have had trouble with some of the code i have found, i am a noob at linux and i don't know too much about it, but.. i am trying to run a php file with a md5 code at the end of it.. and i am getting error messages such as permission denied and cannot find file. The code is as follows.. curl * * * * * /home/test/public_html/cron_minute.php?code=6f1ed002ab5595859014ebf0951522d9 

i have setup all of the web services needed to run a site and i have also installed webmin as well. The crons will not run without the md5 hash at the end, but the crons are the only thing that is giving me a problem. Help on this would be grateful as i am trying not to go crazy in figuring out crons.. lol

---

### Post by p_quarles on 2008-08-13
So, what is the result of loading that page in a graphical web browser? Or just running curl manually? 

In other words, the problem isn't likely to be with the fact that this is a cronjob, but that the web server's permissions are wrong. We need to try to get this same page via other means to figure out what's wrong with it.

---

### Post by QBD on 2008-08-17
When i run it through webmin it says sh: /home/test/public_html/cron_minute.php?code=6f1ed002ab5595859014ebf095152 2d9: not found without the curl * * * * * .. the command with the curl * * * * * outputs as h: curl: not found .. without the md5 hash and without the curl it outputs as sh: /home/test/public_html/cron_minute.php: Permission denied

I am stuck i have tried alot of ways to run this cron and i have no idea what is happening

---

### Post by QBD on 2008-08-17
Here is also some addition information when i try to run them from the webmin command shell

```

> /home/test/public_html/cron_minute.php?code=6f1ed002ab5595859014ebf0951522d9
bash: /home/test/public_html/cron_minute.php?code=6f1ed002ab5595859014ebf0951522d9: No such file or directory

> /home/test/public_html/cron_minute.php
bash: /home/test/public_html/cron_minute.php: Permission denied

```

---

