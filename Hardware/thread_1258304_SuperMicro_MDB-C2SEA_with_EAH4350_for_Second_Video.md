---
title: "SuperMicro MDB-C2SEA with EAH4350 for Second Video"
date: 2009-09-04
forum: Hardware
---

### Post by mslinn on 2009-09-04
The system boots fine and X works using the one monitor at a time only. What must I do to make lspci report both the on board video adapter and the  video card at the same time?

The motherboard is a [SuperMicro MBD-C2SEA]("http://www.supermicro.com/products/motherboard/Core2Duo/G45/C2SEA.cfm") with integrated video, and works well with Ubuntu 64 bit Jaunty. I just installed an [ASUS EAH4350]("http://usa.asus.com/Product.aspx?P_ID=sikN0jmrkCWmk1oD&content=specifications") video card so I can add a second monitor. The video card has an ATI HD 4350 chip set and a PCI Express  2.0 16x connector. I bought this card after reading a [customer testimonial]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16814121310") stating that it worked fine with Ubuntu.

I set the AMI BIOS to boot from the on board video because X tried to use the new video card as the primary device. The AMI v2.61 BIOS setting is found at Advanced / Advanced Chipset Control / North Bridge Configuration / Initiate Graphic Adapter. The default setting is PEG/PCI. When I set it to IGD, lspci did not show the video card. 
```
$ uname -a
Linux ashe 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
$ lspci -nn|grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] 
```Next I tried setting the BIOS to PCI/PEG. The next time Ubuntu started, it ignored the on board video used the 4350 video card instead. Only the 4350 video card was displayed by lspci:
```
$ sudo lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```I rebooted into the BIOS settings, and saw that the 4350 video card was used to display the BIOS settings now.
Seems the default BIOS option was the best option: PEG/IGD, so I went back to that and rebooted. The Ubuntu splash screen appeared, but lspci still only reported the 4350 video card.

I did not use [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Dual.2FMulti_Monitors") to set up the video card. Perhaps this was a mistake. Instead, following [these instructions]("https://help.ubuntu.com/community/RadeonDriver") and [these instructions]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") I tried to remove all of the fglrx drivers and install xserver-xorg-video-ati.
```
$ sudo  dpkg -l '*fglrx*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
pn  fglrx-amdcccle           <none>                   (no description available)
un  fglrx-control            <none>                   (no description available)
un  fglrx-control-qt2        <none>                   (no description available)
un  fglrx-driver             <none>                   (no description available)
pn  fglrx-kernel-source      <none>                   (no description available)
pn  fglrx-modaliases         <none>                   (no description available)
un  xfree86-driver-fglrx     <none>                   (no description available)
pn  xorg-driver-fglrx        <none>                   (no description available)
```Am I trying to do the right thing? I later found [this]("http://forums.gentoo.org/viewtopic-t-781940-highlight-4350.html#5887187"):
> ...nor is ati-drivers compatible with the more recent versions of xorg-x11 and xorg-server. The proprietary ATI driver really lags behind the critical things like kernels and the graphics stack.I edited my xorg.conf to look like this:
```
Section "Device"
        Identifier      "Intel 4 Series Chipset"
        BusID           "PCI:00:02.0"
EndSection

Section "Device"
        Identifier      "Radeon"
        Driver          "ati"
        #lspci does not report a Radeon device so there is no busid
        #BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Monitor"
        Identifier      "Second Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Intel 4 Series Chipset"
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Monitor         "Second Monitor"
        Device          "Radeon"
EndSection

Section "Module"
        Load "glx"
        Load "dri"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Files"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```After all the above, I [discovered]("http://www.phoronix.com/forums/showthread.php?t=18553") this: 
> You should not need to edit the xorg.conf file. Most of the driver behaviour is controlled by a separate file - amdpcsdb. Both amdpcsdb and xorg.conf are set up by the aticonfig --initial command, with parameters for dual-head, multi-GPU etc... 

Did you run "sudo aticonfig --initial=dual-head" after installing the Catalyst driver ? I didn't see that mentioned in the link you posted. If you did not run with the dual-head option, give that a try as a first step. Your symptoms sound as if the driver was initialized as single head rather than dual head. If you have manually edited your xorg.conf file you might want to include the -f option, which allows aticonfig to significantly change portions of the xorg.conf file if necessary.

Let us know whether you want to go with the open source or Catalyst drivers as a first step. If you want to get acceleration working on the open source drivers first, please pastebin your xorg log and dmesg output. If you want to go with the Catalyst drivers, we can go that way as well, but please try the instructions we provide with the driver package. You can either install "natively" or by building packages; recommend that you build packages for Ubunutu then install those packages.

Regarding the open source drivers, Jaunty includes kernel and xf86-video-ati (radeon) support for EXA and Xv acceleration out of the box without needing to install radeonhd. If you don't have 2D acceleration with radeonhd, there are probably leftover bits of the Catalyst driver interfering with the open source kernel driver."Hmm, maybe I should try to undo everything I have done so far. I tried to remove the -ati drivers this way:
```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```I downloaded v9.8 of the Catalyst drivers (91MB) and installed them. The shell script does not require a working X configuration:
```
wget -O ati-driver-installer-9-7-x86.x86_64.run http://www2.ati.com/drivers/linux/ati-driver-installer-9-8-x86.x86_64.run
sudo sh ./ati-driver-installer-9-7-x86.x86_64.run
```A message stating the following was displayed:
> ATI Proprietary Linux Driver 8.64 Installation
You are running a x*6_64 machine with glibc-2.1
Operating System: Debian GNU/Linux (or similar) 5.0Next this:
> Please pick a product to install
1. Install Driver 8.64 on X.Org 7.4 and later releases 64-bit
2. Generate Distribution Specific Driver PackageI picked option 1, the default. After agreeing to the license, I picked the Recommended class of installation. The script worked for a bit, then displayed the following at the command line:
> For further configuration of the driver, please run aticonfig from a terminal window or AMD CCC:LE from the Desktop Manager Menu.
Removing temporary directory: fglrx-install.nqcIIO
I then ran:
```
sudo aticonfig --initial=dual-head --screen-layout=right
sudo aticonfig --glsync-restart
sudo /etc/init.d/gdm restart
```The X display showed alpha transparency which I had not seen before. The system menu showed me an option for ATI Catalyst Control Center (super-user), and when I ran that program it only reported one video adapter. Do I need two ATI cards?

I tried building the package again. This step took a few minutes to execute:
```
]$ sudo sh ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty
Created directory fglrx-install.VicdXE
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.64...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/jaunty
Package /home/mslinn/Documents/xorg-driver-fglrx_8.640-0ubuntu1_amd64.deb has been successfully generated
Package /home/mslinn/Documents/xorg-driver-fglrx-dev_8.640-0ubuntu1_amd64.deb has been successfully generated
Package /home/mslinn/Documents/fglrx-kernel-source_8.640-0ubuntu1_amd64.deb has been successfully generated
Package /home/mslinn/Documents/fglrx-amdcccle_8.640-0ubuntu1_amd64.deb has been successfully generated
Package /home/mslinn/Documents/fglrx-modaliases_8.640-0ubuntu1_amd64.deb has been successfully generated
Package /home/mslinn/Documents/libamdxvba1_8.640-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.VicdXE

```
Why all the AMD64 stuff? Where did that come from?

---

### Post by mslinn on 2009-09-06
ping

---

### Post by mslinn on 2009-11-01
Just did a clean install to Ubuntu 9.10, and ATI Catalyst.  Still can't see two monitors.  Is anyone reading this?

---

### Post by cubicdau on 2009-11-02
Just popped into your thread as I was looking for something about the card itself. Sorry, if i can't help you directly on your problem but I recognised you using Catalyst 9.7 or 9.8 - why so?

[_Here_]("http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English") you can find the recently released 9.10 version (as of 10/22/2009). Maybe that will help ...

I am not sure if this might give you some more details but there had been a bug report on ATI fglrx driver earlier this year at [_bugs.debian.org_]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=521655")

Edit:
Why don't you just use the 4350 for both monitors?

---

