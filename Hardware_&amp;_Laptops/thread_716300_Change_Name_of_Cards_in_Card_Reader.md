---
title: "Change Name of Cards in Card Reader"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by fireman biff on 2008-03-05
I have a multi-card reader and when I insert a card it shows up with the name "Disk". If I insert a different type of card at the same time it shows up as "Disk 2" or "Disk (2)" (something like that, I don't remember exactly).

Is there a way to change the default names for each port, so that the "MS/MS-Pro/MS-Duo/MS-Pro Duo" port mounts cards as "Memory Stick", "SD/Mini SD/MMC/RS-MMC"  mounts as "SD Card" etc?

---

### Post by chewearn on 2008-03-06
I don't have an answer to do exactly what you want, which is to set:
mounted name ==  type of memory port

But I do know that you can set
mounted name == card you inserted
You can do this by setting the disk label.

E.g. you have a SD card; plug this card into the slot, find out the block device location:
```
fdisk -l
```

Let's say you get /dev/sda1.


Then, change the disk label, e.g.
```
e2label /dev/sda1 sdcard
```


Next time you plug the SD card in, it will be mounted to /media/sdcard/

---

### Post by fireman biff on 2008-03-06
Thanks AstalaVista, that will at least let me give my memory stick a recognizable name. It would still be nice to be able to differentiate based on card type though, cause not every card will belong to me and I don't want to change labels on other people's cards.

Changing the label shouldn't affect the operation of the camera right?

---

### Post by chewearn on 2008-03-06
> **fireman biff said:**
> Changing the label shouldn't affect the operation of the camera right?

The label shouldn't matter to a camera; not that I know of.

---

### Post by fireman biff on 2008-03-06
Well I think I figured out how to do it. I put in a card so that it would show up on the desktop and then I right clicked and selected Properties. On the Drive tab I click on Settings and I was then able to enter a custom value for Mount Point (Memory Stick).

The next time I put in the card it mounted in "/media/Memory Stick" and it showed up as "Memory Stick" on the desktop. I was also able to borrow an SD card and do the same for that "drive".

So now its only the "CFI/II/MD" and "SMC" ports that aren't setup, but I don't think I'll be needing to use those anytime soon anyway.

---

