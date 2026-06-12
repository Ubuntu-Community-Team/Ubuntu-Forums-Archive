---
title: "HP Mini Install Problems"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by russ5811 on 2009-10-18
I have an HP 1116nr. 1gb ram, 16gb ssd. i have tried to install 9.10UNR via cd, external hdd, and usb. none of them are working. i was able to install 9.04 via usb cd-rom, but it is not what i want to keep. I really want to use the UNR. the netbook will boot to the disc via cd or usb, however, once i tell it to install ubuntu, it shows the ubuntu logo, then freezes. what can I do?

---

### Post by mspgs2 on 2009-11-10
i had the same problem... selecting anything in the boot menu screen would access the usb disk (it has a blue activity led) the screen would go blank replaced with a flashing cursor and then nada. The following worked for me 

At the menu
F6 - other options
select acpi=off
select noapic 
select nolapic
then install

but i've noticed it doesnt always work.. i think the hp's bios is wonky

---

### Post by Redterp on 2010-02-24
I used [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) tool to create a boot USB (2 GB) with the 9.04 UNR iso and it worked the second time around.

The mistake I made the first time around is that I formatted the thumb drive in NTFS instead of FAT and the first attempt ended up giving a boot error.

Hit F9 at start up and select USB and it should run UNR directly from the USB drive and then it installed OK for me too.

I have a HP 116NR

Though I'm now having trouble getting any of my network connections to work (wired or wireless).. Any tips?:confused:

---

