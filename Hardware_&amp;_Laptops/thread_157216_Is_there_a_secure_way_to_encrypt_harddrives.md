---
title: "Is there a secure way to encrypt harddrives?"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by XPerienced on 2006-04-08
Hi!

I'm having problems to decied method to encrypt my harddrives (for storage only).

I got to be secure and work with password only. Cause it got to work if I reinstall Ubuntu, if I need to change my system harddrive, if I need to put one harddrive in another computer etc.

Cryptloop is not secure enought and DM-crypt is slow I heard. And I couldn't mount the harddrive after the reboot when I encrypted one harddrive with DM-crypt.

I prefer to encrypt the filesystem like in Windows with Drivecrypt.

I need so answers asap. It's hard to find so I give it another shoot.

XPerienced

---

### Post by ghakko on 2006-04-08
We've benchmarked a 600MHz Celeron at around 15MB/s when doing in-kernel encryption with AES128. Most desktop computers are much faster than this, and the bottleneck will likely be the disk, not the processor.

You can encrypt:
[LIST=1]
[*] Entire disks. Encrypting the entire boot disk is not possible without BIOS support and a hard disk with ATA security extensions. Some newer notebooks (including recent-model IBM Thinkpads) can do this, and will prompt you at boot to type in the disk key.
[*] Entire partitions (similar to PGP Whole Disk Encryption, SecureDisk). The "cryptsetup" package (from the "universe" repository) can be used to [encrypt](http://www.saout.de/tikiwiki/tiki-index.php) entire partitions (and hence swap space and filesystems they contain). Encrypting the one with the root filesystem is possible, but very tricky.
[*] User home directories (similar to OS X FileVault). The "libpam-encfs" package (also from "universe") is a PAM plug-in that will automatically mount an [encrypted filesystem](http://encfs.sf.net) at your home directory when you log in, using your regular user password as the key.
[*] Individual files (similar to Windows EFS). Not possible on Linux at present.
[/LIST]

What's probably most important is figuring out what you can encrypt and which of these fits your needs.
[LIST]
[*] Is the computer being physically shared with other users? Will they all be able to supply a key when booting the computer?
[*] Do you want to encrypt swap?
[*] Where is your sensitive data? (/var/log, /home, /var/spool/squid?)
[*] Do you need to pool unused disk space?
[/LIST]

---

### Post by XPerienced on 2006-04-08
I've heard about that. There's a HOWTO on this forum, but is it a good and secure enough?

And what about:
[http://luks.endorphin.org//dm-crypt](http://luks.endorphin.org//dm-crypt)

XPerienced

---

