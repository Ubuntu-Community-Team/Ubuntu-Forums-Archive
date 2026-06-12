---
title: "Tricking my Motherboard"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Utemetsu on 2009-03-21
Huzzah! My server works.

And now I have a new project. Tricking my motherboard to allow 4 hard drives instead of two hard drives and two disc drives.



I have (currently) two hard drives installed. an 80 gb drive for the server OS (Ubuntu 8.1) and a 250 gb that I've got mounted for network storage. It works like a charm.

SO; I want to increase the storage space by creating TWO more drives available for mounting and networking. I unplugged the ATA cords from the CD drives, connected them to the HD's (yes, the jumper is set to 'slave'), and booted....They don't show up under fdisk -l ... Any suggestions?

---

### Post by lindsay7 on 2009-03-21
The first thing I would do is go into the bios and see if it sees the new drives or not. There may also be a setting that you can change to accomodate the extra drives. You may have to play with the settings to see if you can do this.

---

### Post by Mark Phelps on 2009-03-22
> **Utemetsu said:**
> Huzzah! My server works.
And now I have a new project. Tricking my motherboard to allow 4 hard drives instead of two hard drives and two disc drives.


There's no "trick" involved ...

You didn't say what you have on your mobo, but I'm guessing you have two IDE jacks.  If that's true each jack will support two drives, of any mixture: HDD and/or optical.

The catch is some of the older BIOSs won't autodetect a new device, in that case, you have to go into the BIOS and force it to detect the new device.  So, every time you change devices, you have to manually redetect them.

The OSs only see the devices through the BIOS, so whatever the BIOS does NOT see, the OSs won't see, either.

If you want more than 4 devices, you will have to buy an add-in card that will attach additional devices.

---

