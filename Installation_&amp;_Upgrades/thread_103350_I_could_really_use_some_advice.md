---
title: "I could really use some advice"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by kfultz on 2005-12-13
My Windows install won't boot now and I am kind of stuck

---

### Post by aysiu on 2005-12-13
Can you give some more information?

---

### Post by atoponce on 2005-12-13
Did you install Ubuntu on a partition on the same drive or on a seperate drive?  Your MBR may be corrupt, at which point, you would have to rescue it.

---

### Post by kfultz on 2005-12-13
When booting from the cd i just hit enter for the install. I am assuming that tried to install on the main partition, but I am not sure. It never got to a point where it asked what partition or to format. I have two Hard drives. One is a 200 Gb drive with 2 partitions. !st one has windows xp Pro SP2 and the other is blank.
Kevin

---

### Post by atoponce on 2005-12-14
Can you boot into Ubuntu?

---

### Post by kfultz on 2005-12-14
No I got an error when running the install ACPI : looking for DSDT in initrd... not found
I tried linux acpi=no 
and I got a different error

---

### Post by atoponce on 2005-12-14
Do you have a Live CD?  If so, you will most likely need that to resuce your install.  My guess?  Either you installed Ubuntu over Windows, and you have issues with your hardware, or, you installed Ubuntu on a seperate partition or hard drive and just messed up your MBR.  Check out the following link for some better help:

[Click here.]("http://www.ubuntuforums.org/showthread.php?t=98606")

---

### Post by kfultz on 2005-12-14
Do you mean I need to rescue my Windows install? or the Ubuntu?
I have windows xp and tried to boot to it to repair the mbr but it gets to a part where it wants to load the setup and it hangs...

---

### Post by atoponce on 2005-12-14
I mean rescue your MBR.  It's tough to really tell what your problem is, but I am willing to bet it is one of those issues.  When you boot the Live CD, can you get a desktop up?  If so, try pulling up a terminal, mounting your hard drive(s) and seeing what is on it/them.  This may help you find out if your Ubuntu install exists on a seperate drive or partitioned on the first, and whether or not your Windows install is gone.  You will also be able to fix your MBR, if that is the issue.

---

### Post by kfultz on 2005-12-14
Thanks for your help I will try and reload windows or fix the mbr and let ya know 
Kevin

---

### Post by aysiu on 2005-12-14
Microsoft has some instructions on their website for restoring the MBR:
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

---

