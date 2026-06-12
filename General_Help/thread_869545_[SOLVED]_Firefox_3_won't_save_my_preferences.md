---
title: "[SOLVED] Firefox 3 won't save my preferences"
date: 2008-07-24
forum: General Help
---

### Post by chubbtech on 2008-07-24
Hi, 

I don't know what went wrong but for the las few weeks, Firefox keeps starting as if it was first time...looking deeper I also found out it won't save any of my preferences.  This may not be ubuntu related but I can't seem to get passed the anti-bot on firefox's forum

thanx in any case

---

### Post by tamoneya on 2008-07-24
what is the output of ```
ls -l ~/.mozilla/
```
It may just be a permissions issue.

This is my output:```
tamoneya@tamoneyat61:~$ ls -l .mozilla/
total 8
drwx------ 3 tamoneya tamoneya 4096 2008-06-18 14:09 extensions
drwx------ 3 tamoneya tamoneya 4096 2008-05-17 21:37 firefox

```

---

### Post by aysiu on 2008-07-24
You probably ran *sudo -s* or ran a graphical application with *sudo* instead of *gksudo*.

Close Firefox.

In [the terminal](http://www.psychocats.net/ubuntu/terminal), try the command: ```
sudo chown -R *username:username* /home/*username*/.mozilla
``` where *username* is your actual username.

Then restart Firefox.

---

### Post by chubbtech on 2008-07-24
Great!!!  worked just fine...in fact the trouble started when I sudo Nautilus and my whole desktop got switched...is there another way to manage files as root...I used to have a file manager super user mode in fedora?

---

### Post by tamoneya on 2008-07-24
you can still run nautilus as root just use gksudo instead of sudo like this:```
gksudo nautilus
```

---

### Post by aysiu on 2008-07-25
*sudo nautilus* is a no-no and may have been what caused your Firefox problem.

*gksudo nautilus* is the way to go.

Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Tankerdog2002 on 2009-08-15
AYSIU!!!


Thank you. I hosed my Firefox with sudo nautilus.

I was going crazy trying to figure out why my Firefox went to Hell in a handbasket.

All is fine now. Life is good.


Tank

---

