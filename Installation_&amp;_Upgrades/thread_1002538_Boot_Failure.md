---
title: "Boot Failure"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by mm8303 on 2008-12-05
Hello All,

I'm in a jam... I bought a used server with no os and when I tried to install Ubuntu it'd fail during the partitioning. So I should format the hd right? Well, I can't. Now when I turn on the computer I get a Boot Failure message and it halts. I can't get to a command prompt or anything... Any ideas? Please! and thank you! :)

Computer Specs:
Dual Xeon 2.4Ghz
1GB RAM
1-40GB IDE HD
3-36GB SCSI HD
ADA3400 RAID CARD

And so you all know I don't own any Windows setup CD's.

---

### Post by inobe on 2008-12-05
hi and welcome to ubuntu forums.


i just tried to assist someone with the same exact issue

[http://ubuntuforums.org/showthread.php?t=1002506](http://ubuntuforums.org/showthread.php?t=1002506)

---

### Post by mm8303 on 2008-12-05
> **inobe said:**
> hi and welcome to ubuntu forums.


i just tried to assist someone with the same exact issue

[http://ubuntuforums.org/showthread.php?t=1002506](http://ubuntuforums.org/showthread.php?t=1002506)

Thank you! 

In regards to 
[http://ubuntuforums.org/showthread.php?t=224351&highlight=Boot+failure%27+upgrade](http://ubuntuforums.org/showthread.php?t=224351&highlight=Boot+failure%27+upgrade)

The terminal freezes when I enter "find /boot/grub/stage1".

---

### Post by inobe on 2008-12-05
for the record' can you include what version of ubuntu you used.

also i think the alternate cd would be your best bet, if you didn't use it' i would get it, it has more features minus "live"

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by mm8303 on 2008-12-05
> **inobe said:**
> for the record' can you include what version of ubuntu you used.

also i think the alternate cd would be your best bet, if you didn't use it' i would get it, it has more features minus "live"

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

I am using 8.10 Desktop i386. I will give the alternate a shot. :)

---

### Post by littlebat on 2008-12-05
>  Now when I turn on the computer I get a Boot Failure message and it halts.

What is the exact failure message when boot?

You can't boot your installation CD?

Try check the BIOS setup of your server. Because I note you have SCSI and RAID, maybe this need special setup for your installation.

---

