---
title: "Recommended Hardware RAID Controller"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Fooshnik on 2009-04-25
I have an Adaptec 5405 that installs with Ubuntu 9.04 and does not boot. 

Recommendations for a hardware SATA RAID controller that you have working with 9.04 (though preferably with 8.04)? My older Adaptec controllers work fine but the drive selection is now very weak.

---

### Post by Fooshnik on 2009-04-27
Anyone using hardware RAID?

---

### Post by foresto on 2009-04-27
I've been using a 3ware 8006-2LP for the past few releases.  The driver is included in the stock Ubuntu kernels.  However, I have been running into this bug since upgrading to Intrepid:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153)

(Basically, boot sometimes fails until I type 'exit' at a grub prompt.)

---

### Post by Fooshnik on 2009-04-28
Thanks. Are you running that in a 64-bit slot? Do you know if it's backwards compatible with 32-bit slots?

---

### Post by Fooshnik on 2009-05-06
Just as an FYI the card does run and boot just fine in a 32-bit slot.

---

