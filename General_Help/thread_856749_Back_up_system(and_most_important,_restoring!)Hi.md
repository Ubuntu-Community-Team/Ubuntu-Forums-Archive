---
title: "Back up system(and most important, restoring!)Hi"
date: 2008-07-11
forum: General Help
---

### Post by thunderbirdje on 2008-07-11
Hi

I've installed Ubuntu (2nd partition) trying to get rid of Vista (wiha :)). Because I need my laptop a lot, if something gets wrong or messed up, I should be able to restore my whole disc in a few hours with a recent backup. :-) I like to experiment and install new software.

I've came down to the fact that there are a lot of backup options:

1) "automatic" [SBackup (link)]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#Restore%20Your%20Data")
2) "manual" (from the command line)
[INDENT] a) [dd (link)]("https://help.ubuntu.com/community/BackupYourSystem#From%20the%20command%20line")
 b) [tar (link)]("http://ubuntuforums.org/showthread.php?t=35087")[/INDENT]

The problem:

I tried option 2a because it makes a **disc image**, but while backing up to a mounted external drive, the drive itself was also included (*). (A big big file thus :o)

I didn't tried option 1 because it is GUI, and I was wondering if you are able to restore your backup of your GUI is messed up, for example, you can only boot from a live CD and you want to restore your whole drive (in my case /dev/sda4) back in its original state (as written to your backup file).

I don't know if 2b fits, it has no GUI, with a messed up GUI no problem, but it *does not make a disc image*

So, I'm wondering what's the best option for: 

a) backing up a whole disc (an exact copy of it)
b) always able to restore it (from command line, without installing GUI programs or other stuff)
c) possibility to exclude directories (because of problem described above in (*))

Because I'm totally new to Ubuntu, hopefully not a silly question? ;-)

Thanks a lot to everyone for your time and help!

---

### Post by drs305 on 2008-07-11
3) Bootable Rescue Disks with Backup Apps

I don't see it mentioned often but I'm very comfortable using Partimage in fact I'm using it on my other computer at this moment. 

It's on the System Rescue CD ( [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") ). Partimage makes a copy of the entire partition but saves only the portions written to (so it's smaller than the copied partition). You can also compress the image. It takes a bit getting used to the setup but the entire save and restore is accomplished with the rescue CD so it works even if you can't boot your system. (Of course, you would have made a copy BEFORE this happens ;-) )

Another app that often comes up in these threads is [Clonezilla]("http://gpartedclonz.tuxfamily.org/")

Added: I don't use Partimage for routinely backing up data. I install and uninstall a lot of apps. Whenever I start thinking "Gee, ubuntu is really working well right now" I make an image of the root and home partitions so I can revert to a good install should things go downhill.

---

### Post by AliTabuger7 on 2008-07-11
I don't know what your disk space situation is or what kind of applications you use, but I usually just back up the /home directory. It saves space by not including all the programs, just your configurations. Since the programs themselves are free and easily obtainable through ubuntu (usually) it doesn't matter if you loose them. Its the configuration you want.

It's not like windows, nearly all of your personal stuff is in your home directory. But you should be very careful to include hidden files/folders too.

---

### Post by rraj.be on 2008-07-11
You can use partimage to clone entire partition.

Its very simple and handy due to the following

1) It clones only used space so that you can save space for backup.

2)Much reliable

3)You can even clone installed partitions and restore them to work as same as when you cloned it.

better go here for much guidance
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by thunderbirdje on 2008-07-13
I'll try that! Option 4 :D

Thanks for all the input and links!

Greetings

---

### Post by dexter.deepak on 2008-07-13
i wonder how you people missed remastersys !!
it can take an entire backup of / including your personal settings.
it is also helpful in making a distributable cd/dvd of your system, with all your installed packages.you may need this if you want to start afresh,but including all your softwares.

---

### Post by thunderbirdje on 2008-07-13
I tried **partimage** and ended up with the error "DISK FULL!!!"

1) I booted from the Live CD (Hardy) and unmounted /dev/sda4 (partition I want to backup)
2) Synaptic Package Manager > installed 'partimage'
3) Connect my external drive auto mounted at /media/"HP Pocket Media Drive"
4) Open terminal > 'sudo partimage'
5) Followed the steps:
a) PARTITION: selecting drive 'sda4'
b) IMAGE FILE: /media/"HP Pocket Media Drive"/backupSDA4
c) ACTION TO BE DONE: Save partition into new image file
next...
d) COMPRESSION LEVEL 'normal compression'
e) OPTIONS: just default
f) IMAGE SPLIT MODE: 'automatic split'
next...
g) DESCRIPTION: backup of root partition SDA4
next...
Information shows up, partimage starting... and after just a few seconds:

"DISK FULL"... I checked the disc space with terminal and also GUI 'disk usage analyzer'. 7.9GB left. The partition I want to back up is just 3.3GB used (both checked with 'df' in terminal as GUI application 'disk usage analyzer'.

I tried it with an SD card of 2GB (maybe to small), but same error: "DISK FULL!!!' after a few seconds, did a check: 1.8GB free on the SD card (few photos still left on the disk).

Maybe interesting to mention that the file system om my external hard disk is **ntfs**. The filesystem on SD card is **fat16**.

I'm getting out of ideas now...

---

### Post by drs305 on 2008-07-13
> **thunderbirdje said:**
> I tried **partimage** and ended up with the error "DISK FULL!!!"

1) I booted from the Live CD (Hardy) and unmounted /dev/sda4 (partition I want to backup)
2) Synaptic Package Manager > installed 'partimage'
3) Connect my external drive auto mounted at /media/"HP Pocket Media Drive"
4) Open terminal > 'sudo partimage'
5) Followed the steps:
a) PARTITION: selecting drive 'sda4'
b) IMAGE FILE: /media/"HP Pocket Media Drive"/backupSDA4
c) ACTION TO BE DONE: Save partition into new image file
next...
d) COMPRESSION LEVEL 'normal compression'
e) OPTIONS: just default
f) IMAGE SPLIT MODE: 'automatic split'
next...
g) DESCRIPTION: backup of root partition SDA4
next...
**Information shows up, partimage starting**... and after just a few seconds:


I have always formatted to ext3. When I tried NTFS it said it was experimental but allowed the process. 

I don't see any mistakes on what you have reported unless it doesn't like the backup label or permissions for some reason. 

I have always created the backup from the systemrescuecd, which seems would be easier since you don't have to install partimage from the livecd. 

From the rescuecd:

mkdir /mnt/temp
mount /dev/sdaX /mnt/temp # partition to be copied _to_ 
ADDED: SEE NOTE IN POST #10 for ntfs partitions - include ntfs-3g  "mount -t ntfs-3g /dev/sdaX /mnt/temp"
partimage
select the partition to save with up/down arrows
the file pathname must be included in the name: "*/mnt/temp/*anybackupname
tab through the options as you did

At this point, just before I hit 'OK', I check to see the estimated free space. Once it starts, check the Available Space for Image as it starts to write.

Do you have any trash on your backup drive that might be taking up space?
```
sudo find /pathtodrive -type d -iname Trash
```

---

### Post by bodhi.zazen on 2008-07-13
+1 partimage

You can also see this link :

    [uhelp]community/BackupYourSystem[/uhelp]

---

### Post by thunderbirdje on 2008-07-22
[Solved]

**short story**

Because my external drive was NTFS. I have to mount it with ntfs-3g! 

```
ntfs-3g /dev/sdb5 /mnt/temp
```

Where /dev/sdb5 is the path to my external drive.

Thanks to *drs305* for helping me out.

**Long story**

This time I used the sysrescuecd, much easier.

First I did check for trash on my external drive: no trash.

Second, like drs305 suggested, I tried different mounting points.

I (manual) mounted the external drive (/dev/sdb5) with "ntfs-3g /dev/sdb5 /mnt/temp" (sysrescuecd suggested this command for full read/write while booting up, see also [http://www.sysresccd.org/Sysresccd-m...-Write_support](http://www.sysresccd.org/Sysresccd-m...-Write_support))

Everything went smootlhy! Jiha

To be sure, I also tried:

a) "mount /dev/sdb5 /mnt/temp2"
b) in partimage writing to: /mnt/temp2/somebackupname
b) in partimage writing to: /dev/sdb5/somebackupname
c) in partimage writing to: /media/"HP Pocket Media Drive'/somebackupname

All above gave the same error: "Error: cannot create temp file [/path/to/file]. Please check there is space enough and you have access rights."

So I guess (I'm not the specialist ) that if you're writing to a NTFS-partition, you should mount with "ntfs-3g" for full read/write access. Maybe the auto mount, done by the system is not full read/write? But uses another kind?

---

### Post by bodhi.zazen on 2008-07-22
IMO, in general, you should not back up to a FAT or NTFS file system. I suppose you could keep an archive there, but take care as these file systems do not support permissions.

---

### Post by Halibutt on 2008-09-10
> **bodhi.zazen said:**
> IMO, in general, you should not back up to a FAT or NTFS file system. I suppose you could keep an archive there, but take care as these file systems do not support permissions.

So what do I do if Fat32 is the only external drive I have?
Cheers

EDIT/ Never mind, [this solution]("http://ubuntuforums.org/showthread.php?t=875469&highlight=partimage+temp") seems to solve the problem.

---

### Post by leandir on 2008-09-10
Personally, my solution was to use an external hard drive with a partition dedicated to linux system backup only, thus formatted with ext3 (read-write in windows allowed too thanks to ext2fsd, great program). Then I used grsync, which is a GUI frontend for rsync. Tipically I only backup my home partition AND etc folder, sometimes also the /var/cache/apt folder (useful to have all the packages there if you have to reinstall the system from scratch). I tested the goodness of this backup procedure twice in the last days (long, painful story), once also for Windows, and I am very very glad with it.
Advantages:
1- it is just a frontend, if you are dropped to cli only you can use the rsync command
2- if you use the right filesystem (e.g. using a ext3 for linux backup or a ntfs for windows backup) permissions are maintained, thus allowing for a very quick recover
3- intuitive, quick, precise
4- synchronization is very good
5- when timevault (based on rsync) will be released (now beta 1 if not mistaken) it will allow for "time machine"-like functionality
5- if I remeber correctly, you can set up rsync to synchronize with a remote folder
Cons:
1- AFAIK no way to create images of the partition (have to check out some suggestions provided here :D )
2- Best to run it with the appropriate privileges for the folder you are backing up (e.g. normal user permissions for home folder, root for others)
3- AFAIK does not support policykit

Hope it was useful :-)

---

