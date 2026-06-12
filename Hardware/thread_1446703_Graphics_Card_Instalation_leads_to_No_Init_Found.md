---
title: "Graphics Card Instalation leads to No Init Found"
date: 2010-04-04
forum: Hardware
---

### Post by mrecord on 2010-04-04
Hello. 

I am trying to install a [GeForce 2500 PCI]("http://www.amazon.com/PNY-Geforce-FX5200-256MB-Graphics/dp/B000F5IE9Y") graphics card into an [HP Pavilion a1209n]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00551508&lc=en&dlc=&cc=us&product=1162597").
The card goes in just fine (properly seated with a satisfying click).

When I boot the system - Ubuntu 9.10 - I get an error: 
[INDENT] Taget file system doesn't have /sbin/init
no init found, Try passing init=bootargBusybox v1.10.2 (ubuntu 1:1.10.2-1 ubuntu7) built in shell (ash)  Enter 'help' for a list of built in commands
[/INDENT] The same thing happens when I try to run a live CD.


Removing the graphics card and using the built-in VGA slot makes the problem go away.


In the BIOS/Setup Menu, I tried changing the "Primary Video Adapter" from Onboard to PCI and neither setting seems to make a difference.


Help!

---

### Post by a.walker on 2010-04-04
I use that exact same video card in my desktop computer. It works great under 9.10 and 10.04 without any tweaks. Did you buy the card new? Have you tested to see if it works under another OS?

---

### Post by mrecord on 2010-04-04
Yeah, it's a brand new graphics card. 
I took your suggestion and installed the graphics card in an old Dell. Started it up and everything worked fine - booting to a hard drive and to a live CD. I also swapped the Hard Drive from the HP to the Dell and that also worked. 

So the hard drive is good, and the graphics card is also good.

Back on the HP (the problem machine) I'm getting the same error as before.

Now... when I change the BIOS/Setup option "Primary Video Adapter" from PCI to Onboard the system boots up with no problems.

How can a video card keep the system from finding the startup disk?

---

### Post by mrecord on 2010-04-06
Day 4. 

I installed a hard drive with Windows XP and updated the BIOS to the newest version (3.0.9).
After a restart, Windows XP booted up just fine. 
Then I tried the Live CD and got the error: 
[INDENT]*unable to find a medium containing a live filesystem.*
[/INDENT]Then tried a hard drive w/ Ubuntu 9.10 and got the same error as before.
[INDENT]*no init found*...
[/INDENT]
So to recap: 
Ubuntu cannot be found (hard drive or Live CD) if the GeForce 2500 PCI card is being used.
Using the same settings, Windows XP will work properly. 


Please help.

---

### Post by mrecord on 2010-04-07
Day 5. 

Trying Super Grub Disk.
I'm not sure if this is going to help, but I can't figure out what else to do.

Anyway. I used Unetbootin to install Super Grub to a USB drive. 
And when I try to load from that I get the error message: 
[INDENT][I]Could not find ramdisk image
[/I][/INDENT]

Frustrated.

---

### Post by mrecord on 2010-04-08
In a nutshell: 
Using the Onboard graphics BIOS setting == no problem
Changing to PCI in the BIOS == Linux can't be found (on HD or CD)

Windows XP - CD and Hard Drive - both work fine under PCI.


I have no idea where to go from here, except back to using Windows... and I really don't want to do that.

---

### Post by mrecord on 2010-04-08
Found another post about the same issue.
[URL="http://wwww.ubuntuforums.org/showthread.php?t=1144043&highlight=pci+no+init"]
**Hardware conflict - GeForce FX 5200 INcompatible**[/URL]

Trying their suggested fix. 
I hope this will get fixed some day...

---

