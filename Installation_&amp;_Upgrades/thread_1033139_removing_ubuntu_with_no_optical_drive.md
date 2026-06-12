---
title: "removing ubuntu with no optical drive"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by want2bdifferent on 2009-01-07
hey everyone, i currently have ubuntu 8.10 installed on my netbook, and i am not finding much use for it anymore, and want to remove it, with the grub bootloader, is there a way to do this without using the windows disk, it is only taking up space atm, and it is really annoying me to go through grub everytime i boot

---

### Post by melojo on 2009-01-07
you can fix windows mbr open a terminal applications>accessories>terminal and run
Code:

```
sudo lilo -M /dev/sda mbr
```

assuming that windows is on the drive sda

---

### Post by want2bdifferent on 2009-01-07
> **melojo said:**
> you can fix windows mbr open a terminal applications>accessories>terminal and run
Code:

```
sudo lilo -M /dev/sda mbr
```

assuming that windows is on the drive sda

what do you mean by windows is on the sda?

---

### Post by madmilk on 2009-01-07
> **want2bdifferent said:**
> what do you mean by windows is on the sda?

Just simply RUN that Command

sudo lilo -M /dev/sda mbr



it will..  Put back your Original BOOT .. of Windows  **It Eliminates GRUB from starting**

After that command...     Restart your Computer.. (without the liveCD)

And you will be back normally starting the computer into Windows

---

### Post by want2bdifferent on 2009-01-09
> **madmilk said:**
> Just simply RUN that Command

sudo lilo -M /dev/sda mbr



it will..  Put back your Original BOOT .. of Windows  **It Eliminates GRUB from starting**

After that command...     Restart your Computer.. (without the liveCD)

And you will be back normally starting the computer into Windows
thanks heaps, and now do i just format the partition with ubuntu installed on it?

---

### Post by estyles on 2009-01-09
> **want2bdifferent said:**
> thanks heaps, and now do i just format the partition with ubuntu installed on it?

Yes.  You can do that a number of ways, but the easiest IMHO would be to, after you boot back into windows, right-click on the "My Computer" icon, and choose "Manage" (note: this works on XP... dunno about vista if that's what you're using) and go to "Disk Management".  Then you can delete the Ubuntu partition and create a new NTFS partition.  If you're on Vista and that option isn't there, there should be something called "Disk Management" somewhere.

Note that I don't think there is any free utility in Windows to resize a partition.  If you had an optical drive, you could load up the Ubuntu LiveCD and use it to resize the windows partition to take up the whole drive.  But without that, I think you'll just have to live with 2 separate partitions, though you can use the second partition for games, documents, data, whatever...

---

