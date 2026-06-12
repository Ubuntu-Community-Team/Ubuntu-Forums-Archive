---
title: "Dual Boot Question/Issue"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by ddeile on 2009-01-26
Hi,

Sorry if this has been answered elsewhere. I searched the forums for a similar issue to mine, but have been unable to find the exact same.

Installed Ubuntu yesterday on a new SATA HD.  I have a second SATA HD in my machine with Vista loaded on it.  Before installing Ubuntu, I removed the power cable from the Vista HD.  I did not want the boot record on the windows HD to be changed.

The install of Ubuntu went perfectly.  I see that Grub is loaded on boot.

How do I, using Grub, change the boot record on the Ubuntu drive so that I can choose either Ubuntu or Vista at boot up?

The Ubuntu drive is attached to SATA1, and the Vista drive is attached to SATA2.

I see that Grub recognizes SATA1 as hd0,0 at boot.

---

### Post by Pumalite on 2009-01-26
Post:
```
sudo fdisk -lu
```

---

### Post by ddeile on 2009-01-26
What will that command do?

---

### Post by Pumalite on 2009-01-26
It will show your drives/partitions.

---

### Post by ddeile on 2009-01-26
Here is the output from the fdis:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ac599

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   607289129   303644533+  83  Linux
/dev/sda2       607289130   625137344     8924107+   5  Extended
/dev/sda5       607289193   625137344     8924076   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x414e1fe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   153602047    76800000    7  HPFS/NTFS
/dev/sdb2       153602048   358402047   102400000    7  HPFS/NTFS
/dev/sdb3       358402048   488394751    64996352    7  HPFS/NTFS
```

I tried to edit the grub menu list as noted in another post I just came accross.  Here is the contents of that post:

> **caljohnsmith said:**
> How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add at the bottom an entry like:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Note (hd1,0) corresponds to the 1st partition on the other drive (the Windows drive), so if your Windows is on a different partition, you'll need to adjust that. If that doesn't work, then please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

That did not do anything.  This post mentioned to add this to the bottom of the menu.list file.  That file was blank.  Adding it did not update my boot menu.

I'm runnning 8.10, if that helps.

---

### Post by ddeile on 2009-01-26
My problem is that I edited menu.list instead of menu.lst (why it's blank).  I'll edit the correct file in a bit and see if that corrects it.

---

### Post by Pumalite on 2009-01-26
When you get to Grub; choose Windows, then edit boot: hit 'e', then 'e' again and try different combinations until you find your Windows. After you change (hd1,0), hit 'Enter', then 'b' to boot. You can then make the changes permanent in menu.lst. Try: (hd1,1); (hd1,2), etc.

---

### Post by domokunrox on 2009-01-26
Not to hijack your thread dude, but lets kill 2 birds with one stone because we're almost identical in problem

here is my situation
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21432143

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b9b3b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux
domokun@domokun:~$ 
```

As you can see, I want to install windows on that 500GB drive, but the WinXP SP2 CD is throwing a hissy fit over GRUB. Would the best course of action be similar to what the OP did? Disconnect the other drive and install? Or can I b*tchslap windows XP and tell it to get on the drive and shutup? I prefer the latter. Thanks!

---

### Post by ddeile on 2009-01-26
Got it working.  Succesfully dual booting both windows and ubuntu.  Thanks.

---

### Post by Gflatman on 2009-01-26
I am having a simular problem only my setup is Windows xp on my primary sata drive (sdc), I have successfully loaded Unbuntu on my sec sata drive (sdd). When i boot the PC it goes straight to windows, I never grub or anything like that. How do i go about fixing this issue?

---

### Post by caljohnsmith on 2009-01-26
**Gflatman**, if you can set your BIOS boot order so that the Ubuntu drive is booted first on start up, that would be the most ideal. To make sure Grub is properly installed to the MBR of your Ubuntu drive, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu drive, and let me know how far you get.

---

### Post by Gflatman on 2009-01-26
I do not see grub at all and the drives i saw were labeled sdc and sdd. At this point the system boots fine to windows but never sees the other sata drive and there is no way to swap them at this time.

---

### Post by Gflatman on 2009-01-30
I have reinstalled Unbuntu on my secondary sata drive sdd. Win Xp is on my primary Sata drive sdc. I am at theUnbuntu "Ready to Install" i then clicked on the "advanced" button in the lower right now it is asking for a "boot loader install" i am wondering what i should here? I want the system to dual boot til i get comfortable with Unbuntuu.

---

