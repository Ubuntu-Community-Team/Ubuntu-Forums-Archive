---
title: "First hard disk is not visible during install"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by miig on 2009-10-27
hi , I tried to do a clean install of 9.10 (amd64) RC  from a usb pendrive above my 9.04 (amd64) but during the installation process my first hard disk doesn't appear.

[IMG]http://salusa.ath.cx/files/Screenshot-Install.png[/IMG]
the message : "This computer has no operating system on it" is bothering me since I HAVE two on it :(

[IMG]http://salusa.ath.cx/files/Screenshot-Install-1.png[/IMG]
as you can see /dev/sda is not available

but if I do a fdisk -l on a terminal i get :
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cf44cf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       10079    40001850   83  Linux
/dev/sda3           10080       10328     2000092+  82  Linux swap / Solaris
/dev/sda4           10329       60801   405424372+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50ac50ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       60801   447426315    f  W95 Ext'd (LBA)
/dev/sdb5            5100       17847   102398278+   7  HPFS/NTFS
/dev/sdb6           17848       30901   104856223+   7  HPFS/NTFS
/dev/sdb7           30902       43955   104856223+   7  HPFS/NTFS
/dev/sdb8           43956       60801   135315463+   7  HPFS/NTFS

Disk /dev/sdc: 2062 MB, 2062548992 bytes
64 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x0003839c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1015     2013729    b  W95 FAT32

```

I tried with 9.04 (amd64) installer and both drives appear...
I also tried unplugging 2nd hard disk and 1rst is still not visible.
I aslo tried inverting SATA ports between the two hard disks.

Hardware :
  CPU: Core2 Quad Q9550
  MB : MSI P35 Neo2 FIR 
  RAM: 4Gb Hyper-X Kingston PC8500
  HD : 2 x WD SATA2 500GB  
  GPU : Nvidia Gefoce 8800 GT 

I'd like to do a clean install of 9.10, and want to keep the upgrade solution as a last resort...

Any suggestions ? Thank you in advance

---

### Post by shaggy999 on 2009-10-28
Is the first hard drive plugged into a different controller? A lot of motherboards have 2 sata controllers on them, 1 that controls the first few sata ports, and the second one supports the raid-capable sata ports. Perhaps ubuntu doesn't see the first hard drive because it can't talk to the controller for that hard drive?

Or possibly are one drive is set to AHCI and the other to the uh... whatever the other mode is called... in the BIOS?

Actually, neither of those options make sense since the live CD sees the drives.

---

### Post by shaggy999 on 2009-10-28
Another thing I thought of is if you mount a drive in the live CD environment I think the installer ignores it. So make sure the sda drive isn't mounted.

---

### Post by miig on 2009-10-28
my board has 7 SATA ports ( the two first are external ( E-SATA) ) and the other 5 are internal. Since I already switched the SATA cables I almost tried every internal SATA port for my system disk.

as you can see on the ouptut of "fdisk -l" I only have an external disk plugged and its /dev/sdc from where I am running  karmic koala live CD ( I made it with USB startup disk creator).

On my Bios the disks are in RAID mode and not AHCI. Tonight (I am not at home now, work :() I will try to switch between the other 2 modes ( IDE, AHCI). But what's weird is that with 9.04 USB startup disk both disks are detected by the installer...

And to answer your second post I tried once manually unmounting both disks  before install and the installer still don't see my system drive.

Thank you for you answer...

---

### Post by miig on 2009-10-28
I tried to change Bios setting about SATA controller and for each setting 8IDE,RAID or AHCI) the situation is the same my system hard drive doesn't appear at the partionner during Karmic Koala install procedure. Where with Jaunty Jackalope it works perfectly...

Does anyone have a clue ?

---

### Post by niite on 2009-10-28
I had the same problem.  I gave the alternate version a shot, and that one worked when i chose to manually config the partitions (was able to see and select the second hard drive).

---

### Post by miketrek on 2009-10-29
I am having the same problem except install is not seeing my first two SATA drives, but does see the third. I have tried both the desktop and alternate install CDs to no avail. Disks and partitions do show up in the 9.10 live environment no problem and also show up in gparted but just not showing up in the install.

This is the output from fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x509b3168

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          65        8575    68364607+   7  HPFS/NTFS
/dev/sda2               1          64      514048+  83  Linux
/dev/sda3            8576       38913   243689985    5  Extended
/dev/sda5            8576       19517    87891583+  83  Linux
/dev/sda6           38671       38913     1951866   82  Linux swap / Solaris
/dev/sda7           19518       38670   153846441   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001033d

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c4d0b55

 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux



Only sdc1 shows up in the install.

---

### Post by miig on 2009-10-30
Thank you for all your replies
with the alternate install I was able to install Karmic Koala, and both my disks appeared normally.

just to try understand why It didn't work ?
Does you ever build an Raid Array with those disks based on (SATA chipset RAID ) ? Because the only thing odd about my hardware config that cross my mind Is that both disks used to be part of an array RAID 1 (Mirroring ) and I destroyed the array without formating the disk where I keep the System ( the disk that didn't appeared) Next time I format completely that disk I ll try normal Install.

---

### Post by vyruz18 on 2009-10-30
I have exactly the same problem as TS.
Using the following hardware:
- Asus P5N32-E SLI Premium (Nforce 680i chipset)
- sda: 80GB Hitachi SATA Drive for my Ubuntu install
- sdb: 2x WD Raptor 74GB in RAID 0 for Win7 installation
- sdc: 250GB Western Digital drive for data storage
- CPU : C2D E6600

Installer detects both my Nvidia RAID 0 array and the 250GB data drive, however my first 80GB Hitachi drive is never detected.
While I have the installer on the screen I can switch to shell using CTRL+ALT+F1 and when running sudo fdisk -l I can see all the drives and their partitions.
the 80GB drive had some old data and partitions on it so I wiped it clean using Fdisk but still the installer isn't seeing the disk.

So I went ahead and unplugged the other 3 drives so that my system remained with the 80GB drive as its only hard drive.
But still the installer isn't recognizing the disk :S

If I can see the disk when running fdisk that means that the drivers etc. are fine right?
Seems like an installer bug to me...

---

### Post by puleen on 2009-10-31
I am having the exact same issue. I will try to see if using the Alternate iso will change anything. But this is weird. I don't even have RAID configured on the motherboard!

---

### Post by cough on 2009-10-31
The exact same thing is happening to me. I have four hard disks and only sdc1 is visible to the installer. All other disks are available on the live cd, in gparted, disk utility, fdisk - l...etc. I've unplugged all my disks except the one I want to install to and the installer still can't detect it. I've tried the alternate cd and it just hangs when I get up to the partitioning section.  I'm stuck and don't know what to do.  Does anyone have anymore ideas?
 
Thanks to the previous posts too, which helped me get to this point. I almost shelled out hard earned cash to buy new hard disks. I really don't wanna do that, but if I have too; I have too.

---

### Post by D-Dan on 2009-10-31
Me to - except in my case only one drive out of three is vsible to the installer (drives 1 and 3 are missing). 9.04 sees all the drives just fine. I've already tried most workarounds that others have (unsuccessfully) tried, swapping the SATA order, unplugging the other drives etc.

I'll try the alternative but I don;t hold out much hope.

MB is Abit KN9Ultra, and all three drives are Hitachi - same family.

Steve

---

### Post by cough on 2009-10-31
My motherboard is MSI P45NEO3. I'm reformattig and partioning the drive in gparted live cd mode. I read in a post this worked for someone else. If it works for me I'll let you know.

---

### Post by cough on 2009-10-31
I had no luck with partitioning and formatting my drive. I've also forgot to mention, I have these errors (screenshots attached). Could this be the cause of the problem? Do you have the same thing?

---

### Post by Leslie Viljoen on 2009-10-31
This sounds like this known issue:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054)

Should be in a release note or something I would expect - and perhaps it is.
Otherwise I guess people need to automatically know to search Launchpad before downloading a new ISO.

---

### Post by Leslie Viljoen on 2009-10-31
Here they are:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

---

### Post by cough on 2009-10-31
Thanks Leslie.

I'm able to install to my hard disk now. I ran the following command > sudo badblocks -swv /dev/sda and it seemed to have fixed my problem. I didn't even let it complete, I let badblocks do it's thing for ~ 1 hour. I'll plug in the other drives once I have a successful boot into Karmic...hopefully they'll work.

Wish me luck....

---

### Post by cough on 2009-10-31
I'm finally using Karmic (posting from it right now). I tried to install from the Desktop edition, which completed successfully but when I tried to boot I only got a black screen.

I used the alternate CD and now it's working....hurrah!

Thanks everyone. I hope the information I posted helps someone.

---

### Post by rmjb on 2009-10-31
I was also getting this. On the live cd I uninstalled the dmraid package, restarted the installer and now sda shows.

---

### Post by puleen on 2009-10-31
rmjb, what did you do to uninstall the dmraid package?

I selected the "No DMRAID" from boot options, but it still does not detect the drives.

---

### Post by rmjb on 2009-10-31
apt-get remove dmraid

---

### Post by loconet on 2009-10-31
> **rmjb said:**
> apt-get remove dmraid

This is probably a stupid question but how can you remove a package from the CD? :???:

---

### Post by Dakra on 2009-10-31
I suppose it removes it from the system loaded in the RAM memory.

---

### Post by rmjb on 2009-10-31
Yes it does. Sorry I wasn't completely clear. I got through when I uninstalled dmraid from the running system. You can do this with the command:
sudo apt-get remove dmraid

or you can use Synaptic to remove it.

To me it looked as if dmraid was blocking the installer from seeing the first hard disk. I saw something about this somewhere else and it might only affect you if you once played with on-board raid on the drives you are using now. Once you do that the drives are marked as having been in a raid and the installer ignores it.
Booting with the nodmraid option didn't fix it for me, I had to uninstall it.

Hope all this info helps.

- rmjb

---

### Post by Ginsu543 on 2009-10-31
When I initially tried to install 9.10 using the live CD, the installer would only recognize my two WD Raptors as members of a RAID array (even though I don't even have RAID turned on in BIOS) and would not see them separately as sda and sdc. So I tried the advice here and removed dmraid (sudo apt-get remove dmraid). When I ran the installer again, this time I could see them as independent drives. But the RAID array was still there as well. The partitioner let me partition sdc to install 9.10 on it, but when I continued with the installation, I got an error message stating that there was an error formatting the partitions on sdc. I'm assuming that there is some sort of conflict between the installer thinking that my drive is in a RAID array and my asking it to format it as an independent drive. But I just can't seem to delete or remove the RAID array.

Does anyone have an idea how I can fix this?

Thanks in advance.

---

### Post by leo123 on 2009-11-01
The same thing happened to me too. Finally, can't remember which one, but after selecting one of the radio buttons in your first pic, you can use the drop down arrow to select the other hard disk.

---

### Post by shaggy999 on 2009-11-01
> **Leslie Viljoen said:**
> This sounds like this known issue:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054)

Should be in a release note or something I would expect - and perhaps it is.
Otherwise I guess people need to automatically know to search Launchpad before downloading a new ISO.

I don't see any reference to this bug in the release notes and new users should not be expected to search launchpad.

---

### Post by D-Dan on 2009-11-01
I had this exact problem, and whilst I'm not saying it's the definitive reason, I've been able to reproduce it.

In my case, it turns out that a hard drive was failing (I have 3 HD's, one for Ubuntu, one for Vista, and my data drive). In my case, despite it not being mounted for any valid reason, my data drive was reporting errors. I replaced it, and Ubuntu installed.

I moved the failing drive to PC2, and tried to install Ubuntu to the drive that was originally in there (ie. Not touching the failing drive) with the same result - it doesn't appear in the installer.

It seems to me that 9.10 is far more sensitive to potential HD failures. I haven't tried this but an option may be to disable SMART in the BIOS.

Steve

---

