---
title: "How do I check the status of the battery on 11.10?"
date: 2011-11-26
forum: Hardware
---

### Post by supercheetah on 2011-11-26
It seems that I lost the battery indicator/tray icon in 11.10.

What can I use now to check the status of the batter?  Is there a new battery indicator for Oneiric?

---

### Post by BC59 on 2011-11-26
Look here

[http://www.webupd8.org/2010/05/battery-status-01-released-improved.html](http://www.webupd8.org/2010/05/battery-status-01-released-improved.html)

---

### Post by supercheetah on 2011-11-26
Yeah, I tried that one, but there doesn't seem to be a package for Oneiric in the PPA.  When I tried to install the version for Natty, it wasn't installable (missing dependency of python-gnomeapplet).

---

### Post by Redblade20XX on 2011-11-26
If you can stand a cml solution until you get a gui solution,

install acpi
```
 sudo apt-get install acpi 
```the type in the terminal either

```
 acpi -b
``````
acpi -V 
```Hopefully this helps! :)

- Red

---

### Post by supercheetah on 2011-11-26
Yeah, I know about that already.  I was just hoping there would be something for an indicator applet.

---

### Post by supercheetah on 2011-11-28
Found answers here:

[http://askubuntu.com/questions/68445/no-battery-status-icon](http://askubuntu.com/questions/68445/no-battery-status-icon)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/801180/comments/30](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/801180/comments/30)

---

