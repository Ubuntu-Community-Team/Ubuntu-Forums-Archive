---
title: "stop blank screen on intel 945"
date: 2011-10-01
forum: Hardware
---

### Post by th00ht on 2011-10-01
How do I stop screen blanking on a intel 945gmchipset?

---

### Post by Toz on 2011-10-07
If you are referring to the monitor power-saving feature, then see: [http://ubuntuforums.org/showpost.php?p=11304086&postcount=3]("http://ubuntuforums.org/showpost.php?p=11304086&postcount=3")

---

### Post by th00ht on 2011-10-09
It is not the monitor power saving (in fact it is a TV) but 'the computer'. Not sure if this is the os, the driver, adapter. I've checked bios settings and switch all power saving off. still the screen blanks if I don't use the keyboard or mouse.

---

### Post by Toz on 2011-10-09
Try typing, in a terminal window, the following command:
```
xset -dpms
```

Does it disable the screen blanking?

---

### Post by th00ht on 2011-10-12
> **Toz said:**
> Try typing, in a terminal window, the following command:
```
xset -dpms
```

Does it disable the screen blanking?

No it doesn't. 

How do I stop the screen blanking when no mouse or keyboard input?

---

### Post by dentaku65 on 2011-12-27
Hi,

edit/create xorg.conf file
```
sudo gedit /etc/X11/xorg.conf
```
and place this section
> Section "ServerFlags"
	Option "BlankTime" "0"
	Option "StandbyTime" "0"
	Option "SuspendTime" "0"
	Option "OffTime" "0"
	Option "DontZap" "false"
EndSection

Reboot.

---

