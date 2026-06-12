---
title: "Securing external USB Hard disk"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by saltydog on 2007-11-11
I have convinced a friend of mine to install ubuntu on his windows PC, but...
He is using an external Maxtor One Touch 500GB usb HardDisk on which he saves personal data files from Windows. This drive runs a Maxtor utility called DriveLock which password-protects the drive from unauthorized accesses. The problem is that if this protection is activated, Gutsy doesn't event detect the hard disk. Removing the protection, everything runs fine, but he wants his external HD secured.

Is there a way to cheat the DriveLock feature in Linux, or is there a common OS utility to secure the external usb HardDisk in Linux and Windows?

---

### Post by Greevous on 2007-12-27
I was looking for the same thing. Or else is there some way to have Ubuntu utilize the "One Touch" button for backups, maybe with a specific backup utility?

---

### Post by 50words on 2007-12-27
I have never used DriveLock, with my OneTouch or otherwise. I prefer TrueCrypt (FOSS). The Windows GUI is a lot nicer than Forcefield, the Linux GUI (especially if you format the drive/encrypted container as NTFS), but it works. I just use the CLI in Linux, using aliases to make it easier to mount encrypted containers/drives.

Read up on TrueCrypt. It is the best FOSS encryption software I have found, and since it is cross-platform, it works great. You can encrypt a full drive or just a virtual drive using a container file. I prefer the container file, because it is a lot more versatile for backing up, portability, etc.

---

