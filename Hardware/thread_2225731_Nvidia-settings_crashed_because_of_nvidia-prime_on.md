---
title: "Nvidia-settings crashed because of nvidia-prime on 14.04"
date: 2014-05-22
forum: Hardware
---

### Post by 0xddr on 2014-05-22
I am trying to setup nvidia-prime on my laptop. I have added a xorg-edgers ppa, installed the newest nvidia drivers (nvidia-337), nvidia-prime. But it seems it doesn't work - while running nvidia-settings I get this:

```
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no
Segmentation fault (core dumped)

```

My card: GeForce GT 640M LE.

---

### Post by jeremy31 on 2014-05-23
What does lsmod report

---

### Post by 0xddr on 2014-05-23
[http://pastebin.com/SYa5tgrs](http://pastebin.com/SYa5tgrs) 

Is nouveau in use, instead of nvidia driver?

EDIT: 
I have blacklisted nouveau. Nvidia-settings is able to start, but still I got this on a console:
```
** Message: PRIME: Requires offloading
** Message: PRIME: is it supported? yes

ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at either
       /usr/share/nvidia/nvidia-application-profiles-334.21-key-documentation or /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be preopulated or validated, and will not be listed in the help text. Please see
       the README for possible values and descriptions.
```

Moreover, I am no able to use the second display (previously it worked) .

---

