---
title: "sftp logs in to root directory instead of home"
date: 2008-07-14
forum: General Help
---

### Post by vav on 2008-07-14
I use sftp to log in to servers, for e.g. with websites I update. ssh in windows logs into the home directory, which is often on a funny link such as /mnt/disk09345/homes/username or some such. 

On Ubuntu though I get logged into the root directory of the server, which is unnecessary and I can't find the home directory from there...

How do I 'fix' this?

---

### Post by collinp on 2008-07-14
Hmm, sounds like you installed the program as root. Reinstall the program not as root, that should fix your problem. If you dont want to do that, look around in your settings for a option to change the location the program logs at, or just navigate to the directory and view the log yourself. Mabye this will help for redirection: [http://www.vias.org/linux-knowhow/bbg_sect_08_02_03.html](http://www.vias.org/linux-knowhow/bbg_sect_08_02_03.html).

---

### Post by vav on 2008-07-14
Sorry I might have been unclear. What I meant is, when I login to another machine, sftp opens the dest. machine's root '/' folder instead of my home on the dest. machine. e.g. if I logged in to ubuntuforums.org it would open 
ubuntuforums.org/
instead of
ubuntuforums.org/disk232/homes/me/

while on other ssh programs in windows it opens the latter by default (sometimes without showing the entire path)

---

### Post by nanog on 2008-07-16
I posted a bug on this several months ago. It was closed without any confirmation.

---

### Post by nanog on 2008-07-16
If you open a new bug I will confirm it.

---

