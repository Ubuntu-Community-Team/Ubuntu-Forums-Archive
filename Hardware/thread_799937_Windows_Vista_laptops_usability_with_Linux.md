---
title: "Windows Vista laptops usability with Linux"
date: 2008-05-19
forum: Hardware
---

### Post by wirawan0 on 2008-05-19
This question crossed my mind yesterday as I browsed through a Best Buy ad. 

I noted that laptop prices keep going down (at least, they are in favorable prices now than a few years ago, where you had to have at least 10^3 ($1000+) USD to get one of them. But another worrying trend is that many of them are powered with Windows Vista. Now, my question is this: what is the prospect of installing Linux (whatever version, but Ubuntu preferred) on these laptops. I don't have a particular model in mind---it can be Sony, HP, Dell, Lenovo, or whatnot.

As you may know, Windows Vista hardware requirements are quite stringent; seems like Vista doesn't want to support many existing (now they call them "old") hardware. Then there is that effort to imprison the so-called "premium content" so that user would not have access to the unencrypted form of it. This will affect audio and video devices. How are things affected so far with these changes forced by Micro$oft? Please share your experiences! I'd love to know what your experiences are.

Just to give you some background: I am a Linux laptop user since 2002. I have had two laptops that I use with Linux (various flavors), and I was pleased that the support of Linux on these laptops are getting better and better. Originally, these laptop came with Windows XP. I formatted the hard drive and install both Windows XP and Linux on both of them. So I'd like to have this option, at least, if I have to buy another laptop again.

Wirawan

---

### Post by ASULutzy on 2008-05-19
I'm no laptop expert, but I can give you information based on the laptop I just purchased.

I was looking around online at various manufacturers' websites, and had priced some laptops there, then I went to visit Best Buy and actually found a better deal than I had seen on any of the online sales places.

Anyway, I went with the HP Pavillion dv6000, (BIOS reports it as dv6700) It only cost me 700 bucks or so and has an Intel Core 2 Duo, 3 GB of ram, a 250 GB HDD, a built in media remote, DVD/CD burner w/ Lightscribe, VGA and S-video outputs and came preinstalled with Vista.

The first thing I did when I got home was to install Ubuntu, and there have been a few minor issues, but considering this is a laptop and that they're generally tougher to get support for, I've been very happy with this one. Almost everything worked out of the box (The media touch sensitive buttons worked, the touchpad worked, Intel x3100 worked, etc.) The only things that were/are a nuisance: The wireless card didn't work out of the box, but simply download the Bc43xx drivers with ndiswrapper and ndisgtk fixed that problem in about 3 seconds. The only persistant issue I have had with this laptop is that I am unable to get S-Video to work in Ubuntu, though this is more a driver issue probably than an Ubuntu/specific laptop problem. The VGA output works fine though out of the box and it was easy to setup an extended desktop or to clone the output.

All in all I was very happy with this laptop, and Linux distros have certainly come a long way in how much support they offer for the average setup right out of the box.

Anyway, hope this was helpful!

---

### Post by wirawan0 on 2008-05-19
Thanks. That's helpful. Hopefully more people will share their experiences.

---

### Post by ronan_saini on 2008-05-19
hi buddies
             i just purchased vaio CR36 with 2.1 ghz penryn processor n 2 gb ram n 200 gb hard drive with vista home premium installed on it........but  i m not able to install Ubuntu frm live cd......and not even fedora or any other linux distribution........sm ppl say there s sth wrong with arch.....can this b the reason......... pls help me out.........

---

### Post by zzelinski on 2008-05-19
ASULutzy, I have this same laptop -- how did you get the vga dual screen working (extended desktop)? Every time I try the gui screen settings, it either doesn't work or completely destroys my graphics settings and I have to restore to a backup xorg.conf!

> **ASULutzy said:**
> I'm no laptop expert, but I can give you information based on the laptop I just purchased.

I was looking around online at various manufacturers' websites, and had priced some laptops there, then I went to visit Best Buy and actually found a better deal than I had seen on any of the online sales places.

Anyway, I went with the HP Pavillion dv6000, (BIOS reports it as dv6700) It only cost me 700 bucks or so and has an Intel Core 2 Duo, 3 GB of ram, a 250 GB HDD, a built in media remote, DVD/CD burner w/ Lightscribe, VGA and S-video outputs and came preinstalled with Vista.

The first thing I did when I got home was to install Ubuntu, and there have been a few minor issues, but considering this is a laptop and that they're generally tougher to get support for, I've been very happy with this one. Almost everything worked out of the box (The media touch sensitive buttons worked, the touchpad worked, Intel x3100 worked, etc.) The only things that were/are a nuisance: The wireless card didn't work out of the box, but simply download the Bc43xx drivers with ndiswrapper and ndisgtk fixed that problem in about 3 seconds. The only persistant issue I have had with this laptop is that I am unable to get S-Video to work in Ubuntu, though this is more a driver issue probably than an Ubuntu/specific laptop problem. The VGA output works fine though out of the box and it was easy to setup an extended desktop or to clone the output.

All in all I was very happy with this laptop, and Linux distros have certainly come a long way in how much support they offer for the average setup right out of the box.

Anyway, hope this was helpful!

---

### Post by badfish591 on 2008-05-19
i have a toshiba A215-S7428, and its been great. aside from some wireless issues (which only took, me getting the driver and patching it) everything worked perfectly out of the box.

---

### Post by dasunst3r on 2008-05-19
My computer (which I bought one year ago) cost me $ 1,500 (includes 8.25% sales tax, free shipping), and it is perfectly capable of running Vista.  I know of many, many people who would look at me in dismay and ask me why on earth my machine is so expensive.  Well... the options added up: Intel wireless card, nVidia graphics card, high-resolution screen, extended-life battery, 2-year warranty, extra RAM...

But I digress.  I couldn't be happier with Linux while using this machine.  With respect to my media consumption, I occasionally watch TV and I rarely buy music/movies.  But when I do, I will pay whoever will let me have my fair use rights.  But if I were an avid movie watcher, I would like to watch my movies on a bigger screen.

---

### Post by ASULutzy on 2008-05-19
> **zzelinski said:**
> ASULutzy, I have this same laptop -- how did you get the vga dual screen working (extended desktop)? Every time I try the gui screen settings, it either doesn't work or completely destroys my graphics settings and I have to restore to a backup xorg.conf!

Well, like I said, I can get VGA to work, but not S-video.
To get VGA extended desktop to work, you need to add a virtual section to your xorg.conf. (Just google like xorg.conf and Virtual, cause I don't remember 100% what section it goes in) and then I would download a nice little tool called grandr.```
sudo apt-get install grandr
```

One thing that's important to remember is that if you try to enable Compiz over more than like 2280 width it kinda messes up, though it's still usable.

Anyway, I hope this helps, if not post back with your results and I'll try and help out... lol, if you ever figure out how to get S-video to work make sure you return the favor ;)

---

### Post by bford16 on 2008-05-20
> **ronan_saini said:**
> hi buddies
             i just purchased vaio CR36 with 2.1 ghz penryn processor n 2 gb ram n 200 gb hard drive with vista home premium installed on it........but  i m not able to install Ubuntu frm live cd......and not even fedora or any other linux distribution........sm ppl say there s sth wrong with arch.....can this b the reason......... pls help me out.........
If the CR36 has an SATA drive, you won't be able to install from the Hardy Heron Live CD.  There is a problem with SATA recognition in the 2.6.24-16-generic kernel. If you want to install Ubuntu, you will have to stick with Gutsy (7.10) for now. Then you can upgrade to Hardy (8.10) from within Gutsy. If you do that, you'll have to add "pci=nomsi" to the boot parameters for the 2.6.24-16-generic kernel.

I have read that this problem will be fixed in the 2.6.25 kernel, but I dont' have any personal experience with that.

---

### Post by zzelinski on 2008-05-20
Thanks for the tips! I added the virtual section and now I can use grandr to do dualscreen -- but it doesn't stick! Whenever I logout/restart, I have to set it all up again in grandr.

Is this just how it works, or is there a step I'm missing?

> Well, like I said, I can get VGA to work, but not S-video.
To get VGA extended desktop to work, you need to add a virtual section to your xorg.conf. (Just google like xorg.conf and Virtual, cause I don't remember 100% what section it goes in) and then I would download a nice little tool called grandr.

One thing that's important to remember is that if you try to enable Compiz over more than like 2280 width it kinda messes up, though it's still usable.

Anyway, I hope this helps, if not post back with your results and I'll try and help out... lol, if you ever figure out how to get S-video to work make sure you return the favor 

---

### Post by LeoSolaris on 2008-05-20
A little after X-mas, I bought a nice Dell Inspiron 1520, and it had Vista as an option. I opted to put XP on it instead, and duel booted it with Ubuntu. It is working flawlessly, and with the upgrade to 8.04, it is actually working better than it did under 7.10. PulseAudio fixed a little sound glitch that put all of the sound control at the top. (if you pushed sound down four times, it muted, but had about 6 more spaces to go before it said it was muted) Things like that.

Newer laptops can be a little more hit or miss. Just check the hardware comparability lists, or take a LiveCD to the store with you to test out the hard ware. (some stores don't like it though, just to let you know.)

Leo

---

