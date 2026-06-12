---
title: "Issues with adding Ubuntu to a Triple Boot System"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by jackschmaltz on 2009-05-20
hey all,

this is my first time installing ubuntu & have run into a few problems (oh the joys of being a noob again haha!). previous to installing i read multiple guides on the web & with past experience in setting up dual boots i felt confident enough to give it a blast. so i'll try & give as much detail as possible as to what i did.

i currently have a triple boot system with 2x XPx86 & 1x Vistax86 & have decided to try Ubuntu (i gave the Live CD feature a go & was very impressed so would like to delve further). the 1st XP boot is on its own drive (which i have no intention of touching / messing with) whilst the 2nd XP boot & Vista boot are on the same partitioned drive.
so, i shrunk the 2nd XP partition in Vista leaving me with unallocated space for the Ubuntu boot.
i rebooted my system with the Ubuntu disc in, chose to install, set region etc. & on the Prepare Partition page it detected i had Vista & i chose Use Largest Available Free Space to install too. wrote my log in details, chose not to migrate my documents (as all my files etc. are on seperate discs, i rarely store files to the actual OS) & everything appeared fine so chose to continue with the installation.
the installation procedure appeared to go fine, no errors & took about 10-20 mins. chose to restart as prompted & the GRUB loader never appeared, only the Vista Loader with my boot options as i previously had.
so i went into Vista again & rebooted with the Ubuntu CD & went Live, checked my HD & sure enough Ubuntu had installed. so its there, but no GRUB loader.

could it be that i need to install the GRUB loader to another HD rather the 3 partitioned HD with the Vista Loader? if so what is the best way to go about this, would it to be to freshly install Ubuntu? i tried EasyBCD in Vista to see if i could acess the Ubuntu boot after backing up the menu.lst and adding the partitions from this but with no joy.

any help would be greatly appreciated, thanks for your time :D

---

### Post by themusicalduck on 2009-05-20
The grub loader might have been installed onto the other HD for some reason. It might be worth changing the boot order in the bios to the other HD to see if it will load from it.

Also it's might be helpful for people if you post the output of ```
sudo fdisk -l
```on a terminal while booted into the live CD.

---

### Post by jackschmaltz on 2009-05-21
> **themusicalduck said:**
> The grub loader might have been installed onto the other HD for some reason. It might be worth changing the boot order in the bios to the other HD to see if it will load from it.

Also it's might be helpful for people if you post the output of ```
sudo fdisk -l
```on a terminal while booted into the live CD.

thank you for your response.
i tried changing the boot order but with no joy.

heres output from the terminal when booted live:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fe410e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08c508c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   42  SFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08820881

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31360091

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       15201   122102001    7  HPFS/NTFS
/dev/sdd2           15202       22808    61102508    7  HPFS/NTFS
/dev/sdd3           22809       30401    60990772+   5  Extended
/dev/sdd5           22809       30085    58452471   83  Linux
/dev/sdd6           30086       30401     2538238+  82  Linux swap / Solaris

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb12982fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48641   390708801   42  SFS

```hope this helps, as i dont have a clue what any of that means to be honest.

thanks for your time, all help appreciated :D

---

### Post by jackschmaltz on 2009-05-21
can anybody help with this issue?

iv tried multiple things in EasyBCD again with no luck, i basicly just want the GRUB loader to show or at least see where i maybe going wrong.

thanks for your time

---

### Post by Zimmer on 2009-05-21
Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       15201   122102001    7  HPFS/NTFS
/dev/sdd2           15202       22808    61102508    7  HPFS/NTFS
/dev/sdd3           22809       30401    60990772+   5  Extended
/dev/sdd5           22809       30085    58452471   83  Linux
/dev/sdd6           30086       30401     2538238+  82  Linux swap / Solaris

So, it looks like your Ubuntu is on sdd5, an extended partition .
This is where you found the /boot folder and grub and the menu.lst file when you investigated with the live cd?

EDIT: You used that info for EasyBCD,yes?

---

### Post by jackschmaltz on 2009-05-21
> **Zimmer said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       15201   122102001    7  HPFS/NTFS
/dev/sdd2           15202       22808    61102508    7  HPFS/NTFS
/dev/sdd3           22809       30401    60990772+   5  Extended
/dev/sdd5           22809       30085    58452471   83  Linux
/dev/sdd6           30086       30401     2538238+  82  Linux swap / Solaris

So, it looks like your Ubuntu is on sdd5, an extended partition .
This is where you found the /boot folder and grub and the menu.lst file when you investigated with the live cd?

EDIT: You used that info for EasyBCD,yes?

yes i used this info in EasyBCD.  i had copyed the menu.lst over to my windows boot so i could access it for this reason, but still no avail.

im not sure how or what an extended partition is to tell you the truth, all i did was delete the partition in windows & chose the empty space in the Ubuntu installer. everything seemed to install fine untill reboot, im really at my wits end, really dont know what else to try & tbh a little disheartened with my first ubuntu experience as i was so looking forward to using it.

thanks for your time

---

### Post by Zimmer on 2009-05-21
the entry you created in easybcd should have been for Ubuntu on sdd4 (EasyBDC numbers the partitions like GRUB, starting from 0.  So whatever is partition 1 on the disk is 0 to GRUB and EasyBCD).
Is the solution that easy? I guess not because you mention copying menu.lst to another boot partition. Where? have you got GRUB installed to boot Windows? and Can you tell me how you are booting , what drive, boot order etc.?

---

### Post by jackschmaltz on 2009-05-21
> **Zimmer said:**
> the entry you created in easybcd should have been for Ubuntu on sdd4 (EasyBDC numbers the partitions like GRUB, starting from 0.  So whatever is partition 1 on the disk is 0 to GRUB and EasyBCD).
Is the solution that easy? I guess not because you mention copying menu.lst to another boot partition. Where? have you got GRUB installed to boot Windows? and Can you tell me how you are booting , what drive, boot order etc.?

i only copyed menu.lst to my Vista desktop just so i could view it in Vista & add its entrys to EasyBCD.

GRUB loader isnt showing up on start up, which is my only problem it would seem.
the files are there for it, so i have no idea what the problem is with it.
im booting from my Vista drive which is partitioned & includes my 2nd XP & Ubuntu on the other partitions, my 1st XP is on a seperate disk.
so my computer boots straight into the Vista boot loader with the option of Vista or older os boots which includes choices for both my XP boots when selected, no linux in sight.

as for my boot order, its CD-rom, Vista HD, 1st XP HD.

thank you for your time, its appreciated. if theres no solution id imagine id have to reinstall & try again but im certain i selected the right options the 1st time around.

---

### Post by Zimmer on 2009-05-21
You should not have needed to copy menu.lst to read the entries.

If you just start EasyBCD and select add and select the Linux tab, then select the correct partition from the other dropdown list that should be all that is required.

The Vista loader should then contain your 3 entries (Vista, XP and Linux).
selecting the Linux entry should load GRUB , which you should have installed to the Ubuntu partition, NOT the MBR. As your Vista still boots I am guessing you did not install GRUB to your MBR :)
The only other thing I can think of at the moment is that you may need to use a partitioning tool to set the Ubuntu partition's boot flag. But, as there is no entry in your EasyBCD loader screen for Linux I think you should start there...
Regards

must go , it is 1:30 am here...

---

### Post by jackschmaltz on 2009-05-21
> **Zimmer said:**
> You should not have needed to copy menu.lst to read the entries.

If you just start EasyBCD and select add and select the Linux tab, then select the correct partition from the other dropdown list that should be all that is required.

The Vista loader should then contain your 3 entries (Vista, XP and Linux).
selecting the Linux entry should load GRUB , which you should have installed to the Ubuntu partition, NOT the MBR. As your Vista still boots I am guessing you did not install GRUB to your MBR :)
The only other thing I can think of at the moment is that you may need to use a partitioning tool to set the Ubuntu partition's boot flag. But, as there is no entry in your EasyBCD loader screen for Linux I think you should start there...
Regards

must go , it is 1:30 am here...

thank you for your time

yes, there was an entry in EasyBCD which i tried before hand, came up with the Linux & swap partitions (seperatly of course :D) then i tried manually putting it in with no success either.

well, at least it would appear im not totally knackered just yet then haha, i'll have another play around with it. i really dont get why its making it so hard for me, iv read multuple articles & watched a few vids, followed to the letter & oops, no go :).

thanks again for your time, its appreciated

---

### Post by Zimmer on 2009-05-22
[http://neosmart.net/wiki/display/EBCD/Changing+the+Vista+Boot+Drive](http://neosmart.net/wiki/display/EBCD/Changing+the+Vista+Boot+Drive)

and
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Can you make sense of that...?
[http://www.multibooters.co.uk/bootmgr.html](http://www.multibooters.co.uk/bootmgr.html)
from the above it might be the case that EasyBCD has edited a BCD file that is not used when you boot, but I am just guessing here...

So much to read, so little time...

---

