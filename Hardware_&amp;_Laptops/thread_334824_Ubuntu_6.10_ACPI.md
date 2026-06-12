---
title: "Ubuntu 6.10 ACPI"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by tempest130 on 2007-01-09
Hi everybody,

I've got Ubuntu 6.10 running on my Dell 700m. I can suspend the laptop by pressing FN-F2 or from the task bar.  Resume works good to.  However when I the problem is when I close the lid and reopen.  It would appear that if I close my laptop to suspend the computer and re-open the lid to resume, everything works fine.  BUT if I try to close the lid again to suspend, it only blanks the screen and not suspend the computer.  FN-F2 will suspend the computer but closing the lid will not.  Maybe it's in the acpi config files?  I would appericate any help in fixing this problem.  Thanks.

Temp

---

### Post by flossgeek on 2007-01-09
Goto "System>Preferences>Power Management". In the power management preferences dialogue box on the "Running on AC" and "Running on Battery" tabs *choose* the "suspend" action for "when laptop lid is closed".

---

### Post by tempest130 on 2007-01-09
Thanks for the reply.  That's not the problem <smile>  I am aware of those settings.  The problem is when I close my lid again (ie. a second time) the screen only goes blank and not into suspend mode.  It's like I can only suspend the computer one time via closing the lid.  I was looking a command line solution <smile>

Temp

---

### Post by markofealing on 2007-01-09
Same problem with Kubuntu 6.10 on a Dell Latitude c640, using ACPI. 

Suspend key (in my case Fn+ESC) works fine, Shutting the lid (which is configure to "Do Nothing" according to Power Manager 0.42) blanks the screen and shuts down XWindows which is very considerate! When I open the lid XWindows (in my case KDE GUI) restarts (same as doing startx). Which means that the laptop is draining the battery.

Also, I not convinced that the laptops fans (C640 has 2) are being driven correctly unless you run GKrellm with the Dell fan plug-in. Without this application running only the CPU fan runs and at a constant speed. However Centrio, CPU speed seems to be managed correctly.

---

### Post by markofealing on 2007-01-09
I've just dug up some more info in [http://kubuntuforums.net/forums/index.php?topic=10464.0](http://kubuntuforums.net/forums/index.php?topic=10464.0)

The power manager actually runs scripts stored in /usr/share/hal/scripts/

---

