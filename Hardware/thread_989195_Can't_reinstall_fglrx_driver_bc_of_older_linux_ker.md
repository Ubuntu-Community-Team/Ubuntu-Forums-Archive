---
title: "Can't reinstall fglrx driver b/c of older linux kernel"
date: 2008-11-21
forum: Hardware
---

### Post by FunkeyMonk on 2008-11-21
I'm running 8.10 Intrepid on a Toshiba M115, with an ATI Radeon 200M.
I can't run the latest Linux kernel, (2.6.27-7-generic) because it hangs at boot.

So I run the older (2.6.24-21-generic) kernel just fine.

Yesterday, I decided to turn on the proprietary driver for my video card, to see if it would make Compiz work.   It installed fine (I think) and I rebooted.   I found that the proprietary driver actually made things much slower on my card, so I went back to the Hardware manager and turned off the proprietary driver.

When I rebooted, I had nothing displayed but a garbled mess.  I have to reboot in Recovery Mode to get to a command line.

I've tried to reinstall my drivers using these instructions:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and the command 
```
sudo apt-get install xorg-driver-fglrx
```

but it fails to install, giving me this message:
> Error!  Your kernel source for kernel 2.6.24-21-generic cannot be found at /lib/modules/2.6.24-21-generic/build or /lib/modules/2.6.24-21-generic/source.  
Installing initial module

Error!  Could not locate fglrx.ko for module fglrx in the DKMS tree.  You must run a dkms build for kernel 2.6.24-21-generic (i686) first.
Done.

So... any help?  It looks like the fglrx driver no longer has a build for the 24-21-generic Linux kernel, so I'd need to build one, but I have absolutely no idea how.

---

### Post by jocko on 2008-11-21
To install fglrx on your old kernel, you can to build it yourself from [these]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually") instructions, provided you have the kernel source or headers properly configured. However, as you say you were not happy with the proprietary driver (= fglrx), why are you trying to install "xorg-driver-fglrx"? That's the driver you wanted to get rid of in the first place...

---

### Post by FunkeyMonk on 2008-11-21
> **jocko said:**
> To install fglrx on your old kernel, you can to build it yourself from [these]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually") instructions, provided you have the kernel source or headers properly configured. However, as you say you were not happy with the proprietary driver (= fglrx), why are you trying to install "xorg-driver-fglrx"? That's the driver you wanted to get rid of in the first place...

Actually, I'm trying to get ANY driver installed.   It seems like fglrx ununstalled the open-source driver when I turned it on.

I can't get anything to display, and reconfiguring xorg a dozen times hasn't helped.

---

