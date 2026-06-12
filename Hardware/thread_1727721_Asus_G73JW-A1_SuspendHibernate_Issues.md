---
title: "Asus G73JW-A1: Suspend/Hibernate Issues"
date: 2011-04-12
forum: Hardware
---

### Post by Aang_Aero on 2011-04-12
[SIZE=2]_System Info:_[/SIZE]


[LIST]
[*]Asus G73JW-A1
[*]Ubuntu 10.04.02 - 64-bit
[*]Kernel - Linux 2.6.32-31-generic (x86_64)
[*]BIOS Setting: USB3.0 Controller Switch = EHCI Mode
[/LIST]
**_[SIZE=2]Issue:[/SIZE]_**

System will not Suspend or Hibernate.

Upon issuing the command to _Suspend_, the screen goes blank (looks like suspend it is working) but then just pops up the box asking me for my username and password.

Upon issuing the command to _Hibernate_, the screen goes blank, and the screen displays this:
```
[ 1211.867583] pm_op(): usb_dev_freeze+0x0/0x20 returns -2
[ 1211.867588] PM: Device usb3 failed to freeze: error -2
```(I have NO usb devices attached)

Once again the username and password pop-up box is displayed.


_[SIZE=2]Question:[/SIZE]_

Anyone else experiencing this issue (on there Asus G73JW-A1 or other laptop) ?

Anyone have any tips on how to solve this?


Thanks in advance for any tips you can provide :)


**_[COLOR=Blue]Update (04/17/2011):[/COLOR]_**

_In my BIOS_, I changed **USB3.0 Controller Switch** to **XHCI** **Mode** then tried this:

1.  Create the file below:
```
gksudo gedit /etc/pm/config.d/unload_module
```2.  Added this to the first line, save file, and reset:
```
SUSPEND_MODULES="xhci"
```After performing the steps above I could Suspend, but the computer _would **not** wake up_.  I had to power off and restart :(  But I got half-way there :/

Also, I set **USB3.0 Controller Switch** back to **EHCI** **Mode**, and tried this setting for the **unload_module** file above:
```
SUSPEND_MODULES="ehci"
```However, this had _no affect_ :(

---

### Post by Aang_Aero on 2011-04-22
Found a solution that worked, I can now hybernate/suspend! :D

Click on the link to the post below.

Follow the steps listed in post **#7** & **#8**

[http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

---

