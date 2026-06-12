---
title: "Gparted interrupted. Now can't recognize the HDD"
date: 2010-02-10
forum: Hardware
---

### Post by green69 on 2010-02-10
Hi Guys!

I was formatting with Gparted my NEW external HDD with ext4 (it was originally ntfs). I involuntary stopped Gparted and now I can't recognize the disk. I have no data inside but I would to recover my new external HD (1.5 TB). PLEASE if somebody can help me I would be very greatful. I'm lost!!!

Thank you in advance!

---

### Post by ZootNerper on 2010-02-11
HI,

This may or may not help. Take the disk out the it's external box and plug it into the mainboard (motherboard) of your computer, via SATA or PATA whichever it uses (like the internal disk)

I think your problem is that the hardware of the external box can't recognise the messed up disk and so can't report anything over the usb link. What you have done is outside the little hardware's knowledge.

If this still doesn't work you could keep the disk connected to the mainboard and use one of those startup disks that check hardware. I like SystemRescueCD or UltimateBootCD. These boot the computer into DOS and then you can run a disk checking program that is on the CD (It may have the one from your disk manufacturer). (The long tests take many hours to run and the short ones tell you to run the long ones)

Hope the first solution works :)

-- Zoot

---

### Post by green69 on 2010-02-11
> **green69 said:**
> Hi Guys!

I was formatting with Gparted my NEW external HDD with ext4 (it was originally ntfs). I involuntary stopped Gparted and now I can't recognize the disk. I have no data inside but I would to recover my new external HD (1.5 TB). PLEASE if somebody can help me I would be very greatful. I'm lost!!!

Thank you in advance!

I don't know why, but after rebooting the system was able to recognize the disk, although in a not unknown format (obviously). Now I restart the formatting with Gparted.

Thank you anyway ZootNerper!

---

