---
title: "Ubuntu installed on 500MB partition; now can't use the other 74GB"
date: 2005-11-06
forum: General Help
---

### Post by Roobert on 2005-11-06
Wow, what a day yesterday was. I had XP running on one partition, Ubuntu on another, and everything was golden. Then I decided I wanted more space allocated to Ubuntu, so I tried to resize my Windows NTFS partition (hee-hee....oops) and bam, lost everything. That is, I couldn't boot off of the Windows partition anymore. So, I had to reformat the entire disk. That sucked.

My problem that I need help with now is that I after completely re-formatting my drive and re-installing Ubuntu, I thought I had allocated it my entire 75GB hard disk, but apparantly, Ubuntu created a separate 500MB partition (hda1, type ext3), installed itself on that partition, and the rest of my ~74.5GB is being unused on an extended partition (hda2). Hda2 is sub-partitioned, with a sub-partition called hda5 that has filesystem "unknown", with a size of 74.5GB.

My question: How do I just create one big happy partition that Ubuntu runs on, with no other extraneous partitions that aren't being used?

Other than that, I love Ubuntu. This OS absolutely lives up to the hype! Thanks!

~ Roobert.

---

### Post by John.Michael.Kane on 2005-11-06
You can resize the tables using Gparted it should be under the addprograms list. if that does not help then plan-b would be to re-install and setup the tables the way you want when the install gets to the partation setup make your. my numbers may be a little off however should get you going if you need to use plan-b.

boot partation 16m
/ 1-2gig
home 70gig
swap 1.5gig

---

### Post by Roobert on 2005-11-06
Hmm, yeah I would prefer to be able to simply make the Ubuntu boot partition swallow the other huge partition somehow. But looking at it under GParted, the boot partition has a little locked icon on it...so if it is uneditable, is there any other way to add the 74.5GB empty partition to my Ubuntu boot partition? I'm kind of loathe to do a complete re-install, as I've got Ubuntu fully tweaked the way I like it. 

Thanks,

Roobert

---

### Post by John.Michael.Kane on 2005-11-06
Well i have tried to get gparted working with sudo. and no go. however i found this [http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC8](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC8)

---

### Post by poptones on 2005-11-06
Was this an install from a live CD? Have you actually booted into ubuntu?

Don't go messing with your partitions unless you're willing to reinstall again. Ubuntu will not fit in 500MB. type "cat /etc/fstab" in a terminal window and post the result here.

---

### Post by Joh_ on 2005-11-06
I sure hope you didn't have the same problem I did, cause then you wouldn't have had to reformat.

I've got 4 partitions. First one for windows (fat), second for ubuntu (ext3), third is swap, fourth is for storage (fat) so if I have to re-install anything or screw up anything I've still got my files. The problem I had was my first partition (the windows one) was hogging too much space since my ubuntu partition was getting full, so I resized both that and the ubuntu partition. Since I had grub installed on the ubuntu partition to not mess with windows, and grub obviously moved since I resized the partition, I couldn't boot anything. Neither linux nor windows. I solved this by inserting the ubuntu disc, typing **rescue** at the BOOT: prompt, and when I got access to the terminal, typing **grub-install "(hd0,1)"** to reinstall grub to my second partition and it worked like a charm. :)

Other than that, you should be able to let it "swallow" the partition (not really swallow, but to make it hog all available space after removing the other partition) using Partition Magic. That program isn't free however. :???:

---

### Post by Roobert on 2005-11-06
[QUOTE=poptones]Was this an install from a live CD? Have you actually booted into ubuntu?[/QUOTE]

Yes, I have actually booted into Ubuntu. I used the install CD, not the live CD.

[QUOTE=poptones]Don't go messing with your partitions unless you're willing to reinstall again. Ubuntu will not fit in 500MB. type "cat /etc/fstab" in a terminal window and post the result here.[/QUOTE]

I'll try not to mess around more than necessary. It's probably too late for that now, but good advice. Here's the results of cat /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc                               proc        defaults              0              0
/dev/mapper/Ubuntu-root /     ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Sorry it looks like crap. This is what I get, though. Does this help explain what's going on on my disk?

Continued Thanks,

~ R.

---

### Post by RAOF on 2005-11-06
That "/dev/mapper/Ubuntu-root" line makes me suspect that Ubuntu has set up a LVM (logival volume manager) install.

The good news is, you should never have to repartition/reformat again!  LVM allows you to add discs, resize partitions, backup, all sorts of things without formatting (so if you added another hard drive, you could extend your current partitions onto the new drive).  

The bad news is, I don't know how to actually do anything with LVM :(.  There must be someone knowlegeable in that area here...

---

### Post by RAOF on 2005-11-07
You might want to check out the links from [this post]("http://www.ubuntuforums.org/showpost.php?p=474373&postcount=3").

---

### Post by Roobert on 2005-11-08
Well, thanks for all of your help. But I did a complete re-format and re-install, and this time I got the disk partitioned correctly the first time, while still preserving my XP ntfs partition. 

Here's what it looks like now:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.2G  1.9G  6.9G  22% /
tmpfs                 249M     0  249M   0% /dev/shm
tmpfs                 249M   13M  237M   5% /lib/modules/2.6.12-9-386/volatile
/dev/hda5             4.7G  4.0K  4.7G   1% /dos (FAT32,  XP data exchange area)
/dev/hda6              45G  251M   42G   1% /home (for Linux data)
/dev/hda1              14G  2.5G   12G  18% /windows (NTFS, for windows Xp crap)


How does this look? Are the mount points OK?

---

### Post by RAOF on 2005-11-08
I'd mount /windows & /dos under /mnt, so they'd become "/mnt/dos" & "/mnt/windows".  That's mainly cosmetic, though.  Everything else looks good.

---

