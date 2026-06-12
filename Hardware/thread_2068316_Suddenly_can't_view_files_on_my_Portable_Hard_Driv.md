---
title: "Suddenly can't view files on my Portable Hard Drive"
date: 2012-10-08
forum: Hardware
---

### Post by alwaysright on 2012-10-08
Hey there,

This morning, I decided to start using my desktop computer again instead of my laptop.  I have all of my files (movies, music, pictures, documents) on my portable hard drive (toshiba).  I unplugged my hard drive from my laptop computer, and then plugged it into my desktop computer.  An error message appeared that said something about not being able to display my files.  

I can't see any of the files I know are on my portable hard drive. Under properties, it still says that my hard drive is 75% full, but all I can see is my folders, and they appear to be empty.

I moved the hard drive from a 12.04 Ubuntu system to an 11.10 Ubuntu system, but I don't think that matters.  Neither my 12.04 Ubuntu Laptop, nor my Windows 7 laptop, nor my Ubuntu 11.10 desktop computer can see my files.

Someone please help me get access to those files!

---

### Post by ahallubuntu on 2012-10-08
I wish every hard drive and computer came with a warning:

HARD DRIVES ARE NOTORIOUSLY UNRELIABLE!!!  IF YOU CARE ABOUT LOSING YOUR PICTURES AND DOCUMENTS, IT IS VITALLY IMPORTANT TO MAKE REGULAR BACKUPS!!!

I try my best to impart this warning to everyone I know who uses a computer, but some people never seem to get it.

Your hard drive may not be failing - maybe there is just some simple fix or maybe a corrupted filesystem or something non-fatal.  You don't mention what kind of filesystem (FAT32?  NFTS?  ext4?) you used on the drive.  If you never formatted it in Ubuntu, it's probably FAT32.  In that case, I would use a Windows computer (or boot a Windows disc) to try to run the chkdsk program on it to attempt to repair filesystem problems.  If it is formatted for Linux (ext4, ext3, etc.) try running e2fsck on it to do the same thing.

You can also try smartmontools (graphic tool: GSmartControl) to check the drive's S.M.A.R.T. status to see its general health.  If there are Attributes failing (shown in red) in GSmartControl and they are bad ones, your drive may be failing; if no Attributes show in red, maybe it's really OK and it's just some filesystem issue.

---

