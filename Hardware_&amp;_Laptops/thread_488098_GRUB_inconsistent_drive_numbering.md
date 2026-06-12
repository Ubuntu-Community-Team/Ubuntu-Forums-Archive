---
title: "GRUB inconsistent drive numbering?"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by Trebaruna on 2007-06-29
Just installed Ubuntu again next to winxp, but instead of everything going smoothly GRUB threw an error 22 at me. According to [this]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html") page that means "no such partition". I've no idea why it would say that: the installer never complained, menu.lst looks to be okay and so does fstab...

Right now it is setup as follows: sda has a windows partition and holds "/".
sdb has an NTFS partition, and also an extended partition holding the filesystems swap, tmp, var, home, boot and usr. Note that all the linux partitions except boot -which is ext2- are XFS.
The drives sda, sdb and sdc (the latter is a data drive) are on an nForce 4 SATA controller. sdd and sde (also both data) are on a Sil3114 SATA controller which ties into the PCI bus.

It has worked before, though when I had to reinstall windows due to redesign I couldnt get GRUB to work again, so I went about reinstalling Ubuntu.

After some attempts at getting it to work it would appear GRUB is a bit indecisive: for the LiveCD it seems to indicate /grub/stage1 is on hd1,5 one boot, and hd3,5 another. Also it now seems I can boot if I tell my BIOS to boot off of hd1, but only if I tell GRUB that the root is on hd0,5.
So it seems it is inconsistent in numbering drives in different environments.

I am stumped at the moment. I've only got a few months of experience and this is totally bewildering to me. Gparted and windows always show the drives in the same order, only GRUB seems to be confused. I could just leave it sit the way it is now but I dont much trust it, and also I'd very much like to know if there's anything I can do to help GRUB see the drives in the same order all the time.

Would anyone perhaps have some pointers, tips, hints, or anything?

---

### Post by logos34 on 2007-06-29
What is the output for

**sudo fdisk -l** 
(lowercase L)

---

### Post by logos34 on 2007-06-29
If you want to know about grub, [start here]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by Trebaruna on 2007-06-30
Thank you for your response, logos34.

After getting this install of Ubuntu to work it does appear it swaps the order of controllers on every single boot.

Output of fdisk -l on one boot:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2676      522112+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdb2            5223        6793    12619057+   5  Extended
/dev/sdb5            5223        5287      522081   82  Linux swap / Solaris
/dev/sdb6            5288        5291       32098+  83  Linux
/dev/sdb7            5292        5357      530113+  83  Linux
/dev/sdb8            5358        5422      522081   83  Linux
/dev/sdb9            5423        5487      522081   83  Linux
/dev/sdb10           5488        6793    10490413+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sde: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1      387621   195360952+   7  HPFS/NTFS

```

And then for the other:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      387621   195360952+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdc2            2612        2676      522112+  83  Linux

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdd2            5223        6793    12619057+   5  Extended
/dev/sdd5            5223        5287      522081   82  Linux swap / Solaris
/dev/sdd6            5288        5291       32098+  83  Linux
/dev/sdd7            5292        5357      530113+  83  Linux
/dev/sdd8            5358        5422      522081   83  Linux
/dev/sdd9            5423        5487      522081   83  Linux
/dev/sdd10           5488        6793    10490413+  83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       60801   488384001    7  HPFS/NTFS
```

The first one is the way I want it, and the way the previous install saw it. Also, it is how windows sees it.
It does strike me as strange that all first partitions have the boot flag set, but I'm afraid I do not know which partition would need the flag seeing as how / is on sda2 and /boot on sdb6.

Further advice would be much appreciated!

---

### Post by logos34 on 2007-06-30
I have to confess I'm having a hard time making sense out of your setup--lots of drives and partitions, changing filesystem formats and arrangements, different controllers, etc etc.  Seems a case of musical hard drives.  But like you say it seems that the drives are at least recognized by the BIOS (which grub uses) consistently in the same order on each sata controller--it's just that the order in which the bios recognizes the CONTROLLERS changes seemingly with every boot. 
And it also appearS that changing filesystems from XFS to NTFS caused some mischief. I googled around and found no shortage of issues with the Sil3114 controller in linux (although some of it was old and whatever issues there were with previous linux kernels have probably been addressed by now in the 2.6.20 kernel).  My only suggestions are these (probably stuff you;ve already tried):
-flash the bios with the latest version
--poke around in the bios and set RAID to Disabled if necessary--there's a slim chance that if it's enabled it may be affecting the boot even though your drives aren't Raided
--while you're at it disable any ports you aren't using, like parallel and serial (frees up sys resources)
--try Plug 'n play OS vs. Let BIOS configure settings
--try putting the drives with the bootable linux and windows partitions on the nforce sata controller and swap out one of the drives to the Sil3114 controller.  (I may have gotten that backwards)

I don't think the boot flags on the partitions are the problem.  But grub should definitely be pointing to the /boot--not / partition--because that is where the config files are, as well as images initrd.gz and vmlinuz.  Grub points to /boot at different locations because it queries the bios to find the boot partitions, and since the order in which the bios recognizes the controllers changes with every boot, so does the numbering of the drive--hence hd1,5 (2nd drive, 6th partition) vs. hd3,5 (4th drive, 6th partition).

edit:
> After some attempts at getting it to work it would appear GRUB is a bit indecisive: for the LiveCD it seems to indicate /grub/stage1 is on hd1,5 one boot, and hd3,5 another. **Also it now seems I can boot if I tell my BIOS to boot off of hd1, but only if I tell GRUB that the root is on hd0,5.**

The reason is that when you set any drive as the first bios drive it becomes '**hd0'**, hence the need to change the location of /boot to (hd**0**,5)

---

### Post by Trebaruna on 2007-07-01
Thank you again for your time and effort, logos34.

I'd already setup the BIOS to disable any unused ports/controllers, and RAID was disabled for both SATA and IDE.
I cannot find a PnP/BIOS setting, or it is labeled differently so that I dont recognize it.

However: it seems that I overlooked a very basic option (or messed something up before): both system drives on the Sil3114 and the data drives on nForce4, with corresponding BIOS boot order. So far, it seems to work. Ubuntu boots from the drive it is supposed to be on, Windows boots from GRUB...
Ubuntu still has difficulty keeping the order straight once it actually starts booting, but at least GRUB is now keeping them straight. And of course, since Ubuntu itself uses UUIDs for everything it seems to be quite unaffected by the muddling up.

So the immediate problem seems solved. The next question, which is now more a sort of interesting learning experience rather than an accute problem, is can I tell Ubuntu in which order it should list and label its drives?

Also, I know the whole list of partitions and filesystem types sounds confusing, but if you see them in Gparted they make more sense, and also coming up with the system made sense, at least at the time. Basically I want XFS for its qualities but GRUB doesnt like it, and I want my mountpoints on different partitions to give them different flags (like ro, nosuid, et cetera). I will however, review the system in the light of flexibility.

Anyway, thanks very much for your attention so far, and any last educational links would be much appreciated. I've yet a long way to go in the realm of linux :)

EDIT: also, after reading your post again: I dont know if it was/is the BIOS that gives trouble. I've a feeling there was somewhere something else not quite in order, but I truly have no idea. As long as it keeps working I am quite happy to let it sit this way.

---

### Post by logos34 on 2007-07-01
> However: it seems that I overlooked a very basic option (or messed something up before): **both system drives on the Sil3114 and the data drives on nForce4, with corresponding BIOS boot order. So far, it seems to work.** Ubuntu boots from the drive it is supposed to be on, Windows boots from GRUB...
Ubuntu still has difficulty keeping the order straight once it actually starts booting, but at least GRUB is now keeping them straight. And of course, since Ubuntu itself uses UUIDs for everything it seems to be quite unaffected by the muddling up.

Ok, so my suggestion to swap the drives on the controllers works (I just had it backwards -- the bootable sys drives sda and sdb were on the nforce controller and now work when swapped to the Sil3114 controller.  Got it.)  Good to hear that grub is now able to identify them consistently.

Lucky your fstab and kernel lines in menu.lst are using UUID designations, otherwise you'd have real problems.

> So the immediate problem seems solved. The next question, which is now more a sort of interesting learning experience rather than an accute problem, is can I tell Ubuntu in which order it should list and label its drives?

Not sure.  Maybe setting a disk/volume label for each one, if only to make it easier to differentiate them at a glance.  (because fdisk -l and gparted may contiunue to see them according to their drive lettering 'sda' etc, which changes with every boot).  At least they'll show up in your file browser with the same name.

---

### Post by logos34 on 2007-07-01
One way would be to use e2label (you could also try tune2fs):
[B]
sudo apt-get install e2fsprogs[/B]

Then, for example, 

**sudo e2label /dev/sda DRIVE_NAME**

Then change the mount point in fstab to match new name.

more info:

man e2label

*'How to Label' (e2label) section here:
[http://doc.gwos.org/index.php/Understanding_fstab#Ext2.2F3](http://doc.gwos.org/index.php/Understanding_fstab#Ext2.2F3)

---

