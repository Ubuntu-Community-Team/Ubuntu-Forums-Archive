---
title: "Left click stopped working after upgrading to 10.10 (64bit)"
date: 2010-10-10
forum: Hardware
---

### Post by artin1982 on 2010-10-10
Hello ,
After upgrading to 10.10 (64bit) my left click stopped working ...

Mouse : A4tech X7

but its working on my laptop which has 10.04 ...
and surprisely it just has problem with X7 ! when I am using A4tech X5 ( which I am using it on my laptop ) its working without any problem ...

can someone help me to find the problem ?

Thanks

---

### Post by Dark_Stang on 2010-10-10
Load up recovery mode. Navigate to your home folder. Rename the .dbus folder to .dbus.old. Restart and log back in, see if that fixes the problem. I had similar problems with some peripherals when going from 10.04 to 10.10 and that fixed the issue.

---

### Post by artin1982 on 2010-10-10
Thanks but it didn't help :\

I forgot to say left click is working on login window ! but when GDM loads completly its stopping ... and when I am restarting GDM the left click will not work on login window ! mean its working only on Reboot and when login window loads for the first time ...

---

### Post by Dark_Stang on 2010-10-10
If you make a new user account does it work in that?

---

### Post by artin1982 on 2010-10-10
Yes ! its working with new user !

---

### Post by matera.ttp on 2010-10-10
I have the same issue. My mouse A4tech X7 does not work anymore. It works on login screen and does not work after log in.

---

### Post by skfd on 2010-10-10
Same here. Anyone filled bug report yet?
PS: God, that forum is not keyboard friendly.

---

### Post by Dark_Stang on 2010-10-10
> **artin1982 said:**
> Yes ! its working with new user !
So it must be some old configuration files in your user account. I'd start renaming hidden folders one by one to try to narrow it down. On my it was .dbus, on yours who knows.

---

### Post by DisDis on 2010-10-11
Solution:
[https://bugs.launchpad.net/udev/+bug/637208/comments/6](https://bugs.launchpad.net/udev/+bug/637208/comments/6)

---

### Post by artin1982 on 2010-10-11
> **DisDis said:**
> Solution:
[https://bugs.launchpad.net/udev/+bug/637208/comments/6](https://bugs.launchpad.net/udev/+bug/637208/comments/6)

Thanks ! now its working .... :]

---

