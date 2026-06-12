---
title: "hot-plug USB3.0 stopped working after 12.04 updates"
date: 2012-06-05
forum: Hardware
---

### Post by aa-hcl on 2012-06-05
Hi,

I have got Dell E6520 with ExpressCard USB3.0 port. (See my previous post about the speed - [http://ubuntuforums.org/showthread.php?t=1893543](http://ubuntuforums.org/showthread.php?t=1893543))

After upgrading from 11.10 to 12.04 everything worked: 

1. hot-plug the USB3.0 drive into the ExpressCard worked - the drive is recognised
2. the USB3.0 port started to work as USB3.0 after the 12.04 upgrade

However, recently after 12.04 updates or for any other reason, hot-plugging the USB3.0 drive into the ExpressCard USB3.0 port does not work:  the drive is NOT detected.

Plugging the same drive into the built-in USB2.0 port does work - the drive is detected.

Rebooting with the drive plugged into the USB3.0 ExpressCard slot does work: the drive is recognised and the speed is greater than for USB2.0.

Previously (back in ubuntu 11.10) when I first bought the drive and the card - i had the same problem. This was solved by adding the following module:

root@aa-i7:~# sudo modprobe acpiphp

(and then making it permanent by adding to /etc/modules). After the above under 11.10 the hot-plug USB3.0 drive into ExpressCard slot did work.

However, now it does not work even with the acpiphp module active:

aa@aa-i7:~$ sudo lsmod | grep acpiphp
acpiphp                24231  0 


Can you please help!!!

Many thanks!!

---

### Post by aa-hcl on 2012-06-17
Can you please give any ideas what to check in order to find out what modules are responsible for hot-plug detection of external hard drives?

Recent updates did not help! currently I have the latest kernel:

aa@aa-i7:~$ uname -a
Linux aa-i7 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Please help by giving any ideas what to check!

Many thanks!

---

