---
title: "[SOLVED] do I have 2 problems or 1? sata in bios vs. Grub error 17"
date: 2008-08-22
forum: Hardware
---

### Post by screamingturnip on 2008-08-22
Well two days ago I was suddenly assaulted with Logic Errors and after a few reboots, it did load but it then told me that nautilus had to shut down and all I was left with was my wallpaper. I shut down. It finally settled on the good ol grub error 17. This could because I believing in my own version of the boysout motto "Always prepared for a second OS" I have a fifty gig ntfs partition. I booted up a live cd and f'ing around seeing if I could just happen into the solution. I didn't. I tried repartioning my old hard drive but I could not get it to get past the disklabel.

After a few more reboots my bios finally decided that I didn't have any sata drives, which leads me to why this is in Hardware. This is not the first port failure. I've been working w/o pata port 2 since before linux. Could my mobo or bios be dying?

Do I have two problems, one, or should I just start overclocking an etch a sketch?


Hodgeman specs as follows:
(sdb)160 gig sata, (sda)500 gig sata, 1 DVDRW pata
2.4ghz pentium 4
512 mb 2700 ram
865g integrated video and sound

partitions as follows:
100 gig linux (my system)sdb1
50 gig ntfs
460ish gig fat16 (storage)sda1

---

### Post by screamingturnip on 2008-08-22
WEll now it's talking about an isolinux failure. Yay.

---

### Post by lswest on 2008-08-22
I'd say the motherboard is dying, or the hard drive.  If possible, see if you can test the hard drive(s) in a second PC, if it does recognize the hard drive(s), it might be best to invest in a new motherboard (or new PC, whichever will be more efficient for you).  However, I suggest you try to test as much hardware as possible in a second PC before buying anything, and also, have a computer shop test your PSU, it might just be running out of juice.

---

### Post by screamingturnip on 2008-08-22
> **lswest said:**
> I'd say the motherboard is dying, or the hard drive.  If possible, see if you can test the hard drive(s) in a second PC, if it does recognize the hard drive(s), it might be best to invest in a new motherboard (or new PC, whichever will be more efficient for you).  However, I suggest you try to test as much hardware as possible in a second PC before buying anything, and also, have a computer shop test your PSU, it might just be running out of juice.

Here's a stupid question could the battery on my MoBo have anything to do with this?

---

### Post by cooke77 on 2008-08-22
Replace CMOS battery in that Pent 4.
Batteries do not last for ever, you know.

---

### Post by molochi on 2008-08-23
You mentioned overclocking and missing drive controllers. The first thing that I wondered was if your PCI bus was locked to 33MHz. I've seen i865 (and many other) boards that have the option to not lock that down (in bios setup) and if you are running a nonstandard FSB speed, and your controller is dependant on pci speed (common for transitional pci-e boards) usually one of the first thing you lose (that you'll notice) is data integrity to your hard drives.

Just something to check if you are overclocking.

---

### Post by screamingturnip on 2008-08-23
> **molochi said:**
> You mentioned overclocking and missing drive controllers. The first thing that I wondered was if your PCI bus was locked to 33MHz. I've seen i865 (and many other) boards that have the option to not lock that down (in bios setup) and if you are running a nonstandard FSB speed, and your controller is dependant on pci speed (common for transitional pci-e boards) usually one of the first thing you lose (that you'll notice) is data integrity to your hard drives.

Just something to check if you are overclocking.

hehe, sadly that was a joke, I've got a bussiness rig. It's not precisely built for overclocking. 
But back to the battery, could that be responsible? I only harp on this because I know how to replace that and I kinda have faulty a power source; currently operating on a surge protector off a power strip.

Oh and in case this makes a difference...
It's an 8187-CTU Thinkcentre

---

### Post by screamingturnip on 2008-08-23
> **screamingturnip said:**
> hehe, sadly that was a joke, I've got a bussiness rig. It's not precisely built for overclocking. 
But back to the battery, could that be responsible? I only harp on this because I know how to replace that and I kinda have faulty a power source; currently operating on a surge protector off a power strip.

Oh and in case this makes a difference...
It's an 8187-CBU Thinkcentre

Edit: oops not CTU... damn 4ghz

---

### Post by screamingturnip on 2008-08-27
I guessed this is resolved. My motherboard, she is dying. I am looking for a replacement. However she is dying slowly and I still have one pata port.

---

