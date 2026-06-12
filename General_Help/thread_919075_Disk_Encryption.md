---
title: "Disk Encryption"
date: 2008-09-13
forum: General Help
---

### Post by solarwind on 2008-09-13
I have a hard drive with windows and Linux. Linux has 4 partitions. What's the best way to encrypt my entire Linux system (all 4 partitions)? I don't care about the windows partition.

---

### Post by hyper_ch on 2008-09-13
you will have to re-install linux for full disk encryption.

---

### Post by solarwind on 2008-09-13
> **hyper_ch said:**
> you will have to re-install linux for full disk encryption.

Ok scratch that. What about just the /home partition?

---

### Post by hyper_ch on 2008-09-13
you need to move away the data from your home, then encrypt it, then assign it a file system, then alter crypttab and fstab then move the stuff back in.

---

### Post by solarwind on 2008-09-13
> **hyper_ch said:**
> you need to move away the data from your home, then encrypt it, then assign it a file system, then alter crypttab and fstab then move the stuff back in.

Ok I'm a noob when it comes to encryption on Linux, can you walk me through it?

---

### Post by hyper_ch on 2008-09-13
a complete reinstall would be the simplest method and I'm off now... there's info out there, it just needs to be found.

---

### Post by solarwind on 2008-09-13
> **hyper_ch said:**
> a complete reinstall would be the simplest method and I'm off now... there's info out there, it just needs to be found.

No, there's always a way to do it. Linux never needs to be "reinstalled". Reinstalling would be lazy and a huge waste of time. Thanks a lot for being so amazingly helpful.

---

### Post by bodhi.zazen on 2008-09-13
Look through the documentation here :

[http://www.saout.de/tikiwiki/tiki-index.php?page=LUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=LUKS)

and here:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

The process of encryption is destructive, so you need to boot a live CD, make a new encrypted partition for /home, mount it, move home, and config your ubuntu partition to mount it at boot time.

The Ubuntu installer will do all this automagically (from the alternate CD). You can decide for yourself which is easier.

To be honest, I would advise a simple LUKS encrypted data partition, mount it manually or truecrypt.

---

### Post by evilgold on 2008-09-13
The simplest way to go would be encfs. i dont know if it would work with you home folder since encfs prevents files from being read by any users other then the one who mouted the fs, even root, but you could make a folder inside your home folder for encfs and keep whatever you need private in there.

Or you could either resize your main partition and make a new one to encrypt for home, or if thats not possible you could make a file of whatever size you want and use that as an encrypted home.

Yet another option is truecrypt, but it has licence conflicts that make it non-free, so i wouldnt really reccomend it.

It actually is REALLY easy to setup encrypted root filesystem by reinstalling. There is an option for it on the alternative installer. If nothing else, you should keep this in mind for the future.

Also here are some links:

[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)
[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

---

### Post by solarwind on 2008-09-13
> **evilgold said:**
> The simplest way to go would be encfs. i dont know if it would work with you home folder since encfs prevents files from being read by any users other then the one who mouted the fs, even root, but you could make a folder inside your home folder for encfs and keep whatever you need private in there.

Or you could either resize your main partition and make a new one to encrypt for home, or if thats not possible you could make a file of whatever size you want and use that as an encrypted home.

Yet another option is truecrypt, but it has licence conflicts that make it non-free, so i wouldnt really reccomend it.

It actually is REALLY easy to setup encrypted root filesystem by reinstalling. There is an option for it on the alternative installer. If nothing else, you should keep this in mind for the future.

Also here are some links:

[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)
[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

Thank you. I would really hate to reinstall so I'll  figure out another way.

---

