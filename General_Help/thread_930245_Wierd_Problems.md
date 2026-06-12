---
title: "Wierd Problems"
date: 2008-09-25
forum: General Help
---

### Post by fearful on 2008-09-25
Hello, I'm running Ubuntu 8.04 with the latest updates. I'm dual booting Windows XP and Ubuntu. Everything seemed to be going really well until this evening, after everything being O.K as usual I got home and I noticed that my mount of windows partition didn't work. Fortunatley I found the problem my fstab had been modified by no reason and when I log out or restart I have to type in my /dev/sda1 mounting point etc. This is not the major problem since I have found a slight fix, although it is a pain to do that on each startup. The main problem consist in that this morning I had 8+ GB free on my Ubuntu partition, after logging on this evening I only have 2.2GB left. Any ideas why, haven't installed any programs.

---

### Post by taladan on 2008-09-25
My first guess would be to check your system log files.  You can log into your ubuntu partition and go to the cli, type 

cd /var/log;ls -lah

look in the 5th column and that will be filesizes.  If you don't see any overly large files in there it could be something like ~/.xsession-errors filling up or something similar.

Tal

---

### Post by fearful on 2008-09-25
There are no overly large files, biggest one is 5.5MB, any other suggestion. Thanks for the reply.

---

### Post by fearful on 2008-09-25
Well I figured out the problem, I hadn't fully deleted the files in /root/.local/share/Trash. That fixed it :) thanks again for the replies

---

