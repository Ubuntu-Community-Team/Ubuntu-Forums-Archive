---
title: "For long term storage purposes which is better, an external SSD or Thumb-drive?"
date: 2021-01-11
forum: Hardware
---

### Post by cybrsaylr on 2021-01-11
Have some important documents, pix, mp3s etc I want to safely save/store. 
Wondering which is the best above device to save them on for the long term?

---

### Post by #&amp;thj^% on 2021-01-11
Just my 2 cents worth on this and I'm still testing both.
With solid state drives still being in their relative infancy, it will likely be a few more years before we get a true picture of how well they hold up to repeated use.

The lifespan of each memory block in an SSD is limited to a certain number of write cycles i.e. the number of times a piece of data can be stored to it.

The number of cycles will only be a few thousand on most drives. This sounds alarmingly low, but is not really an issue in modern SSDs. Unlike hard drives, which write their data to the earliest free block, an SSD uses technique called wear-levelling to ensure that each memory block is used before the cycle begins again at the first block.

Unless you're writing tens of gigabytes of data a day, every day for several years, you won't get close to the limit on write cycles. Even if you did, the memory would become read-only, so your data would still be accessible.


USB flash drives, as well as memory cards like SD cards, have similar issues to solid state drives.

They have fewer components and are far more robust, but are restricted to a finite number of write cycles usually in the range of 3,000 to 5,000. And since they tend to use cheaper memory modules, they can be less reliable than SSDs.

Again, though, this needs to be kept in perspective.

If you're using the flash drive for its primary purpose of moving files from one location to another, then a cheap drive will be more likely to fail through physical damage (such as breaking the connection between the USB jack and the printed circuit board inside the drive), before the write limit is reached.
My humble thoughts thus far are A good reputable SSD is my choice.

---

### Post by cybrsaylr on 2021-01-11
1fallen thanks for your comments.

To date am still using an old 160GB Seagate IDE HDD in an enclosure from back in 2008 for storage. Along with a couple newer Flashdrives. Lately the 160GB Seagate HDD takes a little time to spin-up after turning it on, which worries me. This got me thinking better get something newer to transfer all its old stored data to while it's still possible.

---

### Post by #&amp;thj^% on 2021-01-11
I know that feeling, I also way back bought a couple of My Books with spinning hard drives, that I use very sparingly now.
I first began my test with an intel 180gig SSD with a 10 year warranty, I transfer d back and forth writing and rewriting almost daily for 5 years now.
My Thumb Drives did not make it past 2-3 years, while the Intel and WD's SSD's i'm using still preform as new.

---

### Post by SeijiSensei on 2021-01-11
I back up my local and remote servers to a 4 TB USB external drive. Been working flawlessly for a couple of years now.

[https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817](https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817)

---

### Post by #&amp;thj^% on 2021-01-11
> **SeijiSensei said:**
> I back up my local and remote servers to a 4 TB USB external drive. Been working flawlessly for a couple of years now.

[https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817](https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817)

Mine aren't seagate but Western Digital 2 TB, and they still function good after 9-10 years, but showing signs of age.
I put mine through a literal hell ie: restoring partitions and data recovery, daily transfers. (Back when they were in everyday use)
But for myself, i convinced me>> For long term storage purposes SSD's will be my choice for local storage.

---

### Post by cybrsaylr on 2021-01-12
SSD's do seem to last. Got a couple in my main i7 desktop that are used every day. 
A 120GB Kingston installed 4/2013 and a 480GB SanDisk installed 2014.
System Monitor report both show Old-age or Pre-Fail but they both still operate like new.

Then again this desktop has a 2TB Seagate HDD installed in 2112 that still runs fine. This 2TB Seagate HDD replaced an OEM 1TB Seagate HDD that failed 3½ years after getting that i7.....6 months after the 3 yr warranty it had expired!

---

### Post by ramonet-net on 2021-01-15
My experience says external USB drives DO FAIL.
And if they got 2 GB of data, thats a problem.
2 times they have failed to me, first one SeaGate 2 TB, second 4TB Western Digital.
Used them for backup, so it was twice a week.

SSD seem pretty solid to me, but size is still a bit expensive

---

### Post by cybrsaylr on 2021-01-23
Got a, Samsung - T7 500GB External USB 3.2 Gen 2 Portable Solid State Drive with Hardware Encryption.

Plugged SSD into my i7 desktop via USB-C cable. 

Disks: does show a 500 GB Disk, Samsung PSSD T7 is there.

But I can't get it to open? Help, what is needed to be able to use this exSSD?

---

### Post by oldfred on 2021-01-23
What format is it?
NTFS, exFAT, FAT or other?

Post this.
sudo parted -l

---

### Post by cybrsaylr on 2021-01-23
oldfred  got this,

[IMG]https://i.postimg.cc/90WytXz3/Screenshot-from-2021-01-23-17-09-31.png[/IMG]


sudo parted -l

Model: Samsung PSSD T7 (scsi)
Disk /dev/sdi: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary

---

### Post by oldfred on 2021-01-23
I would change to gpt, no reason for MBR.

Only if you need compatibility with Windows may I keep exFAT. But support in Linux is newer than support for NTFS. And new version of a driver has recently been released.
If only Linux I would convert to ext4.

[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)
The standard exFAT implementation is not journaled and only uses a single file allocation table and free space map. 
But exFAT will store larger files than FAT32. But still should not be used for larger partitions as chkdsk may take forever. 
And it does not have Linux ownership & permissions.

exFAT File-System Performance On Linux 5.9  Nov 2020
[https://www.phoronix.com/scan.php?page=article&item=exfat-linux-59&num=1](https://www.phoronix.com/scan.php?page=article&item=exfat-linux-59&num=1)

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by cybrsaylr on 2021-01-24
Thanks oldfred,

Well this is getting more complex than anticipated. 

Have an old external IDE 160 GB HDD that was simply put in an enclosure, plugged into desktop via USB port and it was good to go. Been working 15+ years well for both Windows and Linux Ubuntu for data storage using NTFS.

It this possible with this external Samsung T7 SSD if I format it to NTFS?

Got it to work on Windows 10. Plugged it in, installed the Samsung software and it opened up for transferring data between drives.

Still can't get Ubuntu 18.04 to mount or recognize this ext SSD.

---

### Post by oldfred on 2021-01-24
NTFS is not best for backup.
Windows formats do not support Linux ownership & permissions.
So you could backup your data, but if you restore data, you have to reset ownership & permissions.
But you cannot backup any system folder as ownership & permissions vary.

Is the Samsung Software just for Windows encryption? And then unique to this drive?

---

### Post by cybrsaylr on 2021-01-24
The Samsung Software is just for Windows or Mac encryption. 
No Linux software option available. 
Didn't think this mattered since Ubuntu offers its own encryption with ext4 I believe.

Intended this SSD to be used for long term data storage not backup.

---

### Post by cybrsaylr on 2021-01-25
Solved! 
Found this very helpful Google link.
Did it and it worked like a charm opening up the PSSD T7.

[How to Mount an exFAT Drive on Ubuntu Linux]("https://linuxize.com/post/how-to-mount-an-exfat-drive-on-ubuntu/")
> How to Mount exFAT Drive on Ubuntu Linux
To be able to mount exFAT filesystem on Ubuntu you&#8217;ll need to install the free FUSE exFAT module and tools which provide a full-featured exFAT file system implementation for Unix-like systems.

Before installing the packages make sure the Universe repository is enabled on your system. Open your terminal either by using the Ctrl+Alt+T keyboard shortcut or by clicking on the terminal icon and type:
sudo add-apt-repository universe
Once the repository is enabled update the packages index and install the exfat-fuse and exfat-utils packages using the following commands:

sudo apt update 
sudo apt install exfat-fuse exfat-utils
That&#8217;s it! You can now open your file manager and click on the USB disk to mount it.



---

