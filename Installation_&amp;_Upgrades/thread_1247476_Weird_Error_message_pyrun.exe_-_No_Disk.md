---
title: "Weird Error message: pyrun.exe - No Disk"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by brianfactors on 2009-08-23
I am using wubi on my windows desktop. When I try to run it, I get this error:

> pyrun.exe - No Disk

There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR3There are three buttons - Cancel, Try Again, and Continue. No matter which one I click, the message reappears. I have to go to the Task Manager and shut down pyrun.exe, click one of the buttons, and then it will FINALLY go away.

I assume this is a python problem? I'm going to try a restart to see what happens. But this is a major error nonetheless.

The weirdest thing, though, is that I have used Wubi successfully before on this computer.:???:

---

### Post by atomik_wolf on 2009-08-23
Totally ran into the same problem and don't have a clue as to why this is happening. At first I thought it might be because I was using PowerISO with some virtual drives, but disabling that was no help. Anyone have a clue?

---

### Post by mbhmbh on 2009-09-13
Yes, exactly the same problem for me and also on a machine where I had previously used Wubi to install Ubuntu 9.04. Needed to reinstall because I tried to upgrade to 9.10 and resulting installation never let me log in, so I deleted it and was going to start again, but currently no dice.

---

### Post by enobrev on 2009-10-31
I had this same issue and got it resolved following this thread:
[http://ubuntuforums.org/showthread.php?p=8208814](http://ubuntuforums.org/showthread.php?p=8208814)

Which basically just says to disconnect external drives / devices (in my case was an ipod and android phone).

---

### Post by da5id on 2010-09-17
One would think that installation errors would get high priority. We are passing 12 months on this one and no real solution -- just a few anecdotal "this worked for me." I have been unable to install with keyboard, trackball, and native monitor resolution for at least the last four versions of Ubuntu. New PC coming about the same time as version 10.10. It will have 100 GB partition for an Ubuntu dual boot-- any takers on a bet as to whether or not Lucid Lynx will install?

---

### Post by lisati on 2010-09-17
This is a known issue. See here: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by Muaddib67 on 2011-01-04
Ok, I downloaded 10.10 in both 32 and 64 versions. I burned the 64 bit version first, and everything went fine, the menu from the disc even opened up when Imageburn was done verifying. The problem I had was with the 32 bit version, the old pyrun.exe No Disk error showed up on it. Yes, I have an external drive, but I don't want to have to remove it every time I want to use the 32 bit version of ubuntu. I would think after over a year(and a new version), this would have gotten fixed. A good starting place to look would be to see the difference between the 32 and 64 bit versions, since the 64 bit does NOT throw up this error with my external drive connected.

---

### Post by cloube on 2011-01-16
try to remove any usb or drive connected to USB port or disable the smart card reader. it work for me. :)

---

### Post by hakrev on 2011-07-22
The solution is very simple, the error doesn't stay forever, simply click the continue button about 100ish or more times in a row (u may have to do this a few times during the install) then eventually the wubi installer will pop up and let you proceed as usual. Don't give up just keep pressing that continue button like crazy and you'll get there.

---

### Post by Carl Adolfson on 2011-11-08
I just hit cancel until it opened. All it is doing is going through the devices until it finds it.
:D

---

### Post by oreilly123 on 2011-11-11
This would be a great problem to get fixed :P

I wanted to check out Ubuntu again. It's been several years since I last used it as my desktop. I got really excited when I read the download/install information and saw how painless it was described as being! Then... a seemingly endless and loud error message that you have to kill using Task Manager!

Definitely not a good introduction to Ubuntu. If fact, that's about as bad of a handshake as you could think of! Ubuntu is very, very awesome and so many people put a lot of hard work and heart into it. It's a shame to even have it get introduced to new users like this! Most true noobs to Ubuntu will not go any further than this installation error. They will delete the file they downloaded and go back to playing WoW on their windoze box!

---

### Post by lisati on 2011-11-11
When I encountered the error message a couple of years back I discovered that "safely removing" the card reader did the job a lot quicker than repeatedly clicking on "Cancel".....

---

### Post by trevorus on 2011-11-20
I had the same issue on my laptop. The SD card slot shows as an empty drive, which you can't easily remove, so I just popped a card in there, no problems.

---

### Post by kewlzero on 2013-04-18
**I had the same problem.  Not sure if works for everyone but i tested this on 3 computers and 2 laptops and it worked for me.  -- The trick is to wait about 10 minutes, then continuously click the Try Again, it will eventually load the "Are you sure you want to uninstall ubuntu?"  I clicked on it about 20 times till it worked. **

---

