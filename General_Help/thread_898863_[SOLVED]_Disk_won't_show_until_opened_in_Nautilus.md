---
title: "[SOLVED] Disk won't show until opened in Nautilus?"
date: 2008-08-23
forum: General Help
---

### Post by x300 on 2008-08-23
So, I have this partition (of the same HDD as the filesystem), and I want to access it in the terminal. 
I use it as the standard HDD for rtorrent, but when I start rtorrent I get a message saying something like disc unreachable, and I do 'ls /media/' and it's not there. 
Then I start nautilus and just clicks it to the left and boom! It appears in the terminal as if it's been there all along. 

Why?! 

How do I make it visible without clicking on it?!?

---

### Post by Sam Lars on 2008-08-23
The reason is that the disc is not mounted by default.  When you click on it in Nautilus, you're mounting it, and then it shows up in your /media directory.
To get it to mount automatically, you have to edit your /etc/fstab file.
First, you should make a backup copy of the file:
```
sudo cp /etc/fstab /etc/fstab.bak
```
Then open the file as root.
You'll see at least one line that looks like this:
```
UUID=57c9d998-8a37-4eea-884c-bf19095f9bd9 /home           ext3    defaults,errors=remount-ro
```
You have a few things you need to change.  The UUID line you can change to /dev/sda1 or what your drive is.  You can do
```
df -h
```
after you mount the drive through Nautilus to see which one it is based on size.
The next item is where it's mounted.  You can make an empty directory of your choice to mount it to.
The next item is filesystem type.  Change this to the filesystem of your drive.
The rest can be left alone.  You can right click and unmount the drive, and then do
```
sudo mount -a
```
or reboot to see if it works.  The above command will be useful for tracking down errors if something isn't right.

---

### Post by x300 on 2008-08-24
Sweet! Thank you :)

I didn't even think about it not being mounted... should have thought about that!

---

