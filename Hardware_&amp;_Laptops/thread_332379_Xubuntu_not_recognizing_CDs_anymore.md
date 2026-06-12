---
title: "Xubuntu not recognizing CDs anymore"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by Pobega on 2007-01-05
Today I downloaded a program for my father using BitTorrent, and I was trying to burn it to a blank CD. For some strange reason the CD wasn't appearing on the desktop, and nor was it mounting!

But then I tried a used CD (Same brand/size), and the drive read it. Next I tried a DVD, but it didn't pick up the DVD. 

Is there something wrong with my system? I'm running Xubuntu 6.10, and I know this all worked perfectly in normal Ubuntu.

---

### Post by tc10b on 2007-01-16
I have a similar problem.
I first noticed it when totem wouldn't play my DVD's said there was no dev/hdc, but xine worked fine so I ignored it.
Now I tried to rip music from an audio CD and it won't read.
The same CD will work under Windows and I even changed my drive, to no avail.

Manually mount through terminal:

tc10b@tc10b-710:~$ sudo mount /media/cdrom0/ -o unhide
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

tc10b@tc10b-710:~$ dmesg | tail
[17183777.776000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183777.776000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17183777.776000] ide: failed opcode was: unknown
[17183777.776000] end_request: I/O error, dev hdc, sector 64
[17183777.776000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17184719.832000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17184719.832000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17184719.832000] ide: failed opcode was: unknown
[17184719.832000] end_request: I/O error, dev hdc, sector 64
[17184719.832000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16



Can anyone help?

---

### Post by tc10b on 2007-01-16
It is very strange as it will read data CD's fine, just not audio CD's. I dunno why

---

### Post by ZAxisMapping on 2007-01-16
Yeah, I'm having the exact same issues as tc10b (though my device is /dev/hda).  Well, clearly I don't understand what is going on with audio CDs in linux.  Why is it that 

```
ls -l /media/cdrom0/
```

shows nothing, but xmms lists all *cda files on /media/cdrom0 (and can play them fine)?  mount gives no indication that /dev/hda is readable.  Manual mounting gives exact same results as tc10b.

(I've gotten EAC installed using crossover office, but it can't see my drive).

---

### Post by robc02 on 2007-01-17
I had the same problem with Xubuntu and solved it by installing Sound Juicer, the Gnome CD extractor. 
I presume that audio CDs are not supported in the basic Xubuntu setup and that you have to add an application to do it. There may be other applications that will do the job; I used Sound Juicer because that is what is installed with Ubuntu.

---

### Post by tc10b on 2007-01-18
I've already got Sound Juicer installed and it doesn't work. I will try reinstalling it.

---

### Post by tc10b on 2007-01-18
I've reinstalled Sound Juicer and all the suggested packages and still no joy. :(

---

### Post by tc10b on 2007-01-19
I've also installed the gnome sound and CD player and it still doesn't work.

Does anyone have any ideas? Cheers.

---

### Post by tc10b on 2007-01-20
Ah. I just changed the values in the fstab file to read auto and now I can read them in SoundJuicer fine. No Icon appears on the desktop though, but I can live with that.

---

### Post by robc02 on 2007-01-20
I'm glad you got it sorted. Just installing Sound Juicer did the trick for me - but I'll remeber your experience with fstab.
If you expect to use Sound Juicer a lot you can easily add a launcher to your toolbar. Just right click on the toolbar and a menu will appear that allows you to add a launcher with whatever icon you want.

---

### Post by Pobega on 2007-01-22
Yeah, I'm messing with it now; It's weird how no icon shows up on the desktop though, but I *guess* I can survive without it. It is kind of annoying though, I wonder what the source of this problem is.

---

