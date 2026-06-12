---
title: "Partitioner fails every time at the same spot"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by diavolo770 on 2009-05-18
I have tried everything I can think of in order to get Ubuntu to install so here's my situation and where I'm stuck at now...

I downloaded Jaunty and attempted to run the install graphically but it would never get past the status bar (loading) screen and all I would get after about 5 minutes is flashing lights on my keyboard. So, I downloaded the "alternate" Jaunty disc and attempted to install that way. I can get to the partitioner but no matter what option I use (Guided, Manual, etc...) to partition my disk, it fails when writing the changes to the disk at 6% complete. I have tried two separate hard drives and with both drives and any option, the partitioner fails at 6%. I have been having a tough time with this machine and trying to get ANY operating system to install (Ubuntu, Debian, Windows and a couple others). Is this a problem with my machine or am I doing something wrong? I have searched these forums and Google and still have not come up with a solution to this problem.

I'm still a newbie at Linux so I am learning a lot as I go by just messing with stuff. I have successfully installed Ubuntu on other machines but this one will not work to save my life...

---

### Post by 73ckn797 on 2009-05-18
Was the downloaded iso checked for "md5sum" prior to burning to disk? Did you burn disk at a slow speed? These can cause problems. Also, perform the disk check when the CD boots into the menu.

---

### Post by diavolo770 on 2009-05-18
I verified the md5, burnt it slow and ran a disc check before I attempted the install and everything checked out fine. I even re-downloaded the alternate image from a different location, verified it, burnt it slow and ran a disc check and I got the same error.

---

### Post by KapHn8d on 2009-05-18
I'm seeing this same issue where the partitioner basically hangs at the 5% progress mark. As did the OP, I have tried several ISO downloads, re-burns, etc. 
 
Just wanted you to know that you weren't alone :)
 
I have no clue what to try next.

---

### Post by Dragonbite on 2009-05-18
try, try again and not only Ubuntu. Try Fedora or openSUSE as well (both of them have good hardware detection).

The other thing is check if there is a bad sector on your hard drive. My second hard disk has a bad sector and whatever gets stored there is corrupted.

---

### Post by KapHn8d on 2009-05-18
I'm trying a different distro now (Fedora) just to see if I can get it to work. This is a brand new drive just removed from the box. There are no other physical discs in the system as I unplugged the Vista64 (bleh) HD before starting the install.
 
 
update: Fedora 10 was no help. I couldn't get the installer to run in text-only and unlike Ubuntu, there is no "safe" graphics option so the screen just blacks out when it tries to launch the GUI. I'm going to stick it out with Ubuntu and keep trying. I got a fresh, verified, ISO and tried installing again with the same result. I even tried manually setting partition sizes to much smaller (a couple hundred gig instead of "whole disc") to see if it would fail at a different percentage progress with no luck... still stops at 5% and hangs for a while (mouse still respnsive) and then the system locks (mouse locked, no way out but to reset).
 
Apparently the installer doesn't like something about my system. 
 
I've also run memory tests from several vendors under Windows with no errors (just as a datapoint).
 
cheers

---

### Post by Mark Phelps on 2009-05-18
To simply do partitioning, download and burn the GParted LiveCD from distrowatch.com.  It's newer than the version bundled with Ubuntu and other distros and may work better.

---

### Post by KapHn8d on 2009-05-18
I got it working.
 
I did as you recommended and performed the partitioning and formatting with an updated GParted.
 
Then, from booting off the 9.04 64bit install image, I selected the manual partition option and didn't reformat anything.
 
The install went fine after that...
 
thank you for your helpful pointers in the right direction. I really appreciate you taking the time to support a newb. :D

---

### Post by 73ckn797 on 2009-05-18
> **KapHn8d said:**
> I got it working.
 
thank you for your helpful pointers in the right direction. I really appreciate you taking the time to support a newb. :D

That's what these forums here for. Enjoy!!

---

### Post by Dragonbite on 2009-05-18
> **KapHn8d said:**
> I got it working.
 
I did as you recommended and performed the partitioning and formatting with an updated GParted.
 
Then, from booting off the 9.04 64bit install image, I selected the manual partition option and didn't reformat anything.
 
The install went fine after that...
 
thank you for your helpful pointers in the right direction. I really appreciate you taking the time to support a newb. :D

Not sure if it still works, but maybe change the title to include [solved] so people looking for a solution knows one is found here.

---

