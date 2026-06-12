---
title: "Dedicated entiree hard drive to Ubuntu (pretty much)"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by Quest-Master on 2005-01-29
Ok, so I have a dead 16.3GB Windows partition with basically nothing on it, and a 18GB Ubuntu partition which has been enjoying my use ever since I found out about it. I also have a system-used 4GB partition backup-thing which I would like to keep.

The partitions are like so:

hd0 - The system-used 4GB backup partition
hd1 - The Windows partition I want to nuke
hd2 - The Ubuntu partition I want to have practically all of the hard drive for
hd3 - Swap space

Now, what I would like to do is to remove hd1 and move hd2 to the top and resize it. I want to go about doing this by creating a new ext file system where hd1 lies and copy all data from hd2 to hd1, and resize the new Ubuntu partition to take up all space remaining.

I can do this with the Ubuntu Install Disc's partitioner, or with QtParted. However, what I am worried about is if after doing this, GRUB will still be able to detect and boot up the Ubuntu partition when I start up.

Could anyone please outline how I should go about doing this so my computer will still be in a usable state?

---

### Post by valadil on 2005-01-29
One of the nice things about grub is that you can edit your boot options from the grub commandline.  Just hit e to edit, then e again once you've chosen a line to modify.  If your ubuntu partition moves you can use this to boot to the partition then edit fstab and menu.lst to reflect the changes.

What I recommend doing instead though is simply mounting the new partition within your ubuntu install.  Probably on /home.  This way if anything happens to your ubuntu install all your important data is on another parition.  It also lets you install more distros of linux and keep the same home dir.

My os hard drive is partitioned like this:

hde1 15gb windows
hde2 2gb swap
hde3 100mb boot (probably not all that necessary but I had been doing some experimenting)
hde4 (logical parts instead of primary)
hde5 13gb /home
hde6 15 gb ubuntu
unused 15gb whatever os i feel like playing with.  probably gonna be gentoo at some point.

So how exactly would you go about mounting your second partition as /home?

First, blow away everything on the drive and make it ext3 (or your fs of choice).

Then copy the contents of /home to the new partition.  Keep in mind permissions and such.

Add the following line to /etc/fstab:
/dev/hda2       /home           ext3    defaults        0       0

---

