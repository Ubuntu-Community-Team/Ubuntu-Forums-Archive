---
title: "format usb external hard drive"
date: 2009-11-22
forum: Hardware
---

### Post by acefromspace on 2009-11-22
Ubuntu 9.04
What is the best way to format an external (USB) harddrive?
What software to use (that came with Ubuntu 9.04)?
VFAT (FAT32) or NTFS? It will also be used with windows.
Permissions? I don't want to deal with permission issues... keep it simple...
no security needed. This will mostly be used for transferring multimedia stuff, 
nothing critical.

---

### Post by coffeecat on 2009-11-22
To format the drive, either install Gparted and run it from System > Administration > Partition Editor, or boot up from the live CD and access Gparted from there. If you decide to install Gparted to your hard drive install, you also need to install the package 'ntfsprogs' if you want to create an NTFS partition.

So long as you mean a conventional hard drive with platters (not a flash pendrive), I would choose NTFS rather than FAT32  because it is more robust than FAT32, it allows flle sizes greater than 4GB (FAT32 doesn't), and you've got Windows if you ever need to repair the filesystem journal.

External USB drives formatted either FAT32 or NTFS will be automounted by recent versions of Ubuntu and you will not be bothered by permissions problems for the simple reason that Microsoft filesystems do not support Linux permissions. If you look under properties of a file on a NTFS partition, you'll see that it is seemingly owned by root. Don't worry about that - that's all part of the way the ntfs-3g driver copes with mounting the filesystem. You'll still be able to copy, move, delete, edit the files without invoking root powers.

Last point - the only times I would choose FAT32 now is for a flash pendrive or for a drive that I wanted to use on a Mac. MacOS doesn't support writes to NTFS.

---

### Post by loswr86 on 2009-12-19
I haven't found the last reply to be quite true, and I am having a hellofa time getting a iomega prestige 1tb external usb HDD to work. I solely use Ubuntu 8.04, and I formatted the HDD FAT32, as I need to use it between my desktop and my PS3. It will will be used as a media file bank. I will try and remember the steps I have taken so far. 

FYI, it is a brand new blank HDD, so I have no worries about preserving anything on it. 

I used a Gparted live CD to format it (1 large partition) to FAT32, named it "deathstar" and rebooted into ubuntu. 

Nothing, won't automount. After some searching, I learned how to mount it via command line. Presto, deathstar shows up on desktop. However cannot write to drive, as I am told I don't have permission. 

I did a few more searches and tried a few "chown" actions. Nothing. I was helping a neighbor by reformatting and reinstalling his XP box, so I thought maybe I'd just use windows to reformat the HDD, but M$ only gave me the option to format to NTFS. So no go there. Also, when plugged into the windows box, it was recognized, but still could not be written to. 

I fired up gparted again, hoping to reformat again and find some permission/ownership options I missed the first time. Nothing. 

I also discovered that my nautilus wont run. Any time I attempt to fire nautilus up from the command line, I get an error message. 

There was more, but I don't really remember what I have done. Any help would be appreciated.

---

### Post by loswr86 on 2009-12-19
Oh, and when I attempt to use gparted within my 8.04 to view the HDD, my system locks up. I have to reboot. Lame.

---

### Post by loswr86 on 2009-12-19
Well, after more searching I have it up and running, but problem not really solved. I came across this excellent book 

([http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover&source=gbs_navlinks_s#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover&source=gbs_navlinks_s#v=onepage&q=&f=false))

and, while I swear I tried this a week ago, gksu nautilus gave me root file permissions, and deathstar even automounted! I have no idea why, but I am now copying files to this mega hard drive.

---

