---
title: "Desktop effects could not be enabled."
date: 2008-08-12
forum: General Help
---

### Post by gato333 on 2008-08-12
Please im about to go crazy with this i install Ubuntu 8.04 everything ok got the Wireless to work fast and everything downloaded it a bunch of applications, everything fine but when i set up my Advance Desktop effects and when to enable the Extra Visial Effects it doesnt work.
I ran a Conpiz on the terminal and said something about Xgl fail and something about pixmap is not good neither. Oh just to clarify i had this effects working before on this computer so i know this computer takes it and also something i find weird on the Hardware Drivers nothing comes up i dont know why.

Computer-Laptop Dell Latitude 110l
Wireless-yes
Ethernet-yes

Any help would be greatly appreciated.....

---

### Post by overdrank on 2008-08-12
> **gato333 said:**
> Please im about to go crazy with this i install Ubuntu 8.04 everything ok got the Wireless to work fast and everything downloaded it a bunch of applications, everything fine but when i set up my Advance Desktop effects and when to enable the Extra Visial Effects it doesnt work.
I ran a Conpiz on the terminal and said something about Xgl fail and something about pixmap is not good neither. Oh just to clarify i had this effects working before on this computer so i know this computer takes it and also something i find weird on the Hardware Drivers nothing comes up i dont know why.

Computer-Laptop Dell Latitude 110l
Wireless-yes
Ethernet-yes

Any help would be greatly appreciated.....

Hi and welcome, what is the model of the graphics card? You may look at the link in my signature FAQ's :)

---

### Post by gato333 on 2008-08-12
Sorry how would i find that out i am kinda new to this. Thanks for the help.

---

### Post by gato333 on 2008-08-12
i think is this:

Dell Latitude 110L uses graphics card Intel 910GML chipset with UMA graphics (up to 64MB shared).

---

### Post by overdrank on 2008-08-12
> **gato333 said:**
> i think is this:

Dell Latitude 110L uses graphics card Intel 910GML chipset with UMA graphics (up to 64MB shared).

Ok the intel graphics are usually simple. You may try compiz-check in the FAQ's or 
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Mhawkins1 on 2008-08-17
> **gato333 said:**
> Please im about to go crazy with this i install Ubuntu 8.04 everything ok got the Wireless to work fast and everything downloaded it a bunch of applications, everything fine but when i set up my Advance Desktop effects and when to enable the Extra Visial Effects it doesnt work.
I ran a Conpiz on the terminal and said something about Xgl fail and something about pixmap is not good neither. Oh just to clarify i had this effects working before on this computer so i know this computer takes it and also something i find weird on the Hardware Drivers nothing comes up i dont know why.

Computer-Laptop Dell Latitude 110l
Wireless-yes
Ethernet-yes

Any help would be greatly appreciated.....

I have this problem also but I have an Nvidia GeForce 7300 GS graphics card. I just got my resolution issue fixed but my screen appears to be off to the right a little. I have ran the Compiz-Check and the results are as follows:
```

mhawkins@ubuntu:~$ wget http://blogage.de/files/4359/download -O compiz-check
--22:41:33--  http://blogage.de/files/4359/download
           => `compiz-check'
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,814 (27K) [application/octet-stream]

100%[====================================>] 27,814        38.69K/s             

22:41:34 (38.55 KB/s) - `compiz-check' saved [27814/27814]

mhawkins@ubuntu:~$ chmod +x compiz-check
mhawkins@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) Y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) Y
mhawkins@ubuntu:~$ WARNING: modinfo for module nvidia_legacy failed: modinfo: could not open /lib/modules/2.6.24-21-generic/volatile/nvidia_legacy.ko: No such file or directory

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSWARNING: modinfo for module nvidia_new failed: modinfo: could not open /lib/modules/2.6.24-21-generic/volatile/nvidia_new.ko: No such file or directory

```

---

### Post by overdrank on 2008-08-18
Hi Mhawkins1. :)
If the driver is enabled and in use under hardware drivers then you should be able to changed the driver as discussed in your other thread.

---

### Post by Mhawkins1 on 2008-09-03
As weird as this sounds... I removed my wireless card and I was able to get the video driver to work and I could enable my Desktop Effects.  It was a Microsoft MN-740 wireless NIC card. I don't know what would have caused this but it's working now. THANKS EVERYONE!

---

### Post by hoggson on 2008-11-19
I have a Dell Latitude 110L, with the Intel 910GML graphics chip.  I also cannot get the advanced effects to work.  Also all my graphics seem to be slow, and cannot full screen video in anything above 800x600.  I could do all this in 8.04.  Anyone konw what has been changed, how to change it back or a workaround for this problem?

---

