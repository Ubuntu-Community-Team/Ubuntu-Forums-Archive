---
title: "ssd issue"
date: 2014-08-15
forum: Hardware
---

### Post by stan-saraczewski-yahoo on 2014-08-15
I've got a pavilion g7 that has been happily running 12.04 - I decided to replace the hard drive with a crucial mx100 ssd. Day one installed Ubuntu 12.04 from the same .iso dvd that was used for two other installs. Rebooted a few times just to enjoy the increased speed. Day two installed all the updates. Rebooted a couple of times, all was well. Day three - power on got me a message indicating that no operating system was found on the disk. I've performed this exercise now twice and am wondering if anyone has some advice ? Perhaps I have a defective ssd... I would imagine an incompatibility issue wouldn't have permitted a boot after install, much less a second good day. The battery is full btw.

---

### Post by oldfred on 2014-08-15
From live installer run the Bootinfo report. Post link it gives.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by stan-saraczewski-yahoo on 2014-08-16
I decided to try 14.04 again and after getting the gray screen downloaded the boot repair cd on another system. This was very much a challenge as the scripts weren't quite right and they could not be cut/pasted... but I do appear to be booting ok. I wish to thank you very much for your assistance.

---

### Post by stan-saraczewski-yahoo on 2014-08-17
Oh well... THOUGHT we were good to go however got the 'please install an operating system' message once again. I must have a flakey ssd...

---

### Post by oldfred on 2014-08-17
Is default switching in UEFI.
Some UEFI or Windows auto switch default to be Windows in UEFI boot order.

---

### Post by stan-saraczewski-yahoo on 2014-08-18
Not dual boot - pure linux. Vendor has asked me to call the mfg (Crucial) to 'troubleshoot' then they will provide RMA. This has to be a bad unit as it works for a day or so then won't boot. I've put time off an on into it for the last week and am finished with it.

---

