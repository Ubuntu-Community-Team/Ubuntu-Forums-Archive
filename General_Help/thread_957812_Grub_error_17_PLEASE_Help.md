---
title: "Grub error 17 PLEASE Help"
date: 2008-10-24
forum: General Help
---

### Post by cynon83 on 2008-10-24
Just to get this started, I should point out that I don't think this is a normal grub error 17.  however, my system is now completely unusable and I could really use some help.

System info:
Dual boot  WinXP/Ubuntu 8.04

What happened:
I upgraded to Ubuntu 8.04.  It looked like it worked fine, however, I soon began noticing that things weren't working correctly.  Then I noticed that the / system was completely full.

I went into windows and used partition magic 8 and resized my windows partitions, then resized (and moved) the Ubuntu partitions.  Eventually, I booted back into Ubuntu, but it didn't notice the extra space and the file system was still at 100 percent.

Here's where I got completely stupid.

I ran fsk on the disk that held Ubuntu.
fsk /dev/sba was the command I used.

Naturally, I now have a completely dead machine.  I boot, and Grub error 17 comes up.  The thread in these forums points to a dead web page.

Can someone help please?  I'm really hoping this didn't hose the windows partitions.  I can rebuild the ubuntu, if I have to, but I'm going to be very,very upset if I screwed up my windows box.

Thanks for any help.

---

### Post by caljohnsmith on 2008-10-24
I'm not familiar with the "fsk" command; do you maybe mean "fsck"? Also, are you getting the Grub error 17 before seeing the Grub menu or after you get the Grub menu and select Ubuntu?

How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by cynon83 on 2008-10-24
heh.  Sorry about that.  yeah, fsck.

I don't have the live CD, I'm downloading it.  You can be sure that I'll run it once it's down and give your suggestion a try.


Also, the error comes up right after boot.  No grub menu to be seen.
Thanks!

---

### Post by cynon83 on 2008-10-25
I booted up using the 8.04 live CD and ran the fdisk command.  Here's what it came up with:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37c337c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31198229    15599083+   7  HPFS/NTFS
/dev/sda2        31198230   516714659   242758215    f  W95 Ext'd (LBA)
/dev/sda3       516714660   625137344    54211342+  83  Linux
/dev/sda5        31198293   205294634    87048171    7  HPFS/NTFS
/dev/sda6       205294698   512505629   153605466    7  HPFS/NTFS
/dev/sda7       512505693   516714659     2104483+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5908d446

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   625137344   312560640    f  W95 Ext'd (LBA)
/dev/sdb5           16128   307692944   153838408+   7  HPFS/NTFS
/dev/sdb6       307693008   625137344   158722168+   b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x236bcc0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            1008   625142447   312570720    f  W95 Ext'd (LBA)
/dev/sdc5            1071   317441375   158720152+   7  HPFS/NTFS
/dev/sdc6       317441439   625142447   153850504+   b  W95 FAT32

So after that, I ran the following command:
sudo fsck -y /dev/sda3

This came up with a ton of inod,multiply claimed block and other errors.  As far as I can tell, it's still running, but it's says it's doing a clone multiply-claimed blocks.  However, it started that quite a while ago, so I have no idea if it's hung.  I'll probably let it run over night, because I'd rather not kill the process.  I'll have to, however, if I get up in the morning, and find that it's still in the same spot.  At that point, I'd have to assume it was froze, and now my system is totally hosed.  Hope that doesn't happen.

If it does though, I do a repair and get my windoze partition back, then re-install linux from scratch.  That would be annoying, but not catastrophic.

Please feel free to chime in if you have any info you think would help me.

Thanks!

---

### Post by cynon83 on 2008-10-25
Well, fsck stayed in that state for over 2 hours with almost no hard disk access, so I killed the process.  Rebooted and wahoo... I get a new error.  This time Error2.  So, I rebooted into the live CD and am running fsck again in hopes that this time it will work.

If it doesn't, and no one has any help, I'll try and repair the MBR with a windoze disk.  

But some help would be very welcome.

---

### Post by caljohnsmith on 2008-10-26
Well if reinstalling Ubuntu is an option like you mentioned, that would probably definitely fix your problem. If you have any files you want to recover from the Ubuntu partition, you could use [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). It's part of the "testdisk" package, so you can download and run it with:
```
sudo apt-get install testdisk
sudo photorec
```
Let me know how it goes, or what you decide to do.

---

### Post by cynon83 on 2008-10-26
I was hoping that the fsck would work, and maybe it did -- I haven't checked yet.  If it didn't, I'll try and have windoze do a fix, so I can at least boot into that.  If I can, well... I'll get back to Ubuntu.  Eventually.

Of course, the best of all worlds would be if the fsck worked, so I'm off to find that out.

---

### Post by caljohnsmith on 2008-10-26
How about trying to force mount your Ubuntu partition and see if that works:
```
sudo mount -t ext3 /dev/sda3 /mnt -o force
ls -l /mnt
```
Please post the output of the above commands.

---

### Post by cynon83 on 2008-10-26
Hey, thanks for the help.  However, I got tired of messing with it.  I just reinstalled Ubuntu.

Of course, all my customization is gone, and it's going to take weeks to get it all back.  Especially since, for some reason, nfs is not working -- and yes, I installed the common package...

Crap.  maybe I'll just stick with samba, but that sort of annoys me.

---

