---
title: "Solve External USB Drive Woes"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by helfrez on 2007-11-12
Tired of playing hopscotch with external usb drives formated NTFS? Decided to share this tidbit after helping a few people fix ntfs mounting problems....DON'T USE NTFS. Format your drives with ext3. Install the Ext3 driver for Windows ([http://www.fs-driver.org](http://www.fs-driver.org)) and all write your worries away. I have been doing this for quite some time with no corruption or loss of data.

TIP: To get auto-mounting to work across operating systems. Use fdisk to change the partition type to 7 for NTFS. If the ext3 driver is install, Windows will happily mount the drive and give it a letter as if it was a regular ntfs partition. Linux doesn't care what the drive type says, and automount will pick it up as ext3 when its accessed! USB Drive Bliss is but a  step away. =D>

---

### Post by avik on 2007-11-12
Better yet, don't use windows. :p

Okay, so that may not be an option.  Too bad the Ext3 driver only works on x86 processors.  I'm using a 64 bit processor, so it's a no go.  Of course, I only considered it for a couple of days when I wanted to fix an issue with an old hard drive after buying a new computer.  After that, it was out with Windows!

---

### Post by Rhubarb on 2007-11-12
> **avik said:**
> Better yet, don't use windows. :p

Okay, so that may not be an option.  Too bad the Ext3 driver only works on x86 processors.  I'm using a 64 bit processor, so it's a no go.  Of course, I only considered it for a couple of days when I wanted to fix an issue with an old hard drive after buying a new computer.  After that, it was out with Windows!

64bit windows will not work with the ext3 driver, but if you've got a 64bit processor running 32bit windows, then the ext3 driver will work fine in windows.
Indeed, if you can, just don't use windows.  :)

---

### Post by helfrez on 2007-11-12
I have a work laptop I have to go between, so for now I'm stuck with it. Unless you are trying to run 64bit windows, I would think it should still work because most consumer chips do x86 and 64, so I am not sure where the hangup is?

Edit:What Rhubarb said lol..

Even scarier that why are you running windows, is why are you running 64bit windows, that's a real glutton for punishment!

---

### Post by avik on 2007-11-12
> **helfrez said:**
> Even scarier that why are you running windows, is why are you running 64bit windows, that's a real glutton for punishment!

64 bit Windows came preinstalled.  As soon as I got the sound and networking problems fixed (I was using Edgy at the time, and it wasn't until Fiesty that those components worked out of the box), I got rid of Windows.

---

