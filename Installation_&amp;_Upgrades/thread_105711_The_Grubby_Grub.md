---
title: "The Grubby Grub"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by SpEcIeS on 2005-12-19
How does one add Windows 98 to grub, manually, if 98 is on a separate drive, which is    **/dev/hdd**? :confused: 

I have been playing around with this and the rebooting is starting to get to me. :rolleyes:

---

### Post by Sutekh on 2005-12-19
This is what's in GRUB's menu.lst for WinXP on my PC

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I reckon use that but change 
```
root       (hd0,0)
```
to
```
root       (hd3,0)
```

Does that sound reasonable?  I'm not 100%

What have you tried?

---

### Post by aysiu on 2005-12-19
I don't know. My Windows XP is on /dev/hda1, and this is my Grub entry for it: ```
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
``` So if Windows 98 is on /dev/hdd1, maybe it's... ```
title           Windows 98
root            (hd3,0)
savedefault
makeactive
chainloader     +1
``` I'm just guessing.

---

### Post by SpEcIeS on 2005-12-19
Thanks guys, but I guessed the same thing and still nothing? :confused:  I will double.. not quadruple check.. ;D

---

### Post by SpEcIeS on 2005-12-19
*Error: selected disk does not exist.*

Now, I manually added the *_(hd3)   /dev/hdd_* to the device.map, however is there a procedure to allow a software piece to create this?

This is my device.map:
[b](hd0)	/dev/hda
(hd1)	/dev/hdb
(hd3)   /dev/hdd[/b]

Also, this is the menu.lst command that is being used:
[b]title           Windows 98
root            (hd3,0)
savedefault
makeactive
chainloader     +1[/b]

Any ideas? :confused:

---

### Post by Sutekh on 2005-12-19
Argh, this is what you get when you post on a Windows PC

Here's my *real* menu.lst entry for WinXP

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
[b]map		(hd0) (hd1)
map		(hd1) (hd0)[/b]
chainloader	+1
```

Those bold lines are crucial to make Windows think that it is installed on the first disc.  It's actually on my second disc, but GRUB maps the second disc as the first and vice versa, tricking poor WinXP.

Try adding those two lines to our previous suggestions, but this time 
```
map         (hd0)(hd3)
map         (hd3)(hd0)
```

---

### Post by Sutekh on 2005-12-19
I also found this entry on the web for installing GRUB with Linux, Win98, and other OS (did some renumbering)

```
title Windows 98
hide (hd0,0)
unhide (hd3,0)
rootnoverify (hd3,0)
chainloader +1
makeactive
```
It looks like it hides the other partitions, and rootnoverify so it boots but doesn't mount that particular partition.

Also found this one too 
```
title Windows 98
map (hd0,0) (hd3,0)
map (hd3,0) (hd0,0)
rootnoverify (hd3,0)
chainloader +1
```

---

### Post by SpEcIeS on 2005-12-19
Ok..  thanks. ....  :D I will give them a whirl.

---

### Post by SpEcIeS on 2005-12-19
Unforturnatly both fail. This is the error message:

**Error 21: Selected disk does not exist.**

This is a tough one. :???:

---

### Post by SpEcIeS on 2005-12-19
[QUOTE=Sutekh]
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
[b]map		(hd0) (hd1)
map		(hd1) (hd0)[/b]
chainloader	+1
```
[/QUOTE]
Ok..  now it works... I changed the *device.map* to have **(hd2) /dev/hdd** and applied the above with the applicable changes. 

Thank-you very much for the help. :D

---

