---
title: "booting problem"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by sagar gajre on 2009-07-09
hi guys,
i have a pentium4 2.6ghz, 1gb ram pc the problem is when i put my linux cd for installation in complete installation mode when i press F8 which is default key for booting in most of the pcs my cd does not boot i have tried this in other pcs where after pressing F8 the boot msg comes for instalation of linux. how can i fix this currently i am on "windows through install mode"
please assist.

---

### Post by dandnsmith on 2009-07-09
What you need depends on the BIOS provisions -
a couple of the systems I use can boot from a device which is not the usual boot device by pressing F12, for others I need to change BIOS settings for boot sequence if the CD isn't higher in the sequence than HDD.

The thing is to read any documentation for the system hardware and firmware.
If you don't have any, post the details, such as you have them, about the PC and perhaps someone here will be able to help you with precise instructions.

---

### Post by raymondh on 2009-07-09
are you trying to install thru windows (aka WUBI) ... or are you trying to create a true dual-boot (windows and Ubuntu in their own, physical (not virtual) partitions?

If thru WUBI,  here is the guide to install

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

Now, if you are intending to install dual-boot and cannot boot-into the liveCD, .... see this link and look for your system (not, not complete):

[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)

From there, just change the boot order as usual.

---

### Post by sagar gajre on 2009-07-10
i am trying dual boot

---

### Post by sagar gajre on 2009-07-10
still i am not able to boot the cd by for the dual boot purpose
any suggestions?

---

### Post by raymondh on 2009-07-10
Can you explain a little more your issue?  

Are you able to change the BIOS' setting to 'boot the CD drive first'?  If yes, is the CD drive working?  If yes, is the liveCD booting but giving you errors?

Kindly detail the problem.

---

