---
title: "[SOLVED] NVIDIA GeForce FX5500 / Compaq Presario SR1103WM Problem"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by Rastan836 on 2007-03-10
I've been checking out Linux for a couple years now, but just recently decided to get serious about it. Been trying out various distros on an older PC, ran across Ubuntu, loved it and decided to make the big move and migrate from Windows to Linux on my main comp.

I've run into a few snags, most of which could be attributed to just getting to know Linux and feeling comfortable with it :) -- So, have been easily resolved with just a bit of google searching.

There is one major problem, however, that I have not been able to solve. It is with my NVIDIA GeForce FX 5500. This is a major problem that I must figure out -or- (a) purchase another, more compatable GFX card, or (b) go back to ---- ;)  (not something I want to do).

I'll try to explain as much as I can about what I've tried, errors I've gotten and my hardware setup:

Should probably start with the last bit...


Comp Model:
    Compaq Presario SR1103WM 

CPU:
    Intel Celeron D 325 (2533MHZ)

Motherboard:    
   MSI MS-6577 ver. 4.1 board

Chipset:
   Intel Brookdale-G i845GEV

BIOS:
   AWARD BIOS 05/17/04 -- not much can be done here-- but can provide more info if needed.

Memory:
   1 GB (PC3200 DDR SDRAM)

PCI:
   56HP92-D  modem
   NVIDIA GeForce FX 5500 (128MB)

Storage:
   Seagate ST3320620A (320GB)
   Seagate ST360015A (60GB)


For sound and Ethernet, I have gone back to the onboard, mainly because I have only 3 PCI slots and want to keep them free.



When attempting the initial install of Ubuntu, -- (and also note that what I tried with Ubuntu, I tried with many other distros as well-- FC6, Suse 10.2, etc) -- I kept getting this error: "Unknown interrupt or fault at EIP XXXXX", The XXXXX is a number I did not write down, but could easily get again :) :( ... it did vary from distro to distro, sometimes simply rebooting... but this error would occur right at the start of attempting to load the kernel.

Bit of searching, told me to try some options. The one that got me past that was ACPI=OFF. Doing this, the kernel begins to load, but once it scans PCI devices (this was shown attempting a Xandros install), and hits the NVIDIA, it just locks up. Other options such as PCI=BIOS,BIOSIRQ didn't help either. Something else I read to try, was to disable the PnP in BIOS.. still, no good.

The only way to have a successful install was to switch to Onboard GFX.. this worked fine even with the NVIDIA still in. I spent alot of time after installing, switching back and forth between the Onboard and the NVIDA, installing drivers and basically driving myself mad :) This proved to be quite pointless, as I would still always get the same error way before Xorg loads the driver.

I decided about a week ago to just put this on hold until I can find a clear answer and have just been working on other configuring with Ubuntu using the integrated gfx. But, I did have a thought the other day to try the NVIDIA in my older comp (a custom built 500mhz), which does not have onboard gfx, but just an older AGP card.. the NVIDIA worked perfect in this and without the need to use any boot options.

I keep thinking that it's the Onboard GFX interfering.. in the BIOS, I can select which to use as primary.. Onboard or PCI.. when I select PCI for the NVIDIA, the Onboard is still present.. I have no other options with this BIOS -- I checked into getting a BIOS upgrade, full version.. but $50, while may not sound like alot to many, is alot for me.. just as purchasing a new GFX card is.

If I've made some false assumptions about how the Linux kernel loads, etc, please forgive and correct me.. just trying to learn all this.

ANY help will be greatly appreciated!

Thanks!

---

### Post by teaker1s on 2007-03-10
charged for bios upgrade? have you tried live update tool as described in this thread
[http://forums.extremeoverclocking.com/showthread.php?t=132602]("http://forums.extremeoverclocking.com/showthread.php?t=132602")

ask if the motherboard suffers this on msi forums here
[http://www.msi.com.tw/html/service/forum/index_lan.htm]("http://www.msi.com.tw/html/service/forum/index_lan.htm")

---

### Post by al1b1 on 2007-03-10
Had the exact same problem as you and i got it solved by 

1) Switch to onboard graphics and install ubuntu (if dosnt work try acpi=off)
2) Boot into ubuntu under onboard graphics and run the envy script - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
3) to install the envy script you need module assistant which you can get from here - [http://packages.debian.org/unstable/devel/module-assistant](http://packages.debian.org/unstable/devel/module-assistant)
4) After running the eny script open up konsole and type - sudo nano -w /etc/modprobe.d/blacklist
5) add "blacklist agpgart" and "blacklist intel_agp" at the bottom
6) press ctrl x to exit and save
7) Now type in - sudo gedit /etc/modules
8) Add nvidia to the bottom, save and exit.
9) Now type in - sudo gedit /etc/hotplug/blacklist
10) Add "agpgart" and "intel_agp" to the bottom
11) Save and exit

Now the fun begins in editing the x.org file

12) open x.org - sudo nano -w /etc/X11/xorg.conf
13) Find the section device that lists your graphics intel graphics card
14) Make that section look like this
"Section "Device"
        Identifier "GeForce FX 5500"
        Driver "nvidia"
        #BusID "PCI:1:9:0"
        Option "NvAGP" "1"
        Option  "RenderAccel" "true"
EndSection

15) Find the section below that says "Screen"
16) Edit the Device row that currently lists your intel integrated card to "GeForce FX 5500'
17) Save and exit "ctrl x"
18) Reboot and change the bios to nvidia graphics card
19) Pray and hope that ubuntu loads properly
20) If dosnt then run  - "sudo dpkg-reconfigure -phigh xserver-xorg"

If you have any troubles email me at [email]al1b1.watch.it@gmail.com[/email]

---

### Post by Rastan836 on 2007-03-11
Thanks, al1b1 !!! I followed step by step your instructions and now have it working :)

Wasn't sure at first looking at the steps, as I had tried everything, I thought, aside from envy... but perhaps I missed something before or was the envy script.. (I may have only added to one blacklist before as well?).

Point is, it's working and I'm very thankful for the help!

---

