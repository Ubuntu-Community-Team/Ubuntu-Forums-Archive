---
title: "problem with acomdata external hard drive"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by edwinw on 2007-03-17
Hi,

I'm having a problem with my Acomdata 320 GB E5 "Hybridrive", it's a USB connection external hard drive and I'm running Dapper.  I've narrowed down the problem and was hoping for some help from an experienced user.

The main problem is that the hard drive is not your vanilla-type external hard drive, it has some Windows-specific "features" which unfortunately make it unusable in Linux (right now).  Specifically, it has a peculiar factory partitioning which results in the drive being recognized as a CD-partition (with special utilities and autorun stuff) and a separate hard drive partition.  Straight from the manufacturer's User Guide:

[FONT="Courier New"]Your HybridDrive uses an advanced partition scheme called VirtualCD + SecureHD. The Drive was formatted at the factory with two partitions. As the name implies, one is the CD partition; the other is the HD (Hard Disk) partition. When you connect the Drive to your computer, the two partitions will mount as separate, distinct volumes, as if they were two discrete devices.[/FONT]

This works in Windows since the CD partition is recognized, and then the hard drive partition is subsequently recognized.  Unfortunately, in Linux only the CD partition is recognized and mounted as /dev/scd0 at /media/cdrom-1.  In essence, it only detects the first partition, and because it "sees" it as a CD it mounts it with the typical CD options.  The command "mount" gives:

[FONT="Courier New"]...
/dev/scd0 on /media/cdrom-1 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8)[/FONT]

By analogy I tried mounting other partitions manually (scd1, sdb1, sdb2) just in case, but the device does not exist.  By the way dmesg gives me:

[FONT="Courier New"][17184594.016000] usb 3-2: new high speed USB device using ehci_hcd and address 3
[17184594.148000] scsi3 : SCSI emulation for USB Mass Storage devices
[17184594.148000] usb-storage: device found at 3
[17184594.148000] usb-storage: waiting for device to settle before scanning
[17184599.148000]   Vendor:           Model:                   Rev:
[17184599.148000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17184599.176000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[17184599.176000] sr 3:0:0:0: Attached scsi CD-ROM sr0
[17184599.176000] sr 3:0:0:0: Attached scsi generic sg1 type 5
[17184599.176000]   Vendor: DMI       Model: USB2.0 Storage    Rev: 1.15
[17184599.176000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17184599.180000] sd 3:0:0:1: Attached scsi disk sdb
[17184599.180000] sd 3:0:0:1: Attached scsi generic sg2 type 0
[17184599.180000] usb-storage: device scan complete
[17184599.632000] UDF-fs: No VRS found
[17184599.648000] UDF-fs: No VRS found
[17184599.664000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17184599.668000] ISO 9660 Extensions: RRIP_1991A[/FONT]

Also, the command "fdisk -l" does not list any additional partitions (not even the partition which is recognized as a CD).

My first attempt at troubleshooting was to try to remove the factory partitioning so that it would just be a plain external hard drive.  However, I ran into a chicken-and-egg problem here, since the CD partition is mounted as read-only.  As a result, all of the command fdisk, cfdisk, even dd (to try to zero out the partition) did not work since they couldn't write (commands executed with sudo).  I can manually unmount and remount the CD partition, but only as an iso9660 file format, and it gets mounted read-only.  Perhaps there is an option for force-mounting as read-write?

Okay, if you've gotten this far, I'm hoping to get some advice on how to implement one of the following solutions:

1. (preferred solution) Somehow get the hard drive partition recognized and mounted.  It is formatted as FAT32 according to the documentation so I should have no problem once this is done.  Are there additional diagnostic or probing commands I can try to detect this partition?

2. If there's nothing I can do there, is there a way I can force the mounting of the CD partition as read-write?  That way I can just repartition it with cfdisk or something else.

Thanks for any assistance!

---

### Post by killring on 2007-03-19
Plug the drive into a MS Windows XP box. The first thing it asks you is whether or not you want to change or disable the security settings. Disable them. After that you should be able to mount the drive just like a usb memory stick. At least, that was what just worked for me running Debian Etch.

HTH,

kr

---

### Post by alex_0077 on 2007-03-22
The issue at hand is that stoopid VirtualCD. How does one go about deleting the thing, and making the drive one whole contiguous drive?

:confused:

---

### Post by pixeldotz on 2007-03-22
take the drive out from the case (more than likely it's an ide drive) toss it into a pc and format it to your liking then put it back in the casing and you should be set to go.

hdds are so cheap now that i just buy hdds + enclosure separately to avoid these types of problems.

wd+acomdata = best combination :)

---

### Post by kamiccolo291 on 2007-06-26
I am having the same problem with my Acomdata External HD. Were you able to wipe the "CD" partition or find a way to mount the drive partition?
(yes, I have turned off the password encryption using XP.)

---

### Post by atxphoenix on 2007-07-13
On the virtual CD partition of the HybridDrive, there is MacOSX and Windows software to make the hard drive partition visible to your system. Since there isn't, to my knowledge, a MacOSX emulator for Linux, I went with 'wine' the software package that runs quite a bit of win32 software using native Linux system calls. So you will need to install the package 'wine'.

Also, you will need to find the mfc40.dll file somewhere. If you have access to a Windows XP system, it is found at C:\\WINDOWS\system32\mfc40.dll. Copy this file to ~/.wine/drive_c/windows/system32/mfc40.dll.

After that it gets easier:

(1) Open a terminal in Gnome.
(2) Run the command "df" to see where the virtual CD-ROM was mounted. In the case of the 500G Acomdata drive, the virtual CD partition is 124968 1k-blocks. 
(3) cd to where ever the virtual CD partition is mounted
(4) enter exactly the command:
     'wine ONSPCLCK.exe'
without the single quotes, of course!
 If you installed mfc40.dll correctly, you won't see anything happen for a few seconds, then the command prompt will return. On your desktop, you will probably see an icon appear with the label "HD PART". That's it!

"HD PART" is formatted "vfat" because Acomdata expected the drive to be used in Windows and MacOSX. vfat is the only format understood by both. I'm not sure what would happen if one tried to reformat the *entire* drive as a native Linux format. I do know that ONSPCLCK.exe, ONSPCPRT.exe and PWMangr.exe expect the 1st partition on the drive to be formatted VFAT or NTFS. If you don't have any files in excess of, I think, 2G, vfat is fine, and you need do nothing further. If you need to store larger files, reformat the partition as NTFS using the ntfsprogs, then install fuse and ntfs3g; and mount the drive as an ntfs-3g partitiion. It's not as fast ans an ext3 or Reiser4 partition, but otherwise it's quite functional.

A further word:

In spite of Acomdata's hype, the drive is s-l-o-w. USB 2.0 only achieves really good speeds if the processor can devote all it's time to servicing the USB2 driver, which is generally not the case. the best speed I have been able to achieve is 23M/s.

Good luck!

---

### Post by ZMB on 2007-07-15
Ok...so I was having the same problems that everyone else was having, but worse so. I could get the external drive to show up on my roommate's windows machine but on my linux box. I was getting nill...not even showing up as a cdrom. I broke down and took the hard drive out, installed it in my computer...when ubuntu finally booted up it was mounted as /dev/hdb1 to  /media/<what ever the name was>...It was still however acting like a read only cdrom...Then I nuked it with gparted, formated it to ext3, shut off my comp, changed the jumper on the HD from cable select to master, reinstalled it into the enclosure.....and boom...half a six pack of newcastle later, I had a external hard drive worth a damn.

Beware...you will have to void the warranty when opening up the enclosure...but heh...sometimes you got to live on the wild side.

---

### Post by rduggal on 2007-07-15
This drive only seems to work with a USB1 connection, not USB2!

So, I just connect a USB1 hub to the USB2 port of the computer, and plug the drive into the hub and it works!
At USB1 (very slow) speed of course, but at least I can access my data for now.

I wonder if acomdata isn't following the industry norms or if the linux USB2 support has a bug. hmm..


Cheers,
***Rajesh***

---

### Post by DMUSER on 2007-07-27
Ok.  I got my external Acomdata hard drive to function in Ubuntu running in Gnome.  Actually even the LiveCD detected it, and allowed me to access it with no problems(formatted as NTFS).

But for some reason after I installed the Kubuntu destop environment, Kubuntu can't find it at all.  It just shows up as a CDROM device.

Anyone have any idea why this would be?

---

### Post by DMUSER on 2007-07-27
Ok.  I realized that I just had to mount it.

Silly me.

It works perfectly now.

---

### Post by ossgrouch on 2007-08-04
This is how I finally (and I mean with my linited experience with Linux and Ubuntu, I spent hours reading and trying this and that) got the acomdata E5 Hybrid Drive (320GB) with USB connection to work:

My operating system:
KUbuntu 7.04 (Feisty)
ivman is installed
acomdata is formatted NTFS, no access password set.

When I first plugged in the acomdata the system would mount the CD portion as CD PART (scd1).
Opening Konsole (Terminal Program) and running: ls -l /dev/disk/by-uuid
would show me the acomdata as: lrwxrwxrwx 1 root root 10 2007-08-04 18:10 D840163440161A38 -> ../../sda1
and running the df command would give me:  /dev/scd1               161552    161552         0 100% /media/scd1
I then cd'd to /media/scd1 and tried to run Wine as mentioned above by atxphoenix, found that I needed mfc42.dll in wine's windows/system32 directory for the command wine ONSPCLCK.exe to function. Albeit, that did not give access to the HD portion of the acomdata.
From windows I knew that the CD partition was called  CD PART  and the hard drive partition was  HD PART,
so next I entered the command:  pmount sda1 "HD PART"  (with the quotation marks, it appears that if there is spaces in a file name the quotation marks are needed to make the terminal understand where to go).
And BINGO! a drive called USB Drive (HD PART) showed up.

Following a restart of the computer HD PART was of course missing, so I simply opened a Terminal Window and entered from my default prompt the command:  pmount sda1 "HD PART"
and again the acomdata's hard drive partition showed up. Appearently it has to be manually mounted at every restart.

Good luck fellow acomdata users:confused:

---

### Post by ossgrouch on 2007-08-14
I have done some more work with my acomdata USB drive. I didn't get ntfs-3g to work with my drive, and it was sort of useless if I couldn't write to it.

Removed ivman (I can live without it)

Installed fuse-utils (with adept manager)
Installed ntfs-3g    (with adept manager)

A check in /dev/disk/by-uuid (or by running ls -l /dev/disk/by-uuid in the Konsole)
still showed that my USB drive was listed as sde1 (/dev/sde1).

By mounting the drive from the Konsole with the command:
sudo mount -t ntfs-3g /dev/sde1 /media/"HD PART"
I got it to function with read/write priviliges.

(NTFS Configuration Tool don't seem to be able to mount this drive, why I am doing it "manually")

Acomdata advertices this drive's data transfer speed as up to 480 MB/sec!
That is the maximun throughput for a USB 2.0 port, but overhead etc etc, you know the story. In Windows XP it was slow, USB transfer requires heavy use of the CPU. The amazing thing is that it is faster under Linux, on larger files I am getting 15.7 MB/sec, which by no means is fast, but it still was a cheap backup drive of 320 GB.

Ossgrouch

---

### Post by SqdnGuns on 2007-10-24
Anything new for Gutsy and Acomodata 500GB HDD? Fiesty 32 would recognize it with no problem at all, Gutsy 64, no dice.

The below command sees my IDE and 2 SATA HDD's. That damn CD PART mounts............

sqdnguns@JARHEAD:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 43616b7d-48ac-4605-bc4e-91d2b4b3a5da -> ../../hdb1
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 487C333F7C3326DA -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 6CFC23B6FC23798A -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 8ad6fcac-3dc0-474f-80be-63c974ff03dc -> ../../hdb2
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 9680a217-0875-4a45-8edd-f541b1a8579f -> ../../hdb4
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 bc14ea62-495c-4ff0-83f6-934d169131e7 -> ../../hdb3
sqdnguns@JARHEAD:~$ 

I figure I'll have to roll my own kernel for it to work. The custom kernel I have for Slack 12 mounts it with ease...

Appreciate an assist if possible.

---

### Post by SqdnGuns on 2007-10-26
> **SqdnGuns said:**
> Anything new for Gutsy and Acomodata 500GB HDD? Fiesty 32 would recognize it with no problem at all, Gutsy 64, no dice.
 
The below command sees my IDE and 2 SATA HDD's. That damn CD PART mounts............
 
sqdnguns@JARHEAD:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 43616b7d-48ac-4605-bc4e-91d2b4b3a5da -> ../../hdb1
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 487C333F7C3326DA -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 6CFC23B6FC23798A -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 8ad6fcac-3dc0-474f-80be-63c974ff03dc -> ../../hdb2
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 9680a217-0875-4a45-8edd-f541b1a8579f -> ../../hdb4
lrwxrwxrwx 1 root root 10 2007-10-23 22:38 bc14ea62-495c-4ff0-83f6-934d169131e7 -> ../../hdb3
sqdnguns@JARHEAD:~$ 
 
I figure I'll have to roll my own kernel for it to work. The custom kernel I have for Slack 12 mounts it with ease...
 
Appreciate an assist if possible.
 
 
Forget it, I just removed the drive from it's enclosure and intalled it internally and whacked it.
 
Got a good deal at Fry's for this, $90 for 500GB WD HDD.

---

### Post by aponteluis@mac.com on 2007-11-29
I had he same problem getting rid of the CD PART partition.  I tried every partitioning program out there but could not delete the CD partition.  I contacted the manufacturer and they emailed me an .exe file that can remove the CD partition easily.  The gave me permission to distribute it, so help yourselves and good luck.  

The file is 1.5 MB in size therefore is over the limit to post it directly on this thread.  Please go get it in my web page [http://www.luisaponte.com](http://www.luisaponte.com)  look under the blog and tools section.

Follow the following instructions.

Be default there's actually no way to remove the CD Part partition of the drive because it's locked.  I've included a zipped up file that will help you delete the partition and make it a regular external drive for you.  If you'd like to do this, please follow the steps below:
 
***Please note, following the steps below WILL delete any data you might currently have on the "HD Part" drive.  If this is a problem, do not follow the steps***
 
Please save the attached file (REMOVE CD PART) to your desktop and do the following:
 
Unzip the file - will turn into a "REMOVE CD PART" folder.  Open the folder and find the file called "MP251MFG.exe" - Double click on it - will open a new window which will be utility to remove the CD Part.  Your Acomdata drive should be the only drive on the list and you'll only need to click on the button "Cofigure HDD".
 
It should finish rather quick and give you a green "PASS" once it's finished.  When it's done you'll want to turn it off, wait 5 seconds, then power it back on.  Your Acomdata drive will now have 1 solid partition and be ready to use inside "My Computer".

---

### Post by TheGreenLing on 2008-01-26
I bought the product, and the drivers were detected and installed instantly,  But it would not mount, so I read their user manuals and tried reinstalling the drivers many times, I Emailed for tech support and they were no help, I emailed them back and forth for a week, and it ended in them telling me things that didn't work then saying that i tampered with the product. At that point I was not happy I found A lot of people on the internet have the same problem. I tried that remove CD Part thing also and still no dice. My advice, Return it if you still can.

---

### Post by idmacdonald on 2008-02-12
Hi Luis,

> **aponteluis@mac.com said:**
> I had he same problem getting rid of the CD PART partition.  I tried every partitioning program out there but could not delete the CD partition.  I contacted the manufacturer and they emailed me an .exe file that can remove the CD partition easily.  The gave me permission to distribute it, so help yourselves and good luck.  

The file is 1.5 MB in size therefore is over the limit to post it directly on this thread.  Please go get it in my web page [http://www.luisaponte.com](http://www.luisaponte.com)  look under the blog and tools section.

Thanks for that link, That tool indeed deleted the strange 'CD-ROM' partition from the disk and made it work like a normal HD. Much easier than opening up the case and shoehorning it into a laptop. I then created one big partition on the disk and formatted it ext3, It now works great for me.

Many thanks,
-Ian

---

### Post by speirint on 2008-05-21
Okay, I'm still new and not very proficient with coding so please bear with me--I'm describing things to the best of my ability right now:

I was using Gutsy Gibbon when an fsck error (4) occurred.  Before I go ahead and try fixing anything with it, I wanted to back up my data.  The thing preventing me from doing so was the fact that I have an acomdata external hard drive (160 gb), and it was too late for me to return it by the time I noticed it wasn't getting along with Ubuntu.  I've made a Gutsy Gibbon live cd for Ubuntu and was able to access some of the files using nautilus, but from what I understand, the external hard drive needs to be recognized, probably by mounting manually, before I can copy and paste things into it.  I am not very proficient with terminal or sudo unless I can see code to copy and paste as I'm still new. My questions are as follow:

1)  How do I mount the drive [manually]?

2)  Is there a way to manipulate my data using a gui, or are there easy to understand commands/code I can use to copy my data into the hard drive?

3)  Do I really have to delete the CD part petition?

4)  Also, I was wondering how can I log in as the original computer root (non-livecd root, just my already installed ubuntu root)for priveledges through a live cd to access the data.

I tried entering commands like:
/dev/sda1 /mnt/
or sudo mnt/dev/sda1
mount: only root can mount /dev/sdb1 on /media/sdb1

but I actually have no clue as to what the external drive would be called, and have suspicions that by using sda1, I'm mounting into one of my internal hard drive partitions.

---

### Post by speirint on 2008-06-13
Bump?  I'm still unable to access the drive and am unclear as to what I should be doing... I downloaded the file that allows me to clean out the cd image, but it's in exe format, and I won't be able to use it unless I'm on windows or wine as far as I know.

---

### Post by dfmalh on 2008-07-07
Hi I posted this in place (a solved thread... :rolleyes:), but I don'y think it was right, so I moved it here, I hop I am not stepping on any toes.

Here is my situation:

I bought a Seagate Barracuda 500GB SATA 32Mb Cash HD on Friday to use as an external backup HD (thesis, movies, music, etc). The HD is in an Eagle Consus case (support usb2.0 and up to 750GB HDs).

On a XP system, I could partition the Drive but I was unable to format it. Apparently there is some "time-out" error between the USB2 and the SATA connection, I am not exactly sure what it means exactly... but the bottom line is that it can't format the external that way.

I am not familiar with how to partition and format in linux (Ubuntu) so that is why I opted to go for XP... bad choice!

I installed Gparted, and after a long struggle got all the partitions removed, and created new ones. I created 3 partitions, and formated to the FAT32 file system (as a start), checked the 3 drives and they worked, mounted correctly, in Ubuntu and on the XP system.

So I decided to to change the first partition to ext3 file system, and one of the others to NTFS (I downloaded and installed ntfsprogs to do that). Everything fine, and everything is working.

The drives names are however the respective sizes of each partition... that won't do, so I tried to rename them...

I used this for the FAT32 partition: sudo mlabel -i /dev/sdb2 ::usbfat32
and this for the NTFS partition: sudo mlabel -i /dev/sdb3 -s ::usbntfs
and this for the EXT3 partition: sudo e2label /dev/sdb1 usbext3

...bad idea! now none of the drives work.

See the attached picture of the pop up window.

The ext3 and fat32 partitions are mounted, but when you try and access them, it does not work.

When I unmount the drives, I get a message that data is being written to the drive, and I can not unplug the drive. After a while the message disappear, and a new message says that it is now safe to remove drive.

In Gparted I can see the different partitions. See picture.

I included the information windows for the NTFS drive that does not want to mount and also the information window for the ext3 (first partition) which gives me a "superblock" error message.

I can't run a check on any of the drives, it won't work. I can't remove any of the partition, because then the external drive "unmount"...

So, all I want to do is to delete all 3 partitions and start from scratch to create new partition.

Can anybody help with this? Please...  ](*,)

ps. After I changed the FAT32 partition to EXT3 the partition seemed "larger", and the same for the NTFS partition, maybe it is something to do with that...

---

