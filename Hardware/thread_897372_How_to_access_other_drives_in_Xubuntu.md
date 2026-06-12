---
title: "How to access other drives in Xubuntu?"
date: 2008-08-22
forum: Hardware
---

### Post by mirchichamu on 2008-08-22
I am using dual boot. I installed xubuntu but unable to access NTFS windows drives. How it is possible to access those?
Thanks.

---

### Post by Loaded.len on 2008-08-22
try this...

```
sudo apt-get install ntfs-3g
``````
 sudo mount -t ntfs-3g /dev/sd{whatever your ntfs partition is} /{wherever you want to mount it}
```

---

### Post by mirchichamu on 2008-08-22
> **Loaded.len said:**
> try this...

```
sudo apt-get install ntfs-3g
``````
 sudo mount -t ntfs-3g /dev/sd{whatever your ntfs partition is} /{wherever you want to mount it}
```

Thanks but not succeeded.Does it need restart?

---

### Post by Loaded.len on 2008-08-22
Please post the error

---

### Post by mirchichamu on 2008-08-22
> **Loaded.len said:**
> Please post the error

I put the code in terminal. I got something like this.

niaz@niaz-laptop:~$ sudo apt-get install ntfs-3g
[sudo] password for niaz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
niaz@niaz-laptop:~$ sudo mount -t ntfs-3g /dev/sda5/home
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
niaz@niaz-laptop:~$

---

### Post by Archmage on 2008-08-22
Most of the time the ntfs-partition is already mounted after the install.

Please give us the content of your /etc/fstab file.

---

### Post by Loaded.len on 2008-08-22
do this:
```
sudo mkdir /mnt/windows
sudo mount -t ntfs-3g /dev/sda5 /mnt/windows
```

---

### Post by mirchichamu on 2008-08-22
> **Archmage said:**
> Most of the time the ntfs-partition is already mounted after the install.

Please give us the content of your /etc/fstab file.

I got a reply "permission denied"

---

### Post by Loaded.len on 2008-08-22
you shouldn't need root privileges to read your fstab (write, yes...read, no)

```
cat /etc/fstab
```

---

### Post by mirchichamu on 2008-08-22
> **Loaded.len said:**
> you shouldn't need root privileges to read your fstab (write, yes...read, no)

```
cat /etc/fstab
```

Still not able to access other drives

---

### Post by Loaded.len on 2008-08-22
when you did 
```
cat /etc/fstab
```

did you see something like this:

/dev/sda5    /mnt/windows   ntfs-3g    default 0  0 

(or something along those lines)?

---

### Post by mirchichamu on 2008-08-22
> **Loaded.len said:**
> when you did 
```
cat /etc/fstab
```

did you see something like this:

/dev/sda5    /mnt/windows   ntfs-3g    default 0  0 

(or something along those lines)?

I got this in terminal:
niaz@niaz-laptop:~$ sudo mount -t ntfs-3g /dev/sda5 /mnt/windows
niaz@niaz-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=677f84f7-94cd-451e-9636-d66d8705ae3c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=03880fbf-e8e8-4b3e-aedd-a2d78d3b6a96 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
niaz@niaz-laptop:~$

---

### Post by efpc2003 on 2008-08-22
download ntfs-config, search for: "ntfs configuration tool"
I'm using xubuntu 8.04.1 and it works

---

### Post by Loaded.len on 2008-08-22
> **mirchichamu said:**
> I got this in terminal:
niaz@niaz-laptop:~$ sudo mount -t ntfs-3g /dev/sda5 /mnt/windows
niaz@niaz-laptop:~$ cat /etc/fstab

Doesn't look like your mount failed.

try to look in /mnt/windows for your files.

```
cd /mnt/windows

ls
```

---

### Post by randcoop on 2008-08-22
The short answers you've gotten thus far actually have worked, but I think you don't understand enough about how they work to use them.  A short tutorial:

Xubuntu comes with a program called ntfs-3g already installed (that's why when you tried to sudo apt-get install it, you were told you already had the newest version).  Ntfs-3g is the program that allows Linux systems to read and write to Windows NTFS drives (the default file system used by Windows).  

There is a file on your system in the /etc directory called fstab.  Fstab contains the names of drives and partitions on those drives that should be mounted automatically when you start your computer.  Xubuntu does not automatically include your Windows NTFS drives in the fstab file when you install Xubuntu.  That's why your /etc/fstab file doesn't list the NTFS drive.

To mount the NTFS drive after your computer is started, you need to run the command that's been given to you (sudo mount -t ntfs-3g /dev/sda5 /mnt/windows).  Once you've run that command, you'll be able to read and write to all your Windows files by looking in the /mnt/windows directory.

If you want Xubuntu to automatically mount your NTFS drive when it starts, you must add a line to your fstab folder that tells it to do that.  Then the next time you boot your computer, Xubuntu will look at /etc/fstab and mount your NTFS drive.

To add the line to the fstab file, you'll first need to know the UUID of your Windows NTFS partition.  That partition is on /dev/sda5.  The command to find out the UUID of /dev/sda5 is ```
sudo vol_id -u /dev/sda5

```  

Once you know the UUID, you need to add that to fstab.  In Xubuntu, the text editor is called Mousepad.  You need to run mousepad as root in order to be able to edit your fstab file.  

CAUTION! CAUTION!  Before editing your fstab file, which is essential to booting your system, make a backup of the current fstab.  That's done by running the command ```
sudo cp /etc/fstab /etc/fstab.backup
``` Once that's done, you can check to see it was successful by looking in the /etc directory for the fstab.backup file.  Now you know that if you mess up your fstab file, you have a good copy from which you can restore it.

To run mousepad as root to edit the fstab file, you would run the command ```
gksudo mousepad /etc/fstab
```

Once in the fstab file, you want to add a line to the bottom of the file that looks like this: 

```
UUID=8690F53593F52BF5 /mnt/windows ntfs defaults,umask=0002,gid=46,0,2
``` 

except that you would replace the UUID number with the one you found earlier for your NTFS drive.

If you want, you can add a comment line above the UUID line you're adding, so that you know what it is you've done.  A comment line starts with the # sign.  So you might add a line that looks like this ```
# Windows NTFS drive
``` above the UUID line.  It doesn't affect the file in any way, so it's your choice.

The important thing is not to change anything in the file that's already there.  If for any reason you alter the existing code in the file, just exit mousepad without saving the file and no harm will be done.

Once you save fstab, your Windows drive should be visible in the /mnt/windows directory all the time.

If you don't feel comfortable yet editing the fstab file, then don't do it.  You can always mount your NTFS drive after you boot by running the mount command that you've already successfully used.

---

### Post by mirchichamu on 2008-08-22
> **randcoop said:**
> The short answers you've gotten thus far actually have worked, but I think you don't understand enough about how they work to use them.  A short tutorial:

Xubuntu comes with a program called ntfs-3g already installed (that's why when you tried to sudo apt-get install it, you were told you already had the newest version).  Ntfs-3g is the program that allows Linux systems to read and write to Windows NTFS drives (the default file system used by Windows).  

There is a file on your system in the /etc directory called fstab.  Fstab contains the names of drives and partitions on those drives that should be mounted automatically when you start your computer.  Xubuntu does not automatically include your Windows NTFS drives in the fstab file when you install Xubuntu.  That's why your /etc/fstab file doesn't list the NTFS drive.


To mount the NTFS drive after your computer is started, you need to run the command that's been given to you (sudo mount -t ntfs-3g /dev/sda5 /mnt/windows).  Once you've run that command, you'll be able to read and write to all your Windows files by looking in the /mnt/windows directory.

If you want Xubuntu to automatically mount your NTFS drive when it starts, you must add a line to your fstab folder that tells it to do that.  Then the next time you boot your computer, Xubuntu will look at /etc/fstab and mount your NTFS drive.

To add the line to the fstab file, you'll first need to know the UUID of your Windows NTFS partition.  That partition is on /dev/sda5.  The command to find out the UUID of /dev/sda5 is ```
sudo vol_id -u /dev/sda5

```  

Once you know the UUID, you need to add that to fstab.  In Xubuntu, the text editor is called Mousepad.  You need to run mousepad as root in order to be able to edit your fstab file.  

CAUTION! CAUTION!  Before editing your fstab file, which is essential to booting your system, make a backup of the current fstab.  That's done by running the command ```
sudo cp /etc/fstab /etc/fstab.backup
``` Once that's done, you can check to see it was successful by looking in the /etc directory for the fstab.backup file.  Now you know that if you mess up your fstab file, you have a good copy from which you can restore it.

To run mousepad as root to edit the fstab file, you would run the command ```
gksudo mousepad /etc/fstab
```

Once in the fstab file, you want to add a line to the bottom of the file that looks like this: 

```
UUID=8690F53593F52BF5 /mnt/windows ntfs defaults,umask=0002,gid=46,0,2
``` 

except that you would replace the UUID number with the one you found earlier for your NTFS drive.

If you want, you can add a comment line above the UUID line you're adding, so that you know what it is you've done.  A comment line starts with the # sign.  So you might add a line that looks like this ```
# Windows NTFS drive
``` above the UUID line.  It doesn't affect the file in any way, so it's your choice.

The important thing is not to change anything in the file that's already there.  If for any reason you alter the existing code in the file, just exit mousepad without saving the file and no harm will be done.

Once you save fstab, your Windows drive should be visible in the /mnt/windows directory all the time.

If you don't feel comfortable yet editing the fstab file, then don't do it.  You can always mount your NTFS drive after you boot by running the mount command that you've already successfully used.

Thanks a lot randcoop for enormous help. Now I can see at least on drive.
I will contact again if any doubts.
Extremely grateful.

---

### Post by randcoop on 2008-08-22
No problem.  Glad it was helpful.

> Now I can see at least on drive.

For every Windows drive you want to mount, you'll need a separate mount point in your /mnt directory.  Right now, you're mounting your /dev/sda5 NTFS partition in /mnt/windows.  Let's assume that /dev/sda5 is your Windows C: drive.  But these days, many people are also using a D: drive (a separate Windows partition).  

When you run the command ```
sudo fdisk -l
``` you will be able to see all the different partitions on your system.  On the left side of the response to that command, you'll see the /dev file (/dev/sda1 for example).  On the right side of the response to that command, you'll see the kind of file system that partition uses (Linux, for example, or HPFS/NTFS).  Your Xubuntu partitions are, of course, Linux file systems.  Typically, if you installed Xubuntu on top of an existing Windows system, your /dev/sda3 will be your main Linux partition.  The Blocks column shows how big the partition is.  You'll also likely see a Hidden W95 FAT32 (LBA) partition on /dev/sda1.  That's the boot partition.  It's small, but essential, and should be left alone.  

If you have more than one Windows drive (C: and D: for example), then you should see more than one /dev/sda with HPFS/NTFS as the file system.  

If you want to mount the second of these, you need to create the new mount point with the command ```
sudo mkdir /mnt/secondwindows
```
Of course, you don't need to call it secondwindows (which seems a bit much).  You can call it anything you want.

Once that's created, then mounting the second NTFS drive uses the same command as you used to mount the first one, except that you substitute the sda # with the right number and you use secondwindows (or whatever) instead of windows.  

To add it to fstab, you'd go through the same process of finding the UUID of the other /dev/sda by using all the command from earlier and again using the right number after sda.

The line you add to fstab would also be identical to the earlier one, substituting the windows with secondwindows as the name of the /mnt/ and substituting the new UUID number.

In this way, you can mount as many Windows NTFS drives as you have.

REMEMBER THE CAUTION: Don't change a working fstab without backing that file up first.  In the worst case scenario, if you can't boot your computer from your hard drive because of a messed up fstab, you can always boot from a live CD and then replace the bad fstab with the backup and then boot again from the hard drive.

---

### Post by mirchichamu on 2008-08-22
[QUOTE=randcoop;5642141]No problem.  Glad it was helpful.



For every Windows drive you want to mount, you'll need a separate mount point in your /mnt directory.  Right now, you're mounting your /dev/sda5 NTFS partition in /mnt/windows.  Let's assume that /dev/sda5 is your Windows C: drive.  But these days, many people are also using a D: drive (a separate Windows partition).  

When you run the command ```
sudo fdisk -l
``` you will be able to see all the different partitions on your system.  On the left side of the response to that command, you'll see the /dev file (/dev/sda1 for example).  On the right side of the response to that command, you'll see the kind of file system that partition uses (Linux, for example, or HPFS/NTFS).  Your Xubuntu partitions are, of course, Linux file systems.  Typically, if you installed Xubuntu on top of an existing Windows system, your /dev/sda3 will be your main Linux partition.  The Blocks column shows how big the partition is.  You'll also likely see a Hidden W95 FAT32 (LBA) partition on /dev/sda1.  That's the boot partition.  It's small, but essential, and should be left alone.  

Thanks randcoop once again.
Now that I have whatever you told me but there is a problem again. In mnt folder I see sda5, sda6 and windows folders but only windows folder contain data, the others are empty folders. It is worth to note that I am having three ntfs partitions i,e sda1(windows), sda5 and sda6.

How to solve that problem. May be I have done a mistake somewhere?

---

### Post by randcoop on 2008-08-22
I am not sure what you're saying.  You refer to windows (sda1) and two other NTFS drives (sda5 and sda6).  When you're in Windows, are you saying that you have a C: drive, a D: drive and an E: drive?

Remember that I explained that /dev/sda1 is usually your boot partition.  If it is, then you have no reason to mount that and you shouldn't. If /dev/sda5 and /dev/sda6 correspond to your Windows C: and D: drives, then they're the ones you want to mount.

Did you create two different mount points in /mnt?  If you run the command ```
ls /mnt
``` do you get two different directories (windows and something else)?  If so, then your two mount commands would be:

```
sudo mount -t ntfs /dev/sda5 /mnt/windows
``` and 
```
sudo mount -t ntfs /dev/sda6 /mnt/[the_name_of_the_other_mnt_directory
```.

Then you should be able to see all the files.

You need to give more information about what you've done.

I'm going to be away from my computer for the next 24-48 hours, so I'm afraid I can't help more until I return.

---

