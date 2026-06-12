---
title: "[SOLVED] Installing Ubuntu"
date: 2008-09-26
forum: General Help
---

### Post by ^^rac on 2008-09-26
Hi guys!

I need quick help!

I used to run Ubuntu installed within Windows....

Now, i wanna use an actual partition.
I want to use 50 GB for Ubuntu and 30 GB for Windows.......

I tried partitioning the drive with Windows, but in the Ubuntu partitioner, it tried somethig different. That did not work!

My question is, can i create both partitions, when i do the Ubuntu installation first?

Or do i need to install Windows first, and then Ubunutu, using Windows to partition the drives??

Thanks for the info!
:)

---

### Post by lisati on 2008-09-26
You do have the option of doing the partitioning before you do the installation. When the installer asks, you then tell it to use the largest free space.

The other option is to let the installer take care of the partitions, in which case you will need to use one of the other options (I can't remember the exact wording at present), remembering to stay clear of the "Use entire disk" option if you wish to keep Windows on your system.

Either way, be sure to read the options the installer gives you very carefully before proceeding.

It is also a good idea to defrag your Windows partition and make a backup of important data before tinkering with partitions.

---

### Post by Twitch6000 on 2008-09-26
I would suggest buring partition magic to disc or gparted to disc and setting up your partitions that way.

Then after doing so boot up from your ubuntu live cd and edit your grub file and add windows to boot up.

After that everything should work fine.

A good guide that still works well for me is this one.
Link Here- [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Or you could use the easy way and partition during install :).

---

### Post by ^^rac on 2008-09-26
> **Twitch6000 said:**
> I would suggest buring partition magic to disc or gparted to disc and setting up your partitions that way.

Then after doing so boot up from your ubuntu live cd and edit your grub file and add windows to boot up.

After that everything should work fine.

A good guide that still works well for me is this one.
Link Here- [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Or you could use the easy way and partition during install :).

Hi guys!

Luckely, i dont have any information on my HDD now....
Its clean.

So, i just want to get Ubuntu and XP on the same drive.....

I read though some of the posts.....but it seems complicated.
What would you guys suggest i install first Ubuntu? Or XP?

And must i rather do the partitioning in Ubuntu?

---

### Post by prshah on 2008-09-26
> **^^rac said:**
> 
What would you guys suggest i install first Ubuntu? Or XP?
And must i rather do the partitioning in Ubuntu?

Install XP first. In the XP installation program, delete _all_ partitions (since you say you have a "clean" system, I believe you don't need any data from the disks now.)

Then create a single 30Gb partition and install Windows on it.

Partitioning for ubuntu partitions _must_ be done from the ubuntu installation program / ubuntu's partitioning utilities.

During the ubuntu installation, choose the "use Largest available (contiguous?) free space" option. This will painlessly and automatically setup the required ubuntu partitions.

Post back if you have any difficulties.

---

### Post by TeXtonyx on 2008-09-26
It's possible to install them in either order, I'll explain the expert way.
Install XP first. During that install it gives you the option of using part
of the (clean) disk or all of it. Choose to use part of it, the 30gigs.
Download a program called Bootpart for later use with the Ubuntu install.

Next install Ubuntu, and pick largest unallocated partition which will be 
nearly 50 gigs. At step 7, click on "Advanced" and choose to install grub
to the Ubuntu boot sector. Your XP will be on sda1 and Ubuntu will install 
on sda2, so choose sda2. After you reboot, you will be back in XP. Now type
C:\>bootpart <enter> which will generate something like the report below:

0 : C:* type=7 (HPFS/NTFS), size= 59568988 KB, Lba Pos=63
1 : C: type=f (Win95 XInt 13 extended), size= 20844337 KB, Lba Pos=119138040
2 : C: type=b (Win95 Fat32), size= 489951 KB, Lba Pos=159846813
3 : C: type=5 (Extended), size= 19462747 KB, Lba Pos=119138041
4 : C: type=83 (Linux native), size= 19462684 KB, Lba Pos=119138166 

sda2 is the first linux partition where grub is installed, here it's 4
type: C:\>bootpart 4 ubuntu.bin Ubuntu <enter > writes the boot 512 
sectors to ubuntu.bin and places this line in boot.ini C:\ubuntu.bin="Ubuntu" 
providing a Ubuntu boot choice. Now when you boot up you can choose
between Windows XP or Ubuntu. This is slightly more work than using the
default which puts grub into the MBR of your drive, sda. The benefit is
that this method is much easier to troubleshoot and fix if there's a mishap to XP. A Super Grub boot disk can boot Ubuntu from sda2 if needed.

---

### Post by ^^rac on 2008-09-26
> **TeXtonyx said:**
> It's possible to install them in either order, I'll explain the expert way.
Install XP first. During that install it gives you the option of using part
of the (clean) disk or all of it. Choose to use part of it, the 30gigs.
Download a program called Bootpart for later use with the Ubuntu install.

Next install Ubuntu, and pick largest unallocated partition which will be 
nearly 50 gigs. At step 7, click on "Advanced" and choose to install grub
to the Ubuntu boot sector. Your XP will be on sda1 and Ubuntu will install 
on sda2, so choose sda2. After you reboot, you will be back in XP. Now type
C:\>bootpart <enter> which will generate something like the report below:

0 : C:* type=7 (HPFS/NTFS), size= 59568988 KB, Lba Pos=63
1 : C: type=f (Win95 XInt 13 extended), size= 20844337 KB, Lba Pos=119138040
2 : C: type=b (Win95 Fat32), size= 489951 KB, Lba Pos=159846813
3 : C: type=5 (Extended), size= 19462747 KB, Lba Pos=119138041
4 : C: type=83 (Linux native), size= 19462684 KB, Lba Pos=119138166 

sda2 is the first linux partition where grub is installed, here it's 4
type: C:\>bootpart 4 ubuntu.bin Ubuntu <enter > writes the boot 512 
sectors to ubuntu.bin and places this line in boot.ini C:\ubuntu.bin="Ubuntu" 
providing a Ubuntu boot choice. Now when you boot up you can choose
between Windows XP or Ubuntu. This is slightly more work than using the
default which puts grub into the MBR of your drive, sda. The benefit is
that this method is much easier to troubleshoot and fix if there's a mishap to XP. A Super Grub boot disk can boot Ubuntu from sda2 if needed.


Hi there!!

Thanks for the info :)

I was wondering, im gonna install xp first......and leave the partition at 80GB.

Then im gonna install ubuntu, when it ask me, in the partitioner, im gonna choose the first option, and then resize the partitiion to 30GB XP and say 50GB Ubuntu.....

And proceed.

Will this work, and install both OS's on the one partition?
Will bootloader work correclty then?

Thanks!!

---

### Post by ^^rac on 2008-09-26
> **prshah said:**
> Install XP first. In the XP installation program, delete _all_ partitions (since you say you have a "clean" system, I believe you don't need any data from the disks now.)

Then create a single 30Gb partition and install Windows on it.

Partitioning for ubuntu partitions _must_ be done from the ubuntu installation program / ubuntu's partitioning utilities.

During the ubuntu installation, choose the "use Largest available (contiguous?) free space" option. This will painlessly and automatically setup the required ubuntu partitions.

Post back if you have any difficulties.

Aaaah thanks man!!

That was what i wanted to know! That seems cool.....

If i create the 30GB partition in XP, must i leave the other 50GB raw? And just go and install Ubuntu on that? (Or must i also format it?)

---

### Post by ^^rac on 2008-09-26
> **^^rac said:**
> Aaaah thanks man!!

That was what i wanted to know! That seems cool.....

If i create the 30GB partition in XP, must i leave the other 50GB raw? And just go and install Ubuntu on that? (Or must i also format it?)

Also, i have a 120GB drive i use for storage, MP3's etc....

It will not affect this drive at all? (I mean, when i select it to use most free space thingie during the Ubuntu installation?

Thanks for the help fellas!

---

### Post by TeXtonyx on 2008-09-26
The reason to make the 30gig partition during the XP install is that later, one does not
have to shrink/resize the disk with Ubuntu. Rarely, the shrinking will cause XP not to
boot. Why take any risk at all. Do not format the 50gigs of unallocated/free space. The
Ubuntu installer says largest free space and formatted space is not unallocated space 
because one is no longer free to install any OS to that partition without reformatting,
but you are free to install any OS to unallocated space, because it becomes formatted
with the right format for that OS.
Yes, it matters if you have another hard drive installed. I gave instructions for sda as if
you only had one hard drive. The second drive is called sdb. I assume you have made 
your XP 120gig disk bootable. It is likely to be the first drive or sda. Be sure you mean
another drive, rather than another XP data partition all one only one drive.  Assuming
you mean two drives, install xp to the clean drive which means don't reinstall XP to
the drive with XP already on it. When you are done run Bootpart from the Dos prompt
and it will report two drives, which it will label with a C (sda) or D (sdb). One drive
will display information for the 120gig XP data drive. The other drive will show your
30gig new XP install. If that 30gig is on D then have Ubuntu install to sdb, *not* to
data 120gig sda or you may overwrite that drive. Suppose for some reason that the 
30gig drive is reported by Bootpart as being on C or sda. In that case the 120gig is D.
So do not install Ubuntu to the D drive which is sda. After you have pre-determined 
whether sda or sdb has the 30gig XP install, make sure Ubuntu is installed to the same
drive. It may not be a disaster if Ubuntu is installed to the largest free space. Why not
go to your data drive now and at the dos command prompt type: C:\dir <enter>
that will return how much free space you have on the 120gig data drive.  But Ubuntu
is going to install to the largest free space on that drive under selection, I don't believe
to a larger free space on a different drive. But if your free space on the 120gig drive is
less than 50gig, 50,000,000,000, then it won't even matter. When you install XP, do not
overwrite any previous installation of C:\Windows, you've made mistake if you see it.
Did you at one time have both drives installed with Windows, dual booting? 
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Pro" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Data" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="UbuntuA" [this boots to Ubuntu on my first drive on WinXP]
C:\suse.bin="OpenSesame" [this boots to OpenSuse on my second drive]

TeX: In this sample boot.ini I have the Data disk listed as second drive which is rdisk(1)
If your data disk was not second drive, but first drive, which is rdisk(0)
then all you need to do is edit and reverse where the labels appear. 
This is how to do it using it with boot.ini. If I had known that you had
two drives I probably would not have suggested that you install Ubuntu to its
boot partition (sda2 or sdb2, after XP) but to use the grub MBR method, provided
by Ubuntu, until you are more experienced.

---

### Post by ichundu on 2008-09-26
> **^^rac said:**
> Also, i have a 120GB drive i use for storage, MP3's etc....

It will not affect this drive at all? (I mean, when i select it to use most free space thingie during the Ubuntu installation?

Thanks for the help fellas!

do what prshah says, you have the hdd cleaned. i assume this 120GB drive is filled with just a single partition, with NTFS file system (the one that windows uses). in the ubuntu installer, first option should be "Guided - use entire disk" and under that you'll have an option to select one of the 2 drives you have (don't choose this in your case). As for the option "...use the largest continuous free space" i think it will not affect the 120GB drive if there is no unpartitioned space, so selecting this option will create 2 partitions for ubuntu (the system partition wich will be formated with ext3 file system, and the swap partition, which is very small and is the analogue of "virtual memory" in windows). don't worry, this is done automatically. good luck

---

### Post by ^^rac on 2008-09-26
> **ichundu said:**
> do what prshah says, you have the hdd cleaned. i assume this 120GB drive is filled with just a single partition, with NTFS file system (the one that windows uses). in the ubuntu installer, first option should be "Guided - use entire disk" and under that you'll have an option to select one of the 2 drives you have (don't choose this in your case). As for the option "...use the largest continuous free space" i think it will not affect the 120GB drive if there is no unpartitioned space, so selecting this option will create 2 partitions for ubuntu (the system partition wich will be formated with ext3 file system, and the swap partition, which is very small and is the analogue of "virtual memory" in windows). don't worry, this is done automatically. good luck

Thanks alot man!

Yes, im gonna do this!
The 120GB is on one partition(Ons Disc)....no OS, just data.
Im gona install XP on a 30GB partition, and then run Ubuntu installer.....

And select it to use largest continuious free space.......

This will then install it on the 50GB i assume? And leave Windows as its on the 30 GB partition?

Thanks guys! :guitar:

(PS, does anyone know how you get the black taskbars etc??)

---

### Post by prshah on 2008-09-26
> **^^rac said:**
> 
Yes, im gonna do this!
The 120GB is on one partition(Ons Disc)....

No you'd better not!

The 120Gb is sda; which is where ubuntu will install by default. And you have 4 partitions, so no more can be created. One of them (probably swap) will have to be made into an extended partition, and that will have to be expanded to contain the unallocated space at the end of the device. Also the first partition will have to be expanded/moved to include the free space in the beginning. Too many operations.

Where is your 80Gb is it sdb?

---

### Post by ^^rac on 2008-09-26
> **prshah said:**
> No you'd better not!

The 120Gb is sda; which is where ubuntu will install by default. And you have 4 partitions, so no more can be created. One of them (probably swap) will have to be made into an extended partition, and that will have to be expanded to contain the unallocated space at the end of the device. Also the first partition will have to be expanded/moved to include the free space in the beginning. Too many operations.

Where is your 80Gb is it sdb?



Hi prshah.

This is what i have!
80GB Master (Its clean I wanna put XP 30GB, Ubuntu 50GB)
120GB Slave (Full of data, using it for storage) (9GB free)

I want to install XP first on a 30 GB partition on the master disc, and then, install Ubuntu on the same disc.)

I want to be able to dualboot between XP and Ubuntu.

Thats it! 

So, all i want to know is, when i install XP, complete. The boot into Ubuntu to install....Ill then select the option in the partitioner where it says to use the biggest space(After i installed XP on the 30GB partition)

Will this work out?

Cause what happened was, i partioned the 80Gb into 50 / 30, installed Xp on the second partition, then installed Ubuntu.....i got an error, when i tried to boot to XP. Im sure this was wrong!

So i wanna try it now, to install XP on the first 30GB partition first, then Ubuntu on the second partition.......

Thanks for the help guys!!

---

### Post by ericmwebe on 2008-09-26
In short have yourself a dual boot, if you dont have very important data on you PC/Laptop, firstly back up your data, then format your hard drive.
First Os install should be windows then Ubuntu.
Once you are in progress and at the point of resizing,ubuntu installer resize will give you partition sizes of both ubuntu and window,then make your choice of resizing to 50GB or you can use the manual still on that same page of resizing and check manual then once in manual type your GB size and you good to good.
Hope that is a quick help.

---

### Post by TeXtonyx on 2008-09-26
The screenshot you provided shows sda, which is NOT where you want to install XP or Ubuntu.
Notice on your screenshot, the top right corner. It says dev/sda. There is a little triangular dropdown
arrow on the far right. That is what you click on, and it will drop a window down which will give you
a chance to select sdb. It will kind of like that when you install Ubuntu. The drive you want to install
on will just display Windows XP. If you are looking at the wrong drive to install Ubuntu, all that
stuff in your screenshot shows up. So when you are looking at the representation of the correct drive
its only going to show a total of 80gig. When you click on install to largest unallocated space, it will
be install to the largest unallocated space on the drive you have selected. Make sure you select the
drive with XP at the beginning that is only 80gigs large. That information appears on the screen.
The data drive, it shows you have a bit over 39gig unallocated. No, you want where its about 50gig.

---

### Post by ^^rac on 2008-09-26
> **TeXtonyx said:**
> The screenshot you provided shows sda, which is NOT where you want to install XP or Ubuntu.
Notice on your screenshot, the top right corner. It says dev/sda. There is a little triangular dropdown
arrow on the far right. That is what you click on, and it will drop a window down which will give you
a chance to select sdb. It will kind of like that when you install Ubuntu. The drive you want to install
on will just display Windows XP. If you are looking at the wrong drive to install Ubuntu, all that
stuff in your screenshot shows up. So when you are looking at the representation of the correct drive
its only going to show a total of 80gig. When you click on install to largest unallocated space, it will
be install to the largest unallocated space on the drive you have selected. Make sure you select the
drive with XP at the beginning that is only 80gigs large. That information appears on the screen.
The data drive, it shows you have a bit over 39gig unallocated. No, you want where its about 50gig.

Hi TextonyX

Sorry man! Thats not my screenshot!(I got it from another thread, my bad) I wanted to know how you get your theme to be black?

Thats not my setup at all!

Sorry for the inconvinience.......

---

### Post by ichundu on 2008-09-26
is this possible? :

to temporarily remove the 120GB drive, install xp and ubuntu on the 80GB drive, and then reconnect the 120GB?

any idea from you guys if this a good idea?

DON'T try this without being approved by someone else who will ensure you that the 120GB drive will be recognized without issue after reconnecting, because i don't have personal experience with adding extra drives in ubuntu.

---

### Post by ^^rac on 2008-09-27
Thanks for all your help guys!!!

It worked perfectly!!!

Cheers from South Africa!!

---

