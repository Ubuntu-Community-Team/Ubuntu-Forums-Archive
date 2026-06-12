---
title: "Hard Drive &quot;Shredded&quot;?"
date: 2016-09-21
forum: Hardware
---

### Post by harddrive-killer on 2016-09-21
hello, cool people!

i have no idea what i did but my hard-drive is missing. here's what happened :

i downloaded something and my computer caught a virus. Anti-virus failed, Restoration Point failed. Did research and discovered the only way to save my computer - completely wipe out the hard drive.

found a tutorial on youtube on how to erase hard-drive using DBAN. The process was very slow, ETA +6000 hours! i had to stop the process (restart the computer) because that was ridiculous. it's only a 2T hard-drive.

Did more research and discovered that using Linux Live CD/DVD I can use the "shred" command via Terminal to completely clean the hard-drive, a much faster and just as good as DBAN.

during the tutorial I got confused at what /dev/sdwhatever to shred, for what was happening on the tutor's screen has a lot different than mine. it was my understanding that the commands and their functions across linux platforms were somewhat the same, let it be fedora, mint or ubuntu. so i kept following...

following the tutorial, I typed the "sudo su", enter key, "fdisk -l".

And it gave me a long list of /dev/ram (from 1-16 of them or so) and at the end of the list were /dev/loop0 (which i assumed was my dvd where i had ubuntu burned) and /dev/sda (which i assumed was my hard-drive because it's size stated it was 2 terabyte).

so, i did what the tutor did but accordingly to my own situation : shred -v /dev/sda

the shredding task launched, shred : /dev/sda : pass 1/3 random, 1mb/1.9TB 0%

i left for about 3 hours and when i came back, the computer was still running but the screens were blacked out, moving the mouse didnt wake them up from hybernation.

i thought maybe the shredding already finished, so i restarted the computer.

launched the ubuntu live cd again, booted up the OS.

i enter the "disks" tab to examine my hard drive. 

the disk status was okay BUT there was one bad sector.

i take a look at the drop box, hoping to find what that means, and i see the "format" option.

i was told bad sector means, there is still some data left on the drive somewhere - formatting can fix that.

so i hit "format"...

an error pops up (forgot what it was) and the next thing i know there hard-drive lost it's factory name and all data. i mean, the computer now sees it as "hard drive" and there is no more data about the device. no media, no size, no content and for some reason it turned into /dev/sdb.

and then i noticed there is a "drive", a generic storage device (0.00), no media, no size, no contents and now that thing is /dev/sda.

i attempted to try and install windows again - it BSOD.

i attempted to install the ubuntu - no hard drive found.

the bios sees there is a hard-drive and can still read it's factory name and size though.

what happened? can i still fix my hard-drive?

---

### Post by oldfred on 2016-09-21
Drives must be partitioned before formatting.
A few have formatted a drive, and it becomes a SuperFloppy and many tools do not work as they first want to read partition table.

Is system UEFI or BIOS?
If UEFI you need gpt partitioning. Ubuntu only systems can use gpt with BIOS.
If Windows and hardware is BIOS you must use MBR(msdos) partitioning.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table
[/URL]
 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

              Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php) 
GParted partitioning software - Full tutorial older but still essentially the same
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
    
 If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

