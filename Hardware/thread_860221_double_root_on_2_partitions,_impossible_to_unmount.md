---
title: "double root on 2 partitions, impossible to unmount both"
date: 2008-07-15
forum: Hardware
---

### Post by zanoman on 2008-07-15
I had MANY troubles when updating from Edgy to Feisty and from Feisty to Gutsy, so this time I decided to test the update on another partition (after I tested Hardy with a copy of my home partition (sda2)).

sda1 is Feisty (I don't boot anymore, I have to clean it).
sda2 is /home
sda3 is Gutsy original
sda4 is clone of sda3

I cloned the root partition (sda3) to sda4 (with gparted, copy-paste on unformated free space) and modified grub to boot from sda4.
Everything goes fine except that both show as root!
I cannot unmount any of them.
See screenshots.

Of course I removed boot by UUID from grub, so I'm pretty sure I'm on sda4, how can I have a proof of it?
And why sda3 shows as root too?

Sounds stupid but I even wonder if it writes on 2 disks.
If I update I think it will mess up big time.

Unfortunaley "update and everything will go fine" doesn't work for me, my setup is not standard and I had troubles with many hardware (partitions, DVDs, network issues) and packages issues during updates (installed from debian test instead of sticking to ubuntu), so I want to test update first :)
Oh, and booting from a Hardy partition with my /home messed up some services installed in /etc on Gutsy, so I prefer not to start from scratch on Hardy again.

Thanks for your help.

---

### Post by zanoman on 2008-07-15
Even info shows both of them mounted as root.

---

### Post by zanoman on 2008-07-15
Ok, I think it's about UUID and fstab.
For records, see [http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html](http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html)

---

### Post by zanoman on 2008-07-15
Yep, it's UUID and fstab fault.
This UUID is a pain.

If it happens to you (sdaX is the clone, sdaY is the source in the following):
start with a Ubuntu liveCD and the from terminal:
uuidgen
  <givenID>
sudo tune2fs -U <givenID> /dev/sdaX
sudo vol_id /dev/sdaX

mount sdaX the way you like (let's say it mounts as /media/disk)

sudo gedit /media/disk/etc/fstab

add a line for the new sdaX (by copying the sdaY line)
change the sdaY line: from / to /media/sdaY

Now I'm sure I booted /sda4 and sda3 is unmounted, so I can try to upgrade to Hardy and pray for it to work at first attempt!

---

