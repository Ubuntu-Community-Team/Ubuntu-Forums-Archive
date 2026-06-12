---
title: "How can I see my Windows files?"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by sbasak on 2005-12-14
This is my first post in Ubuntu forum!:p 

I have sucessfully ran Ubuntu from LiveCD. However, from Ubuntu session, I can't see my Windows files (well, I understand the filesystem is different but I thought there should be an indication of where my Windows files are in hard disk in Ubuntu file explorer).

Also, when I start my computer in normal WindowsXP mode, there is also no indication of where my Ubuntu live CD wrote my files in the hard disk.

I again expected to see a file/folder with Ubuntu.img or similar.....

Does the liveCD leave any trace of Ubuntu in hard disk?
any help please :???:

---

### Post by linbetwin on 2005-12-14
The Ubuntu LiveCD didn't write any files on your system. It's purpose is to allow you to test Ubuntu without changing anything on your hard drive.

---

### Post by StefanoCole on 2005-12-14
From the Ubuntu live cd open a Terminal.
In the terminal type: sudo mkdir /media/win
Then, if your file system on Windows is ntfs type:
sudo mount /dev/hda /media/win -t ntfs -o umask=0222
Then you can browse through Windows files.
At the end unmount file system with:
sudo umount /media/win

Bye Stefano

---

### Post by harisund on 2005-12-14
Live CDs, as linbetwin mentioned, make no changes in your file system so you will not be able to see any trace of running the Live CD when you boot back into Windows XP. 

If you used an install CD, and went ahead and installed Ubuntu into your hard disk, Windows XP still won't see your Ubuntu partition anywhere. 

However, from ubuntu, Windows partitions are normally available in /media. Could you see there? 

If you are using ntfs partitions, you will not be able to write into the Windows partitions.

---

### Post by sbasak on 2005-12-14
Thanks for the info.

From the live CD, if I create some documents and save into hard disk (Windows XP installed), can I get those files when I re-run LiveCD?

---

### Post by harisund on 2005-12-14
No, I doubt you will be able to do that. 

First, if you have Windows on NTFS partitions, I am not sure if you will be able to write into it at all. Search around for writing into NTFS partitions. 

If you try to save anything into Desktop or home folder, remember they are housed on your RAM and will no longer be there when you reboot into XP or the Live CD itself. 

If you have a FAT formatted partition, another CD drive that can burn CDs, or a floppy disk, your best bet would be to save it into that.

---

### Post by sbasak on 2005-12-14
[QUOTE=harisund]If you try to save anything into Desktop or home folder, remember they are housed on your RAM and will no longer be there when you reboot into XP or the Live CD itself. 
[/QUOTE]

Can I save my files into a floppy then? Will it write to a DOS/Windows formatted floppy? :confused: 

BTW, how much space is required if I want to install Ubuntu into Windows XP hard disk?

---

### Post by harisund on 2005-12-14
Yes..I am sure you can save into a Dos formatted floppy, since they are basically FAT formatted only. 

How much space? I would suggest you look around for space requirements.. they are not much, but if you want to install it along with your Windows XP, you need to resize your partitions and all that.. so I would suggest you read up some information before attempting to do a complete install

---

### Post by esperantisto on 2005-12-14
[QUOTE=sbasak]Can I save my files into a floppy then? Will it write to a DOS/Windows formatted floppy? :confused: [/QUOTE]

Why not use a flash drive (USB)?

[QUOTE=sbasak]BTW, how much space is required if I want to install Ubuntu into Windows XP hard disk?[/QUOTE]

I think, 10 Gb is the amount that will make you comfortable. Or install a second hard :-)

---

### Post by sbasak on 2005-12-14
How do I make Ubuntu  recognize my USB disk? In WindowsXP, it was plug-n-play case. Will it be same for Ubuntu?

---

### Post by sbasak on 2005-12-15
I have one physical hard disk [30GB] with two logical [20+10 GB] partitions.

I issued following commands

sudo mount /dev/hda1 /media/win -t ntfs -o umask=0222
Now it successfully mounts my C drive
However, when I issued following command
sudo mount /dev/hda2 /media/win -t ntfs -o umask=0222
it fails to mount my D drive! It says invalid file system.

Also, I mounted floppy drive as
sudo mount /dev/fd0 /media/floppy -t vfat -o umask=0222
I can see floppy but whenever, I try to save any file to floppy I get Access Denied dialog box.

Any help please?
PS: I'm running Ubuntu 5.10 from liveCD.

---

### Post by esperantisto on 2005-12-15
Well, my USB drive was absolutely correctly recognized under 5.10. However, I must point that it may depend on the model: under Mandrake 10.0 one USB drive was recognized correctly, another &#8212; as a memory card in read-only mode.

But why don't you simply boot and plug your drive to see?

---

### Post by alamba on 2005-12-15
Yep should be the same with ubuntu. Most USB disks i've used worked.

Akshay

---

### Post by esperantisto on 2005-12-15
[QUOTE=sbasak]sudo mount /dev/hda1 /media/win -t ntfs -o umask=0222
Now it successfully mounts my C drive
However, when I issued following command
sudo mount /dev/hda2 /media/win -t ntfs -o umask=0222
it fails to mount my D drive! It says invalid file system.[/QUOTE]

Of course, it fails! You try to mount [COLOR="Red"]two[/COLOR] partitions into [COLOR="Red"]one[/COLOR] directory! It's not allowed;

Try another directory, say
sudo mount /dev/hda2 /media/win_d -t ntfs -o umask=0222
(it's wise to create that directory before you mount).

---

### Post by esperantisto on 2005-12-15
Sorry, did not pay attention that you work with LiveCD. Then, no luck, I guess.

---

### Post by sbasak on 2005-12-15
[QUOTE=esperantisto]Try another directory, say
sudo mount /dev/hda2 /media/win_d -t ntfs -o umask=0222
(it's wise to create that directory before you mount).[/QUOTE]

Sorry, it was a typo. I DID try in a different directory (as you showed) it still failed.

Well, so you meant that I can't make Ubuntu recognize my 2nd partion (as long as I use LiveCD)? :( 

Also, it couldn't recognize my USB drive (I plugged it even before booting).

---

### Post by StefanoCole on 2005-12-15
Sbasak, about mounting the second win partition from the live CD I cannot tell you exactly, since I only have one win partition on my PC. But what I ask you is: is the second win partition ntfs too? If it is not, then you have specify the right file system type (maybe vfat) when you mount it. 
About the floppy disc maybe you cannot write on it because you have mounted it in read only mode. When you mount it you have to specify a different value for the "umask" parameter. Since now I am not on a Linux box I cannot tell you the right value, you can look at the manual (man mount).
About the USB pen try plugging it after Ubuntu live O.S. has been completely loaded and when you have the desktop ready.

Bye, Stefano

---

### Post by sbasak on 2005-12-15
Yes, you're right! I believe that floppy umask should be 000. I'm confused on one thing, in the Unix book, I see umask setting as 3 digit code but why in Ubuntu it is stated as 4 digit (eg. 0222)?

Regarding hard disk 2nd partition, I know it is NTFS too. (I tried with vfat & got same error message)

---

### Post by StefanoCole on 2005-12-15
Sbasak, I am not very expert on Linux, so I cannot tell you about the 4th digit in the umask. Anyway be sure to look at a Linux manual and not at a Unix one since there are many similarities but also differences between Linux and Unix. 
About the two win partitions you can try the following:
in the Ubuntu live CD in a desktop menu, I don't remember the exact name, maybe "administrative tools", there is an option to see hard disc devices/partitions. Try it and see which partitions are listed.
Or, in another desktop menu there is an application called GParted. Start it and see which partitions are listed

Stefano

---

### Post by esperantisto on 2005-12-15
[QUOTE=sbasak]Sorry, it was a typo. I DID try in a different directory (as you showed) it still failed.

Well, so you meant that I can't make Ubuntu recognize my 2nd partion (as long as I use LiveCD)? :( [/QUOTE]

This means, that the directory, where you're going to mount your partition **must already exist**. I don't know much about LiveCDs, but can guess, that there's a /media/win folder there, but no /media/win2 or any alternative. So, it leads us to the sad conclusion, that under such conditions you can mount only one partition at a time and you have to unmount it before mounting another.

[QUOTE=sbasak]Also, it couldn't recognize my USB drive (I plugged it even before booting).[/QUOTE]

I do suspect, it's about LiveCD, but I may be wrong, of course.

Try normal install :-)

---

### Post by Calib on 2005-12-15
[QUOTE=StefanoCole]From the Ubuntu live cd open a Terminal.
In the terminal type: sudo mkdir /media/win
Then, if your file system on Windows is ntfs type:
sudo mount /dev/hda /media/win -t ntfs -o umask=0222
Then you can browse through Windows files.
At the end unmount file system with:
sudo umount /media/win

Bye Stefano[/QUOTE]

____________________________________

Hello,

I am reading posted messages to help myself get some experience in ubuntu.  I haven't looked at the Live CD at all, just the Install CD. 26G NTFS w/ XP and ~9G for Linux and I think 444mb for swap all on same HDD. 

I have the option to boot in Ubuntu or in XP and they both load up great.  One of the things I would like to do is have access to my NTFS partition where my XP Home lives -- and copy files off that to the linux partition.

When I follow the instructions above, it says it has already been mounted or it is busy.  Well...   its not mounted as far as I can tell.   I tried the unmount command as listed above and it states that is is not mounted.

---

I over looked a few entries in this discussion; found them, and then tried to apply.

already made a dir called win in the /media dir
sudo mount /dev/hda2 /media/win -t ntfs -o umask=0222

did the trick.  Awesome :)

---

### Post by harisund on 2005-12-15
just to double check, could you please post the contents of your /etc/fstab file in this forum? 

Thanks
Hari

---

### Post by sbasak on 2005-12-16
My all problems solved.

I did mount my 2nd HD partition as well from LiveCD. However, the trick is that 2nd partition is **hda5 **and NOT hda2 (don't know why but it worked).

I could also write in floppy. Just had to mount it with umask=000

Also, Ubuntu recognizes my USB drive. I had to plug it in when Ubuntu is already running (and not during boot up time).

Thanks for your help.

---

### Post by harisund on 2005-12-16
The difference is that hda5 means it is a logical partition and hda2 means it is a primary partition. I guess your Windows files were in the logical partition and not primary partition.

---

### Post by randum_idiot on 2005-12-16
i have a 3 partitioned HDD

Partition 1 = FAT32, Windows 2000 PRO
Partition 2 = FAT32, WIN98se
Partition 3 = Linux,  Ubuntu

I have found out how 2 mount Partition 1 on my ubuntu, but i need to no what steps to take to mount the second 1, help real appreciated THAnx (I want it to auto mount at startup )

---

### Post by StefanoCole on 2005-12-16
Well, lets go for steps.
First you have to list your partition table:
from a Terminal type:
sudo fdisk -l 
At this point you should detect your win partitions.
Let assume that /dev/hdax is the location of Windows partition (FAT) and that local mount folder is /media/windows
from a Terminal type:
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
Then append the following line at the end of the file:
/dev/hdax       /media/windows  vfat    iocharset=utf8,umask=000   0       0
Save the edited file.
Remount fstab with the command:
sudo mount -a

Bye Stefano

---

### Post by randum_idiot on 2005-12-16
I need to be able to mount my win 98 partition, i have mounted my win2000 succesfully and tried mounting win98, but without success, any help appreciated thanx


Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        1884     4891792+   f  W95 Ext'd (LBA)
/dev/hda3            1885        2432     4401810   83  Linux
/dev/hda5            1276        1856     4666851    b  W95 FAT32
/dev/hda6            1857        1884      224878+  82  Linux swap / Solaris

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda2       /media/win98    vfat    iocharset=utf8,umask=000   0       0

---

### Post by harisund on 2005-12-16
Did you try doing what stephanoCole suggested in the earlier post? 

Also, it appears your partitions might already be mounted in /media. Did you check that folder?

---

### Post by StubornAH on 2005-12-16
Wow, so many questions.  Can I add another?

My WinXP is ntfs, but if I make the following partitions can Ubuntu and Windows both see and use the FAT drive?

Partition 1: 1GB Swap
Partition 2: 5GB FAT32 /media
Partition 3: 53GB ntfs Windows
Partition 4: 8GB Ubuntu /

They are all on the same drive which I thought was only 60 gig, but this is what is listed when I try to install.  I was always under the impression that Windows and Linux couldn't share drives but if I had a intermediate between the 2 it would be awesom.

Thanks a lot for the help.

---

