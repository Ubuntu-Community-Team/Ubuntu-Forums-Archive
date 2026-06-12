---
title: "Ubuntu on external USB drive"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by jperez on 2009-09-25
Hi all,

I haven't posted here in a while, but everything, for the most part, has been working out on my end with (K)ubuntu...except the graphics...

Anyway, my girlfriend wants to use Linux on an external USB hard drive, but we've tried everything so far and nothing has worked.  The drive is just a simple laptop IDE drive in an enclosure and the laptop she's connecting it to can boot USB devices.  Now, the thing we want to do is install Ubuntu onto the drive and get it to boot because she got it to install on the drive, but now it's not booting.

I'm thinking maybe the drive needs to be formatted to have a Linux boot partition on it, but I don't really know.  Any help would be appreciated.  If you need anymore info to help out, please ask and I'll post more.

EDIT:
This is the error she got.  Props to her for typing everything on the screen she saw verbatim:

```
Boot from (hd0,4) ext3   10081609-62c8-4ace-84f2-7ba124b0aa78
Starting up ...
[    0.348001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Loading, please wait...
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
	- Check rootdelay= (did the system wait long enough?)
	- Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid.10081609-62c8-4ace-84f2-7ba124b0aa78 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Jesse~

---

### Post by earthpigg on 2009-09-25
hi,

props indeed to your girlfriend. tell her she gets props from the nerds of ubuntuforums.org, as well :D

i have never encountered this exact problem.

in situations like this, the very first error message is usually the cause of all subsequent error messages and where the focus of effort should be.

in this case:
```

Starting up ...
[    0.348001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
```

well, lets see if we can find someone else with the ***exact same problem*** and see how they went about solving it.

the ubuntuforums.org thread below is the first result on a google search ( [http://www.google.com/search?q=timer+not+connected+to+IO-APIC](http://www.google.com/search?q=timer+not+connected+to+IO-APIC) ), meaning that this link has the most other websites that link to it, meaning a lot of people think it's good stuff. 

take a look here:
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

the first solution i would try in your situation is this, since it is the easiest, if you have this option in your BIOS:

> I just encountered this problem, and solved it by going into BIOS and disabling IOAPIC. This does turn off apic which may be a problem for some people.

if that solution does not work, try the one suggested by the poster "Roobert".

let us know how it works out, please.

---

### Post by jperez on 2009-09-25
Nope, neither method worked as she doesn't have the option to disable IO-APIC on her laptop.  She also tried Robert's method and it came up with the fatal errors and just didn't go past it.  It really is an issue I find myself racking my brain on.  I hate issues at boot up. x_x

Jesse~

---

### Post by BulletTheBlueU2 on 2009-09-25
[COLOR=DarkRed]Hi there!~

Thank you for trying to help us out. Unfortunately since my laptop does not have the option available, I could not turn off the IO-APIC. 

I did figure out what was the problem though. I had downloaded the Ubuntu iso and put it on my USB Flash Drive to use the Live Session to try out Ubuntu before I actually installed.

After I installed onto my External HDD, I booted back up and the errors continued no matter what I tried. Finally I had a lightbulb go off and I unplugged my USB Flash Drive from my laptop so it only booted from the External HDD. Surprisingly that worked!

I guess the problem was that it was trying to read both drives and ended up messing itself up.

Still, thank you for your help!~
[/COLOR]

---

