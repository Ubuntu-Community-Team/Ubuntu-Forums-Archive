---
title: "installing Ubuntu 9.10 on 2nd Hard drive"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by mnielsen1984 on 2009-11-11
I'm trying to install the new version of Ubuntu onto a 2nd hard drive in my system, but the installer won't see the second drive, except for "specify partitions manually (advanced)" option.  When I go to this, I can see the second drive, but it won't let me install without a root file system.

I haven't figured out how to create the root system on the second drive (which as nothing on it), or why it doesn't show up on the main page for installation.

Thanks,
mnielsen1984

---

### Post by dhavalbbhatt on 2009-11-11
Try using the alternate installation CD. It seems that 9.10 desktop installation CD has an issue with partition manager. Alternate installation CD does not have a GUI, but will do the job.

---

### Post by gdbutcher on 2009-11-11
In your "advanced options" screen, click on new partition, a box will appear asking you for a partition size. 

1. In the first box "New Partition size...."; choose your size but leave about 2 - 5 GB bytes spare (I'll explain this in a second)
2. in the "Use as:" box choose "Ext4 journaling system"
3. Tick the "format the partion" box
4. In the "Mount point" box choose: / and click OK

5. In the remaining space (2-5GB) left over from part 1, choose click or add (sorry cant remember which one) keep the size the same, and in the "Use as:" box choose Linux Swap click OK then forward.

click on forward to create the partions, and your root system (/)

**One last step,** in the final screen before installation starts, there should be a button named "advanced" or something similar this asks you where you are going to install grub. it should have by default hd(O,0) or SD0, whatever it says ignore, click on the list and choose your first harddrive (it should have the make and size listed) and thats it. 

It should install now for you, hope this helps.

---

### Post by oldfred on 2009-11-11
If you want to keep your current boot and add the new install to it you can buy using the advanced tab that gdbutcher mentioned but install it to both the root partition and to the MBR of the second drive.

You then can either modify your old boot menu to chainboot to the new or switch drives in BIOS so your new install boots first without modifying your old install. That would make it easy to go back to your old setup.

---

### Post by mnielsen1984 on 2009-11-12
gdbutcher - doing it that way worked.  Thanks.

---

