---
title: "Clonezilla - &quot;Unknown partition exists&quot; and &quot;grub not found&quot;"
date: 2008-10-07
forum: General Help
---

### Post by bobby_d on 2008-10-07
Hi all, 

Searched for ages for this on teh Internets, and barely found my way out. I decided to post here, since Clonezilla forum is on sourceforge, and is not searchable (at least I couldn't find out how). 

Basically, I used Clonezilla to clone a FAT32 XP partition (originally at around 30GB, with only couple of gigs used) to an image on an extern USB drive, also FAT32. All went fine, the problems appeared when I tried to restore the partition. 

The problem is, before restoring, I had reformatted the original disk, and resized partitions as well. Then when I tried to restore using Clonezilla on /dev/hda1, I would get an error like: 
"Unknown partition /dev/hda1 exists"

Subsequent tries might not mention that (as the MBR would unpack in the meanwhile, and screw up the partition entry for /dev/hda1, which was confirmed by booting into Ubuntu Live and Gparted afterwards), but it would apparently fail looking for GRUB (something similar to [this]("http://translate.google.dk/translate?hl=en&sl=fr&u=http://www.frreader.com/msg/1072617.aspx&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3Dclonezilla%2B%2522squashfs%2Berror%2522%2Bntfs%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG"): or [this]("http://ubuntuforums.org/archive/index.php/t-287522.html"))

> > - SQUASHFS error : can't find a SQUASHFS superblock on sdax 
> (Same message for 4 partitions sda ... when there are 6) 
> Then 
> - Grub directory is not found, maybe it does not exist (although there  
> Because I use this bike dual boot), or th file system is not  
> Supported in the kernel. Skip grub-install. 

Well, the solution was close in [here]("http://drbl.nchc.org.tw/one4all/desktop/download/stable/RELEASE-NOTES"): 

>   - "-r" option of clonezilla was turned off by default, since this might cause some problems if an unknown partition exists. Thanks to Thomas Moler.

-r option is about resizing a partition - this got confirmed by [this post]("http://rolfje.wordpress.com/2007/11/06/clonezilla-m4d-sklz/"): 

> I use clonezilla often, to clone xp between machines; There are two things that don’t work — period — you can’t clone to a smaller HD even it is only 1 sector smaller — I discovered that this is LBA’s other such cryptic numbers on the actuall hardrive lables are.

Ok, THEN I decide to check what are the actual sizes of the imaged and actual partitions. The image size can be read from hda-pt.parted and hda-pt.sf in the Clonezilla image dir, but it is given as num of sectors, so you have to multiply by sector size in bytes to get the total; used Gparted in Ubuntu for the size of actual partition. And guess what, the original partition image was 30*1024 MB, whereas the current was made to be 30000 MB - so obviously smaller. 

Once more Ubuntu Live/ Gparted, resized the partition, tried the clonezilla restore - now it works :) Directly afterwards, botting would not work due to "NTLDR is missing", but one more time boot to Ubuntu Live/ Gparted, manage flags of the partition, mark with boot flag, restart - and all seems to be fine!!!

Well, in this case, I guess an error message like "target partition smaller than image partition" would be more useful than "Unknown partition exists", no? :)

Well, hope this helps someone... :popcorn:

---

