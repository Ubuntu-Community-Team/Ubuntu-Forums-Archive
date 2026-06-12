---
title: "can't boot, won't boot"
date: 2008-09-23
forum: General Help
---

### Post by joey-elijah on 2008-09-23
another can't boot query
okay all!


I seem to have 'upgraded' by wubi installation o0nto my vista disk. hmm. Never mind losing vista, but i have a boot predicament upon every boot.
 
On a boot up i'm presented with

UBUNTU
UBUNTU (rfecovery)
UBUNTU (mem test)
OTHER OPERATING SYSTEMS
VISTA/LONGHORN LOADER
UNBOOTIN-PARTITION MANAGER
OTHER OPERATING SYSTEMS
WINDOWS

no matter which i click, i'm greeted either by

error 13 - invalid or unsupported executable format

or

error 17 - cannot mount selected partition

Lush.

I can, however, boot into linux but editing the first ubuntu command and changing the (0,0) bit of the command, except i have to change it EVERYTIME. if on last boot it was (0,0) i have to change it to (1,0) to boot up, or i get error 17. And vice versa, if it was (1,0) last boot, needs to be (0,0). 

Now obviously i'm grateful i can boot at all, but having lost vista and javing to manually muck about to get into UBuntu, i'm getting narked. 

Cny help? i'm a bit novice-esque - mainly used to wearing my sudo apt-get'n boots....

I have two internal harddrives, with ubuntu writing over vista which was on an 80gb drive - set to boot first i think. and teh wubi was originally on a 160gb drive, which now hosts grub, i think... hrrrmph.

any help will be met with marriage proposals, spare livers, you name it!

---

### Post by joey-elijah on 2008-09-28
*bump*

---

### Post by ago on 2008-09-29
What do you mean by "upgrade", did you run lvpm?

---

### Post by joey-elijah on 2008-09-29
thats correct, however, i didn't realise i installed it over vista. ( i don't know my partitions and discs as intimately as hda1 etc lol) 

Not too worried about that, but i'd just love it to boot into ubuntu on start up/restart instead of having to be manually manipulated by me.

---

### Post by ago on 2008-09-29
This is due to an old ubuntu bug. When there are multiple disks, grub-install might get confused about the disk order.

In ubuntu edit the line of /boot/grub/menu.lst starting with 

#groot=(hd0,0)

to

#groot=(hd1,0)

Also change the disk ordering in the windows section
Then run 

sudo update-grub

---

### Post by joey-elijah on 2008-09-29
if this works, i may just offer my hand in marriage.

---

