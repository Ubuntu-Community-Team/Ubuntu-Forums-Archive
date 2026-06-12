---
title: "usb card reader and devices - Ubuntu 14"
date: 2014-07-17
forum: Hardware
---

### Post by rich-andrews on 2014-07-17
I have two nearly identical Dell 690 servers running Ubuntu 14 and both are equipped with a Dell all-in-one card reader.

The first computer assigns the card reader /dev/sdX device names after it has assigned the hard drive names.  That means that HD0 == /dev/sda == first Sata hard drive, etc.  Then the USB card reader devices are assigned (/dev/sde, /dev/sdf, etc.)

THe second machine does things backwards...mostly.  It assigns the card reader devices first (sda, sdb, etc) then the hard drives.  Every now and then it will get things right and it will assign the USB devices last.

I have looked at a few things to determine what is really different between the two machines.  I am at a loss.

Both machines are running the same version of the BIOS.

So my question is this:  Is there some way that I can tell the second machine to be like the first - meaning to map the SATA drives first and then  the USB drives?

---

### Post by rich-andrews on 2014-07-17
In thinking about this some more, I think that USB card readers  should be named something other than /dev/sdX.  How this would impact booting from USB cards is a mystery.

---

