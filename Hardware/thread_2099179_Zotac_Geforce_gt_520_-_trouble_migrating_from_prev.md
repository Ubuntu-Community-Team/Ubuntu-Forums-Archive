---
title: "Zotac Geforce gt 520 - trouble migrating from previous Nvidia card"
date: 2012-12-28
forum: Hardware
---

### Post by compiz addict on 2012-12-28
I just installed a new graphics card, a Zotac Geforce gt 520 with 1 GB memory. In Hardware Drivers, the Nvidia driver was activated as it was before for my previous Nvidia card. Since Ubuntu kept going in low-graphics mode (and compiz stuff wasn't working etc), I  decided to deactivate it, and reinstall nvidia-current. This didn't accomplish anything, and I'm back where I began still...

Any ideas? :confused:

Btw, I'm running 10.04 right now (and not really all that hyped about upgrading until I have another hard-drive to work with)

---

### Post by compiz addict on 2012-12-28
Upgrading from 10.04 now... this is not going to be a fun night :'(

---

### Post by cwsnyder on 2012-12-28
I can tell you go by the motto in your signature. ;-)

Couldn't you at least have tried with the Live disk before doing the upgrade?  One thing that I have been going over in another thread is that any custom settings for video resolution or refresh rate are probably going to break going from 10.04 to later.  I think 10.04 was about the last release which still supported video resolution changes in /etc/X11/xorg.conf , all later required use of the xrandr command because of changes in X.  That's right, X, so it doesn't matter what your driver had been or that your setup worked in 10.04, it may be broken after the upgrade.

---

### Post by compiz addict on 2012-12-28
Yeah, that likely would have been a good idea (thanks for noting the irony in my signature, lol). The damage is already being done though. Seeing as my graphics don't work properly as it is, it can only get better from here (either that or harder to fix ):). The card is supported by Ubuntu though, so I'm a bit confused that it didn't work... though I might as well be up to date and see what happens.

---

### Post by compiz addict on 2012-12-29
Just upgraded to Ubuntu 12.04. (had to run it overnight) It couldn't have gone worse. I can't get past my boot screen. :'(

---

### Post by cwsnyder on 2012-12-29
As I recall, one of the changes going from 10.04 to 12.04 was a change from **gdm** login manager to **lightdm**.  Also, you might try a Live CD of Xubuntu 12.04, that seems to be a little more forgiving if you have video problems than Ubuntu 12.04.  I can't really recommend Ubuntu 11.10 as an interim, as I recall on the hardware which I tried, 11.10 was even worse than 12.04 to get working properly.

---

### Post by oldfred on 2012-12-29
I think it was from 10.04 to 10.10 that I had to start adding nomodeset to liveCD, flash drive installer, or first boot. Same for upgrades as I have seen. They moved some drivers into the kernel.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
See screen examples in links above.

       On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

