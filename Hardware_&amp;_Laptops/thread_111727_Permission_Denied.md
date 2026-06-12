---
title: "Permission Denied"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by jackdirt on 2006-01-02
So i amde some changes to the xorg.conf file and I forgot to specify the monitor in the screen section so I did nano /etc/X11/xorg.conf

fixed then did ctrl+o hit enter 

then got [COLOR="Red"][ Error Writing /etc/X11/xorg.conf: Permission Denied][/COLOR]

please help i was also a dumb ass and forgot to back it up and I cant use teh command reboot says i need super user permissions.

Thank you greatly in advance!

---

### Post by mazelado on 2006-01-02
Did you type 'nano /etc/X11/xorg.conf' or 'sudo nano /etc/X11/xorg.conf'? If you didn't use sudo, you won't have write permission.

---

### Post by jackdirt on 2006-01-02
ha ha sorry I am still a n00b  worked brilliant!!

---

