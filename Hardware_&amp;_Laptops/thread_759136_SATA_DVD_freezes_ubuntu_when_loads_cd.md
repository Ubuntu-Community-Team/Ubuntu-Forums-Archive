---
title: "SATA DVD freezes ubuntu when loads cd"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by daniel,yokomizo on 2008-04-18
I trying to configure a new machine with kubuntu 8.04 (amd64). My hardware setup is:

motherboard: Asus M2N-SLI
processor: AMD Phenom 9500
hd: Western Digital 500gb sata2
dvd/cdrw: LG DVDRAM GH20NS10 sata2
ram: 2x2gb supertalent ddr2 667
video: NVidia GeForce 8400GS

I tried all day to install with this setup, first the usual cd, then the alternate and finally the 7.1 alternate cd. Everything failed. In the end I found that I couldn't mount the cd on the alternate instalation process (i.e. mount -t iso9660 -o ro /dev/scd0 /cdrom/ failed with Invalid Arguments). I checked the CD and it was ok, so I figured out it was some weird issue in the instalation with the optical drive. I attached another optical drive (IDE) and installed from it flawlessly. So far so good.

After the installation was done I booted the computer and log on, and tried to read a cd using the sata drive. I placed the disc in the tray, pressed load/eject, the disc went in and ubuntu froze. It didn't matter what I tried to do, couldn't reset X, nothing but a hard reset worked. I tried to search for this issue but my google-fu isn't strong enough apparently, so I decided to ask for your wisdom.

I've been a happy user of kubuntu for the past six months (on my laptop) and of debian-based distributions (on the old box) for a couple of years now, but this error is baffling me. I have no idea if this is an issue with 8.04 (it doesn't seem to, because 7.1 also could't install from the cd), with amd64 build, with sata optical drives or with this particular drive. [This post]("http://ubuntuforums.org/showpost.php?p=4270075&postcount=172") indicates that the drive can be used with 32 bit Ubuntu, but other things may be getting in the way. The firmware was updated today to the last version (in an attempt to fix the install problem), perhaps this is an issue (but I don't think I can downgrade the firmware to test it).

Thanks in advance,
Daniel Yokomizo

---

