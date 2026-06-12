---
title: "Can Ubuntu read U3 USB memory sticks?"
date: 2008-04-23
forum: Hardware
---

### Post by egruber on 2008-04-23
I have a memory stick with the U3 System on it.  When I mount it, I can only view the U3 system files, not the files I copied to the stick.  Of course, I cannot run the U3 application.  Any ideas on how I can view the files?  Or should I just stick to non-U3 memory sticks?

And I'm really a newbie here, so please explain any steps.  Thanks!!

---

### Post by Lord Xeb on 2008-04-23
Have you tried WINE?I I have a U3 stick, but it is reformated to run Ubuntu on a stick. But I could see all the files I had on there at any time.

---

### Post by egruber on 2008-04-24
The stick came pre-formatted with the u3 software, and I use it on my windows pc.  Is there any way that ubuntu can read it?  Perhaps some sort of add-on driver?  I didn't want to reformat it with something else.

---

### Post by silvanus2005 on 2008-04-24
In my opinion U3 software it`s not useful at all. I had a U3 Sandisk stick, but I formatted it and I`m using it as a simply memory stick. I suggest you do the same; format it in Windows and you can use it in Ubuntu with no problem.

---

### Post by encompass on 2008-04-24
What advantage does U3 have for you...  I don't think there is much support for it.  As it's just a file system ontop of a file system. (Not the brightest idea.)  I would recommend just using the disk like any other USB stick.  Otherwise your going to have trouble where ever you go with that thing.
So to say the least... I don't think a solution is out there.
Sorry,

---

### Post by egruber on 2008-04-25
I liked it for a couple of reasons.  One, because it can be password protected.  Two, it has a couple of great programs.  One lets me synch my outlook and files onto the drive and the second stores my encrypted passwords.  Since I use it mostly on windows machines, I didn't want to mess with it.  I have other non-u3 drives I can use.  I just wanted to see if I could use this one, too.  Thanks!

---

### Post by Bob535 on 2008-04-25
take a look at [www.portableapps.com](www.portableapps.com)

Its essentially a free version of U3 that you can install on a USB stick. It gives the option to run it in the auto-execution pop-up instead of booting strait into it like u3. Not much difference and easier to use.

---

### Post by fno on 2008-04-25
> **egruber said:**
> I liked it for a couple of reasons.  One, because it can be password protected.

There you have it, the password protection is a windows only function (to my knowledge, at least).

The only way to unlock a U3 device for use by computing devices is by starting the U3 launchpad software which detects that the password security is enabled, and in turn prompts the user for the password. Since U3 is only supporting Windows and as far as I know have no specifications available on how to create such an application for other operating systems, chances are slim to zero you ever will be able to use the device on anything other than Windows while at the same time having the password security feature enabled.

On the other hand, if you want to protect the information you store on the U3 stick, I would suggest you seriously consider other options. I haven't seen any technical nor security analysis of the security functionality, but I am *very* skeptical that the design is anything even close to secure.

My suggestion is to check out TrueCrypt for securing documents on a USB stick or wherever. Supporting Windows, Linux and OS X makes Truecrypt a much better solution to protect your sensitive information, while at the same time being designed from the bottom up to be secure, by being based on state-of-the-art encryption technology.

---

### Post by Curtisc on 2008-04-25
It seems as though you're asking whether you can access the data partition of your U3 stick while leaving the rest alone, not looking for a U3 alternative.  If that's the case, then you might be out of luck... according to [this](http://ubuntuforums.org/showthread.php?t=591854) thread, the U3 system does something screwy that prevents Ubuntu from seeing both partitions.

As a first step, can you plug in the drive and type "sudo fdisk -l" into the terminal and then post the output here?  That should tell us whether or not both partitions are being detected.

---

### Post by egruber on 2008-04-25
> **Curtisc said:**
> It seems as though you're asking whether you can access the data partition of your U3 stick while leaving the rest alone, not looking for a U3 alternative.  If that's the case, then you might be out of luck... according to [this](http://ubuntuforums.org/showthread.php?t=591854) thread, the U3 system does something screwy that prevents Ubuntu from seeing both partitions.

As a first step, can you plug in the drive and type "sudo fdisk -l" into the terminal and then post the output here?  That should tell us whether or not both partitions are being detected.


You are exactly right.  I only want to access the data portion. I don't care about the U3 aspects when I use my Ubuntu PC.  I will try what you suggested tonight.  I suspect that it cannot see the data partition.  The U3 part shows up as a CD drive, and that's all I see.

---

### Post by Guinness70 on 2008-05-03
just purchased a Sandisk 4GB Ti, love the slider style, no cap to loose/break. and if it really is titanium it should be strong.

VERY dissapointed it doesnt come with a quickrelease lanyard, no lanyard AT ALL actually.
and then this U3 stuff... i had no clue about U3 and i dont want that U3 malarky.
i dont use skype, i dont use outlook and I DO NOT WANT this STORAGE DEVICE to be used as an MP3 player. if ild want to listen to digital music on the move ild buy an MP3 player, which i still dont own : i enjoy silence when it occurs.

the uninstall tool from Sandisk requires the U3 tool to be running
which isnt gonna happen on this ubuntu only machine becoz it requires Win2000 SP4 
so im buggered there

cant i *format* it in ubuntu? whipe it clean of all that "let me stuff this not-asked-for crap down your throat" software?
**and will it be useable in Windows coz i have to use this on the puters at work.**

or be patient and format it on a Windows machine at work? will that turn this memory stick in JUST a storage device? will it be U3 free?

---

### Post by cracker on 2008-05-03
Guinness70: You should be able to format the device in Ubuntu, but you'll lose all data on it, though I assume that's what you want. First, you need to plug it in, and figure out what device it is. Do this:

```

ls /dev/sd??
```
It'll list all the SATA, SCSI, and USB storage devices on your computer. You should be able to determine which one it is. When you're certain you have it, run the following command to zero it:

```

sudo dd if=/dev/zero of=/dev/sdb bs=1M
```
where sdb is your USB stick. This will erase it, so make sure you have the right device! You don't have to zero the whole stick, so just let it go for a few moments, then press control+C to stop it. You can then use fdisk to create a new vfat partition on it and format it. If you're only interested in using it in linux, use ext2, but if you need windows access, you'll have to stick with fat.


As far as alternatives to the U3 software, I second TrueCrypt. It's multiplatform, lightweight, and proven secure.

---

### Post by Guinness70 on 2008-05-03
thanks Cracker

emptied it as you specified and i did the
```
$ sudo mkfs.vfat /dev/sdf1
```
with sdf1 being the USBstick

then it only showed the U3 partition

so did the emptying again on sdf1 (isnt showing another)
and got this
```
dd: writing `/dev/sdf1': No space left on device
3828+0 records in
3827+0 records out
4013917184 bytes (4.0 GB) copied, 366.927 seconds, 10.9 MB/s

```
no free diskspace ...:(


edit:
done another clearing
and nother format
and now it shows both partitions but the U3 stuff is still there ...
gonna try on the wife's laptop (MS Vista)

---

### Post by encompass on 2008-05-03
I know all the command but gparted does a good job... Just install that.  and format it to what ever you like... if oyur only going to use it on linux systems use a linux format. :D  But otherwise fat file system is best. :D

---

### Post by starcannon on 2008-05-03
I have 4 of these by Sandisk, micro 2GB cruzer with u3 smart software on them.

I just wiped them using gparted, all is well, windows likes them, linux likes them, they were cheap, so I like them to :)

Even turned one of them into a liveUSB with hardy heron on it.

If you want windows to like it as well as linux just choose fat32 or fat16 either way you should be good, unless you want the U3 junk on there, then I don't really know what you should do, wine it maybe as mentioned before.

---

### Post by linuxstl on 2008-07-01
Without reformatting these drives, has anyone been able to read from these drives using linux/ubuntu?  I haven't been able to access this drive even though other non-U3 drives do not.  There will be others using U3 disks who can not format their drives so I am looking for a solution to reading/writing to this drive without reformatting it in any way.

Any solutions out there?  I've googled for hours without a real solution.

---

### Post by stchman on 2008-07-01
> **egruber said:**
> I have a memory stick with the U3 System on it.  When I mount it, I can only view the U3 system files, not the files I copied to the stick.  Of course, I cannot run the U3 application.  Any ideas on how I can view the files?  Or should I just stick to non-U3 memory sticks?

And I'm really a newbie here, so please explain any steps.  Thanks!!

My advice is to remove the U3 software permanently.  U3 is a PITA that serves no purpose IMO.  To remove it you will need to find a Windows machine to run the software.

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

---

### Post by sergiom99 on 2008-07-01
> **linuxstl said:**
> Without reformatting these drives, has anyone been able to read from these drives using linux/ubuntu? 

I just plug my Kingston U3 2Gb and I can access the data partition without problem. And the U3 Sys Partition shows up as a CDROM drive.

---

### Post by cheruvim on 2009-03-18
You can mount it as you would any other disk but you have to know which logical volume is the one that has the data

$ sudo lshw 

should produce something like this:
*-scsi:2
          physical id: 3
          bus info: usb@4:6
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: U3 Cruzer Micro
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             version: 3.27
             size: 1953MiB (2048MB)
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 1953MiB (2048MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000c949d
              *-volume
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   logical name: /dev/sdb1
                   version: FAT32
                   serial: 4990-58c1
                   size: 1953MiB
                   capacity: 1953MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
        *-cdrom
             description: CD-R writer
             product: U3 Cruzer Micro
             vendor: SanDisk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 3.27
             capabilities: removable audio cd-r
             configuration: ansiversion=2 status=ready
           *-medium
                physical id: 0
                logical name: /dev/scd1

There are two partitions there one is the cd and the one with the files the FAT32  one. 

The cd is the one with the ub3 software and the FAT32 volume is the partition with the files.

So you want to mount the volume That is FAT32 which has a logical name of /dev/sdb1 in this case (might be different on your system depending on what's already mounted).

So what I do is make a dir /media/ub3disk as root
then mount to that point.. unfortunatly it mounts it read only :( unless you are root

$ sudo mount -t vfat /dev/sdb1 /media/ub3disk

anyone know how to make it writable?

---

### Post by cheruvim on 2009-03-18
> **egruber said:**
> You are exactly right.  I only want to access the data portion. I don't care about the U3 aspects when I use my Ubuntu PC.  I will try what you suggested tonight.  I suspect that it cannot see the data partition.  The U3 part shows up as a CD drive, and that's all I see.

> **sergiom99 said:**
> I just plug my Kingston U3 2Gb and I can access the data partition without problem. And the U3 Sys Partition shows up as a CDROM drive.

I have a friend who experiences the same thing. Not sure why it works for him and not me. I think he has a later version? I have Hardy Heron, is there one later than than?

---

