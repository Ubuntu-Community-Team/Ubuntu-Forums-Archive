---
title: "CD Drive Will Not Read Disks"
date: 2014-03-05
forum: Hardware
---

### Post by Kestreln8144 on 2014-03-05
I want to install Lubuntu on an old PC of mine. I've burned a disk, but the CD drive is being fussy.

The drive will spin up, goes pretty fast as you would expect when reading a disk, but then winds down again, as if it has "decided not to read the disk." It does not "struggle" to read the disk, by trying to spin it up again and again. It just stops. (The disk slowly spins down again.)

There are no suspicious noises, like clicking or anything to suggest something wrong with the drive itself.

I've been able to get it to read a disk, but it seems fussy. Windows XP (the currently installed system) managed to open and view the disk contents, but I could not run wubi.exe.


I'm hoping this isn't a hardware issue. This drive has worked fine before, although I haven't used it in a while. What could it be?

---

### Post by phidia on 2014-03-05
Try burning the iso again. You may have a bad burn.

---

### Post by ibjsb4 on 2014-03-05
Wubi seems to be supported for 12.04 LTS (Long Term Support).  Lubuntu does not have a LTS and Lubuntu 12.04 has already reached end of life and no longer supported.

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

[http://meta.askubuntu.com/questions/7497/wubi-discussion-again-supported-here-on-ask-ubuntu-13-04-and-later/7596#7596](http://meta.askubuntu.com/questions/7497/wubi-discussion-again-supported-here-on-ask-ubuntu-13-04-and-later/7596#7596)

Why not install Lubuntu (13.10) on its own partition?

---

### Post by Kestreln8144 on 2014-03-05
> **phidia said:**
> Try burning the iso again. You may have a bad burn.

I checked the disk on my main system and I can access it fine. But I will try burning it again.

> **ibjsb4 said:**
> Why not install Lubuntu (13.10) on its own partition?

That's what I want to do, but the disk drive does not work.

I only mention wubi because I tried to run it when I managed to open the disk on Windows. I wanted to see if I could get it to run. But actually I want to install it side-by-side and dual boot.

---

### Post by ibjsb4 on 2014-03-05
What about installing from flash drive?  Your box needs to be able to boot from usb.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Kestreln8144 on 2014-03-05
> **phidia said:**
> Try burning the iso again. You may have a bad burn.

This did the trick. I guess something went wrong that I wasn't aware of. Strange that I could access the ruined disk though.

Lubuntu is now installed beside Windows. Thank you both for your help. :)

---

