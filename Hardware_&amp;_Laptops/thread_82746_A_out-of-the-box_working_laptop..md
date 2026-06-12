---
title: "A out-of-the-box working laptop."
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by bete on 2005-10-27
I am looking for a laptop, it HAS to work flawlessly with ubuntu after installing the OS. Network, video, sound - everything.
So what laptops does work like this?

Ps: Is Mac's working correctly with ubuntu?

---

### Post by poofyhairguy on 2005-10-27
The only way to get that for sure is to buy an HP laptop that was designed to work with Ubuntu:

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)

Ignore the warning about the wireless, as a few of those have Intel wireless which will work out of the box. I don't the the sub notebook will.

Its not advised to get a Mac because the wireless cards for the new ones won't work in Linux and that platform is missing a real flash player and most of the Windows Codecs.

---

### Post by blierp on 2005-10-27
I've got a compaq evo-n620c and it's works perfect out of the box. Only thing i haven't tested is the modem because i don't use that. It is detected, but i never tried it. As for the video, i have to use the opensource DRI drivers (these are installed default) because ATI hasn't released proper drivers. However, tuxracer runs great with these drivers ;)

---

### Post by John.Michael.Kane on 2005-10-27
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops?highlight=%28hardware%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops?highlight=%28hardware%29)
[http://www.linux-laptop.net/](http://www.linux-laptop.net/) <----- has info on laptops with support for linux
[http://www.linuxcertified.com/linux_laptops.html](http://www.linuxcertified.com/linux_laptops.html)
[http://www.pcsforeveryone.com/article.php?art_id=62&osCsid=31f8234d86a82ad010df939ba6a736cf&linux](http://www.pcsforeveryone.com/article.php?art_id=62&osCsid=31f8234d86a82ad010df939ba6a736cf&linux)

This should get you started. do hope it helps..

---

### Post by scb147 on 2005-10-27
I just installed Breezy on a Dell Latitude D610 with the Intel WirelessPRO 2200 and a ATI Radeon X300 video card and everything worked right out of the box.

---

### Post by zorkerz on 2005-10-27
Im useing a gateway m680 and everything has worked since the install.  I have installed different drivers for the nvidia card but the defaults seamed to work fine.  The only trouble i have had is with software under private licenses, or protected formatts, like mp3 and java, but that will happen with any linux machine and its as simmple as adding the universe repositories and grabbing what you need.

---

### Post by souki on 2005-10-31
sony vaio vgn a517b

I've installed breezy two times:
- the first time keeping the windows partititions
- the second *over* the windows partitions, because everything is working (the things I need)

sata,wifi,firewire,usb,frequence scaling,batt status,sound,suspend to disk,suspend by pressing Fn+F12,cd/dvd writer,vaio wireless mouse

and all the install phase with wifi connectivity
too bad, nothing to do after that ;)

so far, the only thing not working is the automatic luminosity feature, I didn't try the modem nor the 3D accel

---

### Post by emperor on 2005-10-31
[quote=scb147]I just installed Breezy on a Dell Latitude D610 with the Intel WirelessPRO 2200 and a ATI Radeon X300 video card and everything worked right out of the box.[/quote] 
I seriously doubt that "everything" is working perfectly after the inital install. This is just not reality.

1. In order to get the Alps touchpad working perfectly, the synaptics driver needs to be patched, compiled and installed. This will fix the tap problem, and enable the touchpad browser scrowl to work properly.

2. Sound in games and multimedia will take some tweaks and installing sdl-all and the alsa-oss packages.

3. Mad will need to be installed to be able to play MP3  files in Rhythmbox.
 
4. Ripping to MP3 will require finding lame on the internet and doing the 3 step to installation.  (Also install grip!)

5. Watching trailers and movies on the DVD drive will take some some additional non-free packages and codecs.

6. Power management does not fully work in Breezy; no automatic "Standby" control yet, but manual does work via the keyboard.

7. Firmware for the Intel wireless adapter is not installed automaticly. This step will require that the user go to the project web site and download and install the correct firmware for their card. 

So, lets be honest about what works "out-of-the-box".

However, Ubuntu Breezy is better than any Linux distro I have tried. My Dell i9300 is working almost perfectly now, but it took nearly 2 weeks of tweaks. In contrast, Ubuntu Hoary took about 4 weeks and I had to patch and compile a kernel to get the DMA working on the sata DVD drive.

---

### Post by k1000 on 2006-06-16
HI I've got sony vaio vgn a517b too 
but after install when I restart it complains about SATA 
can U please give me more specific configuration of install

I woult apritiate help a lot. 
I despèratly need linux.

---

