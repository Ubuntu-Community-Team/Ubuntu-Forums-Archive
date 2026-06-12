---
title: "Need Help With Installing Karmic"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by nishant.singh28 on 2009-11-11
I need to install Ubuntu 9.10 on my friend's desktop that is already running Win 7. Config:

Intel Core i7 920 @ Stock
6 GB Corsair 1600 Mhz Tri-Channel DDR3
MSI X58 Pro
2x Seagate Barracuda 7200.12 500 GB RAID
2x Zotac GeForce GTX 275 896 MB

The RAID works fine on Windows. The Karmic Live iso burned onto a flash drive recognizes the setup properly as a 1 TB hdd. But when we try installation on the 115 GB unallocated space on the drive, it gives installation error "could not install grub on /target/". The iso is fine: me and another friend have installed from it on our laptops. No solution available anywhere....please help....

---

### Post by earthpigg on 2009-11-11
towards the last bit of the partition, right before you click 'apply' or whatever it says, there is an 'advanced' button that people rarely use. it lets you pick where GRUB goes.

have you looked there, yet?

i have no idea how GRUB works with RAID as i have never worked with RAID, but that would be where i'd look.

---

### Post by nishant.singh28 on 2010-01-15
Bump!!!

---

### Post by gilson585 on 2010-01-23
GRUB2 is in beta and fails to boot fakeraid setups. Just follow this and you shall be in Ubuntu in no time [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) fyi this is supposed to be fixed in 10.04

---

### Post by nishant.singh28 on 2010-01-23
It's not fakeraid. That's the whole problem

---

### Post by gilson585 on 2010-01-24
You didn't mention what dedicated raid card you are using so I assumed it was the onboard fakeraid. As much as the onboard solutions look and feel real they are still not true h/w raid solutions nor are the entry level add on cards. Typically it costs $200 or more for a true raid controller.

---

### Post by nishant.singh28 on 2010-01-24
It's not my comp so I can't specify right now. Will have a look and get back on this.

---

### Post by nishant.singh28 on 2010-01-26
> **gilson585 said:**
> You didn't mention what dedicated raid card you are using so I assumed it was the onboard fakeraid. As much as the onboard solutions look and feel real they are still not true h/w raid solutions nor are the entry level add on cards. Typically it costs $200 or more for a true raid controller.
The RAID controller is on the X58 Chipset. What is it supposed to be?

---

### Post by gilson585 on 2010-01-26
This is what you have [http://en.wikipedia.org/wiki/RAID#Firmware.2Fdriver-based_RAID_.28.22FakeRAID.22.29](http://en.wikipedia.org/wiki/RAID#Firmware.2Fdriver-based_RAID_.28.22FakeRAID.22.29) If you are using Raid 0 stripped then my how-to should work just fine.

---

