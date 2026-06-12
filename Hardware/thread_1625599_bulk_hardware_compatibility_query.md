---
title: "bulk hardware compatibility query"
date: 2010-11-19
forum: Hardware
---

### Post by HappyLinux on 2010-11-19
Hello folks, I am a returning Linux user, but I'm no pro. Somewhere between beginner and intermediate - more towards intermediate. I also have another account on this forum by the name of "AuronGrande", but because I have not used the account for some time, I cannot remember the login details, so I have happily created this new account.

I could not use Linux on my current system due to many hardware incompatibilities, but now I need a complete new system, so to speak.

So I need to know if the new hardware is completely compatible straight out the box, or requires little system configuration, e.g. modifying some settings via the terminal, etc.

The system that I have my eye on is the "Mesh Elite Pro 550" from meshcomputers.com. However, I chose a couple of custom options - bigger PSU, nVidia graphics and larger HDD. Going from the website, talking to one of their sales people and from some hardware that will be carried over from the old system, I have a complete list of hardware to be checked.

New hardware
Asus P7H55-M.
Intel Core i3 550.
Elixir 4GB 1333MHz memory.
Asus 1GB nVidia GeForce GTS450 with CUDA.
1TB Samsung Pinpoint F3 SATA 32MB cache.
Staying with the on-board sound.
Samsung Write Master 22X Dual Layer DVD rewriter. (not sure on model.)
Windows 7 Premium 64bit

Hardware reuse from previous system.
Samsung 19" monitor (not sure on the model, but comes up generic PnP under MS Windows Vista)
Microsoft Natural Ergonomic 4000 keyboard
Logitech MX400 M-BZ105A mouse
Canon iP4700 printer
Creative 5.1 speakers
2 USB HDDs

I have previously tried to do a hardware compatibility check, but found very little info. Some hardware could not be found, other were very rare and had little info.

I know that some of this list would be compatible straight out the box so to speak - both USB HDDs and the mouse.

Upon finding about the motherboard, it came up with and Asus board and some brands of memory having compatibility issues in Linux, which were usually solved with BIOS updates.

I chose the nVidia card because nVidia is more compatible than ATi.

As for the rest of the hardware, please help.

Oh yes, before I forget, I would like to dual-boot between Windows 7 Premium 64bit and either Ubuntu 64bit or Fedora 64bit.

Thanks in advance.

---

### Post by dino99 on 2010-11-19
welcome back :)

i think you loose too much time wondering about your hardware, take installation on and then we tweak it if you find some issue, but you might not with the latest release.

to remind you (only):

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

**** for more recent info, follow the links below

---

### Post by ajgreeny on 2010-11-19
Though it will depend on the current partition layout on the machine, I would advise that you shrink the win7 partition with its own disk management tool, rather than using gparted.  Other than that I suggest using a live CD to install as it will give you an indication of any hardware problems that may follow once installed.

The partition layout that dino99 gave was a good one, though I might go with 4GB swap to ease hibernation, so stick with that and all should be good, assuming no other hardware problems.

---

### Post by dino99 on 2010-11-19
> **ajgreeny said:**
> .... though I might go with 4GB swap to ease hibernation,...

my bad, you're right of course, but i never hibernate :)

---

### Post by HappyLinux on 2010-11-19
To be honest, I don't think I'm over thinking about hardware compatibility. LiveCDs don't give a good idea on hardware compatibility. With a previous Ubuntu, the LiveCD was fine, most of the basic hardware was running fine, but then as soon as I've installed it, the graphics go out the window.

The LiveCD ran the graphics at high resolution without a problem, but once installed, it switched down to a low resolution, and no matter how much fiddling was done, it refused to use a higher resolution. The sound wouldn't work after the install either.

So basically, what works under LiveCD, doesn't necessarily work once installed.

As for the partitioning, I was intending, I was intending on installing Windows 7 first, using half the HDD space in 1 partition. Then using the last half, I then install Linux, letting it auto partition, presuming it doesn't try to shrink the Windows partition.

In earlier distros (doesn't matter if Suse, Fedora or Ubuntu), it used what space was available automatically, without trying to shrink Windows partition. In recent years, the automatic partitioning keeps trying to shrink the Windows partition.

Oh, and I never use sleep or hibernation modes in any operating system either.

---

### Post by ajgreeny on 2010-11-19
> So basically, what works under LiveCD, doesn't necessarily work once installed.But at least it shows that it could work with a little work.  I am surprised that you did not find a way to get your system to work when installed if it had worked as a live boot.

---

### Post by cascade9 on 2010-11-20
> **HappyLinux said:**
> To be honest, I don't think I'm over thinking about hardware compatibility. LiveCDs don't give a good idea on hardware compatibility. With a previous Ubuntu, the LiveCD was fine, most of the basic hardware was running fine, but then as soon as I've installed it, the graphics go out the window.

The LiveCD ran the graphics at high resolution without a problem, but once installed, it switched down to a low resolution, and no matter how much fiddling was done, it refused to use a higher resolution. The sound wouldn't work after the install either.

So basically, what works under LiveCD, doesn't necessarily work once installed.

Rare but it happens, and if you actually added some PPA for the newest nVidia drivers and then got them you should get full resolution (GTS450 needs driver version 260.19.12, and 10.10 only has 260.19.06, earlier versions of ubuntu would be even further behind). 

Annoying, but not really the fault of ubuntu (or linux in general). If you use 'OMG its just got released in the last 3 months' hardware you are far more likely to have just this sort of issue.... 

> **HappyLinux said:**
> As for the partitioning, I was intending, I was intending on installing Windows 7 first, using half the HDD space in 1 partition. Then using the last half, I then install Linux, letting it auto partition, presuming it doesn't try to shrink the Windows partition.

In earlier distros (doesn't matter if Suse, Fedora or Ubuntu), it used what space was available automatically, without trying to shrink Windows partition. In recent years, the automatic partitioning keeps trying to shrink the Windows partition.

I've never trusted automatic partitioning. IMO basing the partitions sizes on a % of avaible space (or even non-avaible space) is a bit silly, you can end up with really funny partition sizes.

---

### Post by HappyLinux on 2010-11-20
> **ajgreeny said:**
> But at least it shows that it could work with a little work.  I am surprised that you did not find a way to get your system to work when installed if it had worked as a live boot.

Yes, it surprised me as well. True that the LiveCD proved that it could work, but for some reason, it refused to do so.

---

### Post by HappyLinux on 2010-11-20
> **ajgreeny said:**
> But at least it shows that it could work with a little work.  I am surprised that you did not find a way to get your system to work when installed if it had worked as a live boot.

Yes, it surprised me as well. True that the LiveCD proved that it could work, but for some reason, it refused to do so.

---

### Post by HappyLinux on 2010-11-20
> **cascade9 said:**
> Rare but it happens, and if you actually added some PPA for the newest nVidia drivers and then got them you should get full resolution (GTS450 needs driver version 260.19.12, and 10.10 only has 260.19.06, earlier versions of ubuntu would be even further behind). 

Annoying, but not really the fault of ubuntu (or linux in general). If you use 'OMG its just got released in the last 3 months' hardware you are far more likely to have just this sort of issue.... 

I've never trusted automatic partitioning. IMO basing the partitions sizes on a % of avaible space (or even non-avaible space) is a bit silly, you can end up with really funny partition sizes.

I don't have Linux installed on my current system, which is the one I had previously tried to run Linux on. Also, I don't have a nVidia card installed, but rather a Radeon HD5670. However, I had a Radeon X1950 Pro installed when I tried using Linux, and that card had been out for just over a year.

I don't know how old the hardware is on the new machine that I'm looking at, but the hardware on the old one was over a year old at the time.

I don't really like automatic partitioning either, but it's handy if you're installing a single OS on the HDD, especially when installing Windows. As for Linux partitions, I've never had it try to create funny sized partitions, but repeatedly had it trying to shrink Windows partitions.

---

### Post by HappyLinux on 2010-11-20
Sorry for the duplicate post. Thought my browser had froze and thus I clicked the post button a few times.

---

