---
title: "Default passwd users ?"
date: 2008-11-20
forum: General Help
---

### Post by cole08 on 2008-11-20
Hi all, 

I wonder why every default user comes with shell login access? 

/etc/passwd output:


daemon: x:1:1:daemon:/usr/sbin:/bin/sh
bin: x:2:2:bin:/bin:/bin/sh
sys: x:3:3:sys:/dev:/bin/sh
sync: x:4:65534:sync:/bin:/bin/sync
games: x:5:60:games:/usr/games:/bin/sh
man: x:6:12:man:/var/cache/man:/bin/sh
lp: x:7:7:lp:/var/spool/lpd:/bin/sh
mail: x:8:8:mail:/var/mail:/bin/sh
news: x:9:9:news:/var/spool/news:/bin/sh
uucp: x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy: x:13:13:proxy:/bin:/bin/sh
www-data: x:33:33:www-data:/var/www:/bin/sh
backup: x:34:34:backup:/var/backups:/bin/sh
list: x:38:38:Mailing List Manager:/var/list:/bin/sh
irc: x:39:39:ircd:/var/run/ircd:/bin/sh
gnats: x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody: x:65534:65534:nobody:/nonexistent:/bin/sh



Doesnt every deamon user should have /bin/false and not /bin/sh or /bin/bash ? If I change them to /bin/false could my system work properly?
:popcorn:

---

### Post by cole08 on 2008-11-21
Bump

---

### Post by cole08 on 2008-11-21
Any idea please ?

---

### Post by cole08 on 2008-11-22
[-(:-({|=

---

### Post by cole08 on 2008-11-22
Can someone end this misserable topic by replying the damn question ? :mad:

---

### Post by gTinker on 2008-11-22
[QUOTE=cole08]
I wonder why every default user comes with shell login access? 
[/quote]

I believe that is so there is accountability, same reason each human user has ownership of the files created by that user.

[QUOTE=cole08]
Doesnt every deamon user should have /bin/false and not /bin/sh or /bin/bash ?
[/quote]

No. 

Check and see if /bin/sh is a symlink to bash.

[QUOTE=cole08]
 If I change them to /bin/false could my system work properly?
[/QUOTE]

No. It probably would not and you probably would be disappointed in the user experience.

Sometimes we don't get an answer as fast as we would like, in that case it is usually helpful to display patience.

---

