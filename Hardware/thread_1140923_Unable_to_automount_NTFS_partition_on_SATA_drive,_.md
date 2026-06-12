---
title: "Unable to automount NTFS partition on SATA drive, then I screwed up"
date: 2009-04-28
forum: Hardware
---

### Post by simiansamurai on 2009-04-28
I've been running Ubuntu for about a year now through the various upgrades and couldn't be any happier.

I've always been frustrated how my 2 gig NTFS partition would never auto-mount after a reboot, and I was just trying something else tonight and I screwed it all up bad!

I was changing some mount options on the drive (after I had the icon appear on my desktop) and in the field called "File System" on the **Volume** tab I entered "ntfs". 

I unmounted and remounted it again, but only got the error:

**Cannot Mount volume.** 
Error *org.freedesktop.Hal.Device.UnknownError.* 
Details: 
libhal.c 1399 : wrong reply from hald. Expecting an array. org.freedesktop.Hal.Device.Volume.UnknownFilesystemType


Anybody have any ideas? Suggestions? Did I lose my partition?

---

### Post by espenalb on 2009-06-22
I had the same problem - do not worry - no data is lost. :-)

This is what I did:
Edit /etc/fstab using the following command:

sudo gedit /etc/fstab

add the following line at the end (Assuming your HDD is /dev/sda1:
/dev/sda1 /media/C ntfs-3g defaults,locale=en_US.UTF-8 0 0

Save the file and exit.

Then mount your disk using this command:
sudo mount /media/C

Your windows disk is now available.

I am not able to mount/unmout my disk from the file browser - I am sure that is possible by modifying some of the parametrers after ntfs-3g, but I have not investigated that yet... 

Good luck

---

