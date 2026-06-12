---
title: "Creating a USB install disk with the &quot;Minimal&quot; CD image."
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by rswoods on 2009-10-15
I don't have any (functional) optical drives on any of my machines and have been doing all my system installing/restoring using USB storage devices.

I'm attempting to make one using the CD image found on this page ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) but I'm not being very successful.  I'm testing it on my Dell Mini 9, which when told to boot from it gives this output:

> Missing operating system.
...
PXE-E61: Media test failure, check cable
PXE-M0F: Existing PXE ROM.

I am using unetbootin.  The same machine boots Linux Mint from USB no problem, so I'm not sure where the weak link in my booting fence is.  Any ideas?

---

### Post by prshah on 2009-10-15
> **rswoods said:**
> 
I am using unetbootin.  The same machine boots Linux Mint from USB no problem, 

You can ignore the PXE messages, they are unrelated to USB booting.

You should probably look at the (extensive) community documentation on how to [install from USB]("https://help.ubuntu.com/community/Installation/FromUSBStick"), specifically [isotostick.sh]("#isotostick.sh%20(Command-line%20shell%20script,%20runs%20from%20Linux)")

A (wired) network install is another option (PXE). A USB install will be better than a network install, but if your computer cannot handle booting from USB devices, then you need [Installation from local net]("https://help.ubuntu.com/community/Installation/LocalNet")

---

### Post by rswoods on 2009-10-16
I've tried the isotostick.sh and got dropped to SYSLINUX with a "boot:" prompt from which nothing could be done. I'm certain this machine can boot from USB because I've done it with two other distros already.

Upon further investigation I noticed this output from the terminal when running the script:

```
rsw@desktop:~/pub$ sudo ./isotostick.sh mini.iso /dev/sdb1
Not verifying image...(no checkisomd5 in Ubuntu so skipping)!
Copying live image to USB stick
cp: cannot stat `/media/cdtmp.YnEURx/README.diskdefines': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/md5sum.txt': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/.disk': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/casper': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/pool': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/dists': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/preseed': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/install': No such file or directory
cp: cannot stat `/media/cdtmp.YnEURx/isolinux/*': No such file or directory
Installing boot loader
mv: cannot stat `/media/usbdev.nNUFbc//isolinux.cfg': No such file or directory
USB stick set up as live image!
```

Looks like some pretty important stuff didn't make it onto the USB.

---
Edit:
I got it to work using the manual install on that page you linked to ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)).  Thanks pal.  Tagging solved...

---

