---
title: "Tried to Reformat Hard Drive and now system wont mount it"
date: 2011-12-13
forum: Hardware
---

### Post by typos1 on 2011-12-13
I used Disk Utility to reformat a fairly new hard drive and now it wont mount and doesnt show up if I do lsusb in a terminal, even though you can hear the drive spinning and the light is on.

It gave an error when I first tried, saying that the drive was mounted, so I unmounted it and tried again, but didnt work and when I unplugged it and re-plugged it in it wouldnt mount.

---

### Post by Dlambert on 2011-12-13
> **typos1 said:**
> I used Disk Utility to reformat a fairly new hard drive and now it wont mount and doesnt show up if I do lsusb in a terminal, even though you can hear the drive spinning and the light is on.

It gave an error when I first tried, saying that the drive was mounted, so I unmounted it and tried again, but didnt work and when I unplugged it and re-plugged it in it wouldnt mount.

Maybe you formatted it as an unreadable format in Linux, Try reformatting it. as FAT32, FAT3, or EXT4

---

### Post by typos1 on 2011-12-13
It was formated in FAT32, I was trying to reformat it in FAT32, but I cant format it in anything now as its not recognised when I plug it in, thats the main reason I started this thread.

---

### Post by papibe on 2011-12-13
Sometimes if you reboot with the drive on and connected, it increases the chances of the drive being recognized.

Just a thought.
Regards.

---

### Post by typos1 on 2011-12-14
Thanks, thats an improvement-now it shows up when I do lsusb, but I cant get it to mount.

I ve tried force mounting it but I get the following error :

"$ sudo mount -t vfat /dev/sdb1 /media/external1 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

dmesg just gives me masses of text and numbers which I cant really understand.

Tried doing the method for ntfs but that also gives an error ("$ sudo mount -t ntfs-3g /dev/sdb1 /media/external1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?")

Something is wrong somewhere, any more ideas ? Thanks

---

### Post by Mark Phelps on 2011-12-14
Since you're interested in formatting is using a Windows-compatible filesystem, I would suggest NTFS instead of FAT32.

What you could try is downloading and burning the CD image for Partition Wizard Boot CD. That's a free Windows app -- and it might do better recognizing and formatting the drive.  Also, I believe that it has an option for repairing existing partitions.

---

### Post by typos1 on 2011-12-14
My pc is formatted in ext4, my external hard drives are formatted in FAT32 to allow as many devices I plug them into as possible to read them and neither ext4 or NTFS are good for that.

The drive has worked fine for 2 years, it just went a bit funny after I tried to reformat it. 

I havent used XP for years and it ll probably take that long to install all the updates that will be waiting should I boot up from it! 

And anyway I ve always had more success formatting and partitioning using Ubuntu, not Windows.

Its an external hard drive I m trying to mount via USB.

---

### Post by typos1 on 2011-12-14
Had a look in system settings/removable devices and its recognised in there, but for some reason Nautilus wont recognise it.

---

### Post by typhoon_tip on 2011-12-14
Is it a 2.5" Hard Drive, in a common box connected, with a single USB cable ? If so, I have had a similar problem to yours. Always worked fine till I attempted a format, which failed miserably and rendered the HD impossible to use.

After attempting everything I could, I have connected the drive to an external power supply, and it worked immediately... Don't ask me why is that. It seems that power was just barely enough to make it work in the past, but it did not work anymore after it got a bit "older"...

---

### Post by typos1 on 2011-12-15
I see, thanks, strange that its only afer attempting to reformat it that it hapened, I ll try extra power and see . . .

---

### Post by typos1 on 2011-12-15
. . . no that doesnt work-its still listed as a usb device but Nautilus wont recognise it.

---

### Post by typos1 on 2011-12-15
After trying various other things and not finding out why Nautilus didnt recognise it, but it was showing up after typing "lsusb" in a terminal, I went back into disk utility, which thankfully still recognised it, so attempted to reformat it again and . .  success ! Formatting worked and now it auto mounts and Nautilus recognises it again !

---

### Post by skeltonh on 2011-12-17
A number of USB disk drives require additional power.  Usually in the form of a two headed USB cable.  I had the same problem and found that I had to use my two headed USB cable to get it to format and perform other tasks.  I can plug it into my main USB port without a need of a cable, but when I plug it into the USB port that has my card readers in it, requires additional power.

One other issue I have had is the formatting for FAT32.  Somehow Ubuntu does not format the USB drive correctly.  I had to let "create startup disk" create it then delete the files in it.  There is a utility that will correctly format/reformat a USB hard disk but I don't have the references off hand.

As for the type of format - FAT32 is the most universal.  NTFS may not be recognized on a number of machine.

If the drive is going to be exclusive to Linux, you could go with one of the more fault tolerant file systems.

Just though I'd share my experiences with this.

---

