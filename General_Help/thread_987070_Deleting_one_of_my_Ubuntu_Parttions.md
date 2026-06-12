---
title: "Deleting one of my Ubuntu Parttions"
date: 2008-11-19
forum: General Help
---

### Post by crazysexycool on 2008-11-19
Hello all well i am in a Jam i have Fiesty Fawn gutsy gibbon and i am trying to load vista for a project i am busy with.


I am loading vista via virtual box which works ok but i have run out of space so now i need to delete gutsy gibbon because fiesty fawn has all my data on it.

How do i go about deleting gutsy gibbon from my partition??????

---

### Post by rampageoberon on 2008-11-19
You can use gparted for this. I'd prefer using the ubuntu livecd to do this as you need to unmount the system.

Also you might need to reconfigure grub depending how the partitions were setup.

---

### Post by crazysexycool on 2008-11-19
How do i use gparted is there a sticky somewhere ??

---

### Post by rampageoberon on 2008-11-19
Ok, I'm assuming you have the ubuntu CD at hand and can boot off it. If not you can download the gparted livecd from [http://gparted.sourceforge.net/luvecd.php](http://gparted.sourceforge.net/luvecd.php)

Once the Gparted GUI is loaded you need to select the drive in question. Now you need to know which partiton has what installed as all you will see is sda1, sda2 or hda1, hda2 etc.

Select the partition that you don't need and then delete it. You can then grow your existing partition to use all available space. (this can take a long time)

Please refer to [http://ubuntuforums.org/showpost.php?p=6197271&postcount=5](http://ubuntuforums.org/showpost.php?p=6197271&postcount=5) and if you need to restoring GRUB [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hoep that helps

---

### Post by crazysexycool on 2008-11-21
hell there thank you for those quick replies well i ost my whole ubuntu install 

Gonna have to do a clean install can i still try to get my install back [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
the restoring grub thing.

by using the document in the link above..

I have done a new install of vista but the ubuntu partion is still on my hard drive.

HELLLLLPPPP:confused::confused:

---

### Post by crazysexycool on 2008-11-21
Hell people anyone got some ideas for me?

---

