---
title: "Accessing files on persistent USB stick"
date: 2008-11-07
forum: General Help
---

### Post by greatgoogamooga on 2008-11-07
Rather than do a full install if Ibex, I've installed a persistent image on a 16G USB stick using the Startup Disk Creator.  One thing I like about this is that the disk has only one FAT32 partition and I can store data on this drive and carry it around to use at work.

When using the USB drive as just a storage disk (not booting Ubuntu from the USB) I can store files anywhere I want.  In my case I created a folder /media/sdc1/mystuff.

When I boot from the USB, that same folder is in /cdrom/mystuff and is READ ONLY.  I am unable to write to this location as the ubuntu user and have to use sudo.

Is there something I can change in the fstab or in udev rules to alter this?

Goog

---

### Post by ronz0o on 2008-11-07
I had to do something like this with an external hard drive. One thing you can do is make a new folder, and type "sudo chmod 777 (folder)" . you could also try to chmod the whole drive itself, but that did not work for me. Making the folder is the easiest way to do it imo. Hope this helps!  =)

---

### Post by greatgoogamooga on 2008-11-07
Neither chmod, nor chown did it for me either.

Are you saying create the folder when using the booted USB drive?  Where did you put the folder to be able to access it when not booting from the stick?

Goog

---

### Post by ronz0o on 2008-11-07
Once your running in ubuntu, I would suggest just making a folder at root. sudo mkdir /Folder . then sudo chmod 777 /Folder . You may need to use sudo chmod -r 777 /Folder

---

### Post by greatgoogamooga on 2008-11-08
Swing and a miss.  Creating a folder then chmod did not work.  The folder retains its' permissions.  I did this both under Ubuntu booted from the USB stick, and when using the drive as a storage medium.

Any other ideas...anyone?

Goog

---

### Post by Cincinnatux on 2008-12-16
I don't know if you've already moved past this issue, but I've read elsewhere on the UbuntuForums that commands like chown do not seem to work on FAT32 file systems.  YMMV.  

I only have an 8GB USB to use, but my goals are similar to yours.  My plan is to partition off the first gig and format as FAT32 then do a full install of Ubuntu on the remaining 7 gigs using manual partitioning options.  That way, in theory, I will have a fully persistent Ubuntu environment that is bootable as well as a gig of file swap that Windows machines can read and write to.  I wish I had a 16 gig drive or bigger, but I'll make do with 8.

I have already done a proof of concept on installing full Ubuntu to the USB.  It takes about 3 gig of the drive, but it is fully persistent, survives updates, permits me to add software, etc.  I just need to head out and pick up a blank CD-R to burn a 32-bit .iso (the only CDs I have on-hand are for the 64-bit version that I run on my laptop; I'd rather my USB Ubuntu be a bit more "lowest common denominator" than that, so I'm holding off on the next attempt until I can do it 32-bit.)

Best of luck,

Cincinnatux

- Cincinnatux

---

### Post by greatgoogamooga on 2008-12-16
the problem that I have had, using a partitioned USB drive, is that Windows does not always recognize the FAT partition.  I had been using a drive made with the PendriveLinux.com instructions for a while, which does exactly what you are talking about, but could only use the drive under Linux for storage.

Goog

---

### Post by emptythevoid on 2008-12-31
You could try this:

Open a terminal and navigate to the /cdrom  directory.  Then do this:

**sudo chown -R user:user ./mystuff**

Replace user with your user account name (for example, if your user account is billybob, then you would type in billybob:billybob)

Once this is done, you can go through the folder and edit permissions for files by right-clicking them, going to properties, going to the permissions tab, and changing from read-only to read and write. 

I don't know if this will fix your problem, though.  I'm curious how it'll behave after you've accessed that folder in Windows after you've changed the permissions.

---

### Post by heartwarmer on 2009-01-03
I think the main problem is that you've put "mystuff" folder in /media,i suggest you try putting it in /home/user folder.
I hope this helps :D

---

### Post by albinootje on 2009-01-03
> **greatgoogamooga said:**
>  When I boot from the USB, that same folder is in /cdrom/mystuff and is READ ONLY.  I am unable to write to this location as the ubuntu user and have to use sudo.

Is there something I can change in the fstab or in udev rules to alter this?


Please boot from that stick, and post the output of :
```

sudo fdisk -l
mount
cat /etc/fstab

```

---

### Post by Jose Catre-Vandis on 2009-01-03
If my thinking is right, the folder you have created forms a part of the live usb and therefore will only ever be read only, but will be read /write when you boot up into the live usb OS. As previously suggested, you need to create a separate partition so that files can be stored "outside" of the live usb environment so that you can access in a read/write way from other OS's when not booting up the live environment.

I find that when I boot the live usb, I see the OS file system, and also the "cdrom" is mounted which will be read only.

---

