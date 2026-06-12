---
title: "Install problem - Ubuntu 15.04 i386 on Dell Latitude D820"
date: 2015-07-28
forum: Hardware
---

### Post by jimmie3 on 2015-07-28
I bought four of these laptops and hope to get Ubuntu working on them. I was able to get Ubuntu 7.10 installed.

These laptops have an NVIDIA GeForce GO 7400 cards and it's doing this for version 15.04:

Starts out OK:

[IMG]https://lh3.googleusercontent.com/lvztugGmZ7hHGLRr_pZHHdlKkSZT2ishDgKHKbCenJQ=w293-h220-no[/IMG]

Craps out before installation screen comes up. Same pattern on each laptop. Install DVD works fine on a desktop PC:

[IMG]https://lh3.googleusercontent.com/U524OfFutHchMyhWYnx17P19Wv1ZbyFLrlmDRwyRyiw=w807-h605-no[/IMG]


I'm just starting out in Linux, but I have a solid background in computing. Is there a way to incorporate the NVIDIA driver into the install media? Flash drive? Into the .iso before writing it to DVD?

Thank you.

---

### Post by howefield on 2015-07-28
Looks like you will struggle to get 15.04 Ubuntu with Unity to run on an NVIDIA GeForce GO 7400.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/726496](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/726496)

Maybe try another flavour eg Xubuntu, ie, one not using Unity nor compiz. ?

---

### Post by jimmie3 on 2015-07-28
I don't really know my distros. I hope to find a full and up to date one that I can use on these laptops.

I will grab **X**ubunto tonight. Are there any others that come to mind that I might try?

---

### Post by howefield on 2015-07-28
> **jimmie3 said:**
> I don't really know my distros..

Already got that impression with your comment re 7.10 ;)

> I will grab **X**ubunto tonight. Are there any others that come to mind that I might try?

I'd have said Lubuntu if you hadn't already tried it, but there are other light (non Ubuntu) distributions that you could try, but it would help to know the specifications of the machine (without having to go hunting them down).

---

### Post by oldfred on 2015-07-28
My old desktop with nVidia always needed nomodeset. But it had 4GB of RAM.

My Toshiba CoreDuo2 laptop from 2006 has 1.5G of RAM with just internal Intel video. It does not have enough horsepower to run Unity, but does run 12.04 Ubuntu with fallback or gnome-panel. I have not tried to update to a newer version only because I hope to retire it before 12.04 reaches end of life. 
       Offical flavors:
[http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours)
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

            [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)

    
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

When you get an install working be sure to only install the correct nVidia driver.
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by weatherman2 on 2015-07-28
If you don't "know your distros" and are new to Linux, here's one important point: stick to the LTS (Long-Term Support) editions of Ubuntu when starting out.  Ubuntu 14.04 is an LTS edition, supported until April 2019.  Ubuntu 15.04 is not an LTS and will be supported only until January 2016; after that, you will have to upgrade.  IF you don't want to upgrade the OS every nine months, stick to the LTS editions of Ubuntu.

Not to say even Ubuntu 14.04 will install on your laptop.  But the same applies to Lubuntu.

I'm not crazy about the look/feel of Lubuntu or Xubuntu.  On older machines, I usually install "Gnome Flashback" (aka "Fallback") to use an older, lighter Ubuntu desktop (which no longer uses the "Unity" interface) but is still Ubuntu/Gnome.  What I would do in your case is install Ubuntu 14.04 on some other hardware, install Gnome Flashback, set the default login session to "Gnome Fallback" (Metacity), then clone it back to the three laptops.  (Or, take one of the laptop hard drives out and connect it to some other hardware.)  Linux and Ubuntu (unlike Windows) are very forgiving about moving the same installation between completely different hardware.  Usually it just boots when you put the drive into another computer.  I do it all the time.

---

### Post by jimmie3 on 2015-07-28
Oh sorry. The Dell Latitude d820 is an old laptop that came about as XP was released. 

[http://www.dell.com/downloads/ap/products/latit/LAT_D830_1007_RF.pdf](http://www.dell.com/downloads/ap/products/latit/LAT_D830_1007_RF.pdf)

Maybe this will work for one that I replaced the hard drive and added memory for: [http://www.dell.com/support/home/us/en/19/product-support/servicetag/DGVDVC1/configuration](http://www.dell.com/support/home/us/en/19/product-support/servicetag/DGVDVC1/configuration)

Lubuntu failed, but it just installed. That's one choice I hope.

As to 7.10: [http://old-releases.ubuntu.com/releases/7.10/](http://old-releases.ubuntu.com/releases/7.10/)

That one did install, but I cannot get any connectivity going on it.

---

### Post by jimmie3 on 2015-07-28
Thanks for the other info, guys. I'm checking it out. I can try v14.04 and see what it does.

---

### Post by NathanRodriguez on 2015-07-28
I can recommend Lubuntu 14.04 LTS, have been using it for some months with the MATE (GNOME2 fork) desktop environment and proved itself stable, reliable, lightweight and with a nice traditional user interface.

---

### Post by jimmie3 on 2015-07-28
> **NathanRodriguez said:**
> I can recommend Lubuntu 14.04 LTS, have been using it for some months with the MATE (GNOME2 fork) desktop environment and proved itself stable, reliable, lightweight and with a nice traditional user interface.

On a Dell D820 laptop with Nvidia graphics card?

I'd rather try proven builds first of course.

---

