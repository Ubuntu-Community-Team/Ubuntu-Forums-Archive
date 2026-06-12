---
title: "(another?) dead USB problem... but trust me, this one is tougher !"
date: 2010-05-20
forum: Hardware
---

### Post by xavier_ex on 2010-05-20
[COLOR=Red]**Problem Scenario:**[/COLOR]

    Hey guys I bought a PNY USB drive couple of days ago and I used it to transfer a few files from my Win 7 laptop to my netbook(brand new with win7 installed). However the browser stoped responding when I was attempting to open a folder in my usb, and the whole netbook, so I forced restarted the netbook... And after that my USB drive died... I tried it on my Ubuntu 10.04 netbook version and it didn't work either.


**[COLOR=Red]Symptoms:[/COLOR]**

**Win 7:**
1. Device got detected on both my laptop and netbook, and by detected I meant a sound "dingdong" was heard when plugged in and when plugged off.
2. However device is not shown in "My Computer"
3. In "Disk Management" the usb drive was assigned with letter G, however in property it showed 0 capacity and "no media", unable to change path name and etc.

**Ubuntu:**
1. Device not shown up in file browser, while another good usb drive did.
2. lsusb command detected the device
3. ls /dev/cd* showed a device /dev/sdc which should be my usb drive (somehow sdb became sdc but wutever)
4. fdisk -l /dev/sdc could not open it
5. fsck /dev/sdc could not read it
6. mkfs.vfat /dev/sdc says no medium found
7. disk utility showed the usb drive but said no data, thus unable to format


[COLOR=Red]**Solutions didn't work:**[/COLOR]

    I've tried some low level format software but they either couldn't locate my device or can't read from it. And since the device couldn't show up in my computer at all, I have little can do with it.

    I'm thinking my usb must have been damaged, and I've read through many posts in the forum but most of them were with the device shown up in the computer... I'm thinking if anyone could come up with a possible solution for my problem, or maybe I should just admit that I was cursed and dump my **p**athetic **n**ew-bought **y**et **u**seless **s**hameful **b**ullshit [B]PNY USB...


[/B]

---

### Post by xavier_ex on 2010-05-20
I just updated the Ubuntu symptom #7.

---

### Post by xavier_ex on 2010-05-20
bump, no one's got an answer or anything to say?

---

