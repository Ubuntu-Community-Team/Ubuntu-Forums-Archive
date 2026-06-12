---
title: "SimpleTech External Hard Drive"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by eArquilla on 2007-08-25
Picked up a 500 gig SimpleTech external from best buy (had a sale for $120)

I'm running 64 bit ubuntu if that makes any difference

I turn the external on, ubuntu detects it, great so far. But then I realize it's read-only. After some searching I found the NTFS configuration tool and enabled write support for external devices. Problem is, now when I turn on the external hard drive, I receive the error message: 

Cannot mount volume
Unable to mount the volume 'SimpleDrive'

Details:
$LogFile indicates unclean shutdown (0, 1) Failed to mount '/ dev/sdb1': Operation not supported Mount is denied because NTFS logfile is unclean. Choose one action: Boot windows and shutdown it cleanly, or if you have a removable device then click the 'Safely Remove Hardware' icon in the Windows taskbar notification are before disconnecting it. Or run ntfsfix version 1.13.1 on Linux unless you have vista. Or Mount the NTFS volume with the 'ro' option in read-only mode.



I've tried the command pmount-hal /dev/sdb1 but it once again opens in only read-only mode regardless of the NTFS configuration. 

sudo ntfsfix /dev/sdb1
gives me:
Refusing to operate on read-write mounted device /dev/sdb1



I've also read of some success with 

sudo rm /media/.hal*

but this did nothing for me.

Help is much appreciated, i never post unless I have thoroughly searched for an answer first, but if i missed something, please be sure to let me know.



Noob - maybe. but at least i've taken the initiative to not use windows.

---

### Post by eArquilla on 2007-08-25
bump

---

### Post by merlinus on 2007-08-25
> 
sudo ntfsfix /dev/sdb1
gives me:
Refusing to operate on read-write mounted device /dev/sdb1


Did you try unmounting the partition first?

-merlin

---

### Post by Glaxed on 2008-03-15
Bit late here, but I believe I may have a solution.
Terminal:
[php]
$ sudo apt-get install ntfs-3g ntfsprogs
$ sudo mkdir /dev/exHDD
$ sudo ntfs-3g -o force,rw /dev/<device-name> /dev/exHDD
[/php]
I don't think ntfsfix will do anything for you..
Please look at the install directions on the following thread.;
[http://ubuntuforums.org/showthread.php?t=624943](http://ubuntuforums.org/showthread.php?t=624943)

Good Luck

---

