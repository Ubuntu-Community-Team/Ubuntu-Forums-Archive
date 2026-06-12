---
title: "cannot seem to install (or boot into ?) ubuntu studio on a firewire 800 drive"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-06-21
hello all
as a follow up to this thread 
[http://ubuntuforums.org/showthread.php?p=7484021#post7484021](http://ubuntuforums.org/showthread.php?p=7484021#post7484021)

i'm stuck trying to install ubuntu studio on a firewire 800 drive.
the drive contains two other bootable mac OS's ( 10.4 and 10.5, dedicated to audio and video tasks), and a large ntfs storage space for the two oss's
the drive is a recent firewire 800, 1To, bootable. the machine, a macbook pro, has had no issues with firewire drive booting

the drive, identified as sdb, lets me install ubuntu studio on a dedicated 30 Gig partition in ext4
the partition is bootable, mounted as root / mount point
sbd6

there is a 10gig SWAP partition, use as swap, which is labelled sdb2

installing goes well. i choose manual install, erase and format the dedicated partition to ext.4, designate a / root mount point, bootable 
yet i've had issues with the grub install. i tried to specify the partition on which to install and got a fatal error. it finally worked, i think, with /dev/sdb as a location

i got an "install complete" message, and was asked to restart. yet upon restart it boots directly onto the firewire drive's mac os.

now when i start the machine and press the alt key, usual alternate boot option, i get a choice between 
mac os on my internal hard drive, 
windows xp boot camp on my internal hard drive,
 the two mac os's on the firewire drive,
 and a **new partition on the firewire drive recognised as "windows"**, which i believe is due to the grub install

unfortunately, choosing this "windows" actually boots onto the internal drive's windows xp, instead of the sdb6 ubuntu studio install...

i can't tell if the ubuntu studio os was actually installed or not, as i've never been able to boot into it.

i've tried redoing the install a few times, but to no avail

now i'm really stuck, reading up, or trying to, is becoming confusing

any ideas on how to to check that the system is installed, boot into it or make it bootable would be great

my only concern is to protect the two mac os's on the firewire partition as well as a 600 gig ntfs storage space which contains work related data


thanks greatly

ben

---

