---
title: "i386 version of 6.10 on my MacBook"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by xsphat on 2007-01-12
As the title would lead you to believe, I made a live CD and ran it on my MacBook. It started right up and functioned as it does on my other computer. Do you think that this is safe for my 'book? I would like to install it on my hard drive via Apple's boot camp, but I am unsure if it is a good idea. What do you think? Will run into problems later? I downloaded apps, surfed the web and basically messed around for about 20 minutes in Ubuntu and am now back in OS X and everything is dandy.

---

### Post by ingo on 2007-01-13
I can see no reason why you should run into problems. Naturally I would go with Grub, but that is only 'cos I'm used to it - Apple's boot manager should do the same job.

---

### Post by bilbobagginz on 2007-01-13
macbook's EFI boot needs to be supported by the CD.
I don't know if this is so.

Please refer to [http://linuxlaptop.net](http://linuxlaptop.net) or
[http://modular.math.washington.edu/macbook](http://modular.math.washington.edu/macbook)

and refer to the bootcamp ( which is Apple's BIOS emulation software available from their site)

---

### Post by rickwood on 2007-01-13
I'm triple booting on my MacBook (OS X, WinXP, Ubuntu 6.10).  I much prefer grub, as I haven't used lilo for a few years (grub is much more forgiving).  However, after reading a bunch, I chose to use lilo on the MacBook.  Glad I did -- bootup is working perfectly for all 3 OS's.

I've still have a few issues to work out with Ubuntu -- the trackpad seems a bit jumpy and becomes quite annoying with extended use.  Also, I haven't got wifi to work yet.

This said, I'm taking a bit of a break from Ubuntu while I learn the ropes for OS X (long time Linux and Windows user, but never used OS X before now).  I'll pick back up on Ubuntu this spring when the new version is released.

One thing I have discovered under OS X that is pretty cool:  Fink.  This program allows you to run all of your favorite X11 programs under OS X.  I found I couldn't live without gFTP and Pan, but both are now running well under OS X via Fink.

Also, Parallels is making me lazy.  I rarely boot into Ubuntu or Windows via Boot Camp, but get nearly all of the benefits using them under Parallels instead.  Nice thing is that there are Parallels images out there for Ubuntu that people have already tweaked for a MacBook.

---

### Post by ingo on 2007-01-14
> Also, I haven't got wifi to work yet.
yes, the old wifi issue... broadcom is using frequencies shared by the US army, so details will never be released and reverse engineering is difficult but things like encryption have not been cracked yet. Your best bet is to put a different wifi card in there or use a usb wifi stick.

---

### Post by xsphat on 2007-01-24
My wifi works great and by itself, but I now need help with Parallels. I can't install Ubuntu, I can just boot with the live CD. There is the intall thing on the desktop, but I am terrified to use it. How did you guys / gals get Ubuntu installed with Parallels?

For a refresher, I own a 1.83 Ghz Core 1 Duo MacBook with 2 GB of RAM and a 60 GB hard drive running OS 10.4.8.

Thanks for the help, and in return, I can probably answer some Mac OSX questions.

---

### Post by xsphat on 2007-01-26
Can anybody help me? i can't install Ubuntu from the live CD in Parallels, is there a FAQ or something?

---

### Post by rickwood on 2007-01-26
I installed Ubuntu 6.10 under BootCamp as part of a triple-boot configuration using this tutorial as a guide (it's for 6.06, but with a few slight mods worked fine for 6.10):

[URL="http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu"]
http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu[/URL]

However, I never installed it under Parallels.  Instead, I downloaded a Parallels image of Ubuntu 6.10 via bittorrent.  I picked up the torrent file at:

[http://thepiratebay.org]("http://thepiratebay.org")

You can search there using the terms "Parallels" and "Ubuntu" and find at least one or two hits.  Then you simply copy the downloaded image to the appropriate location -- I'm on a Windows machine at work now and can't remember the exact location, but it's in your home directory under Library/Parallels.  You can put it in the appropriate subdirectory (something like linux26) there.  The userid & password are supplied with the torrent, so then it's a simple matter of booting the image in Parallels and setting up an account for yourself.

The image I downloaded had already done the work of configuring video properly, and made some other specific changes tailored for the MacBook.  You can also find some other useful information about configuring Ubuntu on you macbook toward the bottom of this wiki:

[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

Hope this helps.

---

