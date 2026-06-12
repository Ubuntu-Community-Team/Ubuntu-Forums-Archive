---
title: "fingerprint reader in HP DV6-7040tx"
date: 2012-12-21
forum: Hardware
---

### Post by vikkyhacks on 2012-12-21
I have a "**ID 138a:0018 Validity Sensors**" in my HP laptop. I need to use to login to my desktop. I tried fprint and fingerprint but the device did not seem to be detected, and it also does not seem to be supported in the hardware list in the following link

*_[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)_*

Any help to get it working ???

I use this laptop [http://h10010.www1.hp.com/wwpc/in/en/ho/WF06a/321957-321957-3329744-64354-64354-5226230.html?dnr=1](http://h10010.www1.hp.com/wwpc/in/en/ho/WF06a/321957-321957-3329744-64354-64354-5226230.html?dnr=1)

thanks in advance

---

### Post by cloroxX on 2013-02-09
bump, this is also in my hp pavilion 1035dx, would love to get it supported somehow :D

---

### Post by SeijiSensei on 2013-02-09
Last I looked, which was over a year ago now when I was setting up a dv6t, the device was not supported in Linux.

---

### Post by cloroxX on 2013-02-11
meaning it can't ever be supported??

---

### Post by SeijiSensei on 2013-02-11
It probably could be supported if either the manufacturer chose to write a Linux driver for the device or a Linux kernel developer chooses to reverse-engineer it.  You could complain to HP, but I doubt they care to invest resources in supporting Linux.  I don't have the machine available to see who manufactures the fingerprint reader itself.  If you have Linux installed on that machine try running "sudo lshw" to see who the device manufacturer is and bitch at them.

---

### Post by vikkyhacks on 2013-02-11
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc.  is the validity sensor in my notebook....

Awwww that sucks, I thought that if the hardware is on the unsupported list It will be supported some other time infuture, HP providing linux drivers ??? That day will never come.

---

### Post by SeijiSensei on 2013-02-11
[http://ubuntuforums.org/showthread.php?t=1585180](http://ubuntuforums.org/showthread.php?t=1585180)

Validity Sensors claimed they would write a Linux driver, but apparently they never followed through.  The last posting in that thread points to a page in Italian suggesting there is a Debian driver which could work in Linux.  You might want to push that page through Google Translate and see what you find.  Let's us know.

---

### Post by Hìr0 on 2013-05-19
It seems that the validity sensor 138a:0018 is supported now but I was not able to compile and make it working. Please have a look at  [https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/827669](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/827669)

---

### Post by vikkyhacks on 2013-05-19
Hey can you post the "how and what" s of the INSTALL, I installed it via synaptic but could not get it to work !!!

---

