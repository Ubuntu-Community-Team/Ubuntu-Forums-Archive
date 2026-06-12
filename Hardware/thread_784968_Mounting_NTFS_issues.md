---
title: "Mounting NTFS issues"
date: 2008-05-07
forum: Hardware
---

### Post by Winsbreaker on 2008-05-07
I have a 80GB My Book external HDD and it's connected via USB. I can read and write perfectly in Windows; yet when I plug into Hardy it provides me with a mount error that looks like below.

---

### Post by iPodAddict181 on 2008-05-07
Ubuntu doesn't support NTFS, in fact, only Windows does because Microsoft created it. What you have to do is format the disk to be FAT32, be warned though, formatting the disk will erase it, so copy all the data on the disk to a USB stick, format it, load it on Ubuntu, and then plug in the stick, and copy everything back onto the drive. I'm sure you could find NTFS mounters for Ubuntu/Linux/Unix, but I have tried and have failed every time.

---

### Post by Victormd on 2008-05-07
Ubuntu does have support for NTFS, it doesn't limit you to FAT32 or EXT3. What might have happened is that either you did not eject the external drive under windows so it blocks access to it. Try properly ejecting (safely removing) the drive, unplug it, log in to ubuntu, plug the drive back in and see if that works...

EDIT: just saw your error message and that's seems to be exactly what happened.
This will happen any time you don't shut windows down properly (i.e., hard reset/power down) and affects both the internal HD or external devices connected at the time. This will also happen if you don't "safely remove" the device under windows.

---

### Post by sideburns on 2008-05-08
> **iPodAddict181 said:**
> Ubuntu doesn't support NTFS, in fact, only Windows does because Microsoft created it.

I suggest you look at ntfs-3g.  If it isn't already installed on your system, it's easy to add.  Once it's in, you just specify that as the filesystem type either when mounting the drive or in fstab and Bob's your uncle.

---

### Post by sackbj on 2008-05-08
I remember reading at one point in time that Linux was not able to read/write to an NTFS filesystem, but that Samba was the answer to this.  Is this still true or was that old information?

This is important to me becasue my computer has two drives.  One Raptor that I use to boot into Vista, and one 640GB drive (NTFS) that I use for all of my media, images, etc.  I would like to add another, smaller, hard drive and boot into Ubuntu, but I would still like to easily access my files on the 640GB drive.

---

### Post by shug33 on 2008-05-08
From my experience, victormd is exactly correct.  Do as he says and you should be able to access your NTFS drives.

---

### Post by Victormd on 2008-05-08
> **sackbj said:**
> I remember reading at one point in time that Linux was not able to read/write to an NTFS filesystem, but that Samba was the answer to this.  Is this still true or was that old information?

Samba is a networking protocol to allow you to access windows networks via Ubuntu.

---

### Post by danwood76 on 2008-05-08
I use a 1TB NTFS drive with Ubuntu perfectly thanks to NTFS-3G.
I even get faster transfer speeds compared to Vista ;)

---

### Post by nero_86 on 2008-05-08
Probably the last time you have used the drive from Windows, you unmounted it in a bad way. In my computer simply i restart win, open and close the drive and unmount it in a clean way.
Than it will be accessible fron Linux.

This happen because the NTFS driver for Linux for security reason don't access NTFS filesystem not clean.

---

