---
title: "Booting from USB?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Sashin on 2008-12-30
If I was to install Linux Mint on a USB would it be a temporary session like a live CD, or would I be able to have my own applications, themes etc installed?

Also how will it perform, will it be much slower than the live CD?
And do I have to partition it, to use it as a normal USB as well since partition 'causes me to lose space.

It's a 16GB stick if that changes anything. I want at least 8GB for use as a normal USB.

---

### Post by Sashin on 2008-12-30
Also, is there a disadvantage of installing the system to the USB as opposed to using the USB creator in Intrepid?

Are Live USBs much faster or something?

---

### Post by aurelieng on 2008-12-30
Here is my experience about Kubuntu, it should be the same for Mint. There are basically two options to install a distro on a flash usb disk.
 
1. You can use the same mechanism that the live CD. This requires the creation of a first FAT32 partition containing a read only filesystem containing an image of the live CD, and a second partition called "casper-rw" which will be mounted on top of the first one (overlayed, using AuFS), giving the impression that you can alter the initial read only filesystem. This first approach is implemented in USB creator.

2. Alternatively, you can install a "real" distribution on your flash disk. Simply unplug your hard disks for safety, then plug your flash disk, the installation desktop or alternate live CD, and reboot. If you are to lazy to open you box, you can also use a virtual machine such as vmware. Perform the install as usual, your flash disk should be seen as /dev/sda. Afterwards, you may have to replace grub with syslinux, use tmpfs to avoid to many read/write cycles on your key. It is quite easy to do that from your regular linux installation, with your flash disk plugged in.

The second option is much faster since there is no overlayed nor compressed filesystem. It also uses less disk space, since you do not keep two versions of the same file (this happens when you update a package with the first option, since the original files remain on the ro partition, and the new ones on the rw partition).

All in all, the second option is my favorite. 

If you want to be able to use your key normally on windows afterward, you have to create a primary partition formatted with FAT32. This partition must be the first one to be visible from Windows.

If your flash disk is a 16Go and you want to go for the second option, you can partition it like this:

- 8Go FAT32, 1st primary partition (usual USB stick)
- 100 Mo EXT3, 2nd primary partition, /boot
- 7.9G o EXT3, 3rd primary partition, /

It is a good idea to install using the alternate CD to be able to encrypt your / with LUKS, so that your whole system remains secure if you loose the key.

Cheers,

Aurélien.

---

### Post by Sashin on 2008-12-30
Thanks for the reply.

What version of Kubuntu did you install?
I was actually planning to use the USB creator on Intrepid, which I'll boot from Virtual Box. (Doesn't it have an option for a permanent install?)

How well does your Kubuntu perform from USB? Will it be fast?

Also will I be able to install apps and change the theme etc if I choose the second option?

---

### Post by aurelieng on 2008-12-30
I installed Kubuntu Intrepid Ibex 8.10. It is much faster than the live CD, altough it depends on your key, of course. With the second option, sure, you'll be able to put anything you want, since it is nothing but a real installation, and thus behaves similarly.

---

### Post by Sashin on 2008-12-30
That's all I needed to know. Thanks alot.

---

### Post by 5BallJuggler on 2008-12-30
Have a read of this thread

Let me know how you get on

[http://ubuntuforums.org/showthread.php?t=1022708](http://ubuntuforums.org/showthread.php?t=1022708)

Phil

---

