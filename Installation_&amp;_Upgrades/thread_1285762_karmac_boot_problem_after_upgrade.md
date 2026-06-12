---
title: "karmac boot problem after upgrade"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by mcm307 on 2009-10-08
Hello,

Computer is a system 76 laptop 64bit intel laptop. Now on Karmac 2.6.31-12-generic

I was on 9.04 and did a update manager. Did not work a few times (error something like - only partial upgrade poseble unapproved packages, not compatible) but after getting rid of a few new sources I added for GIS upgrades it worked. Even then I had to run dkfs repairer or something because something was no longer used.I know this is not clear but I can't go back. 
 
After I rebooted got new icon followed by a normal looking screen that searchers for Ethernet. But then I got  blinking screen. I can get in to Ubuntu from a recovery mode. 


 blinking screen looks like-

fask from util-linux-ng 2.16
fsck from until-linuc-ng 2.16
/dev/sda1:clean, 372130/1831424 files, 3190521/3662109 blocks (check in 5 mounts)
*starting init crypto disks...
/dev/sda3: recovering journal
/dev/sda3: clean, 47036/14024704 files, 2489224/28045473 blocks
*Preparing restricted drivers....
*Starting early crypto disks...
*Atarting remaining crypto disks...
*Starting AppArmor profiles
*Starting Postgre 8.3 database server (note sometimes start 8.4 as well)
*Runing DKMS auto instillation service for kernal 2.6.31-12-generic
*nvidia(180.44) (note I get an error message sometimes but I did a reper during the bootup i think this might be the problem
*Starting Kernal Oops catching service kerneloops
*Starting the Winbind daemon winbind
*Startig Common Unix Printing System:cupsd
*PluseAudio configured for per-user sessions
*Enabling Additional executable binarly formats binfmt-support

(that it just blinks, different thinks will fail depending on I don't know what)

In an ideal world I would like to run some reverse update to get back to where I started. I think I did a massive updrage to an unstable tree by accident. I think my drivers are not working with what ever I downloaded. 

Help me!

---

