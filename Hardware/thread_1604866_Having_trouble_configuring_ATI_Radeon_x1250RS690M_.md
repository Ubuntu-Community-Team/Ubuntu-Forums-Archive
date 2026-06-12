---
title: "Having trouble configuring ATI Radeon x1250/RS690M with Open Source Drivers"
date: 2010-10-24
forum: Hardware
---

### Post by xovertheyearsx on 2010-10-24
This Article is for those with Either a ATI Radeon Integrated Chipset, the x1200/x1250 RS690M, Series. This Article also applies to those with Toshiba Satellite Laptops. This Article applies sole to Ubuntu 10.04.1 Lucid-Lynx.

***************
* The Problem *
***************
Hello Linux Community!

I'm having trouble configuring my ATI RadeonHD Drivers on my Lucid Lynx Edition!

Again, any help and guidance would be much appreciated!

**************
*The Solution*
**************

AMD/ATI has stated the following...
> AMD has moved a number of DX9 ATI Radeon™ graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.

The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series

AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Now this is a problem, since AMD/ATI should not have done this... but understandably, we must move forward! As Linux Users, we have a lot of information and resources at the tips of our fingers!

It took me awhile to figure this out since I am new to Linux, but the more I use Ubuntu, the more comfortable I feel with it.

With a fresh installation on the A215 and L305D Toshiba Satellite models, Linux drops the Proprietary Settings and Installs its own Open Source Drivers for most of the computers hardware. The only two Drivers that are left out are the Realtek High Definition Sound Card and the ATI Radeon Integrated Video Card which are replaced by the ALSA Driver and the xserver-xorg-radeon driver set.

To narrow down my problem, I've visited the following sites and completed a fresh install of Ubuntu 10.04.1 Lucid Lynx...
```
Read this first for Compatibility information...
http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README
```
```
Read this second for Driver information... 
You can also find the Stable Driver Set or the Latest Driver Set within this document...
https://launchpad.net/~xorg-edgers/+archive/ppa
```
```
 This is the introductory for installation...
https://help.ubuntu.com/community/RadeonHD
```
```
Customize your Video Settings and Configuration...
https://help.ubuntu.com/community/RadeonDriver
```

The Configuration of the Drivers can get a bit tricky, especially since a lot has changed with Karmic Koala(9.10) and Lucid Lynx(10.04). 

Honestly, the Directions are all over the place, so it can become difficult discerning the information thats important.

**Configuring Your Drivers**
What's nice is, that there really isn't much to do. If your Chipset Supports 3D Acceleration, it should work afterwards. I haven't figure that out yet and will up-date this thread once I do. For now, you'll have to deal with the sole 2D Acceleration.

In Lucid-Lynx, A lot of Steps are skipped over which is where the confusion begins. It does a lot of the work for you automatically.

1. After your fresh install, check your Update your copy Linux and restart. 

2. Then open Synaptics Package Manager. There you should Search for ATI or Radeon or xserver-xorg. With each Search, you'll receive slightly differing results. So if you don't see what you want to see, try another.

System -> Administration -> Synaptic Package Manager

3. Make sure none of the fglrx drivers are installed (leave the jockey files alone! they're for proprietary drivers only!). Most likely they won't be there.

4. Close the SPM (Synaptic Package Manager) and open your Software Sources Manager.

System -> Administration -> Software Sources

5. Click on the "Other Software" Tab within the "Software Sources" window. A basic list of PPA's should show up. Click "+Add" and type "http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu" Hit ok and then close. You will be prompted to update, it's highly suggested that you do.

6. Open the SPM again and search for your drivers which you added with the PPA in your "Software Sources" by typing "radeon" in the search bar to narrow down your results.

7. Right-click and select for installation the "xserver-xorg-video-radeonhd" Package. Then install and restart your system and thats pretty much it.

If you'd like to do a little more, you could. By default, the vesa drivers are installed, these are the lowest settings possible and you can change this by alternating to another package.

> By default, Ubuntu will already try to use one of the open source drivers for your hardware. If the feature set and stability work for you, then you don't need to change anything.
The drivers that may be used are:
1. vesa - Lowest common denominator across all graphics vendor, not many features.
2. ati - Actually a facade that will invoke the radeon driver.
3. radeon - Driver support all radeon classes of hardware - with limited 3D for newer cards.
4. radeonhd -  An alternate driver support R520 hardware and later.
By default there is no configuration file for X anymore, so X will try to do the right thing.
If you run into stability problems with 3D applications using the radeon/radeonhd drivers, consider trying a more recent kernel. mainline-2.6.29.3 did the trick on a few machines.
There's an ongoing debate about how and if the radeon and radeonhd drivers will be used in the future. For more information, see [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

The mesa Drivers are a lot better, but less stable and they're included with the xorg-edge packages... so all you have to do is replace them by entering your Synaptic Package Manager:
1. type in vesa, select the vesa drivers for uninstallation
2. type mesa, select the mesa drivers for installation...
and you're done. Afterwards, close all your windows and restart your computer and you should be all set. For any further information you can visit these sites...

1. [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Hardware_requirements](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Hardware_requirements)
2. [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

By the Way!!! There is no more xorg.conf file as of Lucid Lynx!

> By default there is no configuration file for X anymore, so X will try to do the right thing.

So don't be surprised when you can't find your xorg.conf file. You can set up the Xserver so that it does have one, but you'll have to play with the settings and follow the guides above. If you make any mistakes, you'll notice after you restart your computer and have the option to debug or revert to your initial settings.

Good Luck... If any information comes out on the 3d acceleration, please let me know as I am still trying to figure that one out myself!
--------------------------------
Good-bye Blue Screen of Death :mad:... Hello Linux :popcorn:

---

### Post by xovertheyearsx on 2010-10-24
> By default there is no configuration file for X anymore, so X will try to do the right thing.
^^ Source > [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Well, that answers that question! :)

---

### Post by alswar on 2010-11-01
Hello,

thanks a lot for your guide but i think i need further help.
I have a MSI X410 which is using RS690M with X1250.
I followed your procedure but it's not exactly brand new installation (10.04), just installed 4 days ago and updated everything. I'm a newbie in Linux :(

Anyway everything seems fine with normal activity but for example if I try to put a YouTibe video on full screen is a disaster... I think i'm having a couple of frames per second.

Do you have any suggestion or any other try that can explain better the situation?

I'm just trying everything to avoid to be pushed to install Windows :(

---

### Post by xovertheyearsx on 2010-11-06
My apologies for taking so long to respond, i've been busy...
> **alswar said:**
> Hello,

thanks a lot for your guide but i think i need further help.
I have a MSI X410 which is using RS690M with X1250.
I followed your procedure but it's not exactly brand new installation (10.04), just installed 4 days ago and updated everything. I'm a newbie in Linux :(

Anyway everything seems fine with normal activity but for example if I try to put a YouTibe video on full screen is a disaster... I think i'm having a couple of frames per second.

Do you have any suggestion or any other try that can explain better the situation?

I'm just trying everything to avoid to be pushed to install Windows :(

***************************
* to answer your question *
***************************
You need to keep a few things in mind before you go through this check-list... first off, Mobile Integrated Video Cards ARE NOT Stable on linux. 

Linux overall has made many impressive improvements with there compatability with laptops, but overall, if you're looking for complete stability, consider running linux on your desktop first. 
I personally like having a mobile version of linux, but i do notice an improvement on my desktop vs my laptop. 

second, its better to keep a lighter load on smaller spec computers (such as laptops)... suggested for laptops, esp. newbies, is to install the Desktop 32bit Version of the Ubuntu OS. These 32bit versions require less processor power and less ram of up to 4gigs of RAM... the 64bit version uses more power and can provide up to 8+gigs of RAM!

but i looked up your model and i noticed your laptop has a ATI® Mobility Radeon HD 5430 Intergrated Card... Im not sure, so you can actually run this in the commandline and find out exactly what your hardware set-up is, especially for your video card!

```

go to Applications -> Accessories -> Terminal
type:
lspci -k
and hit enter.
```

after you should see results like this
```

0:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Kernel modules: ati-agp
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Kernel modules: shpchp

```

this information is important because it identifies your exact model and this can help tell you if your running the right drivers or not and what you can do to improve it. if you have anymore questions, feel free to ask. this was the best i could do with the information you gave me about your set-up.

If you need any more help, ill see what i can dig up. just post your results and that should be enough for me to verify what you may or may not need.

---------------------------------------
+Extra Info
---------------------------------------
also, make sure you've installed your flash-plugins from the software center, this helps with flv videos, such as youtube.

video is choppy even on my laptop, but im running on lower specs... 
and i haven't had that problem. the video is slightly lossy and i get lines across my screen on occasion, nothing unbearable though.

make sure you have your radeonHD driver enabled/installed and you should have full 3D Acceleration as well.

If you want compiz, this enables the famous desk-top cube, visit your synaptic package manager and type *compizconfig* and install the Compiz Config Settings Manager. From then you can access your visual settings for your OS by going to System -> Preferences...

---

### Post by alswar on 2010-11-10
Thanks a lot mate for taking care of a poor newbie :)

The video card is the X1250 even if it's showing X1200.
So I reinstalled completely Lucid using the 32bit this time as suggested.
I did the updates suggested and install the drivers for the wireless card.

Everything else is as installed

And here the lspci -k

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Kernel modules: ati-agp
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
    Kernel modules: shpchp
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
    Kernel driver in use: ahci
    Kernel modules: ahci
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
    Kernel driver in use: ohci_hcd
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
    Kernel driver in use: ohci_hcd
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
    Kernel driver in use: radeon
    Kernel modules: radeon
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
    Kernel driver in use: rt3090
    Kernel modules: rt3090sta

```I've just seen that the one installed is xserver-xorg-video-radeon/ and not the radeonhd but i'm quite sure on the previous installation i was using radeonhd. If I install this one shall i deselect the xserver-xorg-video-radeon/ from synaptic package manager?

Thanks again for the help!

---

### Post by alswar on 2010-11-13
I followed these instructions [http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664) and flash at least SD Videos are smooth, still slow for 720p.

Currently I'm using the radeon drivers from the original repository.

I've seen few problems in the past using radeonhd and mesa

---

### Post by xovertheyearsx on 2010-12-01
> **alswar said:**
> Thanks a lot mate for taking care of a poor newbie :)

The video card is the X1250 even if it's showing X1200.
So I reinstalled completely Lucid using the 32bit this time as suggested.
I did the updates suggested and install the drivers for the wireless card.

Everything else is as installed

And here the lspci -k

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Kernel modules: ati-agp

--This is Important:
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
    Kernel modules: shpchp

--Tells you your type of gpu

--This is Important:
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
    Kernel driver in use: radeon
    Kernel modules: radeon
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

--Tells you the model version of your gpu


```
I've just seen that the one installed is xserver-xorg-video-radeon/ and not the radeonhd but i'm quite sure on the previous installation i was using radeonhd. If I install this one shall i deselect the xserver-xorg-video-radeon/ from synaptic package manager?

Thanks again for the help!

No Problem for the help, I spents more time trying to figure this out than i wanted to... trust me. 

Leave the other drivers alone, and install the HD driver... everything should work fine after you install the Compiz Manager.
The screen flickers here and there, but its do-able and i like linux enough to put up with it. :popcorn:

-Good Luck

---

### Post by xovertheyearsx on 2010-12-01
> **alswar said:**
> I followed these instructions [http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664) and flash at least SD Videos are smooth, still slow for 720p.

Currently I'm using the radeon drivers from the original repository.

I've seen few problems in the past using radeonhd and mesa

Since I've started using them, I've had little to no issues :)
A little glitchy here and there, but nothing i cant handle
They did an amazing job on the drivers

---

