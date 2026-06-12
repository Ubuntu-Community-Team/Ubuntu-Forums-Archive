---
title: "No Suspend-To-RAM after upgrade to Intrepid (amd64)"
date: 2009-04-07
forum: Hardware
---

### Post by hal10000 on 2009-04-07
Hi,
last week i upgraded my notebook (Fujitsu-Siemens Amilo Xi 2528 with NVidia GeForce 8600M GS ) to Kubuntu 8.10. Everything works perfect, except Suspend-To-RAM, which worked on the previous hardy-System.

Hibernate works, but after a Suspend the screen remains blind while i can hear harddisks and fan, and i have to switch the notebook off and on again to get it to work.

After searching in some forum threads (here in ubuntuforums, on other linux-sites and in Amilo-related forums) i found this link

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

and followed the steps to change my /etc/default/acpi-support file and /etc/X11/xorg.conf, but it didn't work.

Now i'm wondering why it worked in hardy although i didn't make the changes described in the link above and why it is not working in intrepid, regardless if i use the original (unchanged) acpi-support and xorg.conf files or the changed files as described in the link.

Has anyone similar problems with the Standby mode?
Any help is appreciated.

---

### Post by lee-anna-loo on 2009-04-11
Yes, I have the same problem from recently. 

I have Dell Inspiron 1520 with nVidia Corporation GeForce 8400M GS, and I use Intrepid. Also, I use the NVIDIA accelerated graphics driver (version:180).

From the beginning everything was working fine, but before few days I installed some upgrades with the update manager and since then I have the same problem as you - it can suspend, but when I'll restore the system all I get is a black screen, I can hear the fan and hard disk working, but it does not respond to anything.


The Hibernate mode is also working just fine.

edit:
I changed the NVIDIA accelerated graphics driver from version:180 to version:177 and everything is ok again.
I tried going back to version:180 but I had the same problems again with the restoring.

---

### Post by hal10000 on 2009-04-14
Hi lee-anna-loo,
thanks for the tip to downgrade the acc. NVidia driver, as soon as i have time to try it out, i'll will do it. Maybe it's a bug in the latest NVidia driver

---

### Post by hal10000 on 2009-04-15
It's the NVidia driver. I just downgraded to version 177 and everything works again

---

