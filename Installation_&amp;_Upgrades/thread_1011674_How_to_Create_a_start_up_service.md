---
title: "How to Create a start up service?"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by sai438 on 2008-12-15
Hi,
   I'm a newbie,i wanted to create a service for STAF (Software Testing Automation Framework) which will start at the time of bootup. How can i create that. I actually created service of STAF in fedora which will start while booting. I want to do that for Ubuntu as i migrated to Ubuntu from fedora. can any one please help me out of this??


Thanks in advance,
sairam

---

### Post by xjcannonx on 2008-12-15
Well, i don't really know about STAF but you can have programs you want to start by adding them in session preferences by going to System (on the gnome panel) and then go to preferences-->sessions, and add a new program to start up

---

### Post by sai438 on 2008-12-15
> **xjcannonx said:**
> Well, i don't really know about STAF but you can have programs you want to start by adding them in session preferences by going to System (on the gnome panel) and then go to preferences-->sessions, and add a new program to start up
thanks for the reply, but i'm having minimal image which doesn't have GUI. how can i do that in console mode?

---

### Post by xjcannonx on 2008-12-15
well i think you could edit the /etc/rc.local file. It loads at bootup and anything added to it should start as well. cd into /etc and edit the file by ```
sudo nano rc.local
``` edit the file before the "exit 0" and save it by ctrl-x and y to save

---

### Post by sai438 on 2008-12-15
Actually i want to start it as service, not as a part of rc.local file. If i want to restart the service without restarting the machine, its not possible right? I guess you understood my problem.

--sairam

---

### Post by xjcannonx on 2008-12-15
ok well see if you can edit your autostart file .config/autostart and create a file in there ```
nano filename
``` and then put something alone these lines in the file```
[Desktop Entry]
Encoding=UTF-8
Version=Beta2
Type=Application
Name=YOURFILENAME
Comment=
Exec=[COLOR="Blue"]firefox[/COLOR]
StartupNotify=false
Terminal=false
Hidden=false
```I am not sure if all this is necessary or if it will work or not, but hopefully it does...

---

### Post by sai438 on 2008-12-15
Thanks for the reply, but i did it another way. I created a soft link of the startup script at /etc/init.d directory to /etc/rcS.d directory as S98stafd and rebooted my machine and it worked.

---

