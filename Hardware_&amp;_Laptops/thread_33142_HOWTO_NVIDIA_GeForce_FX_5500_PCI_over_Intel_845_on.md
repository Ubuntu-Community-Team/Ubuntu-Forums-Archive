---
title: "HOWTO: NVIDIA GeForce FX 5500 PCI over Intel 845 onboard graphics"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by mstralka on 2005-05-09
Wow, I finally got my NVIDIA GeForce FX 5500 PCI to work properly.  My PC has onboard Intel 845GV graphics so whenever I tried to switch to the NVIDIA, my computer would freeze on bootup at the hotplug section.  Even though I disabled the onboard graphics in the BIOS, agpgart would still try to load the onboard graphics instead of my NVIDIA.  After beating my head against the wall for 2 days, here's what I did to finally make it work.  Please note this may not work for everyone.

Here's my system:
Ubuntu 5.04
Kernel: 2.6.10-5-686
Compaq SR1210NX
512 mb Ram
Intel Celeron D 330 - 2.66 GHZ, 256kb L2 Cache, 533 Mhz FSB
80 GB Hard drive
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=431081&dlc=en&docname=c00063244](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=431081&dlc=en&docname=c00063244)


PREWORK: Configure Linux to boot into text mode by default - not X.  I'm not sure of an easy way to do this with Ubuntu (because I used Webmin), but you basically don't want X to but up in runlevel 2, in case something goes wrong, you'll at least get to a login prompt easily.
You can try using update-rc.d to reconfigure gdm to boot only in 3, 4, and 5 [http://ubuntuforums.org/showthread.php?t=20583](http://ubuntuforums.org/showthread.php?t=20583)

1. Figure out what PCI port your NVIDIA card is on (Mine is PCI:1:9:0)
```

lspci -X

```
Here's mine (yours will look different)
```

mstralka@ubuntu:~ $ lspci -X
PCI:0:0:0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
PCI:0:2:0 Display controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
PCI:0:29:0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI:0:29:1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI:0:29:2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI:0:29:7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI:0:30:0 PCI bridge: Intel Corp. 82801 PCI Bridge
PCI:0:31:0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge
PCI:0:31:1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller
PCI:0:31:3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
PCI:0:31:5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
PCI:1:9:0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500]
PCI:1:12:0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

```
Your card may show up as an "unknown device" if it is not in /var/lib/misc/pci.ids.  You can look yours up at the official source: [http://pciids.sourceforge.net/iii/?i=10de](http://pciids.sourceforge.net/iii/?i=10de), then add it to /var/lib/misc/pci.ids in the appropriate place, or download pci.ids from that website and replace /var/lib/misc/pci.ids


2. Follow the Ubuntu 5.04 Starter Guide instructions to install the NVIDIA drivers [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) - here's the important part
```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

```

3. Add nvidia to /etc/modules so it will load at startup
```

sudo gedit /etc/modules

```
Add to the end
```

nvidia

```

4. Add agpgart and intel_agp to the hotplug blacklist so they won't load at startup
```

sudo gedit /etc/hotplug/blacklist

```
Add the following to the end:
```

agpgart
intel_agp

```

5. Edit /etc/X11/xorg.conf (after backing it up)
-In Section "Modules", be sure to comment out GLCore and DRI, but make sure glx is enabled.
-Modify the Section "Device" appropriately for your system.  Mine looks like this:
```

Section "Device"
        Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Driver "nvidia"
        BusID "PCI:1:9:0"
        Option "NvAGP" "1"
        Option  "RenderAccel" "true"
	Option "NoLogo" #This is optional - it will hide the NVIDIA splash screen
        #0 : Disable AGP
        #1 : use NVIDIA's internal AGP support, if possible
        #2 : use AGPGART if possible
        #3 : use any agp support (try AGPGART, then NVIDIA's AGP)
EndSection

```

6. Reboot and enter the BIOS Settings.  Disable the onboard video
7. Unplug your monitor from your onboard video card and plug it into the NVIDIA card
8. If it hangs at hotplug, do a hard-reboot, and when it gets to hotplug again, press CTRL-C and adjust settings.
9. Try to start X
```

sudo gdm

```
10. If that doesn't work you may have to reconfigure X
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by anumeetsoni on 2005-11-12
Oh man ! i cannot tell you how many sleepless nights i've had trying to get linux to run on my damn 845 motherboard with an extra graphics card. i've hunted the net, IRC and a lot of places, some ppl told me to disable hotplug itself, sadly that did put my system up but without the sound/modem and stuff.
I am gonna try your how-to in a while (as soon as i finish downloading latest ubuntu..i have version 4.1), but if it works, and i am pretty sure it will...Man i owe a LOT of thanx to you :) . 
So anyway thanx

---

### Post by DJ_Tobias on 2006-03-06
That worked great! But heres the thing.. I reboot, doesnt hang at hotplug, nvidia loads( as far as I know ) but my internet wont connect.. i use ndiswrapper for my wireless connection, i can connect to my essid and put in the key but then when i do dhclient wlan0 is just wont connect... and this far beyond my expertise, any ideas?

---

### Post by kgodoy on 2006-09-23
Wow... this might be an old post, but this FINALLY worked for me following these instructions! I've been trying to get the NVIDIA driver working on my FX 5500 without any luck the whole last week. I tried other distributions and  kept having the same issue. But now it works!!! Next step is XGL/Compiz.

Thanks for the help!

Ken

---

### Post by po0f on 2006-09-24
Me love you long time <3 <3

Seriously, this solution solved several of my problems with my install.  I am eternally in your debt.

---

### Post by SinxarKnights on 2007-01-13
This is just crazy! after a year of searching I FINALLY found this thread. I have an HP a705w with this board and had nothing but trouble trying to get ANY distro to work. All because of the onboard graphics.

---

### Post by captainpotato on 2007-02-23
I've just stumbled upon this thread (thanks, SinxarKnights), but haven't had the same luck as the rest of you.

On a Dapper box with an FX 5200 pci card and the 845G chipset, my attempt goes astray at:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings

When I do the latter one, it uninstalls the former one. If I reinstall the former one, it uninstalls the latter. I've tried carrying on ignoring this (using nvidia-glx, not nvidia-settings), but I'm still having the same problem at hotplug.

Any ideas?

---

### Post by captainpotato on 2007-02-23
To update - I just found the following link that looks like that it should help. Looks like some of the file locations have changed since this thread was started.

Anyway, I'll give this a shot (once I download Edgy, as I may as well go for that instead, whilst I'm at it).

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by captainpotato on 2007-02-24
Another update (so that others may find this whilst searching, I hope) - the aforementioned link does exactly what it's meant to and I can now boot using my FX 5200 PCI card.

Now to solving the issue of why my nvidia installation refuses to use X upon booting, but after re-installation it is fine, yet breaks again after a reboot :P

---

### Post by sjust on 2007-03-10
I want to say thank you. This and a few minor tweaks and my PCI graphics card works on a five year old HP. THANK YOU

---

### Post by saphyrre on 2007-04-28
Awesome article, man, you have no idea how many hours i've spent trying to fix the damn nvidia.. i use the latest ubuntu 7.04, and the only thing i changed in your guide was the driver's name from "nvidia" to "nv" (have no idea why they've change it). But it works!!! Once again, thanks a lot.

---

### Post by paul527 on 2007-09-29
Thank you so much mstralka! Now I got Ubuntu working great by following some of your instructions. Turns out for my computer I didn't have to go through all the steps. Just a few steps and reboot and it worked. Most likely I just needed nvidia-glx and nvidia-settings and a reconfigure of the xserver-xorg file, and it worked. Thanks again.

---

### Post by Akt on 2007-09-30
I tried your steps on an HP a705w, after readying through your post replies for a user who has the same model and said he got it working.  However, I'm still hung at the hotplug section.  Pressing Ctrl-C does absolutely nothing.

Origninally to get Feisty Fawn installed we had to set ACPI=off, then we were able to install it using the onboard graphics, but would now like to use the GeForce FX 5500 card as it is obviously a better video solution.

Do you have any other suggestions that might help?

Thanks!
Akt

---

### Post by rmjesse on 2007-10-20
In feisty, I had to do a little modification for this.  instead of /etc/blacklist, i put it in a file called bl-nv-agp under /etc/modprobe.d/ - then the file read:
blacklist: agpgart
blacklist: nv_agp

Other than that, this worked perfect!  THANKS THANKS THANKS!!!!!

---

### Post by fearlex on 2007-10-26
The funny thing is that this doesn't work if your card is plugged, and that's my problem, every six month i have to open my computer and remove the nvidia card and make all this process, then put it back and yes it work, but is there a way to blacklist those two modules from the begining, i can't run a live cd on my pc, since those two modules, are compiled inside the Kernel, is there a way to shut them down in the installation process.

 Any ideas ???

---

### Post by slockton on 2008-04-10
I was having a related issue with an FX 5500 and an old business hp (lacking an AGP slot). In a lot of machines you cannot turn off the on-board video, just change the priority so that PCI video cards are used before the on-board. When ubuntu tries to boot and recognises both video cards a kernal panic happens and locks up the machine.

What you have to do to get round this problem is described here: [http://ubuntuforums.org/showthread.php?p=4640049#post4640049](http://ubuntuforums.org/showthread.php?p=4640049#post4640049)

Basically, you have to blacklist agpgart and intel_agp. It fixed my FX5500 problem.

So, if youhave tried this fix and the computer still hangs at boot, go back to using the on-board video and change the blacklist settings...

Ste

---

### Post by Jessica Lynn on 2008-04-12
Thank you so much for this wonderful thread!  Last night I spent HOURS trying to fix this video card problem with no luck.

I have a prebuilt (last time I make that mistake)  1009189Gateway GT5238E Media Center Computer
Ubuntu: Gusty Gibbons, 7.10
PCI slot video card: GeForce FX 5500, 256mb

What I did to try and solve this is I removed the geforce card used to onboard card to boot into ubuntu (otherwise it got stuck and I couldn't access command lines or anything).  I followed all of the instructions listed by Mstralka and CaptainPotato's link, and tried changing the driver from "nvidia" to "nv"... nothing is working.  It still gets stuck :(

Any more ideas? Ps, can you make any suggestions as detailed for beginners as possible?  I'm still pretty new to this :)  

OH I wasn't able to figure out how to get into a non-graphical boot for ubuntu by default.  When I booted in recovery mode all it did was run numbers all night; they were too fast to read :(  This was a different error than what happened before; before it would do a kernel panic.

---

### Post by theaceoffire on 2008-04-20
I wish I had found this when trying to fix my ATI card...
However, now that I know this, I should have less problems in the future! Thanks!

---

