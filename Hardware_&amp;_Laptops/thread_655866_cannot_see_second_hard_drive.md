---
title: "cannot see second hard drive"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by derkaderka on 2008-01-01
Ive got a compaq presario SR5234X that i recently bought.  I wanted to add my old WD external 250 GB hard drive to it as an internal.  the drive is powered up, and functioning when i boot the computer, but i cannot access, or even see the drive.

my friend assures me that I can simply plug the drive in without any fuss or extra drivers.

currently, the original HD (that came with the computer) that im running Ubuntu 7.10 gutsy off of is SATA.  the former external that im plugging in is IDE.  they are obviously connected through different cables to the motherboard, but does that make a difference?

any idea as to what i should do, or else ask me to clarify something?

---

### Post by taurus on 2008-01-01
Does it even show up when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That would be a lower case letter L, not number 1.

---

### Post by derkaderka on 2008-01-01
i can see my main drive listed as

dev/sda1 * Linux
dev/sda2   Extended
dev/sda5  Linux Swap / Solaris

and the new drive comes up as

dev/hda1   W95 FAT32 (LBA)

so my computer does recognize the drive, but how would i access it?

---

### Post by FrankVdb on 2008-01-02
You didn't mention any tries at mounting the drive. Under Linux, drives need to be mounted before they can be used.

---

### Post by derkaderka on 2008-01-02
how would i go about doing that?  when i say i cannot see the drive, i mean that nothing shows up in all the places that i look for it, mounted or not.  theres no icons, no dialog boxes, nothing different from when it was the the SATA drive by itself.

---

