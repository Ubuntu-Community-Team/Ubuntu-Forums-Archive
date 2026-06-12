---
title: "Onboard video card not recognized"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by ArtMan on 2006-03-28
I installed Ubuntu 5.10 a few months ago with no problems. At the time I was using an nVidia Riva TNT2 AGP video card.

This weekend I removed that card because of some issues I was having with WinXP. 

So now I am using the on-board video circuitry, which Windows identifies as VIA/S3G UniChrome IGP. (The PC is an HP Pavilion a720n with the Via KM400A chipset.)

Unfortunately, the result of this change is that when I attempt to start Ubuntu, it boots into the command line (after the graphic splash screen).

I'm pretty sure what I need to do is replace the "Device" section of /etc/X11/xorg.conf that currently reads as follows >>

[COLOR="DarkSlateBlue"]  Identifier     "NVIDIA Corporation NV5M64 [RIVA TNT 2 Model 64/Model Pro]"
  Driver     "nv"
  BusID     "PCI:1:0:0"[/COLOR]

I can edit the xorg.conf file with nano if I know what to put in there. Will that be enough, or are there other things I need to do also?

I almost reinstalled Ubuntu, figuring the video would be auto-detected, but I figured this would be a good learning experience, and I didn't know what other mischief a reinstall would do.

Thanks for your help. I'm pretty new at this, so clear, step-by-step directions would be very much appreciated.

TIA,
-Art-

---

### Post by John.Michael.Kane on 2006-03-28
[http://www.ubuntuforums.org/showthread.php?t=75393&highlight=S3](http://www.ubuntuforums.org/showthread.php?t=75393&highlight=S3)
[http://www.ubuntuforums.org/showthread.php?t=124604&highlight=S3](http://www.ubuntuforums.org/showthread.php?t=124604&highlight=S3)

---

### Post by ArtMan on 2006-03-28
I came up with a different solution that, to this newbie at least, seemed much easier. So far it seems to work OK.

I booted from the Ubuntu Live CD. In the process it created a new xorg.conf file based on its check of the hardware (including the onboard video, now that the nVidia card is uninstalled). Then I just copied the xorg.conf from the RAM-based file system created by the CD to the /etc/X11 directory of the file system on my hard drive. I made a backup of the old xorg.conf file just in case, and it took me a few minutes to mount the drive, change permissions, and generally do stuff I hadn't had to do in a while and so was pretty rusty. 

I haven't tested everything, so maybe there is a problem lurking somewhere, but right now it looks good.

Thanks, SD-Plissken, for your very quick reply.

-ArtMan-

---

