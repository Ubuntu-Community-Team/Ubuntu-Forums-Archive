---
title: "Scrambled image with Ubuntu 9.04 + fglrx (ATI X850)"
date: 2009-04-25
forum: Hardware
---

### Post by Prodoc on 2009-04-25
Hi,

I've got a X850 ATI Radeon card. As mentioned by someone else in an earlier (closed) threat ([Scrambled image when I boot up Ubuntu 9.04](http://www.uluga.ubuntuforums.org/showthread.php?t=1125164)) I now get a scrambled image after upgrading to 9.04 and activating the proprietary ATI drivers. How can I revert this change? The system just hangs with a distorted screen displaying the Ubuntu startup progress bar and logo twice.

---

### Post by Prodoc on 2009-04-25
Things really got weird (messed up?) now.
I tried to boot Ubuntu in recovery mode and used the 'auto fix graphics problems' option. Now when I boot Ubuntu I get a scrambled screen with the top half displaying the new Ubuntu background and the bottom half displaying the 'Windows XP is shutting down' screen(!). :-S

How can this be? How can I get into Ubuntu again?

---

### Post by Beaon on 2009-04-25
I have the exact same problem. Mine was an upgrade from 8.10 and I was using the fglrx driver, all was well life was good. After the upgrade when rebooting I get the exact same symptoms as you. I have also tried "auto fix graphics problems", it did nothing to help

It's funny, my scrambled screens shows blotched up ubuntu loading screen up top and my Bios options down below! crazy...

I hope someone figures this out asap, it sucks not being able to get into my desktop. :(

---

### Post by Beaon on 2009-04-25
Prodoc I found a post that will get us back into gnome, problem now is there is no hardware acceleration.

Boot into recovery mode and remove the fglrx driver via this command

sudo apt-get remove xorg-driver-fglrx

Check out the below post
[http://ubuntuforums.org/showthread.php?t=1135107](http://ubuntuforums.org/showthread.php?t=1135107)

---

### Post by Prodoc on 2009-04-25
Thanks for the heads-up. At least it got my system running again.

I found that the problem is ATI, not Ubuntu. Support for quite a number of cards was dropped as of Catalyst 9.4. Catalyst 9.3, however, does not support X Server 1.6 which is included in Ubuntu 9.04. Ironically support for X Server 1.6 was introduced in Catalyst 9.4. Please, let ATI know what you think of this and ask them to include those cards for just one more round to let them have X Server 1.6 support: [http://www.amd.com/us/LinuxCrewSurvey](http://www.amd.com/us/LinuxCrewSurvey)

---

### Post by markitoxs on 2009-04-25
Yes, i also had the same issue, think the problem is ATI.

---

