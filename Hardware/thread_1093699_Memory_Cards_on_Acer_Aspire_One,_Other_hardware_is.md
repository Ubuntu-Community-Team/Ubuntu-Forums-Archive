---
title: "Memory Cards on Acer Aspire One, Other hardware issues"
date: 2009-03-11
forum: Hardware
---

### Post by nago on 2009-03-11
Hi, everybody. I need some help with my Acer Aspire One netbook and the SD Card readers. I have some experience with linux, but it's not enough to assume I know anything. Please treat me like a certified moron and hold my hand a little. I would certainly appreciate it!

I am using Ubuntu 8.10, with kernel 2.6.27-11-generic. The BIOS version for my Acer is #3309. I have all of the security and recommended updates for Ubuntu as provided by a "vanilla" install of Ibex. The install was performed two days ago under BIOS v 3305. (I updated the BIOS afterward to attempt to resolve compatibility issues.)

As per [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) I have been installing and setting up my new netbook, but I've hit a few snags; the following are some relevant bits of interest for what I've done and what I am seeing.

1) No problem here, just info: I was able to get the wireless working mostly properly as per the instructions, installing MadWifi and inserting the appropriate lines into /etc/modules, /etc/sysctl.conf, and creating the restart script for awakening from wireless, everything seems to be looking good here.

2) As per the page's warning, I believe I've lost connectivity in my hardwired 10/100. How can I get this functionality back? The page mentioned that the -13 kernel fixes this issue, is there a way I can install this or is it not recommended, and I should just wait for it?

3) The big reason for my coming to the forums is the SD card readers. Although they work, their working is sporadic and auto detection doesn't work consistently. Here is my analysis of what occurs:

A) If I boot Ubuntu without an SD card in either slot, once I am booted, putting an SD card in either slot does not create an icon on the desktop.

B) If I boot Ubuntu with an SD card in the left slot, The SD card is mounted at boot and appears on the desktop. Subsequently, I can remove the card and put in others in the left slot, and all are auto-mounted for me. The right slot, however, remains inoperative.

C) If I boot Ubuntu with an SD card in the right slot, the SD card is mounted at boot and appears on the desktop. Subsequently, I can remove the card and put in others in either slot, and all are auto-mounted for me.

D) If I boot Ubuntu with SD cards in both slots, both are automounted, but the icons overlap each other on the desktop. If I remove them, only the left slot will have automount work; whereas the right slot only seems to work if the left slot is occupied. I can access the card in the right slot if I take out the left slot card, but if I remove and re-insert it, it will not automount.

I tried adding these lines as per the AspireOne doc page;
```

options sdhci debug_quirks=1
options pciehp pciehp_force=1

```

But I saw no noticeable change in the behaviors listed above, so I deleted them.

4) I have no luck getting the unit to Hibernate, and the Doc page suggests this should work fine on the non-SSD models. Any tips here?

5) Lastly, any tips from other Aspire users for tweaks I should make to the install to make it fully functioning?


Thank you all, and sorry for the long "SOS!" post, but any help would very truly be appreciated.

---

### Post by scprosser on 2009-03-11
Have you tried Linux4One?

It's a customized version of Ubuntu 8.04 (LTS) that has been recompiled and customized specifically with the drivers and setup for the hardware of the AA1.

I'm presently running a dual boot between it, and XP, and it works like a dream (make sure to get version 1.1, they fixed the SD Card and Bluetooth issues in 1.1)

Just Google Linux4One and go to the English section of the Forum

---

### Post by scprosser on 2009-03-11
Have you tried Linux4One?

It's a customized version of Ubuntu 8.04 (LTS) that has been recompiled and customized specifically with the drivers and setup for the hardware of the AA1.

I'm presently running a dual boot between it, and XP, and it works like a dream (make sure to get version 1.1, they fixed the SD Card and Bluetooth issues in 1.1)

Just Google Linux4One and go to the English section of the Forum

---

### Post by nago on 2009-03-11
> **scprosser said:**
> Have you tried Linux4One?

I haven't tried any of the many Ubuntu Variants for netbooks, like crunchbang, easy peasy, etc. I was trying to stick with vanilla ubuntu if possible, but I will regard Linux4One as a possible fallback in case I can't seem to get this working, thanks for the tip.

---

