---
title: "Nvidia: Graphics issues when Installing/using Ubuntu"
date: 2013-05-29
forum: Hardware
---

### Post by JJossie on 2013-05-29
I have a fairly old computer (5-6 years) and I've been trying to install and use Ubuntu, but I've been having a ton of graphics-related problems. I have an AMD Turion(tm) 64 x2 Mobile Technology TL-60 2.0 GHz Processor, and a NVIDIA GeForce 7150M / nForce 630M graphics card.

Anyway, at first I downloaded the 32-bit version of Ubuntu 13.04 and put it on a usb disk. I booted it up and it worked okay until it went to the desktop. Every other row of pixels was messed up, so everything was twice as tall as it should be. I could only see half of the vertical aspect of the screen, and about every 200 pixels or so horizontally, it would repeat a small segment of what the screen should look like. Basically, it was so messed up it was inoperable. I couldn't see most of the installation dialog, so I couldn't click "Try Ubuntu".

I figured it might be a 32/64 bit compatibility issue, so I downloaded the 64 bit version. After wiping and re-formatting the USB Disk, then loading the iso onto there, I booted the disk and got the exact same problem. By now, I was pretty ticked because each download took about 5 hours. So I decided to try downloading the windows installer of version 12.04 LTS. After letting it download and install, I booted yet again to get the EXACT SAME PROBLEM. 

So I decided to try plugging in my second monitor. That fixed some of the issues, but since they are different resolutions, one screen always looked terrible. I can now use Ubuntu, but there is still a ton of graphics problems. I can't have the displays extend, because I get tons of weird pixel repetitions on one or both monitors. Just about everything is extremely buggy and lagging. It sometimes freezes up and I have to kill it. When I went into the system details, it said "Unknown" under "Graphics Card". I try using the "Additional Drivers" Thing, but it says there are no proprietary drivers. 

What should I do??? This is driving me nuts! Is there a way I can download a driver from NVIDIA and install it into Ubuntu? Do I need to just get a newer graphics card (which I can't afford)? I can post pictures if needed, just let me know and I will do that ASAP. Any help and/or feedback is appreciated. Thanks in advance!

---

### Post by ohnonot on 2013-05-29
have you searched if other people had problems with your particular graphic card and ubuntu/linux?
the good thing about using old hardware is that most problems have been covered largely.

---

### Post by mörgæs on 2013-05-29
Best you can do is trying X/Lubuntu 13.04, as they are much less demanding with regards to the graphics card.

---

### Post by Mark Phelps on 2013-05-29
One thing you might try is an older Ubuntu version.  Starting with Ubuntu 12.04.2, the X-server was upgraded to a new version -- which made it incompatible with all but the most recent AMD video chipsets.  I don't use Nvidia, so I don't know if it has the same limitations.

---

### Post by ohnonot on 2013-05-30
@ mörgæs & mark phelps:
my own computer (laptop) is 5-6 years old and unity is running no problem.
though it has an intel onboard graphics card.
so it is a problem with old nvidia cards, not with old computers generally?

---

### Post by Yellow Pasque on 2013-05-30
It sounds like an issue with the open-source driver for nvidia cards (nouveau).
> I try using the "Additional Drivers" Thing, but it says there are no proprietary drivers.
That's odd. Try installing them manually:
```
sudo apt-get install mesa-utils nvidia-304
```

---

### Post by alexthunder on 2014-02-03
I had problem with Lubuntu 13.10 and Linux Mint 16 when installing onto HP Pavilion dv6700 with NVIDIA GeForce 7150M/ nForce 630M. The graphics was either distorted or I was getting a black screen. The only way to run an installer was in the compatibility mode. Unfortunately some distributives don't have this option.

But nothing has changed after rebooting.

After editing grub options with E and adding "nomodeset" instead of "quiet splash" I was able to boot. After installing nvidia-current and nvidia-settings and rebooting I had the same distorted graphics.

When running nvidia-settings I was getting the following error: 
You do not appear to be using NVIDIA X driver. Please edit you X configuration file (just run nvidia-xconfig as root), and restart the X server.

The problem is that I don't have nvidia-xconfig and unable to install it with "sudo apt-get install"

I edited /etc/default/grub and added nomodeset, so don't have any problem with black screen or distorted graphisc
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

Tried to add "nouveau.blacklist=1" with nomodeset to no avail. 

Still have no idea how to blacklist nouveau properly and use the NVidia driver. Any suggestions?

---

