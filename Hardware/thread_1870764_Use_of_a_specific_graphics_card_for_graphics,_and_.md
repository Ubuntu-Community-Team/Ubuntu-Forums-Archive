---
title: "Use of a specific graphics card for graphics, and using another as a block device"
date: 2011-10-27
forum: Hardware
---

### Post by jebler on 2011-10-27
I received a Radeon HD 6790 1GB 256-bit GDDR5 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814150564](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150564) for use in my work computer. I couldn't get a stable system, X would hang randomly 10minutes-2hours after boot. After trying various solutions (but stopping short of disabling acceleration) and losing time restarting and re-setting up my environment I just pulled the card out. The integrated graphics on my mother board are good enough to get a 3D accelerated window manager -- and that's all I really need from a graphics card as a web developer. I lost the packaging and docs, so I can't return the card.

I was hoping to mount the card's RAM as a 1GB SSD-like drive to reduce latency for a new frequently used files. I've sucessfully used a variant of the procedure [http://en.gentoo-wiki.com/wiki/Using_Graphics_Card_Memory_as_Swap](http://en.gentoo-wiki.com/wiki/Using_Graphics_Card_Memory_as_Swap) to achieve this on my hope computer. I plan to use a RAID mirror with a 1GB loop-mounted filesystem to help persist writes to the faux-SSD across reboots. Cool, huh?

My question is:
Both my (bad) graphics card and my motherboard use the fglrx driver. How can I make sure that the system only used the motherboard's graphics card for graphics, and doesn't write to the bad card's memory (and corrupt my filesystem).

I'm aware of the possibility that it may be impossible to stop the card from writing to the first few MB of graphics ram, but with 1GB I figure I should be able to get 99% untouched.

I haven't reinserted the card just yet, but my mobo card identifies as:
```
$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
```

xorg.conf
```
Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection
```

I suspect I'll need to configure the kernel module somehow so it doesn't load for the bad card. I believe I should make a: /etc/modprobe.d/fglrx.conf but I'm not sure what to put inside it. Do I need to blacklist the module for a certain PCI address, or tell the module to only load for a certain PCI address (whitelist). I would RTFM, but I'm not sure where TFM is.

Thanks!

---

### Post by jmate24 on 2011-10-27
the 6790 does not readily work with ubuntu only the 5670 and lower plus you have to uninstall the ubuntu fglrx drivers and fglrx xorg drivers before you install the graphics card or else it won't work because there is a file in /etc/mopdprobe.d/ that blacklists the latest fglrx drivers from being installed. so once you uninstall it delete any blacklist-fglrx.conf files that you find.  if you were to get the latest driver for that video card i would suggest going to [http://http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

then opening a terminal and typing: 
```
cd ~/Downloads && sudo chmod -x ati-driver-installer-11-9-x86.x86_64.run && sudo sh ati-driver-installer-11-9-x86.x86_64.run 
```

and follow the instructions to install it directly for oneric. then you will have to go to:
[http://http://www.splitted-desktop.com/static/libva/xvba-video/]("http://http://www.splitted-desktop.com/static/libva/xvba-video/") 
and download xvba-video_0.8.0-1_amd64.deb if you are running x64 but if you are running x86 then download the one above this one.

then install it.

---

