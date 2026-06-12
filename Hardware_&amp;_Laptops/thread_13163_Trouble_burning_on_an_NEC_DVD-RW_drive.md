---
title: "Trouble burning on an NEC DVD-RW drive"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by Sham on 2005-01-29
Hi all,

I'm trying to burn an iso using an NEC DVD+RW 1100A drive. I did the usual right click -> write to disk, but I was prompted to reload the rewritable or blank media. 

I can't burn any type of image, but I can mount prewritten disks OK.

dmesg gives:

```

ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1252, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

```

Any help would be appreciated.

---

### Post by cwaldbieser on 2005-01-29
I am also having problems using Nautilus to burn on my NEC CD RW.  To get around this problem, I have been using xcdroast, which is a really excellent front end for CD Burning in my humble opinion.  When I first set it up, it didn't recognize my NEC right away because it isn't using SCSI drivers.  However, if you hit the rescan button and enter the device name for the drive (/dev/hdd in my case), it is able to detect the drive.  You can then save that config info and not have to worry about it again.

For burning ISOs, sometimes the quickest way is to just use the command line.

For example:
```
sudo cdrecord dev=/dev/hdd driveropts=burnfree ~/ISOs/hoary-live-i386.iso
```

burns a copy of the new Hoary Hedgehog live CD in my ISOs directory.

Hope that helps! 

Carl Waldbieser

---

### Post by Sham on 2005-01-30
[QUOTE=cwaldbieser]I am also having problems using Nautilus to burn on my NEC CD RW.  To get around this problem, I have been using xcdroast, which is a really excellent front end for CD Burning in my humble opinion.  When I first set it up, it didn't recognize my NEC right away because it isn't using SCSI drivers.  However, if you hit the rescan button and enter the device name for the drive (/dev/hdd in my case), it is able to detect the drive.  You can then save that config info and not have to worry about it again.

For burning ISOs, sometimes the quickest way is to just use the command line.

For example:
```
sudo cdrecord dev=/dev/hdd driveropts=burnfree ~/ISOs/hoary-live-i386.iso
```

burns a copy of the new Hoary Hedgehog live CD in my ISOs directory.

Hope that helps! 

Carl Waldbieser[/QUOTE]


That did help. Cheers buddy.

---

### Post by dilmah on 2005-02-13
[QUOTE=Sham]Hi all,

I'm trying to burn an iso using an NEC DVD+RW 1100A drive. I did the usual right click -> write to disk, but I was prompted to reload the rewritable or blank media. 

[/QUOTE]

I also have the exact same problem, I have a NEC DVD_RW ND-3500AG. Burning with cdrecord from the command line as suggested works, but it would be very nice if I could do this using the built-in GUI. Any ideas *why* this doesn't work or if its already been fixed in hoary?  [-o<

---

### Post by sunscape on 2005-02-13
Positive you have the correct media? e.g. dvd-r as opposed to dvd+r?

---

### Post by dilmah on 2005-02-13
Brilliant!

I just thought I'd share my expereiences here since my last post...
I found a [very interesting thread](http://ubuntuforums.org/showthread.php?t=12462) on one of the other forums here regarding alternatives to xcdroast, k3b and the such. One highly recommended one was graveman (ubuntu deb link provided in the above thread). Just installed it and not only does it look great, but I just burnt a shiny new copy of BeatrIX_2005.1F.iso to install on my ancient P200 Laptop (Ubuntu is currently on it but runs pretty slow on only 96mb ram)

Looks like it's some sort of bug with the nautilus-cd-burner package or something.

Ubuntu proves itself again!   \\:D//

dilmah

---

### Post by dilmah on 2005-02-13
[QUOTE=sunscape]Positive you have the correct media? e.g. dvd-r as opposed to dvd+r?[/QUOTE]

Thanks for your reply,

I'm not 100% sure about the others, but I'm pretty sure they were just trying to burn a CD-R ISO on their DVD writer.

dilmah

---

### Post by Windsurf1990 on 2007-08-12
> **dilmah said:**
> Brilliant!

I just thought I'd share my expereiences here since my last post...
I found a [very interesting thread](http://ubuntuforums.org/showthread.php?t=12462) on one of the other forums here regarding alternatives to xcdroast, k3b and the such. One highly recommended one was graveman (ubuntu deb link provided in the above thread). Just installed it and not only does it look great, but I just burnt a shiny new copy of BeatrIX_2005.1F.iso to install on my ancient P200 Laptop (Ubuntu is currently on it but runs pretty slow on only 96mb ram)

Looks like it's some sort of bug with the nautilus-cd-burner package or something.

Ubuntu proves itself again!   \\:D//

dilmah


Thank you Dilmah for your post. I too have tried Graveman, and it is a very nice working GUI for DVD/CD burning. I once used k3b on SUSE running on the KDE desktop. I've since switched to Ubuntu and more specifically Gnome. Gravman is a nice replacement and does seem to work.

I too was having the same experience with the Nautilus-Cd Burner package.  Thanks again for your fine suggestion.

---

