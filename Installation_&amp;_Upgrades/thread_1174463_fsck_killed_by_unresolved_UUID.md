---
title: "fsck killed by unresolved UUID"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Jesdisciple on 2009-05-30
Yeah, I have yet another problem.  I just finished setting up three parallel Jaunty partitions; see [here]("http://jesdisciple.blogspot.com/2009/05/my-ubuntu-adventure.html").  I just logged into the main one, and I got this error:> Log of fsck -C3 -R -A -a 
Sat May 30 22:17:55 2009

fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sda6: 0 files, 1/234480 clusters
open UUID=024B-6A06:No such file or directory
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
fsck.ext4: Unable to resolve 'UUID=84e296fb-7fb3-48f2-8748-9a22aa131d72'

/dev/sda5: clean, 214904/655776 files, 2378669/2622603 blocks
fsck died with exit status 9

Sat May 30 22:17:56 2009
----------------

One of the two mentioned partitions is for transferring files between Ubuntu and my future Windows installation; it will be NTFS, but the Live CD didn't give that option.

The other is my swap partition; I thought that was sda5, but the FAT32 errors are around sda6.

I'm sure I did something horribly wrong...  Would someone please tell me what that is?  Thanks.

---

### Post by mcduck on 2009-05-31
Could you post the outputs of "sudo fdisk -l" and "blkid",and contents of your /etc/fstab file here?

Most likely there's something wrong with your fstab.

---

### Post by Jesdisciple on 2009-05-31
I meant to say that I thought the swap was sda6, but I was forgetting about the extension which contains 3 partitions and increments the index.  EDIT: Oh, and sdb1 is my flash drive.> $ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025eb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2755    22129506   83  Linux
/dev/sda2            2756        5510    22129537+  83  Linux
/dev/sda3            5511        8174    21398580   83  Linux
/dev/sda4            8175        9729    12490537+   5  Extended
/dev/sda5            8175        9480    10490413+  83  Linux
/dev/sda6            9481        9597      939771    b  W95 FAT32
/dev/sda7            9598        9729     1060258+  82  Linux swap / Solaris

Disk /dev/sdb: 4076 MB, 4076863488 bytes
156 heads, 48 sectors/track, 1063 cylinders
Units = cylinders of 7488 * 512 = 3833856 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1064     3981288    c  W95 FAT32 (LBA)

$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="233e0e09-aa16-4335-a004-50834698130c" TYPE="ext4" 
/dev/sda2: UUID="a82fe1cd-375c-47a1-b38d-463f76d0e84f" TYPE="ext4" 
/dev/sda3: UUID="8a584d98-10ea-4725-9b15-3a7afa9e6efc" TYPE="ext4" 
/dev/sda5: UUID="8f4c89b8-6e85-43dc-8da4-565c144a73ef" TYPE="ext4" 
/dev/sda6: UUID="5393-38DF" TYPE="vfat" 
/dev/sda7: TYPE="swap" UUID="2a22f359-908e-43df-9fb6-d8fdb10daaa0" 
/dev/sdb1: LABEL="UDISK" UUID="17B6-D82E" TYPE="vfat"

---

### Post by mcduck on 2009-05-31
Could you post the /etc/fstab file as well. The problem is most likely in that file and information from those other two commands will be needed to fix the file, but I can't do that without seeing the file itself. :)

---

### Post by Jesdisciple on 2009-05-31
As I thought about it today, I realized that I formatted some partitions between installs.  Would that invalidate the UUID?  I also wonder if I can fix the mounts so the partitions can access each other via their filesystems.> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=233e0e09-aa16-4335-a004-50834698130c /               ext4    relatime,errors=remount-ro 0       1
# /code was on /dev/sda2 during installation
UUID=84e296fb-7fb3-48f2-8748-9a22aa131d72 /code           ext4    relatime        0       2
# /home was on /dev/sda5 during installation
UUID=8f4c89b8-6e85-43dc-8da4-565c144a73ef /home           ext4    relatime        0       2
# /shared was on /dev/sda6 during installation
UUID=5393-38DF  /shared         vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda3 during installation
UUID=024B-6A06  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=2a22f359-908e-43df-9fb6-d8fdb10daaa0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2009-05-31
> 
*fstab:*
# /code was on /dev/sda2 during installation
UUID=84e296fb-7fb3-48f2-8748-9a22aa131d72 /code ext4 relatime 0 2

# /windows was on /dev/sda3 during installation
UUID=024B-6A06 /windows vfat utf8,umask=007,gid=46 0 1


Neither of these fstab entries match blkid's results:

The fstab entry for /code UUID is now 
a82fe1cd-375c-47a1-b38d-463f76d0e84f

The /windows UUID no longer exists: UUID=024B-6A06
It appears to be sdb1 with a UUID of:  17B6-D82E

Make the fstab entry look like this for the /code entry:
> 
UUID=a82fe1cd-375c-47a1-b38d-463f76d0e84f /code ext4 relatime 0 2


Make the fstab entry look like this for the windows entry:
> 
UUID=17B6-D82E /windows vfat utf8,umask=007,gid=46 0 1


Note I don't reference the commented lines. Although they make it easy to identify a partition (sda2, for instance), they are commented and are not updated. Note they say "during installation". Once the user starts adding or deleting partitions, these comments are not necessarily correct and therefore should not be relied upon until they are verified.

---

### Post by mcduck on 2009-05-31
> **Jesdisciple said:**
> As I thought about it today, I realized that I formatted some partitions between installs.  Would that invalidate the UUID?  I also wonder if I can fix the mounts so the partitions can access each other via their filesystems.

Yes, formatting partitions will change their UUIDs so you will have to fix the fstab afterwards. Based on the information it seems you have formatted sda2 and sda3 to ext4, you should edit (or remove) their entries in fstab.

Also, the last number in the fstab entries tells if the partitions nshould be checked by fsck or not, and the order in whcih they are checked. "0" means that the partitions will not be checked, "1" should be used for root partition only, and for every other partition you wish to use fsck you should use "2". So, while the entry for sda3 is otherwise correct you should change the last number to "0" or "2".

I assume sda1, sda2 and sda3 are root partitions for your three parallel Linux installs? In that case you could edit the fstab into something like this:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=233e0e09-aa16-4335-a004-50834698130c / ext4 relatime,errors=remount-ro 0 1
# Ubuntu-2 on sda2
UUID=a82fe1cd-375c-47a1-b38d-463f76d0e84f /media/ubuntu2 ext4 relatime 0 2
# Ubuntu-3 on sda3
UUID=8a584d98-10ea-4725-9b15-3a7afa9e6efc /media/ubuntu3 ext4 relatime 0 2
# /home was on /dev/sda5 during installation
UUID=8f4c89b8-6e85-43dc-8da4-565c144a73ef /home ext4 relatime 0 2
# /shared was on /dev/sda6 during installation
UUID=5393-38DF /shared vfat utf8,umask=007,gid=46 0 0
# swap was on /dev/sda7 during installation
UUID=2a22f359-908e-43df-9fb6-d8fdb10daaa0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
This would mount your second ubuntu install as "ubuntu2" and third one as "ubuntu3". You'll also have to create the mount points for sda2 and sda3:
```
sudo mkdir /media/ubuntu2
sudo mkdir /media/ubuntu3
```

What comes into your Ubuntu installs seeing each other, that's just a question of fixing the fstab file in each install to mount the partitions somewhere. Each install has it's own fstab file.

---

### Post by Jesdisciple on 2009-05-31
Yes, the first three have Linux, although the third is just a temporary one so I can debug my /home data without screwing up a permanent installation.

If /media/* is the mount point, what are /code and /windows?

Now I'll cross my fingers and restart...

---

### Post by mcduck on 2009-05-31
> **Jesdisciple said:**
> Yes, the first three have Linux, although the third is just a temporary one so I can debug my /home data without screwing up a permanent installation.

If /media/* is the mount point, what are /code and /windows?

Now I'll cross my fingers and restart...

They were the mount points you used for those partitions before formatting them for new purposes. Partitions can be mounted on any loaction in the file system, but unless there's some specific reason to do otherwise partitions are usually mounted inside /media or /mnt. Everything mounted in /media will appear on your desktop and in the Places-menu, while /mnt works fine as a generic mount location for those partitions you want to have mounted but not to show in desktop or the Places menu.

---

### Post by Jesdisciple on 2009-05-31
Oh, I missed the /media/* parts in fstab and thought there was some mapping from the old mounts.

fstab somehow found sda3 without the correct UUID...?

Is there any way to give the partition a name on the desktop?  It's a lot easier to identify them by what I'm using them for than how big they are.

Finally, GRUB keeps booting on sda3 by default; can I change that?

Thanks for the help. :)

---

### Post by drs305 on 2009-05-31
To make labels for ext2/3/4 partitions, you can run this command:
```

sudo tune2fs -L <label> <dev>

```
Example: sudo tune2fs -L mydata /dev/sdb1

To format any of the popular filesystem types, the easiest method is to open Gparted (System, Administration, Partition Editor or "gksudo gparted"), select a partition, and then Partition, Label.

To set the default OS, the gui way is to use StartUp-Manager. Install via Synaptic and then run via System, Administration, StartUp-Manager. Or via the command line:
```

sudo apt-get install startupmanager
gksudo startupmanager

```
In the boot options section, you can select the default kernel or OS you would like.

StartUp-Manager has lots other grub menu items you can select, such as menu displays and timeouts. See the link in my signature line for a StartUp-Managager guide.

---

### Post by Jesdisciple on 2009-05-31
OK, I'll definitely be referring to this thread from the other partitions.

You're right, I should have used GParted after I got the first partition set up.  I got a warning of "idiosyncrasies" in CD installers from someone unfamiliar with Ubuntu, but I tend to learn the hard way.  That term is a big understatement for Ubuntu; we have a unit conversion bug.

I only see one partition's options listed in SUM:[list]
[*]normal
[*]recovery
[*]memtest
[/list]It may be relevant that I don't have a dedicated /boot partition.

---

### Post by drs305 on 2009-05-31
When StartUp-Manager (SUM) starts, it looks at the existing menu.lst and the kernels available in the current system's /boot folder. So if you have 2 OS's but one isn't currently listed in menu.lst and not in your /boot folder SUM won't be able to see it. 

Your option in this case is to manually add the other system to the grub menu, including the correct locations on the root and kernel lines.

Here is an example of one of my extra versions. Note the title line can say anything you want.
> 
title		JAUNTY2-9, kernel 2.6.28-11-generic (ext4) (on /dev/sdb9)
[noparse]root		(hd1,8)[/noparse]
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=740da112-511e-4f0e-b1e7-d8db9962d8c5 ro splash quiet rootfstype=4 
initrd		/boot/initrd.img-2.6.28-11-generic


---

### Post by Jesdisciple on 2009-05-31
Woah, that's a lot to digest.  I found a handy [reference]("http://www.howtoforge.com/working_with_the_grub_menu") on Google, but I'm definitely not done yet.

I don't really want to keep 3 boot options for each partition, but neither do I want to lock myself out of safe mode.  Is there any way to enter safe mode after GRUB (e.g., by restarting)?

Thanks again.

---

### Post by drs305 on 2009-05-31
Do you see the grub menu.lst during boot? 

If so, do you see a default entry like this. Note the highlighted portions depict the recovery mode option:

You can type "cat /boot/grub/menu.lst" to see what your's contains. This entry should be near the bottom:

> 
title		Ubuntu 9.04, kernel 2.6.28-11-generic (**recovery mode**)
uuid		40c00255-22b3-488b-ae7e-9dbe4e2beac7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=40c00255-22b3-488b-ae7e-9dbe4e2beac7 **ro  single**
initrd		/boot/initrd.img-2.6.28-11-generic


If you don't see the grub menu during boot, you can change the timeout and "show bootloader menu" settings via StartUp-Manager or you can hit ESC during the start of the boot process. Hitting ESC will reveal the grub menu if you do it early enough and you could then select the recovery mode at that time.

If you don't see the recovery mode option, you can copy the main entry and change the highlighted portions as in the example to make a recovery mode option ( ro single ) and change the description to include what it is. You can also make sure you see the recovery mode option by setting it in SUM.

---

### Post by Jesdisciple on 2009-06-01
Yes, I see the recovery mode...  But I'm not sure how many I should have - 1 per OS?  That seems like clutter until I need one.  I guess I could put the normal ones up top; see below.

But why is GRUB checking the menu.lst for the third partition to the exclusion of the others?  Could I point it to the first partition instead so I don't have to do this on every partition?

> title		Main (Ubuntu 9.04, kernel 2.6.28-11-generic)
uuid		233e0e09-aa16-4335-a004-50834698130c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=233e0e09-aa16-4335-a004-50834698130c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Code (Ubuntu 9.04, kernel 2.6.28-11-generic)
uuid		a82fe1cd-375c-47a1-b38d-463f76d0e84f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a82fe1cd-375c-47a1-b38d-463f76d0e84f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Temporary (Ubuntu 9.04, kernel 2.6.28-11-generic)
uuid		8a584d98-10ea-4725-9b15-3a7afa9e6efc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8a584d98-10ea-4725-9b15-3a7afa9e6efc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Main (Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode))
uuid		233e0e09-aa16-4335-a004-50834698130c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=233e0e09-aa16-4335-a004-50834698130c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Code (Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode))
uuid		a82fe1cd-375c-47a1-b38d-463f76d0e84f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a82fe1cd-375c-47a1-b38d-463f76d0e84f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Temporary (Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode))
uuid		8a584d98-10ea-4725-9b15-3a7afa9e6efc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8a584d98-10ea-4725-9b15-3a7afa9e6efc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Main (Ubuntu 9.04, memtest86+)
uuid		233e0e09-aa16-4335-a004-50834698130c
kernel		/boot/memtest86+.bin
quiet

title		Code (Ubuntu 9.04, memtest86+)
uuid		a82fe1cd-375c-47a1-b38d-463f76d0e84f
kernel		/boot/memtest86+.bin
quiet

title		Temporary (Ubuntu 9.04, memtest86+)
uuid		8a584d98-10ea-4725-9b15-3a7afa9e6efc
kernel		/boot/memtest86+.bin
quiet

---

### Post by drs305 on 2009-06-01
You *could* have a recovery mode for each OS, but the purpose of a recovery mode is to be able to get in and fix what is wrong. You can do that from your other versions. 

Memtest86+ : When is the last time you ran that? 

If I had your menu.lst and wanted to compact it, I would trim it as below. You can always restore the memtest86+ option for your main OS via StartUp-Manager; or you could leave one (commented out) that you could uncomment if needed. I'd leave only one recovery mode for the version I use most often. You could comment out the others ( # ) instead of deleting them.

Here's what I'd be left with. You would only see the first four options. Of course, all this is personal preference.

> 
title Main (Ubuntu 9.04, kernel 2.6.28-11-generic)
uuid 233e0e09-aa16-4335-a004-50834698130c
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=233e0e09-aa16-4335-a004-50834698130c ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Code (Ubuntu 9.04, kernel 2.6.28-11-generic)
uuid a82fe1cd-375c-47a1-b38d-463f76d0e84f
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=a82fe1cd-375c-47a1-b38d-463f76d0e84f ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Temporary (Ubuntu 9.04, kernel 2.6.28-11-generic)
uuid 8a584d98-10ea-4725-9b15-3a7afa9e6efc
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=8a584d98-10ea-4725-9b15-3a7afa9e6efc ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Main (Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode))
uuid 233e0e09-aa16-4335-a004-50834698130c
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=233e0e09-aa16-4335-a004-50834698130c ro single
initrd /boot/initrd.img-2.6.28-11-generic


# title Main (Ubuntu 9.04, memtest86+)
# uuid 233e0e09-aa16-4335-a004-50834698130c
# kernel /boot/memtest86+.bin
# quiet


If you don't like the partition grub is using to boot from (i.e. you would prefer it use one of the other menu.lst files) you can tell grub where to look by running "sudo grub" and then "find /boot/grub/stage1". It will find your /boot partitions and you can choose the one you want. You can only designate one. If you do a search of the forums for those strings you will find plenty of explanations on how to run the command and what inputs to make.

---

### Post by Jesdisciple on 2009-06-01
I was also considering that option, but I wasn't sure how partition-specific they are - particularly memtest.  But I guess I could copy-and-paste a UUID if it came to that.

Should I start a new topic for pointing GRUB to a specific partition?

Thanks.  I try to not thank in every post so it means more, but I've appreciated all of them.

---

