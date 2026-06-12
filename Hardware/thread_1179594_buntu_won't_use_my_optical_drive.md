---
title: "*buntu won't use my optical drive"
date: 2009-06-05
forum: Hardware
---

### Post by negativ on 2009-06-05
I have a Dell Inspiron 8200 laptop, and when running any variant of Ubuntu 8.10 or 9.04, the system detects the optical drive but insists that there is no media in the drive.  Any attempt to access the drive at all, even to eject it, results in "Unable to mount media - There is probably no media in the drive."

I am pretty sure this is something specific to Ubuntu, because it works fine with WinXP (currently dual-booting).  It also worked fine with Fedora 9, which is what I had on it before I installed Ubuntu Intrepid.

hwinfo detects:
```
40: SCSI 01.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_CDRW_DVD_SN_324B
  Unique ID: KD9E.rXgP8cnoGhD
  Parent ID: 3p2J.wlEL3EhKcSD
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:1:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
  Hardware Class: cdrom
  Model: "SAMSUNG CDRW/DVD SN-324B"
  Vendor: "SAMSUNG"
```

which is correct, as far as I can tell.

Any help figuring this out would be extremely appreciated.

---

### Post by migs73 on 2009-06-10
I am having the same problem with my Dell inspiron 1501 laptop cd/dvd drive. Drive appearing but unable to mount it. Also I am dual booting with Vista and it works fine there.

---

### Post by migs73 on 2009-06-22
I have now got a clean install of Jaunty on my machine. 
I am now able to mount the drive and the disc name is displayed, but I cannot see any of the files on the disc. Have only tried with a data disc (on a DL/DVD)so far. Will try with a CD, DVD etc later.

---

### Post by migs73 on 2009-06-22
I have now tested other types of disc and have the following results;

Music CD; No problems. Mounted and all tracks available:)
Data DVD+R; Not mounting:(
Data DVD+R Dual Layer; Mounting but not able to read data (disc name being displayed):(
Video DVD-RW: Mounting and data available. Stutters/stops in movie player and no audio (mp4 codec problem I think).:(
Video DVD; Mounting and data visible but won't play in Movie Player as I 'don't have permission to open file'!!:confused::confused:

I am wondering if I download the Dellbuntu distro if it will help if this is some sort of driver problem??

---

### Post by negativ on 2009-06-24
I am still having the problem.  Unlike migs73, I can't get any media mounted.  Grr!!

---

### Post by migs73 on 2009-07-02
Negativ, when I said I was dual booting with Vista, that was only half the story as it was using the Wubi version of ubuntu. Don't know if this had any effect on the outcome, but certainly now I am only booting with ubuntu the results are better, if just as frustrating. I don't want try Dellbuntu as I think it is only really for the PC's they bundle with Linux and that is not the case with the model I have.

---

### Post by migs73 on 2009-07-17
I am almost there. After following the howto on this ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)) sticky in the media section, I now have everything except the DVD+R DL data. Still getting the disc name displayed and it recognises disc type and size, but says disc is empty.

---

### Post by migs73 on 2009-11-01
Now got 9.10 but still the same. Surely someone out there must have a solution for this problem on dell laptops!?!!?!

---

### Post by migs73 on 2010-04-30
Still same problem with 10.04!!
I am glad I don't use many DL disks

---

