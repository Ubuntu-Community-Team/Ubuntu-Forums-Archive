---
title: "No signal during boot / shutdown"
date: 2008-08-04
forum: General Help
---

### Post by morglum82 on 2008-08-04
Hi everyone,

    On it's first day my Hardy Heron worked fine.  Now I'm not sure what I did but here's my issue:

During boot up I get no signal at all before the NVIDIA logo and the ubuntu login screen.
During shutdown I get no signal as soon as I press "shutdown".


During bootup I dont even see my video card's and motherboard's info.  Nothing at all.  This is very problematic considering I have a dual boot and I need to access WinXp..

any idea?
I already tried changing specs in usplash.. to no avail.

Computere is a Dell Insprion 530 with a 8600GTS

Thanks

---

### Post by morglum82 on 2008-08-08
... anyone?

---

### Post by Mgiacchetti on 2008-08-08
are you saying you dont see post?

---

### Post by d111 on 2008-08-08
I have a similar problem. I loose signal after the grub screen and it does not come back until the login screen.

This all started when I installed a new 8600GT video card and used Envy to install the driver.

---

### Post by morglum82 on 2008-08-13
> **Mgiacchetti said:**
> are you saying you dont see post?


Exactly.
No POST.  Nothing at all (no signal) until the NVIDIA screen appears berfore the hardy heron logon screen

---

### Post by morglum82 on 2008-08-21
Hi everyone.

Just noticed I wasnt alone in this :
[http://ubuntuforums.org/showthread.php?t=67605](http://ubuntuforums.org/showthread.php?t=67605)


Basically I get no signal during POST.  No signal at grub menu... but if I wait long enough I will see the NVIDIA logo then the Hardy Heron logon screen and everything will be fine.

When I go to the virtual console (ctrl alt f1) or shutdown, I lose the signal.

---

### Post by WWSmith36 on 2008-09-27
I´m having the same problem as with older machine hooked up to a wide screen LCD.  No signal from grub to gdm.  I am assume that something is out of range.  So instead of looking at a blank screen I removed the kernel boot options ¨quiet splash¨

Would prefer to fix the cause of this rather than doing this workaround.

---

