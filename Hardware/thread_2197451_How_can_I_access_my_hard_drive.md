---
title: "How can I access my hard drive?"
date: 2014-01-03
forum: Hardware
---

### Post by diricos77 on 2014-01-03
First off, when I try to start my laptop, it fails to start up Windows 7 after the HP logo screen. So I decided to boot Ubuntu from a disc so I could backup my files, however, when I go to Computer and try to access my hard drive after Ubuntu has started up, I get the following error:

> Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: The remote application did not send  reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

From my understanding, I need to use commands in Ubuntu to be able to access my hard drive again, and if anyone could walk me through that you'd have my endless gratitude.

I apologize if this might be in the wrong location, and I'd be happy to provide any additional information you may need. Thanks!

---

### Post by varunendra on 2014-01-04
Welcome to the forums diricos77 !

Your thread is in a perfect place and you have provided a good description of the problem.

Commands are rarely necessary in **Ubuntu** (or most of its variants/derivatives) and something like accessing windows partitions absolutely doesn't need it. Just clicking on the drive's icon on the left pane should automatically mount it and open it for you.

The error message is an indication of some unusual problem - either in the hardware (hard disk or its partitions) or software (Ubuntu itself).

The live cd of Ubuntu has "GParted" installed on it. Can you post its screenshot showing your hard disk?
Or the command outputs of -
```
sudo parted -l
```

And are you using default Ubuntu (not Xubuntu or Lubuntu etc.)?

---

### Post by diricos77 on 2014-01-31
Very sorry for the late reply. I haven't had the opportunity to set that laptop back up until now.

Unfortunately, clicking the drive's icon doesn't mount or open it.

I can't post a screenshot (unless I physically take a picture of the screen), but I entered the command and received this output:

```
Model: ATA ST9320325AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  308GB  308GB   primary  ntfs         boot
 2      308GB   320GB  11.7GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

ubuntu@ubuntu:~$
```

This is default Ubuntu as far as I can tell. I still have the original ISO that I made the live disc from, and it says 11.10 in its file name. Perhaps that its version?

---

### Post by varunendra on 2014-02-01
> **diricos77 said:**
> and it says 11.10 in its file name. Perhaps that its version?

Yes, and it's an outdated version, no more supported : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I'm not very sure, but the error message may be due to a corrupt ISO or disc. There is also a possibility that the hard disk has succumbed to some physical/logical errors and is unable to function properly, also a reason why Windows failed to boot.

Suggestions are :

[INDENT]1) Check the integrity of the ISO that you used to burn the optical disc : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) If the above test is successful, boot from the CD, press 'Shift' (or 'Esc' on some systems) to get [advanced boot menu]("https://help.ubuntu.com/community/BootOptions"), and select the "Check disk for defects" option.

3) If both the above checks are successful, try installing "Testdisk" program on the live session. While being connected to internet -
```
sudo apt-get update
sudo apt-get install testdisk
```
..Since your version of Ubuntu is no more supported, the related repositories may have been moved. If so, you may not be able to install it normally. So if there are errors in installing, it would be better to simply use some System Recovery disc that already has such tools, like [SystemRescueCD]("http://www.sysresccd.org/Download") or [HBCD]("http://www.hirensbootcd.org/download/").

4) If any of the integrity tests fail, download a supported version, burn a cd or create a live usb from it, boot and try accessing the partitions from it. It is highly recommended to download the ISOs using official torrents to ensure integrity of the ISO as well as a faster download.

Links to official torrents can be found here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)[/INDENT]

---

### Post by diricos77 on 2014-02-03
Ok, many things to report:

I went to the link you supplied, and followed the instructions under **MD5SUM on Linux**. However, even the first step is unclear for someone who isn't too familiar with Ubuntu. It asks "[COLOR=#333333][FONT=Ubuntu]First open a terminal and go to the correct directory to check a downloaded [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]iso[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] file" - I can open the terminal of course, but they exclude how to go to the correct directory. I assume it is for that reason that when I tried the commands afterwards I got inconclusive results. Nevertheless, I doubt that the integrity of my ISO is at the heart of the problem.

As you predicted, attempting to install **Testdisk** failed to work. I burnt a new copy of Ubuntu - 12.04.3 - but encountered significant trouble just trying to boot it up. I selected "Try Ubuntu" as usual, but the screen that followed asked for a login, but more importantly looked very "buggy" as in it appeared to have graphical pieces misplaced throughout the screen and random letters strewn across the top. Furthermore, it would let me connect my laptop to my TV via HMDI which I've been doing successfully with 11.10 (I've been doing this because the backlight on my laptop is dead, which leaves only ~5% of the display working).

So, because 12.04.3 isn't working for me, I can't get **Testdisk** there either. If that is crucial to the recovery process, I could try to burn 13.10 and see how that works out. In my own dealings, I'm quite certain that this whole problem stems from a damaged or corrupted hard drive. I've heard about forcing a mount and accessing it that way, but none of the resources I've searched have been particularly helpful, especially for someone with my relative inexperience.[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-02-03
diricos77; Hi !

A simi poke in the dusk;
Let's "assume" that the ubuntu install disk is good, and that the problem is graphics related. Now not knowing what graphics card you are running, a blind poke that might be productive to get ya to a desk top.

Boot the liveDVD, soon as the bios screen clears, depress and hold the left shift key -> language screen; escape key to accept the default; -> Boot options screen-> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Desktop, launcher on left side of the screen -> system Settings -> Additional Drivers -> Install the recommended driver.

All good now ?
OK, now you need a terminal to to finger out how to gain access to the Windows partitions;
Key combo ctl+alt+t will yield a terminal.
Now comply with the above request for terminal command outputs.
And/or download and install "testdisk" to see what it might be able to do to recover the Windows data (gotta have an external drive as large or larger than what you are working on ).

[INDENT][INDENT]piece of cake 
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2014-02-03
Since it's Win7 that is not working, you could also try doing a windows repair.  You need a Repair CD to do that -- which you could have made for free when Win7 was working OK.  But now that it's not, you will have to "purchase" the ISO image from the source in the link, download the ISO file to a PC and use a CD burning app to create a Repair CD:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

A free CD burning app for Windows is ImageBurn -- which you can download and install from their website.

---

### Post by varunendra on 2014-02-04
> **diricos77 said:**
> So, because 12.04.3 isn't working for me, I can't get **Testdisk** there either. If that is crucial to the recovery process, I could try to burn 13.10 and see how that works out.

You can use one of those CDs that I gave links of - HBCD or SystemRescueCD. Both of them are bootable system repair/maintenance discs and both have testdisk already installed on them.

Or, if 11.10 is working fine for you and you wish to install testdisk on it (would save you hassle of downloading a whole new ISO), just change the address of software sources -
```
sudo sed -i 's|archive.ubuntu|old-releases.ubuntu|' /etc/apt/sources.list
```
Then do -
```
sudo apt-get update
sudo apt-get install testdisk
```

You should be able to install testdisk this time.

The "nomodeset" option that Bashing-om mentioned is mentioned in detail here, along with several other boot options that you may try - [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you are interested in repairing Windows (assuming the hard disk partitions and the data on them are intact), you should also consider what Mark suggested.

---

