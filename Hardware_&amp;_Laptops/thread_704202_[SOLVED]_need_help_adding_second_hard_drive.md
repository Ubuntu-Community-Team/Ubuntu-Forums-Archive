---
title: "[SOLVED] need help adding second hard drive"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by noremacyug on 2008-02-22
i'm a windows convert so please bear with me as most everything i know about an o.s. is based on a pretty gui that guides your hand.

i never thought i'd ask a question as simple as "how do i install a second hard driver", yet here i am.  so, i have a second hdd that will be used for storage.  how do i go about this? i have gparted installed and (as far as i know) have formatted the hdd to ext3 file system.  someone please guide me through this?  thanks in advance!

---

### Post by noremacyug on 2008-02-22
anyone?

---

### Post by taurus on 2008-02-22
_Assuming_ your second harddrive is /dev/sdb1, you can add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
And add this line to the end of it.

```
/dev/sdb1   /media/storage   ext3   defaults   0   1
```
Save it and close down the gedit editing window.  Now, create a new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```
And if you want to write to /media/storage without using sudo/gksudo, then you need to change the ownership of /media/storage from root to your login name, _assuming_ again it's **nore**.

```
sudo chown -R **nore**:**nore** /media/storage
ls -la /media
```

---

### Post by Dillibag on 2008-02-22
Hi mate,
just srew your 2nd HDD into the bay below your master drive, make sure you take the little jumper out first( no  jumper needed on slave, but the master needs one) The position is given on the HDD. then connect your Ultra cable.( Blue, Grey, Black) Blue goes onto your motherboard, then grey onto slave ( hdb ), and finally black onto the master drive ( hda )
Your Linux system should then automatically detect the two drives after the next start.
If you have no Ultra cable, its a good idea to get one. Have fun!

---

### Post by noremacyug on 2008-02-23
> **taurus said:**
> _Assuming_ your second harddrive is /dev/sdb1, you can add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
And add this line to the end of it.

```
/dev/sdb1   /media/storage   ext3   defaults   0   1
```
Save it and close down the gedit editing window.  Now, create a new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```
And if you want to write to /media/storage without using sudo/gksudo, then you need to change the ownership of /media/storage from root to your login name, _assuming_ again it's **nore**.

```
sudo chown -R **nore**:**nore** /media/storage
ls -la /media
```
i appreciate the help here.  i've yet to go through the steps and see if i can get it to work.  if at all possible do you care to either explain a little about the different "commands" or perhaps point me to a thread that explains it.  i'm just wanting to learn what it is that i'm entering into the terminal rather than just goin through the motions.  (it't the whole you can teach a man to fish scenario)  i'm also curious about the file system, in terms of where things are located, like program files, ect.

---

### Post by kevmitch on 2008-02-24
Ok here's a more detailed rundown:

gksudo gedit /etc/fstab

gksudo is a graphical frontend for the sudo command which allows you to perform actions as the root user ("Administrator" in Windows terms). In the present case, the command to be executed as root is gedit /etc/fstab which opens the file /etc/fstab in the gnome editor (gedit). The /etc directory is where most of the system configuration files are stored. It might very loosely be compared to the windows registry. The /etc/fstab file is where the information about commonly mounted storage devices (as well as some more abstract filesystems) are kept. Now lets look at the line you're adding to this file.

/dev/sdb1   /media/storage   ext3   defaults   0   1

For the most part, each line in the fstab file links a hardware device partition (/dev/sdb1) to a "mount point" within the filesystem (/media/storage). The hardware device is actually a virtual file provided by the Linux kernel to access the hardware. Such files are pretty much always located in the /dev directory and the file name will depend upon the type of storage device, the enumeration of the storage device among the others on your system, and the partition of the device you want to mount. Usually ide device filenames will begin with "hd", whereas ata and usb devices will begin with "sd". This is then followed by a letter that uniquely identifies a specific physical device (if this is your second hard disc, then it will probably be "b"). This is then followed by the partition number that you want to mount. If you just formatted the entire drive as one partition, this will just be "1". Thus you would probably use "/dev/sdb1" for the first partition on your second sata/usb disk. 

Unlike Windows, Linux assigns devices to directories within the filesystem rather than drive letters. You can mount a given storage device anywhere you want within the filesystem. A common place in Debian/Ubuntu to a subdirectory of the /media directory (other distributions may use the /mnt directory). If you're adding a new device, you'll need to create the directory on which to mount it. Hence the command 

sudo mkdir /media/storage

You also need to specify the type of filesystem such as ext3, reiserfs, ntfs, or fat32. You'll find that Linux gives you a lot more choices for filesystems than the fat32/ntfs options of Windows. For a new device, you make this choice when you format the device (as in gparted). Ext3 is usually the default, but Reiserfs or XFS provide a bit better performance in most cases. 

You also need to provide various options specifying how to mount the filesystem, but usually, the default ones are fine, hence the "default" in the fourth field. 

The final two fields a for backup and filesystem checks. I won't get into it too much, but 0 1 as suggested are probably what you want.

---

### Post by noremacyug on 2008-02-24
thanks a lot for taking the time to write that up!!! that helped shed some light.  MUCH appreciated!

---

### Post by Yellow Pasque on 2008-02-24
Other useful commands:
```

sudo lshw -C disk
fdisk -l
blkid
```

---

### Post by noremacyug on 2008-02-24
> **Temüjin said:**
> Other useful commands:
```

sudo lshw -C disk
fdisk -l
blkid
```

what are these commands, what do they do?

also, i followed these commands and of coarse they work fine and i now have access to my hdd just as i wanted.  just wondering if i could have a brief explanation on what they are doing.
also sudo mount -a
df -h
ls -la /media

---

### Post by pannerrammer on 2008-02-24
> **Dillibag said:**
> Hi mate,
just srew your 2nd HDD into the bay below your master drive, make sure you take the little jumper out first( no  jumper needed on slave, but the master needs one) The position is given on the HDD. then connect your Ultra cable.( Blue, Grey, Black) Blue goes onto your motherboard, then grey onto slave ( hdb ), and finally black onto the master drive ( hda )
Your Linux system should then automatically detect the two drives after the next start.
If you have no Ultra cable, its a good idea to get one. Have fun!

I am having fun too! There are no jumpers on my SATA II drive. Also, the cable has an orange thingy on each end. Which end goes where?

 Is my kit getting just too old, mate? :lolflag:

PS. Removing the jumper don't don't make a Master into a Slave on all ATA drives, and if the Master is set to CS, then the Slave needs to be set to CS too!

---

### Post by kevmitch on 2008-02-25
> **noremacyug said:**
> what are these commands, what do they do?

also, i followed these commands and of coarse they work fine and i now have access to my hdd just as i wanted.  just wondering if i could have a brief explanation on what they are doing.
also sudo mount -a
df -h
ls -la /media

Oops, forgot the last ones. mount is the command used to actually mount a device. The -a option tells it to mount everything in fstab excluding those devices with "noauto" in their options list. 

df is short for "disk free" and shows you how much space is used/available on all *mounted* devices. The 
"-h" option tells it to give that info in "human readable" (i.e., Mb and Gb rather than bytes) format.

ls is probably the most commonly used command on the command line. It is short for "list" and gives a list of files under the directory specified as an argument, or if a file is given as an argument lists just that file. If no arguments are given it lists the current directory. The -l option tells it to use "long listing" format which includes permissions, size, modification times, while the -a option lists also files that are prefixed by a "." which are normally hidden. So running ls -la /media will confirm that you you have indeed created the /media/storage directory and give you some info about it.

lshw is a really handy command which gives you detailed info about all your hardware. The -C option restricts that information to a specific "class" of devices such as "disk", "net", "video", etc.

fdisk does the same thing as its windows/dos counterpart (and probably a bit more). Thus it should be used with caution as it can easily delete entire partitions. The -l option however just tells it to "list" the available partitions without changing anything. blkid does pretty much the same thing with a slightly different output format. 

In general, if you want to know what a particular command does, you should read its "man page" which can be accessed by running
man <command>
This documentation can be a little terse for beginners, but it contains information about the gist of what a command does as well as all of its valid options. A couple handy things to know about reading man pages: 1) quit with the "q" key 2) search with the "/" key.

[http://xkcd.com/293/](http://xkcd.com/293/)

---

### Post by noremacyug on 2008-02-25
once again, thanks!

---

### Post by kushykush on 2008-04-08
Using Heron Hardy beta.  It has worked very well.  Except I added a third SATA drive.  And UBUNTU is in a fit.  It gives me the user longin screen and once logged in, Ubuntu is not starting.  I am staring at a brown screen.

I booted Ubunut twice in recovery mode.  It checked everything and then gave me the option to boot normally.  However, after the normal boot, again the same brown screen. Not start.

Ubuntu, obviously is not recognizing my newly installed third SATA drive.

In contrast, Vista took just a few seconds to recognize the third drive it and installed it automatically in 3 seconds.  

What needs to be done here.  You will have to let me know all the steps or direct me to the link.  I am not a Linux expert.

---

### Post by noremacyug on 2008-04-11
got a few Q's again and though it better to just resurrect this thread.

so, i've decided to say screw wine, virtualbox, and all the other emu's.  i made me a smalle xp partition for a couple of games.  what i'm wanting to do is to make that partition of my hdd not visible in ubuntu.  in other words i don't want it showing up on my desktop all the time.  and i'd also like to know how to rename it so i don't accidently do something thinking it's a different partition.

the next think i'd like to do is i have another partition that i want to access without having to enter my pw everytime i access it.  i'd also like it to be visible in my places menu, but not have it on the desktop all the time, or ever really.

as always, thanks guys/gals.

---

### Post by 2waytec on 2008-04-13
I am new to ubuntu, had the exact same problem. Thanks for the help this was exactly what I was looking for.:)

---

### Post by noremacyug on 2008-04-15
> **noremacyug said:**
> got a few Q's again and though it better to just resurrect this thread.

so, i've decided to say screw wine, virtualbox, and all the other emu's.  i made me a smalle xp partition for a couple of games.  what i'm wanting to do is to make that partition of my hdd not visible in ubuntu.  in other words i don't want it showing up on my desktop all the time.  and i'd also like to know how to rename it so i don't accidently do something thinking it's a different partition.

the next think i'd like to do is i have another partition that i want to access without having to enter my pw everytime i access it.  i'd also like it to be visible in my places menu, but not have it on the desktop all the time, or ever really.

as always, thanks guys/gals.

anyone?

---

