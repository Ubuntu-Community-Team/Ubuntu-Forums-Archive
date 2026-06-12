---
title: "How to mount iso images like in Windows"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by philidox on 2009-01-23
I have used many programs including Gmount to mount my iso images, however none of them mount images like image mounting programs for windows.  For example when I use virtual clone drive under windows xp to mount an iso image, it emulates the game so good that you couldn't tell that it was a virtual drive, it acts as if someone physically put the disc inside the optical drive.  **How do I get that same level of mounting power/emulation from ubuntu?**.  For example when using ubuntu, I mount an image of a game disc in the /media/cdrom0 directory I got a icon on my desktop that looks like a blank disc in contrast to when I put in the actual game disc i get the game icon.

---

### Post by Coreigh on 2009-01-23
The mount is done with the command line but once mounted the ISO appears as a regular folder or directory.

Here is the how to:
[http://www.tech-recipes.com/rx/2747/ubuntu_how_to_mount_unmount_iso_files/](http://www.tech-recipes.com/rx/2747/ubuntu_how_to_mount_unmount_iso_files/)

---

### Post by Herman on 2009-01-23
> For example when using ubuntu, I mount an image of a game disc in the /media/cdrom0 directory I got a icon on my desktop that looks like a blank disc in contrast to when I put in the actual game disc i get the game icon.[-( You shouldn't be mounting anything in your /media/cdrom0 directory, that's for real CDs or DVDs in your optical drive.

:) You should make your own 'mount point' in /media instead.
A 'mount point' is just an empty directory for mounting another file system in. 
Your mount point can be anywhere, but it's a Linux tradition to make them in /mnt. 
In Ubuntu, we make them in /media instead. If you make your mount points in /media, you should be given a desktop icon for them.
```
sudo mkdir /media/yourCD
```Okay, now that you have a mount point, there are two ways to mount your .iso file.
The first way is for mounting it just for one session, (only until you reboot).
To do it that way, (the temporary way), you can use the mount command, 
```
sudo mount -o loop -t iso9660 mycdrom.iso /media/yourCD
```Where: the .iso file to be mounted is located in your /home/username directory
    Where:  the name of the file is 'mycdrom.iso'
    Where: the mount point you made for it is named '/media/yourCD'

The other way to mount an .iso file is to make an entry in /etc/fstab for it. That means it will be mounted automatically at every boot-up. That's useful if you're working on a project that may not be completed in one session, it be a long running project.
```
gksudo gedit /etc/fstab
``````
/home/username/mycdrom.iso /media/yourCD iso9660 loop,ro,user  0    0
``` You might wan to do it that way if you have some game or something that you want to play again very often.
> For example when I use virtual clone drive under windows xp to mount an iso image, it emulates the game so good that you couldn't tell that it was a virtual drive, it acts as if someone physically put the disc inside the optical drive. **How do I get that same level of mounting power/emulation from ubuntu?**
 Ubuntu will run anything in your mounted .iso ten or twenty times faster than a real CD in the CD-ROM drive, because the hard disk is many times faster than a real CD in a CD-ROM drive. If Windows is slowing it down, that's probably normal for Windows. You may need to defrag and scan for viruses and consider turning off your antivirus program because that slows your computer down almost as much as a virus. (LOL) (Sorry, but it's true!).
About using an emulator, well, that's another subject. We have some good emulation programs in Ubuntu, but I haven't used one recently. I'm not very well informed or up to date on that subject. I can't imagine any reason why you shouldn't be able to open a mounted .iso with one though, but I'm not sure. There might even be one that can mount your .iso by itself, (by clicking somewhere instead of needing commands), I would need to go searching and testing emulation programs to fine out. Maybe someone else knows?

**Note:** We can read and copy from a mounted .iso file but we can't write to one.  At least I haven't been able to find out how. To alter an .iso file we mount it so we can copy the contents to a regular directory. Then we do whatever work we need to do, and then make a new .iso file out of the directory with a genisoimage command. 
Click the following link to look further down this page for some information about [genisoimage commands]("http://users.bigpond.net.au/hermanzone/p10.htm#genisoimage_commands").

One of the reason we don't mount .iso file like in Windows is because Linux is not Windows. In Windows they treat users as if they are stupid, and they do everything automatically for you. That way they keep everything secret so you can't learn how to do things for yourself, so you can't learn anything. That way, they can make you pay, and pay, and pay . . . 
In Ubuntu, there are more and more nice programs for making things easier and quicker, (more convenient). That's a good thing. There probably is a program somewhere that will do all those things I just gave you the commands for. While you're waiting for someone to suggest a program for you to try out, see if you can do it with the command line. I'll bet you can. :D

Regards, Herman :D

---

### Post by philidox on 2009-01-26
Thank you so much I figured out what your told me to do and I got my starcraft.iso game to work just like i use with VirtualCloneDVD in windows xp.  Thanks once again

---

### Post by Herman on 2009-01-27
:D Alright! Cool! Thanks for the feedback. :D

---

