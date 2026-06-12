---
title: "gpsbabel and Garmin USB GPS"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by ok67 on 2007-05-28
To be able to use gpsbabel with a Garmin GPS unit with USB interface the "kernel garmin_gps module" must be blacklisted. This has been working fine until a resent kernel upgrade. With the latest kernel releases this dos not work any more. The case is described at: [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)

In brief: 
"The instructions above for Dapper Drake seem to apply, but another peril awaits users of Ubuntu 7.04 with kernel 2.6.20-15. This product ships with a kernel built with CONFIG_USB_SUSPEND which apparently breaks the libusb support that we need. Recompile your kernel without this options and/or contact your support provider for current status or help."

Do I have top compile my own kernel? or will this be changed in the future?

---

### Post by ok67 on 2007-05-30
Anyone ?

---

### Post by ok67 on 2007-06-04
No one ????

---

### Post by rogerdean on 2007-06-10
Hi there 67
Yeah this one is a real pain. I'm trying to figure it out too - did you get anywhere?
Roger

---

### Post by ok67 on 2007-06-11
No, I see that there is a new kernel for Ubuntu ready for install, but I have not tried it yet. But I assume I have to compile my own kernel. I was just hoping that I did not have too. 

I changed to Ubuntu from Slack some years ago to avoid the compiling and still have the latest version running.......

---

### Post by ok67 on 2007-06-13
Latest news:
It seems like gpsbabel is working OK with the garmin kernel driver, ie. using gpsbabel -igarmin -f/dev/ttyUSB0 .......

No need to blacklist the garmin kernel driver anymore.

---

### Post by rogerdean on 2007-06-13
Gosh 67, you are quite right! I've undone all my changes and everything seems to work. I'm using a usb garmin venture cx and the command...

gpsbabel -i garmin -f /dev/ttyUSB0 -o kml -F gpsfile.kml

...pulls data from my handset and saves it in a Google Earth file in /home/roger/

I'm delighted - thanks for the tip-off. Is it working for you?

Cheers
Roger

---

### Post by ok67 on 2007-06-20
No, well partly. But I have decided to compile my own Kernel..........

---

### Post by ok67 on 2007-06-23
Using gpsbabel through /dev/ttyUSB0 using the garmin_usb kernel driver simply was too unstable, only a few of my waypoints was transfered. After some effort I finally managed to compile my own kernel, 2.6.21.5, and now gpababel works very well. 

(When compiling my kernal I had some problems with the nvidia driver and paravirt_ops, I just removed the paravirt option to solve that problem. I also had some problem with "device_mapper table lookup failed", but since I am not using RAID I just removed the entire RAID option from my kernel)

---

### Post by rogerdean on 2007-06-23
sounds like some serious work - sadly this is way above my competence level...
i've managed to get reliable transfer using gpsbabel on ttyUSB0 from GPS to file, but nothing the other way yet. will struggle on though
good luck!
Roger

---

### Post by ok67 on 2007-06-26
It is actually not that difficult, but what made it difficult was my use of the NVIDIA display drivers. The problem with the NVIDIA drivers is experted to be fixed in 2.6.22

Added: The best solution would be if the UBUNTU team just could turn of the USB_SUSPEND option which are causing the problem for the libusb.

---

### Post by rogerdean on 2007-06-26
Ubuntu team, could this be fixed for us please? Us GPS junkies would be very grateful...
If anyone knows of a better place to make this request please let me know
Cheers
Roger

---

### Post by ok67 on 2007-06-27
Hopefully the Ubuntu team read this.

More information is also available at: [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)

---

### Post by ivt on 2007-07-11
can you point me in the right direction for advice on rebuilding the kernel as you have done?

---

### Post by ok67 on 2007-07-13
You can download the entire kernel source from [www.kernel.org](www.kernel.org)
You also need several build packages installed to be able to build the kernel, packages named something like build-essential etc.
Included with the kernel source there should be several readme files with a lot of information, you might also look in the Documentation folder included with the source.

You might also look here:  [http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO.html](http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO.html)
and here: [http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

You might also google for kernel howto or kernel build or kernel configuration etc.......

---

### Post by ivt on 2007-07-13
thanks, i found building the kernel the ubuntu way, this may sound odd, but compiling the kernel from vanuilla sources in gentoo was a much simpler process, I have reinstalled xp to dual boot now, and now that is all i use windows for, getting data from my garmiin then using webupdater to get kml files for google earth

---

### Post by ok67 on 2007-07-15
Actually I am building the kernel from the normal kernel source, and not the Ubuntu way......... I never tried do it the Ubuntu way, but you might also download the kernel source as an Ubuntu package and build it from that I suppose.

---

