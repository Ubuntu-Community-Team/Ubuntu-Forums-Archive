---
title: "USB Drives - Mac and Windows"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by FRGus723 on 2007-06-01
I am relatively new to Linux and have a few questions.  In a recent attempt to ditch Micro$oft I took a laptop and loaded Ubuntu Feisty.  I have 2 USB NTFS drives attached to the Linux box which I can read movie and MP3 files from just fine.  I have the old Windows laptop also hard wired to my network which I am solely using as an Azureus bittorrent machine (mainly because I can't write to the NTFS drives without having to first convert to FAT32 or EXT2/3 which I don't wish to do for data integrity)  I also have a MacBookPro (my primary machine) and 5 other machines which connect wirelessly to the network and can also play all the movie and MP3 files from the USB drives connected to the Linux box.  The question I have is now when I am done downloading a torrent to the windows box and try to copy the files to the NTFS USB drive connected to the Linux box I get a permission error.  I am not trying to write to the USB drives from Linux but rather copying an AVI or MP3 file to it from a Windows box.

Can someone, in plain beginner language, explain how I would set permissions on the USB drives to be able to write to them from a Windows box.  The linux box will never try to write to them nor do I need them to.  I want the USB drives in NTFS so when I take the drive to friends houses who have Windows boxes they can read the files.  So changing the file structure on the drives is not what I am looking for, just the ability to write to it from a Windows box.  My thought is I probably need to go to etc/fstab and do a chmod to the mount point for the USB drives but I haven't tried this yet.  Is this the right first step?

Anyone have some suggestions?  Thanks for your help.

I have reposted this to General help because this may be the wrong category...sorry.

---

### Post by youthforlinux on 2007-06-01
ntfs-3g allow for write access to NTFS Drives in Ubuntu

---

