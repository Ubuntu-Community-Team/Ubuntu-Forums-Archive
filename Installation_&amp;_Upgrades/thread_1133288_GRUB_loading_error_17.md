---
title: "GRUB loading error 17"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by knixo4 on 2009-04-22
Although I have found numerous boards dealing with error 17, I haven't found anything that deals with my specific problem, perhaps mostly because I'm not exactly sure what my problem is!  I've tried reinstalling(?) GRUB, you know, grub, root, setup, quit, with no luck.  What should I do next?

---

### Post by ronparent on 2009-04-22
Have yoou tried 'find /boot/grub/stage1' from a grub prompt (sy=udo grub) in a terminal from the live cd boot.

---

### Post by knixo4 on 2009-04-22
Yeah, and I get:
 (hd0,0)
 (hd0,2)

---

### Post by knixo4 on 2009-04-22
I think I want the hd0,2 partition to be "master" or whatever (actually second in the boot order, after the PenDrive Ubuntu OS that I tried to set up, and which I think originated the problem in the first place...)  Can anyone help with this?

---

### Post by ronparent on 2009-04-22
Do you know which grub installation you are tryin to get to?

ie

root hd0,0)
setup (hd0)

Will this get your grub menu up on boot?

---

### Post by knixo4 on 2009-04-22
Unfortunately, no.  I've tried that twice now.

---

### Post by knixo4 on 2009-04-22
I should say, I've tried it once with hd0,0, and once with hd0,2. In both cases, the second command was hd0, which I don't understand, but which seemed consistent with everything else I was reading online.

---

### Post by ronparent on 2009-04-22
The command root (hd0,0) designates the location of the file stage1. The command setup(hd0) rewrites the mbr to enable grub to find the grub installation with the stage1, stage2, menu.lst, etc. The error 17 simply states that grub cannot mount selected partition. This error is returned if "the partition requested exists, but the filesystem type cannot be recognized by GRUB". If you examine menu.lst on the target drive are you trying to mount by uuid or by disk and partition number? If by either the uuid should correspond to the uuid of the target drive (ie sda1) or the root of the target (ie (hd0,)). Or if using intrepid or later you might correct the problem with a filesystem check. Check this site for a fuller explanation: 

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by k3ntegra on 2009-04-23
Were you sure to mount the other partitions you made under windows while installing ubuntu?

If not, next time while you install ubuntu make the windows partition mountable. to do this go to "use as" drop menu and select ntfs. After that go to "mount point" drop down and type in /windows/[partition letter] , keep in mind you can name it what you want, just make sure you set a decent path.

For any linux system i make sure i have swap (1.5 times the size of your ram), / (8gb minimum), and /home (this is where your documents pictures desktop items and stuff will be stored)

I learned this from the OpenSuse dual boot installation guide.

---

### Post by tirot on 2009-04-23
> **knixo4 said:**
> I should say, I've tried it once with hd0,0, and once with hd0,2. In both cases, the second command was hd0, which I don't understand, but which seemed consistent with everything else I was reading online.

Well, have you tried re-installing Grub? [[COLOR="Blue"]A Grub menu booting 100+ Oses[/COLOR]]("http://www.justlinux.com/forum/showthread.php?t=143973") has an expert example on booting. Post #4, question 9 details the installation of grub to either the MBR or directly to the partition containing your OS installation.

---

### Post by pk2003 on 2009-04-23
hello there,

I had this one earlier:

1. Do not panic. Boot through ubuntu live CD or USB 
2. To find the location of your backup superblocks, you use a command like, 

xxx@SSS-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90029002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7737    62147421    7  HPFS/NTFS
/dev/sda2            7738        9690    15687472+   5  Extended
/dev/sda4            9691        9729      313267+  88  Linux plaintext
/dev/sda5            7738        9602    14980581   83  Linux
/dev/sda6            9603        9690      706828+  82  Linux swap / Solaris

LINUX ROOT LOCATED AT /DEV/SDA5 

SO...


xxx@SSS-laptop:~$ sudo dumpe2fs /dev/sda5 | grep -i superblock
dumpe2fs 1.41.3 (12-Oct-2008)
  Primary superblock at 0, Group descriptors at 1-1
  Backup superblock at 32768, Group descriptors at 32769-32769
  Backup superblock at 98304, Group descriptors at 98305-98305
  Backup superblock at 163840, Group descriptors at 163841-163841
  Backup superblock at 229376, Group descriptors at 229377-229377
  Backup superblock at 294912, Group descriptors at 294913-294913
  Backup superblock at 819200, Group descriptors at 819201-819201
  Backup superblock at 884736, Group descriptors at 884737-884737


NOW

sudo e2fsck -b 32768 /dev/sda5  
9 out of 10 times it should help you out. For the fixes just say yes till it gets complete. Do not exit just press y as many times it asks for fixes.

If that doesn;t fix it, try the same command but replace the number '32768' with the number for a different backup superblock.

---

### Post by knixo4 on 2009-04-23
When I type: "sudo fdisk -l" I get:

"Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10691069

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9192    73834708+  83  Linux
/dev/sda2           11786       12161     3020220    5  Extended
/dev/sda3            9193       11785    20828272+  83  Linux
/dev/sda5           11786       12161     3020188+  82  Linux swap / Solaris

Partition table entries are not in disk order"

I did not have windows installed previously.  Before this problem, I had two bootable Ubuntu 8.10 OSs, that would be sda1 and sda3 I think.  If it weren't for some pictures I'd like to salvage off of one of the partitions I would just start over!  I'll try to post the menulst or whatever.  Might take me a minute to dig up the command though...

---

### Post by knixo4 on 2009-04-23
Okay, after a brief search I decided it must first be necessary to mount the main partition.  So I tried to do so with: 

sudo mount /dev/sda1 /mnt

Nothing appeared to happen, and at the next cursor I entered:

gedit /boot/grub/menu.lst

Which, if I remember correctly, was how I originally pulled up the menu.lst.  However, this time there was NOTHING in the window that opened up.  Just how bad is that?  I really appreciate everyone's help so far!

---

### Post by knixo4 on 2009-04-23
pk2003,

I followed your instructions, and finally, after hitting "y" many times got:

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 127533/4620288 files (0.4% non-contiguous), 1450809/18458677 blocks


Will follow up with results after rebooting.  Hope this worked!

---

