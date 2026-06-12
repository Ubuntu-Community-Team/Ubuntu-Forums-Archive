---
title: "screenblank IBM x40"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by joshpelkey on 2006-06-01
Hello all!

I've just upgraded to Dapper, and I'm very pleased with how everything works on my laptop [IBM X40].  I am having trouble with ACPI though.  My Fn-F3 button (screenblank) doesn't work unless I change the screenblank.sh file to simply read xscreensaver-command -activate.  Whenver I reboot I also have to restart acpid after I've logged in.  I've tried reinstalling acpi-support and acpid but no luck.  Any suggestions??  Thanks.


Josh

---

### Post by joshpelkey on 2006-06-03
Anybody else with an X40 have this problem?  Anybody with a Thinkpad?

Josh

---

### Post by steve k on 2006-06-04
hey,

i have an x40 that i'm considering upgrading from breezy to dapper this week (monday possibly, i have to find the time to back everything up first...) i know that in breezy everything is hunky dory, the laptop suspends, the screen blanks,  etc.  so i would hope i can get the same deal out of dapper.

i'll let you know if my screen blank button works when i'm done!

---

### Post by linuxworld on 2006-06-04
[QUOTE=joshpelkey]Anybody else with an X40 have this problem?  Anybody with a Thinkpad?

Josh[/QUOTE]
My Fn-F3 button works perfect here.
This is what /var/log/acpid reports when I push Fn-F3

[Sun Jun  4 17:56:21 2006] executing action "/etc/acpi/thinkpad-lockorbattery.sh"
[Sun Jun  4 17:56:21 2006] BEGIN HANDLER MESSAGES
[Sun Jun  4 17:56:21 2006] END HANDLER MESSAGES
[Sun Jun  4 17:56:21 2006] action exited with status 0
[Sun Jun  4 17:56:21 2006] completed event "ibm/hotkey HKEY 00000080 00001003"

---

### Post by joshpelkey on 2006-06-04
/var/log/acpid is showing this:

[Sun Jun  4 13:27:03 2006] received event "ibm/hotkey HKEY 00000080 0001003"
[Sun Jun  4 13:27:03 2006] notifying client 4056[119:119]
[Sun Jun  4 13:27:03 2006] executing action "/etc/acpi/thinkpad-lockorbattery.sh"
[Sun Jun  4 13:27:03 2006] BEGIN HANDLER MESSAGES
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
xset:  unable to open display ":0"
[Sun Jun  4 13:27:04 2006] END HANDLER MESSAGES
[Sun Jun  4 13:27:04 2006] action exited with status 0
[Sun Jun  4 13:27:04 2006] completed event "ibm/hotkey HKEY 00000080 00001003"

Obviously I got something setup wrong.  Suggestions?

Josh

---

### Post by steve k on 2006-06-07
no suggestions of my own yet, but my screen blank totally works.

however, i used to have my open/close lid set to put the computer to sleep, this is a fairly simple change in breezy yet here it doesn't seem to work at all.  when i tell the acpi to attach sleep.sh to the lid event it just locks the screen and brings up the screen saver (presumably, that's what it looks like it did when i open it again).

on the lighter side: is you SD card slot working? mine is! awesome!

---

### Post by joshpelkey on 2006-06-07
The same thing happened to me with my lid close function.  I downloaded gnome-power-manager from the repos and set a setting in its prefrences to suspend on lid close and now it works.

Haven't tested the SD card reader yet (i thought it wasn't going to work) but I'm pumped to hear yours does!

---

### Post by steve k on 2006-06-07
well,
although it probably deserves it's own thread, the SD card reader kind of works.

if you take the card out and put it (or another for that matter back in) it doesn't re-appear on the desktop.  

i haven't looked into it much farther (i haven't bothered to look at the dmesg output or anything) but it only seems to put the SD card back on the desktop if i reboot the computer (maybe it also works if i restart the session, not sure)

so yeah, it kind of works, which is better than NOT working.  by miles.

---

### Post by arthur on 2006-06-07
Hope you don't mind my intruding here with a different question altogether: _does Dapper work on your X40s as well as Breezy?_
I am worried about losing suspend/hibernate ...

---

### Post by joshpelkey on 2006-06-07
> Hope you don't mind my intruding here with a different question altogether: does Dapper work on your X40s as well as Breezy?
I am worried about losing suspend/hibernate ...

Yes siree.  I think Dapper works better for the X40 (Especially the networking aspect).  I had trouble in Breezy connecting to the internet after a suspend, but now it works great.  I recommend the upgrade.  After I installed gnome-power-manager my suspend/hibernate worked just like before.

Josh

---

### Post by arthur on 2006-06-07
I take good note of that :D 
Cheers!

---

### Post by alexludwigklein on 2007-10-04
> **joshpelkey said:**
> /var/log/acpid is showing this:

[Sun Jun  4 13:27:03 2006] received event "ibm/hotkey HKEY 00000080 0001003"
[Sun Jun  4 13:27:03 2006] notifying client 4056[119:119]
[Sun Jun  4 13:27:03 2006] executing action "/etc/acpi/thinkpad-lockorbattery.sh"
[Sun Jun  4 13:27:03 2006] BEGIN HANDLER MESSAGES
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
xset:  unable to open display ":0"
[Sun Jun  4 13:27:04 2006] END HANDLER MESSAGES
[Sun Jun  4 13:27:04 2006] action exited with status 0
[Sun Jun  4 13:27:04 2006] completed event "ibm/hotkey HKEY 00000080 00001003"

Obviously I got something setup wrong.  Suggestions?

Josh
I had the same problem today and I don't know why. But I found this:
[http://www.linuxquestions.org/questions/showthread.php?threadid=331779](http://www.linuxquestions.org/questions/showthread.php?threadid=331779)

They solved a similar problem connected with:
```
Xlib: connection to ":0.0" refused by server
```
by
```

xhost local:root
```

This solved my problem as well.

Kind regards

Alexander

---

