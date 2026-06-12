---
title: "Murdered Windows Vista?"
date: 2008-09-03
forum: General Help
---

### Post by Canadian_Psycho on 2008-09-03
While I can't say that I would feel terribly if this were the case, I think the kids are going to light my bed on fire as I sleep.

I went about installing Ubuntu and now do not get an option to boot into Windows Vista on my desktop PC.  Did I just unceremoniously kill Windows Vista Home Basic or is there a way to retrieve the files which I admittedly...did not back up.  *sigh*

Even better, is this simply a case of the MBR being rewritten by Ubunti and is Windows still lurking around on my HD somewhere just waiting to be booted in to?

Cheers

---

### Post by RolandFlagg on 2008-09-03
simple way to test that, in ubuntu, can you see the windows partition at all? if you can, then u probably just hav to change the booting thing, otherwise... bad luck i guess

---

### Post by Canadian_Psycho on 2008-09-03
Nope, can't see anything at all.  That and the hard drive seems very very roomy.

It's definitely dead I guess.  Ah well, thanks anyway.  I'll see what I can do to mitigate the tears.  A literary masterpiece about horses was on there I am told...bad bad news!

Cheers

---

### Post by fooman on 2008-09-03
might still be there....run the following command in a terminal and post the output back here:

```
sudo fdisk -l
```

---

### Post by Canadian_Psycho on 2008-09-03
What character is that last character in the command?  I thought it was a one but looking closer, it's not?

Cheers

---

### Post by drs305 on 2008-09-03
> **Canadian_Psycho said:**
> What character is that last character in the command?  I thought it was a one but looking closer, it's not?

Cheers

small L == sudo fsdisk -l

---

### Post by Canadian_Psycho on 2008-09-03
Unfortunately it gave me nothing.

Upon typing in sudo fdisk-l it give me "sudo: fdisk-l: command not found"

upon typing in "sudo fdisk" I get the following if it's relevant to this at all.

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
```

Cheers

---

### Post by fooman on 2008-09-03
yeah,  sorry thats a lower case "L"

---

### Post by drs305 on 2008-09-03
> **Canadian_Psycho said:**
> Unfortunately it gave me nothing.

Upon typing in sudo [COLOR="Red"]**fdisk-l**[/COLOR] it give me "sudo: fdisk-l: command not found"

upon typing in "sudo fdisk" I get the following if it's relevant to this at all.

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
```

Cheers

There is a space in there:  sudo fdisk -l

It's best just to cut and paste the commands if you can... ;-)

---

### Post by Canadian_Psycho on 2008-09-03
Ah I see....uno momento

---

### Post by DanJC on 2008-09-03
There needs to be a space between "fdisk" and "-l".

So instead of "sudo fdisk-l" it should be "sudo fdisk -l".

EDIT: Oops, looks like someone got there before me. :)

---

### Post by Canadian_Psycho on 2008-09-03
output is as follows.

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1506d080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19740   158561518+  83  Linux
/dev/sda2           19741       20023     2273197+   5  Extended
/dev/sda5           19741       20023     2273166   82  Linux swap / Solaris

```

Cheers

---

### Post by WYzzard on 2008-09-03
The command is 
```
sudo fdisk -l
```
 that is sudo [space] fdisk [space] -l (lower case L)

---

### Post by RolandFlagg on 2008-09-03
yea it doesn't seem to be there... if it's there there should be something that says "NTFS"... you still have a recovery disk or something for vista right?

---

### Post by Canadian_Psycho on 2008-09-03
Wll just a recovery disk.  Made it from the ACER laptop.  Unfortunately, it will not bring back any of the files I am seeking, just Vista.

I'm not sure I want uninstall ubuntu and put vista on just so I can put ubuntu on again as a dual boot system.

Thanks anyway.  I do appreciate the effort a great deal.

Cheers

---

### Post by charonred on 2008-09-03
If you still want or need to run Vista, then virtualisation is the answer; just run Vista inside Ubuntu.

There are several Virtualisation systems available, but I've chosen VirtualBox which I think is great.

There's the OSE (open source edition) available from the Ubuntu repositories via Synaptic Package Manager, or the proprietory (but still free) version from Sun Microsystems.

I installed the Sun xVM version a few days ago (it comes with USB support enabled, whereas the OSE edition doesn't)

[get it from here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") (24 MB); just select the Ubuntu version and download it, then click on it for the install process - easy as.

I have XP Pro and Vista Ultimate installed in VBox and both work fine. Both the OS's install and run faster than they did natively on their own hard disc -  and the kids might just thank you for making Vista 'better' (maybe)

---

### Post by Shazaam on 2008-09-03
Not trying to stir the pot but that is an odd size for a hard drive (164.6gigs). Could there be a bios-locked Recovery partition hiding somewhere? Usually fdisk will show those.

---

### Post by Gannon8 on 2008-09-03
Try using testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by bobbob1016 on 2008-09-04
Try using a file-recovering program.  Usually boots off of a CD.  This one [http://www.download.com/Active-File-Recovery/3000-2248_4-10174457.html?tag=mncol&cdlPid=10792192](http://www.download.com/Active-File-Recovery/3000-2248_4-10174457.html?tag=mncol&cdlPid=10792192) requires Windows to be installed.  I'd suggest taking the drive out, putting it in a $30 drive enclosure, and running the program I gave you.  You should be able to get some files back, not sure if all though.

---

