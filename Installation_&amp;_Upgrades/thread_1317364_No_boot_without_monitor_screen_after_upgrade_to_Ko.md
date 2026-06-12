---
title: "No boot without monitor screen after upgrade to Koala..."
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by FizzBuntu on 2009-11-06
Hi there,
I was on Ubuntu 9.04.
The computer runs without a monitor screen because I use it thru NX Nomachine.
After upgrading to Ubuntu 9.10, the computer seems to freeze during boot and won't actually work when disconnected from a screen. If I connect a screen afterward, it's blank (well black in fact) and the keyboard is not responding).
If I boot the computer with a monitor screen connected, it boots normally and I can remove the monitor screen and work normally (that is without a monitor screen on the computer and using the computer thru Nomachine)

How can this be solve.
It must have something to do with screen detection at some point but what has been change from the last version ?


Any clues ?

thx

---

### Post by fcappy on 2009-11-07
Hey man, it's my problem too, I use koala for a Nas server, with VNC local connection over the lan, but if a monitor isn't connected, gdm cannot start...so everything is blocked, samba upnp, etc...

can someone explain howto resolve the problem please?

---

### Post by FizzBuntu on 2009-11-07
mmhm good to know that I'm not the only one having this problem.
We'll just have to search some more and wait some till we come up or somebody comes up with a solution...

---

### Post by ghthor on 2009-11-07
Yes I'm on the Case, I mean as far as I"M concerned I don't mind having a 5$ thriftstore monitor for it just incase I have to reboot my headless machine.  This is quite ironic, I never thought this was going to be an issue with a linux headless machine, I started the Project today so lets see what we can do about this, I really need this machine for my webserver/internet Gateway and the desk it is on doesn't really have room for the 5$ thriftstore CRT monitor, and I don't really want to drag it out everytime I need to restart the machine.

Found this, I"ll break out a soldiering iron and try it tomorrow

[http://www.motherboardpoint.com/info-sd-11-wont-boot-without-monitor-t55993.html](http://www.motherboardpoint.com/info-sd-11-wont-boot-without-monitor-t55993.html)

To drunk and tired to try it tonight

---

### Post by fcappy on 2009-11-08
sorry, it could be a good idea but I'm searching some software solution, disabling DDC from X server could be...but in karmic xorg it's no more used...:(

However thanks for your answer!

---

### Post by anrke on 2009-11-09
Since the update, I too am experiencing this same issue.

With the monitor plugged in the machine boots... without a monitor (my standard format of operation, I connect to it via VNC or SSH from my day to day pc) it will not boot.  I had a similar problem on an earlier version, which I *think* was resolved by using a -vesa flag in xorg.conf.

This is my xorg.conf to date.  I can confirm that it has not changed since the upgrade, thanks to the upgrade making it's own backup of these files :)  (unless the backup is buggy!)

The pc is an ex IBM P4 office workstation.  So not-too-flashy onboard video is in use.

Any help in resolving this new problem I am getting is greatly appreciated!

```
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
Option "NoDDCValue" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 31.5-48.5
VertRefresh 50-70
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

```

---

### Post by aigibson on 2009-11-10
I also had this problem running a headless server.  Created an xorg.conf using information in this link and problem solved!!

[http://ohioloco.ubuntuforums.org/showthread.php?t=1223504](http://ohioloco.ubuntuforums.org/showthread.php?t=1223504)

I don't know if there is a better way to achieve this but I can now put the monitor back on the shelf.

---

### Post by anrke on 2009-11-11
> **aigibson said:**
> I also had this problem running a headless server.  Created an xorg.conf using information in this link and problem solved!!

[http://ohioloco.ubuntuforums.org/showthread.php?t=1223504](http://ohioloco.ubuntuforums.org/showthread.php?t=1223504)

I don't know if there is a better way to achieve this but I can now put the monitor back on the shelf.

Cheers.  As I mentioned above, changing my xorg.conf to my current (posted above) config fixed the issue for me previously.  I thought the key to that was the vesa driver selection, but I might be completely wrong there.

I'm not overly confident, because the link you posted and my xorg.conf are not too dissimilar, but I will give it a shot and see if I am (hopefully) wrong.

A very frustrating issue, when you need to re-arrange the office furniture every time I want to turn the server on.  During winter, it was a 24/7 machine, but now in summer I'd prefer to switch it off when not required.

---

### Post by FizzBuntu on 2009-11-18
Tried that, doesn't work for me...

Anybody would know how to disable the screen detection of ubuntu ?

---

### Post by FizzBuntu on 2009-11-22
up !!!

---

### Post by FizzBuntu on 2009-11-23
Finally fixed it with anrke's solution in xorg.conf
But I made a new file from scratch, didn't test how the video output looks like now, but it works fine with nx

thx

---

### Post by anrke on 2009-11-27
> **FizzBuntu said:**
> Finally fixed it with anrke's solution in xorg.conf
But I made a new file from scratch, didn't test how the video output looks like now, but it works fine with nx

thx

Glad you had some success!  I'm still stuck.. :icon_frown:

---

### Post by rajivceh on 2009-12-03
i m still stuck

---

### Post by scacinto on 2010-03-22
same problem here.  xorg.conf "fix" did not work for me either.  For those of you for whom the fix didn't work, what machines are you running Karmic on?

my machine: Compaq Presario 6000


Cheers,

S

---

### Post by scacinto on 2010-03-22
Also, are you using restricted video drivers?  I didn't install any on my machine.

---

### Post by notrump3 on 2010-04-29
Same problem here with an IBM P4 desktop.  Worked great in 9.04 but not anymore... Has anyone found the solution?

---

