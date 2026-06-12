---
title: "Can't Install Ubuntu or Kubuntu Karmic 9.10 NBR"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2009-10-29
I boot Ubuntu NBR 9.10 from the USB Drive, and I get the little flashing Ubuntu logo (Nice BTW), then it goes to a black screen with a wristwatch cursor for my mouse. I can move the mouse around, but it just stays in mouse moving limbo, with a black background, doing nothing. Not even reading off of the USB Drive.

So I decided to download the Kubuntu Netbook Remix, and it hangs on installation with this on the screen.

```
* Starting early crypto disks...
* Starting remaining crypto disks...
* Starting Kernel Oops catching service kerneloops
* Starting Common Unix Printing System: cupsd
* Checking battery state...
...done.
```

Now, I've tried just the Ubuntu i386, and the Kubuntu i386 standard ISO's. Still, it just hangs there.

So my question is, does this have something to do with the way I am trying to install this? Is it a unetbootin problem? Are there any alternative methods for installation?

---

### Post by Nokes on 2009-11-03
i have a different problem, mine boots from the image very nicely and everything works, then when i run the install, after choosing my location it hangs, im using virtualbox

---

### Post by Shibblet on 2009-11-04
My problem was resolved when I booted from a 9.04 USB Drive and formatted the Hard Drive from NTFS (Xp was on it) to EXT4 with Gparted.

Then the Ubuntu NBR installation went off without a hitch.
I don't know if that makes any sense, but that's what it took to make it work.

---

### Post by pantera10 on 2009-11-04
i have this exact same problem...im running ubuntu currently using startx..im afraid to reboot cause i might end up with the same problem and startx may not work..
i saw the xorg.conf fix but i dont need to do tht caus a xorg.conf file alreadt exists...i even edited the grub login file
[daemon]
something something

---

### Post by Shibblet on 2009-11-05
At this point, I think it has something to do with the USB service in Karmic.  

The MSI Wind USB ports stop reading from flash drives.  I was able to get 9.10 installed by installing 9.04 and doing an upgrade.

After the upgrade, I plugged in a USB Stick to transfer some data to the HD.  It was like it wasn't there.  The computer didn't register that there was a USB Stick, and the stick didn't light up at all.

This is a known issue.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/413185]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/413185")

---

