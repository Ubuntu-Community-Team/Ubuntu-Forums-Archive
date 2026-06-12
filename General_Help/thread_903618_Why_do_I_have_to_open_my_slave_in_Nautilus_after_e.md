---
title: "Why do I have to open my slave in Nautilus after every boot?"
date: 2008-08-28
forum: General Help
---

### Post by Solidcell on 2008-08-28
So every time I start my computer, my NTFS slave drive (that used to be on my old windows box) doesn't show up in /media when using the terminal.  Only after I use Nautilus to go to /media and then open 'Music Slave' (it only shows up in Nautilus), it asks for my root password, and then afterwards it shows up and is accessible in the terminal (and other programs like Rhythmbox).

Before opening it in Nautilus for the first time after each boot, it's unaccessible.  I don't get it...  I made 'Music Slave' readable to everyone. with chmod, but i don't know what device in /dev it is, if that even makes a difference.  Any ideas?

---

### Post by WRDN on 2008-08-28
It may be because you are not mounting the drive at bootup.

To do this, open the Terminal, and type:

```
sudo fdisk -l
```

This will allow you to identify which device the NTFS partition corresponds to. It will be either /dev/sdaN or /dev/hdaN (where N represents a number). 

Now, type:

```
sudo mkdir /media/music
```

This folder just created will be the mount point for the drive. If you wish, you can replace the word "music".

Next type:

```
sudo gedit /etc/fstab
```

Add the line:

> /dev/[device] /media/music ntfs defaults 0 0

Replace [device] with the device listed for the NTFS partition (in the output to "sudo fdisk -l").

Save the file, and when you reboot the disk should be mounted automatically.

---

