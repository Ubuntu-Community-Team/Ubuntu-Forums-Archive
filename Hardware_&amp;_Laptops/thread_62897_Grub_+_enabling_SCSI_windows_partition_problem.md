---
title: "Grub + enabling SCSI windows partition problem"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by Swerver on 2005-09-06
Hi im new here!
Just installed Ubuntu and was hoping like some other distros, would just keep the windows installation as bootable in grub. it didnt, so...........

Basically i have 3 IDE drives, linux on the hda1, and 1 scsi drive with 2 parts 9I have no problem mounting these drives in ubuntu, just want to add to boot loader...

heres what fdisk shows

----------------------------------------------------------------------------------------------

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+  83  Linux
/dev/hda2            2551       14946    99570870    f  W95 Ext'd (LBA)
/dev/hda5            2551       14946    99570838+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      238216   120060832+   7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         510     4096543+   7  HPFS/NTFS
/dev/hdd2             511        4865    34981537+   f  W95 Ext'd (LBA)
/dev/hdd5             511        1785    10241406    b  W95 FAT32
/dev/hdd6            1786        3060    10241406    b  W95 FAT32

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4427    20201737+   f  W95 Ext'd (LBA)
/dev/sda5            1913        4427    20201706    7  HPFS/NTFS


---------------------------------------------------------------------------------------

i want to enable /dev/sda1 (windows partition) to be selectable in grub when booting..

what do i need to add to /boot/grub/menu.lst to get this working
I havent had this problem before with IDE drives...
Any ideas?

Cheers

---

### Post by wvslkr on 2005-09-06
# on /dev/sda1
title		Windows
root		(hd3,0)
savedefault
makeactive
chainloader	+1

This should work for you.  I am gathering the sda is the 4th drive.  If not change the 3 to the appropriate number.

---

### Post by Swerver on 2005-09-06
Thanks for that wvslkr, 

Yes the SCSI drive is the 4th Drive
I made the mistake of using sd3,0 instead of hd3, 0 thinking SCSI should be different :(

I will try this when I get home from work
Thanks again for a response, post back when it working

Brett

---

### Post by wvslkr on 2005-09-06
GL hope it works for you :)

---

### Post by Swerver on 2005-09-08
Ahhh it didnt work I have also done a lot of reading about ppl in the same situation, somethings have worked for them but in my case it doesnt seem to be, so I will explain what I have tried and done

What does work (not dual booting really) is if I change the the BIOS to boot of my SCSI drive (HDD3),  I can boot into windows, and when i switch it back to boot of HDD0 I get grub and can boot into Ubuntu.... So BOTH OS's load, nothing is corrupt

First off, my fdisk situation is still the same as my 1st post - refer to that
HDD0 is Linux and EXT2
HDD1 is storage and NTFS
HDD2 is Storage and NTFS
HDD4 is Windows and NTFS and a SCSI drive (Ubuntu sees this just fine and can mount no problems from the desktop)

Ubuntu on reinstall found my Windows installation and recommended installing to the MBR as long as no other OS's were missing, So I did this.... and the entry it put in was..

title Microsoft Windows XP
root (hd3,0)
savedefault
makeactive
chainloader +1

Now this didnt work and gave the error after selecting The windows installation with a black screen and this text, also tested with (rootnoverify) and still did not work
--------------------------------------------
root (hd3,0)
filesystem type unknown, partition type 0x7
CHAINLOADER +1
--------------------------------------------

So I then read some more and then tried this and found because windows is expected to be on HDD0 I should map the drives in reverse so it sees windows as HDD0., grub then looked like this.

--------------------------------------------
map (hd0) (hd3)
map (hd3) (hd0)
title Microsoft Windows XP
root (hd3,0)
savedefault
makeactive
chainloader +1

---------------------------------------------

This still did not work, and now gives me the infamousc missing NTDLR error, I also tried rootnoverify to test..
Now both OS's boot so this ntdlr not found thing is crap, Windows isnt corrupt!

Now I heard ppl saying that if they reinstalled Windows as FAT it worked, that is not an option I need NTFS on my system drive for XP.....

I need a dual  boot option that will work without having to switch drives in the BIOS.

Anymore ideas?

Thanks

---

### Post by wvslkr on 2005-09-09
I noticed in the fdisk printout /dev/sda1 is not marked as bootable.  Try enabling the bootable flag and see if it works then.  I don't think you need the mapping for this.

---

### Post by Swerver on 2005-09-09
yah sorry i reinstalled and the boot is active on that drive second time round....

heres the updated one..

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+  83  Linux
/dev/hda2            2551       14946    99570870    f  W95 Ext'd (LBA)
/dev/hda5            2551       14946    99570838+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      238216   120060832+   7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         510     4096543+   7  HPFS/NTFS
/dev/hdd2             511        4865    34981537+   f  W95 Ext'd (LBA)
/dev/hdd5             511        1785    10241406    b  W95 FAT32
/dev/hdd6            1786        3060    10241406    b  W95 FAT32

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4427    20201737+   f  W95 Ext'd (LBA)
/dev/sda5            1913        4427    20201706    7  HPFS/NTFS

---------------------------------------------------------------------------

hmmmm..

---

### Post by wvslkr on 2005-09-09
Only other things I can suggest:
  
I believe the device mapping goes after the root entry in menu.lst.

Possibly make sda the primary boot in bios and install Grub to it instead of hda which I'm assuming you are using now.

Consider using ntldr       [http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

Also take a look at this and see if it gives you any help or ideas  [http://ubuntuforums.org/showthread.php?t=62657](http://ubuntuforums.org/showthread.php?t=62657)

GL.

---

