---
title: "XP not appearing in Grub - new sata drive"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by albrown41 on 2009-02-17
Here's the situation:

I had XP installed on my desktop on an 40 GB IDE.
I just added a new 80 GB SATA drive. I reinstalled XP, but didn't unplug the IDE drive when I did it, so apparently the MBR was on the old IDE drive.  So I installed Ubuntu on the new SATA drive (with the old IDE unplugged), thinking with grub I'd be able to boot to windows.

For some reason, I XP doesn't show up in the Grub list, even though I can access the windows partition from within Ubuntu.

I've read on here that you are supposed to add an entry to menu.lst for xp.  I've tried that, but can't seem to get it set right for the partition.  I'm confused with the (0,1) etc. I've tried with lots of combinations, and am not sure what to put on the root (?,?).

When I run: sudo fdisk -lu at terminal, I get

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007ea5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   105161489    52580713+   7  HPFS/NTFS
/dev/sda2       105161490   156296384    25567447+   5  Extended
/dev/sda5       105161553   153983024    24410736   83  Linux
/dev/sda6       153983088   156296384     1156648+  82  Linux swap / Solaris



sda1 is the windows partition, right?  How do I make grub see it?

---

### Post by cdtech on 2009-02-17
This is a warning that fdisk does not support GPT which is probably not compiled in the kernel. What kernel and version of Ubuntu are you using?

You'll need to use gparted to see the device layout rather than fdisk.

---

### Post by caljohnsmith on 2009-02-17
Before setting up Grub to boot Windows, the first question is: did you intentionally set up your sda drive with a GPT (GUID Partition Table)? Unless you are using a Macintosh, I doubt your BIOS supports it. If you don't have a BIOS that supports GPT, I would recommend erasing the GPT sectors that come after the MBR. Also, there is a copy of the GPT stored at the very end of the HDD which you will have to erase too. So if you didn't intentionally set up a GPT, how about doing:
```
sudo dd if=/dev/sda count=70 | gzip -c > ~/Desktop/sda.MBR.gz
```
That will create a small "sda.MBR.gz" file on your desktop that will contain the sectors with the GPT information. Please attach that to your next post if you would like help removing the GPT from your HDD.

---

### Post by albrown41 on 2009-02-17
No, I didn't do it on purpose. I'm not particularly sure what that even means... so here's my question:  How complicated/time consuming will this be (I'm pretty new at the linux game)? And would it be faster to just reformat the drive and reinstall windows and ubuntu?

If the latter, is it better to install xp first or second?

What did I do wrong to end up with a GPT. I'm not on a mac

Oh, and it's XP pro and Ubuntu 8.1

---

### Post by cdtech on 2009-02-17
I've seen a corrupt MBR cause this problem (garbage at the end of the sector). It would probably be to your benefit to reinstall, if you have nothing to save. XP first.

Are you installing two drives? or is this one drive, separate partitions?

---

### Post by albrown41 on 2009-02-17
well, this is all on one. There is going to be a second one too (the original IDE drive - 40 GB)

Am I better off doing them on seperate drives rather than partitions on one, with the other as space accessible to both?

---

### Post by Twitch6000 on 2009-02-17
I find it easier doing it on the saem driver and installing xp first.

Because then ubuntu will detect xp and you just partition and it will install grub and add windows to boot up

If you install ubuntu first it gets a bit more complicated =[.

---

### Post by cdtech on 2009-02-17
I have two separate drives. I installed Ubuntu on the second drive and chose to install GRUB on the Ubuntu drive (second drive). I then swapped drives (primary / secondary) so now the PC would boot into the GRUB menu and edited the menu.lst file to include the Windows drive.

I used this method because I didn't want to corrupt the MBR of the Windows drive. You can do it anyway you want......

---

### Post by caljohnsmith on 2009-02-17
I would not recommend reinstalling yet unless you particularly want to, because it is usually a simple matter to convert a GPT to a standard MS-DOS partition table; the reason is because the GPT fortunately leaves the MBR untouched (where a standard MS-DOS partition resides) and only uses the sectors that come after the MBR. Thus if you simply erase the sectors that contain the GPT, that is usually all it takes to fix the problem. If you plan on reinstalling anyway, you have nothing to lose by trying and seeing if it solves the problem. If you want to give it a shot, please post the output of all the following commands:
```
sudo dd if=/dev/zero of=/dev/sda seek=1 count=60
sudo dd if=/dev/zero of=/dev/sda seek=156296400
```
Then try again:
```
sudo fdisk -lu
```
And hopefully it won't complain about a GPT again. Also, if it works, you might have to reinstall Grub again, but first let me know if fdisk doesn't report a GPT any more, and we can work from there if you want.

---

### Post by albrown41 on 2009-02-17
I just decided to reformat last night.  I think the problem was that I pulled the new sata out of a macbook.  when i did the windows install, i just did the quick ntfs format... maybe that's why i had the guid.

everything seems to be working now... thanks for all the help everyone!

---

### Post by curly_nostrill on 2009-04-22
> **caljohnsmith said:**
> ...the following commands:
```
sudo dd if=/dev/zero of=/dev/sda seek=1 count=60
sudo dd if=/dev/zero of=/dev/sda seek=156296400
```
Then try again:
```
sudo fdisk -lu
```
And hopefully it won't complain about a GPT again. Also, if it works, you might have to reinstall Grub again, but first let me know if fdisk doesn't report a GPT any more, and we can work from there if you want.

I cannot thank you enough.  I've been tearing my hair out over this for days.  After googling all kinds of Mac advice and other useless or incomplete info, I googled "dd if=/dev/zero erase gpt" I finally found this post.  I'm actually using Debian 5.  Even though the drives seemed to work properly with the gpt record, the fdisk warning was driving me crazy.

I had tried ```
dd if=/dev/zero of=/dev/hdb
``` on my 500gig ide and after a day it was about 2/3 done.  I ctl C'd it but still had the warning.

Your directions worked great but I still had to do a little figuring.

The first command wipes the hidden sector just after the MBR I assume.

The second command I altered by subtracting 5088 from the total sectors reported by fdisk -lu for my drive.  Et, VOILA! No more warning! YAY!

Please report my errors in assumption if anyone sees any since I'm sure this isn't the last time I'll have to do this.

Thanks again.
:popcorn:

---

### Post by caljohnsmith on 2009-04-23
> **curly_nostrill said:**
> I cannot thank you enough.  I've been tearing my hair out over this for days.  After googling all kinds of Mac advice and other useless or incomplete info, I googled "dd if=/dev/zero erase gpt" I finally found this post.  I'm actually using Debian 5.  Even though the drives seemed to work properly with the gpt record, the fdisk warning was driving me crazy.
Glad to hear it worked OK. :)
> 
Your directions worked great but I still had to do a little figuring.

The first command wipes the hidden sector just after the MBR I assume.

Yes, the GPT takes up about 34 sectors after the MBR if I remember correctly, so the bottom line is to just wipe the sectors clean after the MBR but before the start of the first partition. Usually the first partition starts on the second track of the HDD, or sector 63. 
> 
The second command I altered by subtracting 5088 from the total sectors reported by fdisk -lu for my drive.  Et, VOILA! No more warning! YAY!

Please report my errors in assumption if anyone sees any since I'm sure this isn't the last time I'll have to do this.

Thanks again.
:popcorn:
The GPT standard calls for also having a backup of the GPT at the very end of the HDD; therefore, to make sure you wipe all traces of the GPT, you can just wipe all the sectors clean after the end of the last partition (you can use fdisk -lu to find the ending sector of the last partition), which is what I originally recommended to albrown41 with the dd command that starts at sector 156296400. Or you could subtract about 34 sectors from the ending sector of your HDD and wipe those sectors clean, because those should be the GPT backup sectors. Anyway, I'm glad that you were able to get rid of your GPT without going to the extreme of wiping the entire drive clean or something like that, because it is certainly not necessary to do so. :)

---

