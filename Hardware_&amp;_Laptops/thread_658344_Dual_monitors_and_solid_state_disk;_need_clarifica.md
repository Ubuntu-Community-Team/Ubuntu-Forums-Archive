---
title: "Dual monitors and solid state disk; need clarification."
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Opeth on 2008-01-04
Okay, before I buy a second monitor and an SSD, I need to know something for sure.


With the monitor, can I have two separate desktops so that I can play WoW full screen and have my browser on my right monitor?

With the SSD, would I be able to put Ubuntu on it and have all of my files on a separate hard drive? Would I have to access a different drive everytime I wanted to create/delete/edit/view a file? Is it worth the extra boot up seconds for a little bit of a hassle?


Thanks.

---

### Post by pjkoczan on 2008-01-04
> **Opeth said:**
> With the monitor, can I have two separate desktops so that I can play WoW full screen and have my browser on my right monitor?

Yeah, you just need to make sure that xorg.conf or whatever screen configurator you use knows that it's two separate monitors instead of one very large wide monitor. Here's how it is on my computer (with Nvidia hardware, you should change things as appropriate):

Section "Device"
    Identifier "Nvidia GLX"
    VendorName "Various"
    BoardName "NVidia chipsets with hardware go-fasters"
    driver "nvidia"
    Option "TwinView"
    Option "SecondMonitorHorizSync" "30 - 121"
    Option "SecondMonitorVertRefresh" "50 - 180"
    Option "MetaModes" "1600x1200,1600x1200"
EndSection

If you're going to play WoW on Windows, I'm sure there's a way to do it in there as well, but I don't know it offhand.

> With the SSD, would I be able to put Ubuntu on it and have all of my files on a separate hard drive? Would I have to access a different drive everytime I wanted to create/delete/edit/view a file? Is it worth the extra boot up seconds for a little bit of a hassle?

As long as the SSD is big enough to hold a full installation, there's no reason you can't do that.

I'm guessing that you want your home directory on the non-SSD drive. You'll just have to make sure to mount the different drive before using it (and put an entry in /etc/fstab so it will be mounted on bootup). The rest is very transparent and taken care of by Linux, so you don't have to do anything outside of the fstab entry. I do this on my box (80 GB HD is the OS, 250 GB HD is /home) and it works very well.

As far as performance goes, it will only add a fraction of a second to the bootup since mounting a filesystem takes very little time. In normal usage, it will likely be faster than everything on a single drive since the disk doesn't have to continually switch access between the program files and your data files.

There are lots of benefits to doing this. If Ubuntu installs on your SSD, there's no reason you shouldn't do this.

---

### Post by Opeth on 2008-01-05
Thanks!

---

### Post by fwendt on 2008-02-08
I'm currently running the entire system on a single SSD 32 GB Transcend device (four partitions, /boot, /, /home and a small swap) and my aproach was to block-copy (using gparted) the filesystems onto this SSD disk. It works. Most of the time there's no difference from how the system behaved earlier, but under average io-load (starting several apps at the same time - think Open Office, pidgin, evolution and firefox) there are long waiting times. From what I can tell it all has to do with the filesystem and it's priority model of io commands.
I've yet to try JFFS2 (trying to find tools from/for Ubuntu) and see if it helps, cause it's starting to become too annoying.

---

