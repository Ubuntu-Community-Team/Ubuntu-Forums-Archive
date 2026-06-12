---
title: "USB/IDE bridge : Sabrent"
date: 2009-12-06
forum: Hardware
---

### Post by twjolson on 2009-12-06
I have a Sabrent Model : USB-DSC5 USB to IDE bridge that isn't working.  When I plug the hard drive in, the platters will spin up, and not stop, and ubuntu will see the disk (/dev/sdc, for instance), but won't mount (automatically or by command) and won't recognize the partitions (via `ls` or within gparted or anything else)

I don't know what to do.  I got it to work before, but ever since then, it won't recognize any hard drives, and I've tried several.

Either the bridge is junk, or I am missing something to get it to work.  Any ideas?

---

### Post by lindsay7 on 2009-12-06
Have looked for software for the device to load drivers?

---

### Post by twjolson on 2009-12-06
It doesn't require drivers, for windows, linux, or mac.  Sabrents website, the waste of hard drive space that it is, doesn't have any drivers listed, or any meaningful support either.

Any other ideas?

---

### Post by lindsay7 on 2009-12-06
try hooking up the drive and then go to the web site of the hard drive manufacturer.  look for a tool, sometimes in the warranty section, on testing the drive.

---

### Post by twjolson on 2009-12-07
Nope, nothing.  Their site is quite bare.  I haven't even found a phone number yet.  I did email them, but haven't heard anything back yet.
 
> **lindsay7 said:**
> try hooking up the drive and then go to the web site of the hard drive manufacturer. look for a tool, sometimes in the warranty section, on testing the drive.

---

### Post by beefcurry on 2010-07-25
I believe all USB IDE bridges are not working in Ubuntu 10.04. I am not sure if it worked in previous ubuntu versions as I havn't used my old 2.5" disc for years, but when I needed to use it, with 3 different USB/IDE bridges I get the same symptoms as you described.

Getting desperate I tried everything, even resorting to VM windows. Apparently the solution was ridiculously easy. Remove the bumper to set the drive to Device0, then it just mounts automatically viola.

I have no idea why, or how that made it work, but I just know it worked for my ide-usb when dealing with a 2.5" Fujitsu 60GB device.

Hope this helps someone.

---

### Post by hgraca on 2010-12-14
Hey guys, did you find a solution for this?

I'm having the same issue, with a fugitsu MHT2080AT 80Gb.

There is no jumper in the HD so it's already in "device 0" mode and I cant try other configuration.

tkx for any help.

---

