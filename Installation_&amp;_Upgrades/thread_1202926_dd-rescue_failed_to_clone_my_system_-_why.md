---
title: "dd-rescue failed to clone my system - why?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by ticket on 2009-07-02
dd-rescue failed to clone my system - why?

I am trying to clone my system disc using dd_rescue. (I just want a backup in case the original gets zapped).

The system disc and the backup disc are both Western Digital 80Gb drives with the same geometry.

I used  dd_rescue because I thought it could copy the boot, MRB and partition stuff as well as all the data.

The end result was a backup with an invalid partition table.
What went wrong?

=====================================================

This has been solved.  :popcorn: The problem was the USB cable was too long, causing i/o errors.  So here's a quick how-to on how to clone your ubuntu system disc. I was using IDE discs, but SATA discs should work as well, if you get the required adaptor.

1. Get a new disc for the clone. It must have capacity equal to or greater than your current system disc.  Identical size is fine.

2. Boot a live distro from the CD-ROM (the Ubuntu install disc does fine).

3. Connect your clone disc to a power source and then to the PC using an IDE-USB 2.0 adaptor.

4. Fire up a terminal and run the command
```
sudo fdisk -l
```
to identify the disk devices.  Your system disc will probably be /dev/sda and the clone /dev/sdb or /dev/sdc, etc, depending on how many other discs are connected to your system. Make sure you have identified the clone device.
 
5. Issue the command:
```
sudo dd if=/dev/sda  of=/dev/sd* bs=2M
```
where * refers to the clone disc.  You **must** get this command correct, otherwise you risk wiping out data from one of your discs!
(dd is a standard Unix command that will be available on the live CD - no need to download it)

6. The cloning will begin, and may take an hour or so depending on the disc size. If you get an i/o error, then you may have a bad cable or bad source disk. The dd command does not provide any progress reports (all you will see is the disc activity lights flashing). When done, it should report that it copied a number of GBs equal to your source disc size. 
You are now done!  

7. (optional step).  If your clone disc was much larger than the system disc, use GParted to resize the clone partition to reclaim unused disc space.

8. Shutdown (removing the live CD), replace your system disc with the clone and reboot to test it.  Or just keep your clone safe for the day you might need it.

Note that dd will not attempt to write to bad blocks on the clone - dd only uses logical blocks. The hard disc firmware takes care of avoiding bad blocks. 

Also, dd copies over everything, including the Master Boot Record (MBR), partition tables and partitions. Even the disc UUID gets cloned!

One puzzle remains - if one updates one's system to a new distro, can one avoid a 'dd' op and instead just get away with an rsync from then on?

Back to the old story ...  :

==============================================================


Here's what I did:

I attached the backup disc using an USB-IDE cable.

I then booted a knoppix live CD and made sure all drives were unmounted.

Using fdisc -l, I noticed that knoppix saw my system disc as /dev/hda and my backup as /dev/sda
(I also had a data disc as /dev/hdb)

(Curious to know why the backup disc was recognised as scsi)

I started ddrescue:
 
*(CAUTION - dd_rescue can destroy your disc if you get the disk names wrong. Don't use the dd command below as is - tailor it to your system!) *
```
root@Microknoppix:/home/knoppix# dd_rescue -b 2M -A -v /dev/hda /dev/sda
dd_rescue: (info): about to transfer 0.0 kBytes from /dev/hda to /dev/sda
dd_rescue: (info): blocksizes: soft 2097152, hard 512
dd_rescue: (info): starting positions: in 0.0k, out 0.0k
dd_rescue: (info): Logfile: (none), Maxerr: 0
dd_rescue: (info): Reverse: no , Trunc: no , interactive: no 
dd_rescue: (info): abort on Write errs: no , spArse write: never
dd_rescue: (warning): /dev/sda (2097152.0k): Input/output error!    2064384.0k
dd_rescue: (warning): /dev/sda (3145728.0k): Input/output error!    3112960.0k
.....(many more)
dd_rescue: (warning): /dev/sda (76546048.0k): Input/output error!    513280.0k
dd_rescue: (warning): /dev/sda (77594624.0k): Input/output error!    561856.0k
dd_rescue: (warning): /dev/sda (78149632.0k): Input/output error!    118912.0k
dd_rescue: (info): ipos:  78149632.0k, opos:  78149632.0k, xferd:  78149632.0k
                   errs:      0, errxfer:         0.0k, succxfer:  78149632.0k
             +curr.rate:    33556kB/s, avg.rate:    43337kB/s, avg.load: 24.7%
dd_rescue: (info): problems at ipos 78149632.0k: Input/output error 
                 fall back to smaller blocksize 

dd_rescue: (info): /dev/hda (78150744.0k): EOF
Summary for /dev/hda -> /dev/sda:
dd_rescue: (warning): /dev/sda (78150744.0k): Input/output error!    
dd_rescue: (info): ipos:  78150744.0k, opos:  78150744.0k, xferd:  78150744.0k
                   errs:      0, errxfer:         0.0k, succxfer:  78150744.0k
             +curr.rate:   219070kB/s, avg.rate:    43338kB/s, avg.load: 24.7%
root@Microknoppix:/home/knoppix# 
```

Do these errors mean the brand new backup disc is bad?

Anyway, I rebooted ubuntu and ran gparted to look at the backup (attached to the USB/IDE connector)
(see picture - it shows the disc space is unallocated) 

and here is the output of fdisc -l
(which shows the extended partition and the swap partition missing.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb592

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9542    76646083+  83  Linux
/dev/sda2            9543        9729     1502077+   5  Extended
/dev/sda5            9543        9729     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058f60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb592

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9542    76646083+  83  Linux
/dev/sdc2            9543        9729     1502077+   5  Extended
```


Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda1
UUID=e1828209-42aa-4d4d-acb7-1ff1a3fca58c  /              ext3         relatime,errors=remount-ro          0  1  
# /dev/sda5
UUID=afdebb9e-4701-4a3e-aad9-e50620dc40e2  none           swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/sdb1                                  /media/Data    ext3         defaults,users                      0  0  
```

Is there a way to fix the backup?

What did I do wrong to cause this problem?

---

### Post by ticket on 2009-07-03
Well I tried following the how-to at

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

(using the Ubuntu install disc, backup on the USB-IDE) and got the same result:

```
ubuntu@ubuntu:~$ sudo cfdisk -z /dev/sdc

Disk has been changed.

WARNING: If you have created or modified any
DOS 6.x partitions, please see the cfdisk manual
page for additional information.
ubuntu@ubuntu:~$ sudo dd_rescue -b 2M -v /dev/sda  /dev/sdc
dd_rescue: (info): about to transfer 0.0 kBytes from /dev/sda to /dev/sdc
dd_rescue: (info): blocksizes: soft 2097152, hard 512
dd_rescue: (info): starting positions: in 0.0k, out 0.0k
dd_rescue: (info): Logfile: (none), Maxerr: 0
dd_rescue: (info): Reverse: no , Trunc: no , interactive: no 
dd_rescue: (info): abort on Write errs: no , spArse write: if err
dd_rescue: (warning): /dev/sdc (16777216.0k): Input/output error!    744448.0k
dd_rescue: (warning): /dev/sdc (17825792.0k): Input/output error!    793024.0k
dd_rescue: (warning): /dev/sdc (18874368.0k): Input/output error!    841600.0k
dd_rescue: (warning): /dev/sdc (19922944.0k): Input/output error!    890176.0k

(-- miss out lots)

dd_rescue: (warning): /dev/sdc (77594624.0k): Input/output error!    561856.0k
dd_rescue: (warning): /dev/sdc (78149632.0k): Input/output error!    118912.0k
dd_rescue: (info): ipos:  78149632.0k, opos:  78149632.0k, xferd:  78149632.0k
                   errs:      0, errxfer:         0.0k, succxfer:  78149632.0k
             +curr.rate:    33314kB/s, avg.rate:    32066kB/s, avg.load: 25.2%
dd_rescue: (info): problems at ipos 78149632.0k: Input/output error 
                 fall back to smaller blocksize 

dd_rescue: (info): /dev/sda (78150744.0k): EOF
Summary for /dev/sda -> /dev/sdc:
dd_rescue: (warning): /dev/sdc (78150744.0k): Input/output error!    
dd_rescue: (info): ipos:  78150744.0k, opos:  78150744.0k, xferd:  78150744.0k
                   errs:      0, errxfer:         0.0k, succxfer:  78150744.0k
             +curr.rate:   173425kB/s, avg.rate:    32066kB/s, avg.load: 25.2%
ubuntu@ubuntu:~$ 
```

However, by playing with gparted on the drive I managed (somehow) to get the partition table the same as the system disc.  But when it mounted, the backup was clearly missing some folders.  So I used rsync to copy the system folders to the backup.  
```
sudo rsync -aHx --delete /media/[source]/  /media/[dest]
```
In my case [source] was *disk-1*  and [dest] was *disk*, so I had to be very careful to get this the right way round!!
But this appeared to fail part way (i/o error), and also reported it couldn't copy some directories. I then tried doing a 
```
sudo swapoff -a
```
and repeated the rsync command.  This time no errors and the backup does look like the system (doing a cursory check).  
The used space is still different between the two discs though - I am wondering if the backup got its root spare blocks.

There has got to be a better way!!??

---

### Post by ticket on 2009-07-04
I decided to try out my shiny new system backup disc by replacing my current system disc and re-booting.  Bit of a pain to have to open the case and swap out drives though.

Here's what happened:

System loaded grub and started to boot.

First signs of unhappiness was a slew of text messages, including:

```
iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
```

After this, the gnome desktop appeared, but a pop up also appeared saying unable to start gnome clock.  But all the other task bar items appeared, including the lmsensors temperature monitors.  But no icons on the desktop.

I soon discovered that was because nautilus couldn't be run (it seg-faulted).

Many of my installed apps could run however, (netbeans, open movie editor) but not firefox, which gave the error "couldn't load XPCOM".

The same happened after a re-boot.  

*So my 'cloned' system disk isn't a clone after all*.  Gonna have to start all over again.

To anyone listening out there: are my problems due to using an external  IDE-to-USB adaptor card?  Should I  connect the back-up disc to the PC internal slave IDE instead?  Has anyone successfully cloned their system disc?

---

### Post by ticket on 2009-07-04
I have tried again, using the Ubuntu live CD and this time just using the dd command, which is built into the live cd.
So I did
```
sudo fdisk -l
```
to confirm my device names, followed by a 
```
sudo swapoff -a
```
to stop any swapping going on (this may have been unnecessary), and then

```
sudo dd if=/dev/sda of=/dev/sdb conv=noerror,sync bs=32768
```
*(CAUTION - dd can destroy your disc if you get the disk names wrong in the if/of parameters. Don't use the above dd command as is - tailor it to your system)* 

The bs option forces the copy to transfer bigger chunks of data.  Without the option, the default chunk size is quite small, so you will experience long transfers.  The cloning of my 80Gb system disc took about 30 minutes.  

After the dd completed, and with the live CD running, I was able to compare the system and cloned discs. Worryingly, the content of the root directory on the clone appeared to have a number of folders missing (as was the case when I tried dd_rescue previously).

Anyway, I then decided to reboot normally using the system disc.

I then looked at the cloned disk with GParted. It said "Unable to find mountpoint", which after a bit of research is just a symptom of a duplicate UUID in the system (both the system and the clone have the same UUID). 

The next step is to substitute the system disc with the clone and see if it works. I have my doubts because of the missing folders. I'll let you know tomorrow.

---

### Post by ticket on 2009-07-05
Plugged in the cloned disc and rebooted and got ...

```
GRUB loading stage 1.5

Grub loading, please wait ...
Error 2
```


The grub docs say:
> Bad file or directory type
This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 

Perhaps not surprising since the clone didn't appear to have a /boot directory (but why didn't the dd copy produce one?).

So started again.
This time I booted the live CD and attached the clone disc to the USB.  I used gparted to create the same partitions from scratch. For some reason I couldn't get exactly the same partition sizes as the system disc, but I succeeded in creating a primary partition and an extended partition containing the swap partition.  The formatting of the primary partition (~70Gb) to about 20 minutes. I gave the primary partition the name System1

I then used rsync to copy files from my system disc to the clone disc:
```
sudo rsync -avHx (source) (destination)
```
where in my case (source) = /media/disk  and (destination) = /media/System1
This took absolutely ages - at least 1.5 hours! (maybe I should have used gparted copy/paste partition?) 
Finally, to get the clone to be bootable, I did:

```
sudo grub
```

 and entered

```
find /boot/grub/stage1
```

grub responded with

```
(hd0,0)
(hd2,0)
```
(I have a data disc taking up (hd1))
I then entered
```

root (hd2,0)
setup (hd2)
```

and grub printed some success messages. Entering quit exited me from grub.

The thought occured to me that the rsync copy would have copied the system fstab, which contains the UUIDs for the system disc drive.  These would, I thought not be useable for the clone, so I entered
```
sudo blkid
```
to get the UUIDs for the clone disc.  I gksu edited the clone fstab to use these UUIDs.
Ok, I shutdown, opened the case and replaced the system disc with the clone and re-booted.
Holding my breath, I got a ...

```
Error 15: file not found
```

followed by much gnashing of teeth. Ok, maybe my edit of fstab wasn't a good idea, to I booted the live CD and edited the fstab back to what it was (same as the system disc).  Rebooted and got a

```
Error 15: file not found
```

again.
I'm nearly out of ideas now. Can anyone shed some light on all this?

---

### Post by ticket on 2009-07-05
Ralphie's post #9 may offer a solution here:

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

It appears that menu.lst and fstab need to have a consistent set of disc UUIDs which correspond to those returned by blkid.  I'll try editing the files on the clone to fix this and attempt another boot (when I feel like opening the case again ...).

But I'd sure like to know why dd & dd_rescue failed to do their job properly.  Maybe the clone disc has to be strictly larger than the source (and not identical)?

---

### Post by ticket on 2009-07-06
Bumping for some help here - any ideas why dd / dd_rescue failed?

---

### Post by JC Cheloven on 2009-07-06
Sorry to see nobody answers your repeated posts. I have little experience with dd, but I think I have a good reason for that. You may be interested:

FSArchiver runs flawesly for me, and is far more flexible than dd. It can copy a partition in a compressed file or another partition of different size, and restore to a partitin which has not to be of the same size or format than the original one (yes, ext2 to ext3 or whatever). 

I often restore my testing machine to "a known state" using that. It comes in SystemRescueCD, fyi :-)

EDIT: and yes, if you expect your restored system to boot, and you specify your HDs by UUID in fstab and grub's menu.list, the UUID's have to be consistent. I haven't issues with this, as I don't need to re-format the partition when I restore the system, so the uuid remain unchanged.

---

### Post by ticket on 2009-07-08
Thanks JC, nice to know I am not being totally ignored!

FSArchiver isn't quite the right solution for me.  I am trying to cater for the situation where my system disk suffers a hardware failure and is irrecoverable.  If I have a clone of it, I can simply replace the dead disk with the clone and I am up and running again.  

The dd command works quite fast - so making a clone shouldn't be too much of a chore - or so I thought, until I tried it!  It would be even faster if I just used a 20Gb system disk.  I am only using an 80Gb one because that is what I originally installed Ubuntu on, along with lots of data.  I have since shifted my data off the system disc.

I'm gonna take a break from opening and shutting my PC case (maybe until this weekend).  Unfortunately my machine (old Dell precision) doesn't support booting from a USB. If it it did, I could test the clone disc without opening the case.

I'll report back later ... but I'd sure like to know why 'dd' failed.

---

### Post by ticket on 2009-07-11
Finally figured this out.

I should have been more suspicious of the i/o error messages I saw when using dd_rescue.  I noticed I was using a rather long USB cable to connect the IDE dive to the computer (2m).  I tried using a much shorter one (10 cm) and hey presto! no more i/o errors.

To cut the story short, I found that the following clone command worked best:

sudo dd if=/dev/sda of=/dev/sdc bs=2M

when finished (after 1 h 11m) it produced the output:

38159+1 records in
38159+1 records out
80026361856 bytes (80 GB) copied, 4271.91 s, 18.7 MB/s 

I tried different transfer buffer sizes to see what worked the fastest:

bs=32256     2h 15m   9.8 MB/s
bs=2M        1h 11m   18.7 MB/s

I couldn't improve on the bs=2M.

I didn't bother with the "sudo swapoff -a" business - not needed.

Interestingly, when running "sudo blkid" after the transfer finished, the clone disc had exactly the same UUIDs as the source disk!  So no need to mess with fstab and menu.lst.

I simply replaced the source disk with the clone and rebooted.  The system came up fine, no problems whatsoever.

So the message is, to clone a disc, just boot a live distro, connect your new drive and use 'dd'.  

:popcorn:

---

### Post by JC Cheloven on 2009-07-12
Glad to hear you solved your problem. I've been watching this thread since your previous post, and I enjoy the happy end, and to get something learnt myself. 
Thanks for sharimg your experience.

---

### Post by jorx on 2009-10-09
I'm about to attempt the same thing, so it's been helpful learning how you did it! Thank you for your concise easy to understand explanations (with cautions)!

---

### Post by aheckler on 2009-10-09
**jorx:** You could also use [Clonezilla]("http://clonezilla.org/"), it might be faster than dd.

---

