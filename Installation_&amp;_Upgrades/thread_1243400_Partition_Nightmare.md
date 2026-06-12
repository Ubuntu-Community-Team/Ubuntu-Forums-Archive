---
title: "Partition Nightmare"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by slickred on 2009-08-18
Hi,

I just got myself a new Aspire Revo, and I am intending to dual boot with Windows Vista (already installed) for games etc, and Ubuntu for everything else, including xbmc.

I am not very familiar with Ubuntu, and I think I've made a mess. I've been searching for a solution for about 7 hours, and I'm ready to pull my hair out, so I really hope someone here can help.

Ok, here goes...

I have Ubuntu installed, however the partition Ubuntu created for itself is only 2GB in size. I want to extend this partition substantially. In order to do this I freed up some space from within Vista (reducing the size of the Vista partition).

Now, when I boot from the USB pen I used to install Ubuntu, and run gparted, this is roughly what it looks like.

Partition____FileSystem__Label_______Size___Used__Unused 

/dev/sda1___ntfs________PDQService__14.65__9.85__4.8           
/dev/sda2___ntfs________ACER_______37.43__21.4__16.03
unallocated__unallocated_____________94.47__----__----
/dev/sda3___extended_______________2.49___----__----
   /dev/sda5___ext3___________________2.32___2.03__293.93MB 
   /dev/sda6___linux-swap______________172.54MB_--__----

I can extend the Windows partition, but not the Ubuntu partition.

I know nothing about partitions, and I really don't understand any of this, so if you have a solution please pretend you're talking to an idiot. Because you basically are.

Thanks in advance for any help,
SlickRed

---

### Post by realzippy on 2009-08-18
You run gparted from your installed ubuntu?

---

### Post by snowpine on 2009-08-18
First expand the extended partition (/dev/sda3) to fill the unallocated space. Then, you should be able to expand the Ubuntu partition (/dev/sda5).

Think of an extended partition as a "container" that can hold other partitions...

---

### Post by raymondh on 2009-08-18
> **slickred said:**
> 

I can extend the Windows partition, but not the Ubuntu partition.

SlickRed

Gparted will not work on any partition that is mounted, SWAP included.  A live session uses swap.

Rt. click on partitions.  If given the option to unmount, do so.  For swap, select swapoff.  You know it's mounted if you have a greyed-out option to resize.

For guidiance/reference:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Back up your files too.

EDIT : as snowpine says .... enlarge the extended (sda3) first and then enlarge root (/) sda5

Good luck.

---

