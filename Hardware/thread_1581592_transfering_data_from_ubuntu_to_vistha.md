---
title: "transfering data from ubuntu to vistha"
date: 2010-09-25
forum: Hardware
---

### Post by harries on 2010-09-25
hi,

i need to transfer files from one laptop which is running ubuntu to anther which is running vista. 

the laptop which is running ubuntu is 10 yrs old and really slow, and only used for utorrent

tried using a flashdrive but copying speed decrease to 50kb/s within a few secs

before u answer plz consider that im a real noob at ubnutu and computers.

thanks

---

### Post by mmad on 2010-09-25
Quickly googling it would have given you plenty of options :confused:. However, check [[COLOR="Red"]here[/COLOR]](http://ubuntuforums.org/archive/index.php/t-531536.html). 

I personally would use the external hard drive method, but you could look for a guide on Samba and do it like that too (I haven't done it myself). If you have no external hard drive, you could try ethernet with encryption off - but you'd have to research that because I personally dont know how to do that.

EDIT: Sorry although you talked about a flashdrive, I only mention the external hard drive because you may just have a really slow memory stick. However if your old laptop has only USB 1.1 ports then I'm afraid you'll have to live with the slow speed and just leave it going for a while.

---

### Post by IcarusR on 2010-09-25
Your options are an exernal drive, (flashdrive or hdd) burn to cd / dvd or network.

Can use a 'crossover' ethernet cable & connect both, then you should be able to 'see' both drives from both boxes.
You can then use either SSH, ftp or samba.
If all files are in same directory you could setup rsync to copy files, will do it unattended & do md5sum checks on files. Can also do incremental copy's, so will only copy new files. Usefull if this is going to be an ongoing situation.

---

