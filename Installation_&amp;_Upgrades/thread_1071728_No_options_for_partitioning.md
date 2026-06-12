---
title: "No options for partitioning"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by hhall on 2009-02-16
Hi.

I have been on another forum here, looking for help with Wubi, which did not forthcome. Ubuntu live CD runds well on my laptop (a 2008 Fujitsu Siemens Amilo Pi 2520, 2.2. GHz dual core centrino, ATI Radeon graphics etc etc), it just doesn't shut down properly.

With Wubi not working,I decided to let Ubuntu install itself on its own partition. After defragmenting through Vista, I have about 30 Gigabytes space at the end of my harddrive. Unfortunately, Ubuntu's graphical installation interface does not offer me any dual boot option. I can only wipe the whole drive, which I don't want. The same applies in manual mode. 

I have tested this both with a prepared unformatted 25 Gb section of the harddrive and without. Ubuntu's installer will not offer me a guided partitioning option. 

Does anyone know what I need to do?

HH

---

### Post by oldos2er on 2009-02-16
"I have tested this both with a prepared unformatted 25 Gb section of the harddrive and without."

 When you say "prepared," do you mean partitioned? If so, use manual installation and point the installer to that particular partition.

---

### Post by hhall on 2009-02-17
By "prepared", I mean that I freed up that space using the native Vista procedure for doing so. I had left the space unformatted, i.e. not alloocated a partition name or format, as I thought the Ubuntu installer would do that by itself. As I say, I'm very new to all this. Would I have a higher chance of success, if I formatted the 25 Gigabytes as partition D: or something?

HH

---

### Post by caljohnsmith on 2009-02-17
How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
Also, can you take a screen shot of what you are seeing in the installer and post it? Just hit the PrtScrn button on your keyboard.

---

### Post by oldos2er on 2009-02-18
> **hhall said:**
> By "prepared", I mean that I freed up that space using the native Vista procedure for doing so. I had left the space unformatted, i.e. not alloocated a partition name or format, as I thought the Ubuntu installer would do that by itself. As I say, I'm very new to all this. Would I have a higher chance of success, if I formatted the 25 Gigabytes as partition D: or something?

HH
  You'd need to use manual installation to create a partition out of free space on your hard disk.

---

