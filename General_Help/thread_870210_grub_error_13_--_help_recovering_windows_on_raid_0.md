---
title: "grub error 13 -- help recovering windows on raid 0 stripe"
date: 2008-07-25
forum: General Help
---

### Post by SodiumKPump on 2008-07-25
Hey guys, I started installing hardy heron and partitioning my linux drive when I realized I hadn't backed up some important data.  I screwed something up and now I can't boot into windows which is on a raid 0 array (I never changed anything to this in the installation).  Somehow my boot configuration is screwed up and I don't know how to get grub to let me boot back into windows.  Any and all help is greatly appreciated!  Below is my current menu.lst windows entry

/boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by wannadumpwindows on 2008-07-25
Did you have windows installed before ubuntu?

If you did, it looks like you might just have one simple little error.

In the lione that says (hd0,0) I think it should be (hd0,**1**)

Change that and you should be all set. IT did the same thing to me on my most recent install. Grub thought my windows partition was (hd0,2) But it wasn't.

---

### Post by SodiumKPump on 2008-07-25
Tried that but still same error.  What do the two numbers mean?  I have 3 hard drives in my computer, 2 of them are SATA RAID 0 and the third is SATA with ubuntu installed.  I've had ubuntu on my computer for some time now, installed feisty fawn a while back and had windows xp already installed on hte stripe.  It all worked fine until I started trying to install hardy and then things got squirrely.  I will toy around with the numbers and see if I can get a combination to work unless you have any other ideas.  Thanks!

---

### Post by wannadumpwindows on 2008-07-25
I'm not very familiar with raid set-ups. So I can't get into too much more detail.

But as far as the numbers go, they mean which hard disk and partition that the entry is pointing to. Numbering starts at zero, instead of one.

So (hd0,0) means the first hard disk (hd0) and the second part means the partition, which in this case, would be the first partition (,0).

---

### Post by SodiumKPump on 2008-07-25
Okay, now I've got a new problem. I hda1,0 seems to work but now it just says 

Starting up...

And doesn't do anything.

---

### Post by caljohnsmith on 2008-07-25
Please post the output of:
```
sudo fdisk -l
```
so we can have a better idea which HDD and partition has your Windows on it.

---

### Post by SodiumKPump on 2008-07-25
Well, following some recommendations on another forum regarding this I used my xp boot disk to run fixmbr but now it's saying error loading operating system.

Any suggestions?

---

### Post by SodiumKPump on 2008-07-26
Okay so I said **** it and cut my losses.  Thanks for help anyway.

---

