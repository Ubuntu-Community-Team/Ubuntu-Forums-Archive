---
title: "[SOLVED] Having problems duel-booting XP"
date: 2008-10-18
forum: General Help
---

### Post by Monotoko on 2008-10-18
What im trying to do, is duel-boot XP and Ubuntu, this computers hard-disk is currently entirely taken up by Ubuntu, but i wanted to duel-boot with XP so i could play games etc in windows as well.

So i shrunk the first partition, and created a second, under formatting NTFS

The only problem is, at setup, XP gave me:

```

Unknown Disk
<There are no partitions in this disk>

```

So i went back, and noticed XP would also install to unallocated space, so i got rid of the second partition altogether, leaving unallocated space, reload the windows disk, and still get the same error.

Have i missed something??
(someone has told me to use a Super Grub Disk, but hasnt exactly told me what to use it for or what the heck to do with it)

Thank you for helping me with this extremely frustrating problem

---

### Post by Monotoko on 2008-10-18
please?

---

### Post by Helios1276 on 2008-10-18
Put in an Ubuntu Live CD , from there you can shrink your Ubuntu install and make room for XP. This may,however, wipe out Grub and you will have to fix it with the Super Grub Disk you talked about.

It's way easier installing Xp first and then Ubuntu.

---

### Post by caljohnsmith on 2008-10-18
Did you create a primary partition for Windows and not a logical one? I've helped a number of people in the forums who had the exact same problem as you do with the Windows Install CD not recognizing the HDD, and it usually turns out to be a problem with the HDD's partition table being corrupted. 

To check your HDD's partition table, first post:
```
sudo fdisk -l
```
Then enable all your repositories in System > Admin > Software Sources, and download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by Monotoko on 2008-10-19
```

monotoko@monotoko-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16781   134793351   83  Linux
/dev/sda2           29649       30401     6048472+   5  Extended
/dev/sda3           16782       29648   103354177+   7  HPFS/NTFS
/dev/sda5           29649       30401     6048441   82  Linux swap / Solaris

Partition table entries are not in disk order

```

and sudo testdisk, following the instructions you gave me:
```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 16780 254 63  269586702
 2 E extended             29648   0  1 30400 254 63   12096945
 3 P HPFS - NTFS          16781   0  1 29647 254 63  206708355
 5 L Linux Swap           29648   1  1 30400 254 63   12096882










*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

```

---

### Post by Monotoko on 2008-10-19
Can someone tell me what that means? is my HDD currupt??

---

### Post by caljohnsmith on 2008-10-19
Your partition numbers all look consistent between fdisk and testdisk, and also testdisk didn't report any errors; so your partition table looks like it is fine. Are you trying to install XP Home or XP Professional edition? Also, is the HDD SATA or IDE?

---

### Post by Monotoko on 2008-10-19
XP Professional, and its IDE

someone told me that i had to make it into a windows partition for windows to recognise it, and told me to download "Super Grub Disk" I now have the disk, but i have no idea how to do it

---

### Post by Monotoko on 2008-10-19
actually, im not to sure what hard-drive, i thought it was IDE, how do i check? (without opening it, its a new laptop)

---

### Post by Monotoko on 2008-10-19
Guys, please, i need your help, how do i identify what kind of harddrive i have?

---

### Post by sea_monkey987 on 2008-10-19
run ```
sudo lshw -C disk
```
find your HDD.  use google and its product # / model # to find what type it is.  be careful not to use the serial #.

as for your original problem, i don't have a clue.  sorry.

---

### Post by Monotoko on 2008-10-19
That took a while, its SATA
do i need another version of windows to install it on a SATA HD? (Its XP)

---

### Post by caljohnsmith on 2008-10-19
If I remember correctly, when you first boot your Windows Install CD, at some point it will give you a chance to load additional drivers; at that point you would need to show Windows where your SATA HDD drivers are, because I believe that's the only way you can get the Win Install CD to recognize a SATA drive. If your HDD came with a CD, it should have the drivers, or you could always download them from the manufacturers website.

---

### Post by sea_monkey987 on 2008-10-19
Here's a thorough post explaining how to add the drivers to the windows xp cd:
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by Monotoko on 2008-10-19
is there anything like Nlite that works under linux?

---

### Post by sea_monkey987 on 2008-10-19
> **Monotoko said:**
> is there anything like Nlite that works under linux?
doesn't seem like there is anything.

---

### Post by linuxluver on 2008-10-19
If I were you, I'd just wipe the hard drive, unless you've been using Ubuntu for a while, then you would probably just copy the home folder and any other personal files and folders to a blank CD.

---

### Post by Monotoko on 2008-10-19
Nah, XP still wont recognise my SATA harddrive (i dont think?)
Leaving me with nothing

---

### Post by linuxluver on 2008-10-19
Well, I know that the type of harddrive(ATA or SATA) doesn't matter with the type of Windows. If you still have an OS installed and working, try to do what I said in my previous post. If that works, install XP first, and during the partitioning process, make the XP partition(NTFS) about half of your HD(if you want just one Linux) or about a third of your HD(if you want Linux to take up two-thirds of the HD or if you want two other OSes). Hope this helps!

---

### Post by sea_monkey987 on 2008-10-19
> Nah, XP still wont recognise my SATA harddrive (i dont think?)
Leaving me with nothing

yeah.  your problem is definitely the missing drivers for the SATA controller.  so, you're right.  doing that would leave you with nothing.  it seems like nLite is the best way to do it.  you're just going to need access to a windows xp computer.  here's another link on how to do it.  this one goes into more detail about acquiring the actual driver: [http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)


P.S.  if you really can't get access to a win xp computer, you could install win xp in a virtual machine, install nLite in the virtual machine, create the modified xp install disk, copy the resulting .iso file onto the physical file system of your real machine, and then burn the iso.  as you can see, this would be a painstakingly long process, but i'm willing to help you through it.

---

### Post by Monotoko on 2008-10-20
Thank you guys for all your support and help, i would still be banging my head against walls if it wasnt for you! This is why i love linux :)

I managed to get my mum to let me have a go on her PC to use NLite and it worked flawlessly :)

XP is now duel-booting with ubuntu, instead of vista -.- (yays!)

Popcorn for all!
:popcorn:

PS: i shall now go through and click the little thanks button on everyone whos helped :)

---

### Post by linuxluver on 2008-10-21
Did I help?

---

