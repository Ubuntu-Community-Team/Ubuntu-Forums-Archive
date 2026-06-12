---
title: "Windows does not recognize partitions on Ubuntu disk"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by chilisastry on 2009-04-06
Sometimes I need Windows, sorry. (Skype, Logitech webcam, etc.)

My computer has three disks - one SCSI and two IDE-ATA.

Windows 2000 was installed on the SCSI drive, and Fedora on one of the IDE drives.  The second IDE drive has many partitions (about 5 I think) - one for /boot, one for Ubuntu-linux, one for swap, and a NTFS partition for data backup common for both Windows and Linux.  The grub bootloader is on the Ubuntu drive, and I could boot any of the three OSs.  Worked quite well till recently.

I had to re-install Windows 2000 (don't ask why) so I disconnected the IDE drives and installed Windows 2000 on the SCSI drive (as before).  I then connected the IDE drives thinking that all will be back to normal - imagine my surprise/chagrin when all I could see in Windows was unformatted hard drives for the IDE drives.  I thought all my data was lost, and both the Linux installations as well.

However, I can still boot from the IDE drives, use the grub loader, and boot to any of the three OSs.  After booting to Linux (Ubuntu or Fedora), I can access the NTFS (data) partition, as well as the SCSI drive (NTFS as well).  So I still have my data - but I can't access it if I boot into Windows.

I can, of course, take the long route and repartition the Ubuntu drive from Windows, reinstall Ubuntu, and restored data into the (common) NTFS data partition.  I am sure this will work.

But..... is there an easier way to bring this back to normal?

A long narrative, but detailed description is essential to accurately describe this problem, in case someone knows of a solution.

---

### Post by upchucky on 2009-04-06
if i understand this right, you are trying to read/write Linux partitions using the windows operating system.

this will not work, The Microsoft gods do not support that in their os, after all when you are all high and mighty why would you want to use something that is better than yourself. 

unless i have misread your post, and you meant to say you cant read/write windows from linux. if this is the case then some permissions need to be redone.

now if windows cant read the NTFS partitions, this is beyond me and the gods need a slap.

i suspect some file permission, hide, or association settings in windows.

---

### Post by dtoronto on 2009-04-06
Ubuntu file system is not recognized by any version of Linux.  Sorry bro.

---

### Post by Didius Falco on 2009-04-06
> **chilisastry said:**
> Sometimes I need Windows, sorry. (Skype, Logitech webcam, etc.)

My computer has three disks - one SCSI and two IDE-ATA.

Windows 2000 was installed on the SCSI drive, and Fedora on one of the IDE drives.  The second IDE drive has many partitions (about 5 I think) - one for /boot, one for Ubuntu-linux, one for swap, and a NTFS partition for data backup common for both Windows and Linux.  The grub bootloader is on the Ubuntu drive, and I could boot any of the three OSs.  Worked quite well till recently.

I had to re-install Windows 2000 (don't ask why) so I disconnected the IDE drives and installed Windows 2000 on the SCSI drive (as before).  I then connected the IDE drives thinking that all will be back to normal - imagine my surprise/chagrin when all I could see in Windows was unformatted hard drives for the IDE drives.  I thought all my data was lost, and both the Linux installations as well.

However, I can still boot from the IDE drives, use the grub loader, and boot to any of the three OSs.  After booting to Linux (Ubuntu or Fedora), I can access the NTFS (data) partition, as well as the SCSI drive (NTFS as well).  So I still have my data - but I can't access it if I boot into Windows.

<snip>

But..... is there an easier way to bring this back to normal?

 

Okay, this is a Windows problem. First, have you reinstalled all the updates for it? A quick search led me (through a couple of detours) to this:

[http://support.microsoft.com/kb/305098](http://support.microsoft.com/kb/305098)

A quick read-through leads me to believe this may well be your problem. 

If it is, you can try applying all the updates/patches to W2K and see if that works.

If it doesn't, don't lose hope - remember that it's windows that is screwed up, not your data partition. You could always unplug the IDE drives again, wipe/reinstall W2K, bring your patches up to date and then plug in the IDE drives again.

No guarantees, of course, but the only partition you really need to worry about is the shared NTFS one. Need be, you could simply back that one up, wipe it, make a new one, get W2K to see it and restore the data.

In any event, I hope the MS support document I linked helps.

Good Luck

---

### Post by Vrekk on 2009-04-06
> **dtoronto said:**
> Ubuntu file system is not recognized by any version of Linux.  Sorry bro.

Dont stop in you tracks just yet! I have mouted and writen to the ubuntu part of my HD from within windows xp and vista
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

It is the drivers for ext3 (probally wont work with the new ext4).  A nice little app opens and you just select the ones you want to mount and reboot windows.

While it has caused no problems for me, this could create problems.  Dont mess with ANY system files while booted into windows because you can screw up your ubuntu, with powers close to root

---

### Post by chilisastry on 2009-04-07
> **Didius Falco said:**
> Okay, this is a Windows problem. First, have you reinstalled all the updates for it? A quick search led me (through a couple of detours) to this:

[http://support.microsoft.com/kb/305098](http://support.microsoft.com/kb/305098)



If it doesn't, don't lose hope - remember that it's windows that is screwed up, not your data partition. You could always unplug the IDE drives again, wipe/reinstall W2K, bring your patches up to date and then plug in the IDE drives again.

No guarantees, of course, but the only partition you really need to worry about is the shared NTFS one. Need be, you could simply back that one up, wipe it, make a new one, get W2K to see it and restore the data.


Good Luck

Thanks for understanding the problem (unlike many other replies!).

I have Windows 2000 SP4 with all the latest updates.  But I see the registry key for LBA is missing - so I added it.  It does not work yet, but I have to restart the computer to try.

I don't know any way to wipe out just the NTFS partition in the IDE drive, so I will have to reinstall Ubuntu as well (if I take the long route).

Thanks for the support.

---

### Post by chilisastry on 2009-04-07
> **Didius Falco said:**
> Okay, this is a Windows problem. 

[http://support.microsoft.com/kb/305098](http://support.microsoft.com/kb/305098)

A quick read-through leads me to believe this may well be your problem. 


Good Luck


Didius,

Adding the key to the registry, and restarting Windows worked. Thanks for all the help.

---

### Post by Didius Falco on 2009-04-07
> **chilisastry said:**
> Didius,

Adding the key to the registry, and restarting Windows worked. Thanks for all the help.

No problem. I'm glad it turned out to be as simple as adding a registry key.

The only thing better than a very simple solution is not having a problem. <G>

---

