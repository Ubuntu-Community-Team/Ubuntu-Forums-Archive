---
title: "No second harddrive or third cd/dvd drive detected :("
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by Davyp on 2006-02-08
No second harddrive or third dvd drive detected :(

Hello,

I just installed Ubuntu Breezy Badger after fancying a change from Suse 10.0. Big thumbs up on all counts except on the hardware detection, but I suspect it may have something to do with the lack of user knowhow ;)

I have two phyiscal harddrives and three cdrom/dvd drives. Both harddrives are partitioned. The first is fully detected, the second not at all, neither is my dvd writer. The drives are all fully functional as they work under windows and under Suse 10.0 they were also all detected. Under suse they all corresponded to device filenames /dev/hd*. Here's what I get now with ubuntu, with an explanation of each:

$ ls /dev/hd*
/dev/hda   /dev/hda4  /dev/hda6  /dev/hdc
/dev/hda1  /dev/hda5  /dev/hda7  /dev/hdd

/dev/hda - first harddrive
/dev/hda1 - windows ntfs partition
/dev/hda4 - Extended partition
/dev/hda5 - Swap partition
/dev/hda6 - ext3 partition used for /home files
/dev/hda7 - ext3 partition used for everything else
/dev/hdc - cdrom0
/dev/hdd - cdrom1

So basically I'm a bit stuck, if there were a device file that I knew about I'd know to mount it, but unless it's under some other name and I'm being a fool, I'm stumped! If it helps the second harddrive is also ntfs and is devided into two partitions.

I have attached the output from both lspci and dmesg, which will hopefully be
useful to someone :)

Any help would be really appreciated, thanks in advance,

David

---

### Post by taurus on 2006-02-08
For your second HD with two partition of NTSF, try

sudo /mnt/windows_1 /mnt/windows_2
sudo mount -t ntfs /dev/hdb1 /mnt/windows_1
sudo mount -t ntfs /dev/hdb2 /mnt/windows_2
df 

Now, you should see them listed...

---

### Post by lha on 2006-02-08
Five ide devices is a bit unusual. Could those missing two devices be sata/scsi? Try
> ls /dev/|grep sd
(or 'ls /dev/sd*' if you want)

---

### Post by wrtrdood on 2006-02-08
From the dmesg and lspci info it looks like your SATA devices are seen but might not be completely configured.  One way to check (since it shows them being defined as SCSI) is to use cdrecord -scanbus (quite handy, actually).  If that shows your devices, check to see if sr_mod got loaded (lsmod | grep sr_mod).  That would prevent you from seeing them.

---

### Post by Davyp on 2006-02-08
Thanks for the help everyone :)

I've tried everything you suggested, no luck yet, but here are the results:
------------------------------------------------------------------------------
From taurus' post:

sudo mkdir /mnt/windows_1 /mnt/windows_2
$ ls
windows_1  windows_2
$ sudo mount -t ntfs /dev/hdb1 /mnt/windows_1/
mount: special device /dev/hdb1 does not exist
$ sudo mount -t ntfs /dev/hdb2 /mnt/windows_1/
mount: special device /dev/hdb2 does not exist
------------------------------------------------------------------------------
From lha's post:

$ ls /dev/|grep sd
ptysd
ttysd
$ ls /dev/sd*
ls: /dev/sd*: No such file or directory
------------------------------------------------------------------------------
From wrtrdood's post:

$ sudo cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

$ ls /dev/pg*
ls: /dev/pg*: No such file or directory

$ sudo lsmod | grep sr_mod
sr_mod                 15652  0
cdrom                  33952  2 sr_mod,ide_cd
scsi_mod              124872  3 sr_mod,sbp2,libata
------------------------------------------------------------------------------

So I think that means there is not a device filename for the hard drive under hd* or sd*. But as wrtrdood suggested it looks like an SATA drive that has not been correctly configured. How do I go about configuring it? And any clues on the dvd recorder?

Thanks again

---

### Post by LordBug on 2006-02-08
It would be beneficial to know *exactly* where all 5 drives are attached.  Which IDE, Parallel or SATA, master/slave, channel, etc.  At this point, I'm thinking you have a missing device driver for one (or more) of your IDE controllers.

---

### Post by Davyp on 2006-02-09
Hello again!

I've taken the back of my pc and have been rummaging around in there, I've attached an ascii table (had a lot of fun making that) showing the run down of the relevent hardware on my pc.

First thing I noticed was my IDE cable to my undetected hard drive was back to front, with the motherboard end plugged into the hard drive and the master end plugged into the motherboard. I should fire the fool who put this togther (me ;). It didn't seem to matter though on windows or Suse, but I thought probably best change that round. But unfortunately no luck.

The next thing I noticed when reading through the motherboard manuals (available below) was that the motherboard only has two IDE channels. Which seemed a bit odd as I've got four IDE cables plugged into my board. I then saw something about it having two GigaRaid controllers, and sure enough the two devices not working are plugged into the GigaRaid Controllers on the motherboard.
[http://tw.giga-byte.com/Support/Motherboard/Manual_Model.aspx?ProductID=1678](http://tw.giga-byte.com/Support/Motherboard/Manual_Model.aspx?ProductID=1678)

So I'm guessing that's why those devices are not working, because they are plugged into GigaRaid controllers not IDE channels. One solution to this would be to remove hdc and hdd as my DVD/CD rewriteable drive covers all thier functionality in one drive. I could then use one IDE channel for a hard drive and the CD/DVD RW, and the other for a just a hard drive. But if I'm honest I don't really want to do that. Over the years I've paid for these drives I want to use them all, sometimes they come in handy such as you need two cd drives to copy from one cd directly to another. I also like having each drive as a solitary master on an IDE cable if I can, as I suspect it allows for faster transfer of data, than having the IDE cable shared between master and slave (although that may not necessarily be accurate). Furthermore I know it is not impossible under linux as it worked with Suse 10.0.

So I hope that information helped, any ideas on how get these guys working?

thanks for all your help,
David

---

### Post by Davyp on 2006-02-10
Lord Bug was right I had a missing driver for one of my IDE controllers, the IT8212 driver to be precise.

I followed the guidelines in the excellent post below and all devices are now fully functional.

[http://ubuntuforums.org/showthread.php?t=106285](http://ubuntuforums.org/showthread.php?t=106285)

thanks for your help all :)

---

