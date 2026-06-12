---
title: "Need Backup Advise"
date: 2008-09-08
forum: General Help
---

### Post by the guitarist on 2008-09-08
hello everyone,

i'm trying to backup my ubuntu gutsy and create something similar to a restore point trough flyback program.

but i need someone to tell me which folder should i backup beside my home folder ... i mean the critical ones..

because i formated and re-installed ubuntu like 4 times in a month because after an update sometimes my nvidia driver crashes and after trying every solution nothing works...so

up until now I'm thinking about backing up these 2 folders:

1- Home folder
2-etc folder

but I'm no expert so please give me your advise about the matter ..


thanx

---

### Post by skullmunky on 2008-09-08
Those are the two I always back up.

if you're running a web server for anything on that machine, you should back up /var/www, which is where the website is.  

for most applications, libraries, etc, it's safest to reinstall.

if you run commercial apps that use flexlm licensing, like Maya, back up /var/flexlm.

if you installed other stuff manually by compiling, or not through the package manager, they might be in /usr/local.

---

### Post by the guitarist on 2008-09-08
> **skullmunky said:**
> Those are the two I always back up.

if you're running a web server for anything on that machine, you should back up /var/www, which is where the website is.  

for most applications, libraries, etc, it's safest to reinstall.

if you run commercial apps that use flexlm licensing, like Maya, back up /var/flexlm.

if you installed other stuff manually by compiling, or not through the package manager, they might be in /usr/local.

thanx alot skullmunky ..

so up till now the folders i have to backup are :

1- home folder
2- etc folder
3- usr folder

do you recomend any backup tool other than flyback which has an easy interface ?

---

### Post by skullmunky on 2008-09-08
I've never used Flyback, but I love anything with a nice interface!  

let us know how you fare with it.

---

### Post by the guitarist on 2008-09-08
> **skullmunky said:**
> I've never used Flyback, but I love anything with a nice interface!  

let us know how you fare with it.

so you just do it manually?...I'm trying it right now..and it's realy easy ..it just backups the folders or files you specify and than restores them if any of them got deleted or missed up .. 

by the way ... I'm only doing this because a couple of times after updating my gutsy starts in low resolution mode. i tried everything to restore my nvidia driver back even downloading and installing it manually from the nvidia website but didn't work ... so i thought about backing up..so whenever something gets missed up i only have to restore and that's it..

any ideas?...maybe another approach?

---

### Post by skullmunky on 2008-09-16
I've always just used the command line, with rsync or just cp -a.  I like how simple Flyback is.  cool.

For that kind of restore-in-case-of-utter-catastrophe i also sometimes use partimage, to just keep a whole disk image of the entire partition which i can just clone back on.  

If the restore fixes the problem it might be that the driver is fine, but the config file has the error.

Try nvidia-settings, see if that gets you the right resolutions again.

---

