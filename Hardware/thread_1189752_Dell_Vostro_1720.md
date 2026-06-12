---
title: "Dell Vostro 1720"
date: 2009-06-17
forum: Hardware
---

### Post by nielz on 2009-06-17
I just got a Dell Vostro 1720 and installed Ubuntu on it. I'm posting this so others will know what to expect (and I hope to get some help with the remaining issues).

* Installation of Ubuntu hung unless I used safe graphics mode
* The keyboard + touchpad often only works after I've rebooted a couple of times. The keyboard works fine in grub and the bios though.
* When I use the headphone jack the laptop's speakers don't turn off. I think this is due to [Bug 382836]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382836"). (Fixed, but only in karmic).
* My wifi has mysteriously disappeared after working fine for a few days.

My specific config has (I took this from the order confirmation):
* Dell Wireless 1397 Mini Card (802.11 b/g) European
* Intel® Core™2 Duo Processor P8600 (2.4GHz, 1066MHz FSB,3MB L2 cache)
* 512 MB NVIDIA® GeForce™ 9600M GS Graphic Card Black

---

### Post by jay_tee on 2009-06-22
Concur - there may be a problem with the new hal updates and wifi on Dell Vostro.

I just allowed Update Manager to download the hal-related updates (and only those updates) to my Dell Vostro 1520, and it nuked the wifi (now greyed out in NetworkManager). The wifi had been happily working for the past 3 weeks, but now. . . :frown:

---

### Post by jay_tee on 2009-06-22
Confirmed - using the methodology as explained by jzurawski99 (thanks ! :D) here:

[INDENT][http://ubuntuforums.org/showthread.php?t=490250](http://ubuntuforums.org/showthread.php?t=490250)[/INDENT]

I backed out the hal updates from
**0.5.12~rc+git20090403-0ubuntu3 **
to 
**0.5.12~rc+git20090403-0ubuntu1**. 
I then rebooted, and my Vostro 1520 immediately reconnected to my wifi network as in the past.

So it is looking as there is something odd with hal 0.5.12~rc+git20090403-0ubuntu3 and the Dell Vostro. . .

---

### Post by rmhartman on 2009-06-27
> **nielz said:**
> I just got a Dell Vostro 1720 and installed Ubuntu on it. I'm posting this so others will know what to expect (and I hope to get some help with the remaining issues).

[snip]

* The keyboard + touchpad often only works after I've rebooted a couple of times. The keyboard works fine in grub and the bios though.

[snip]



Ok.  I'm trying with a Vostro 1310 and the keyboard and touchpad do not work, as you said.  Did you find a fix?

---

### Post by Vesperatus on 2009-07-02
> **nielz said:**
> I just got a Dell Vostro 1720 and installed Ubuntu on it. I'm posting this so others will know what to expect (and I hope to get some help with the remaining issues).

* Installation of Ubuntu hung unless I used safe graphics mode
* The keyboard + touchpad often only works after I've rebooted a couple of times. The keyboard works fine in grub and the bios though.
* When I use the headphone jack the laptop's speakers don't turn off. I think this is due to [Bug 382836]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382836"). (Fixed, but only in karmic).
* My wifi has mysteriously disappeared after working fine for a few days.

My specific config has (I took this from the order confirmation):
* Dell Wireless 1397 Mini Card (802.11 b/g) European
* Intel® Core™2 Duo Processor P8600 (2.4GHz, 1066MHz FSB,3MB L2 cache)
* 512 MB NVIDIA® GeForce™ 9600M GS Graphic Card Black

Confirmed. 
I just received my 1720, installed jaunty. Wireless, touchpad, keyboard, etc, it all worked. The sound was not working.

I updated , rebooted and lost wifi, keyboard and touchpad. Sound was okay, but even that seems intermittent. 

I reverted hal, libhal and libhal-storage and I now have my keyboar, my wifi , my touch pad AND sound back.

---

### Post by Vesperatus on 2009-07-02
Bah. Spoke too soon. 

Just rebooted my pc and the Keyboard and Mouse didnt worked. Had to reboot a second time and it was fine.

Couple of things of interests on the 1720 and Jaunty ( with the updates, has of July 2nd 2009 ) :

* My integrated webcam is working. No tweaks to do ( skype and luvcview )
* Latest version of alsa is 1.18rc3 and there was only 1 mixer in alsamixer. Installing 1.20 seemed to fix most of my issues since I can use skype without an issue after the update
* Brightness keys are working
* Volume touch keys are working.
* Play/Pause, Stop , FForward and Rewind keys are working.

Beside the issue with losing keyboard and mouse, once it's booted correctly, everything on that laptop seems available so far.

And that 1900x1200 ultra-crisp display simply kicks-*** !
):P

Let me know if you have questions.

---

### Post by FabriceMG on 2009-07-03
hello

distro : DELL Ubuntu 9.04

I have Dell 1510 wireless

I have same problem

For the wifi, use Wicd , he works fine (Network Manager doesn't work after update)

but for sound , he doesn't work :(

Later

---

### Post by Vesperatus on 2009-07-03
> **FabriceMG said:**
> hello

distro : DELL Ubuntu 9.04

I have Dell 1510 wireless

I have same problem

For the wifi, use Wicd , he works fine (Network Manager doesn't work after update)

but for sound , he doesn't work :(

Later

Did you update Alsa ?

---

### Post by FabriceMG on 2009-07-04
> **Vesperatus said:**
> Did you update Alsa ?

Hello

yes, now it's works

Tutorial : [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

thx

my hardware :

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
```

---

### Post by dimoftheyard on 2009-07-24
Hello,

I installed Jaunty on my Dell Vostro 1720 yesterday, and did all the upgrades. And for me (nearly) everything works out of the box. Sound, wireless network and the webcam did work immediately. Sleep/Hybernate does not, as of yet.

Sound is not comfigured perfectly, as I have hardly any volume controls in kmix, but it does play sound.

I have booted several times, and keyboard and touchpad worked just fine, although they did not work during the installation.

All in all I have to say: Since the somewhat tricky installation is done, the laptop works like a charm. I am astonished how erverything was perfectly detected, very much unlike the descriptions in the forum. I am very, very happy with both the laptop and the operating system! Thank you guys :)

---

### Post by dimoftheyard on 2009-07-25
Ok, now sleep and hybernate work as well, using the closed source nvidia-driver instead of the default (nv?). It just keeps getting better...

---

### Post by moted1 on 2009-07-27
@[dimoftheyard]("http://ubuntuforums.org/member.php?u=880448")

Mind posting the hardware specs of your 1720?  I gathered that you went with the Nvidia graphics card, but I'm curious to see what else 'works out of the box.'


Thanks.

---

### Post by cmreigrut on 2009-08-11
The keyboard/touchpad issue is a known problem.  To fix it, simply add the following to your kernel options (which is usually in /boot/grub/menu.lst):

i8042.reset noapic

---

### Post by Vesperatus on 2009-08-12
cmreigrut, i will try that right away. 

any reason the keyboard / trackpad would start working at the second reboot ?!

---

### Post by Vesperatus on 2009-08-18
Thanks for the tip by the way. That solved my issue with the laptop keyboard and trackpad not being detected.

---

### Post by dimoftheyard on 2009-08-22
Hello,

I'm sorry to post in this old thread. I have a Dell Vostro 1720 with Jaunty and tried to upgrade alsa to get sound working. I tried to avoid compiling it myself and instead installed alsa-base and alsa-utils from Karmic. But after rebooting cat /proc/asound/version still says "Advanced Linux Sound Architecture Driver Version 1.0.18rc3". Can anybody tell me what I need to install, apart from these two packages?

---

### Post by dimoftheyard on 2009-08-22
@moted1

I'm sorry, I should read in the forum more often. My Vostro 1720 has:
 - Intel® Core&#8482;2 Duo Prozessor P8700,
 - no fingerprint reader, so I can't say whether it works,
 - the smaller display (1400x900),
 - the webcam (I'm not quite sure what kind it is, but you can choose only one, and it works fine),
 - 4GB of Ram, which work fine with the server kernel,
 - 512 MB NVIDIA® GeForce&#8482; 9600M GS Graphic Card Black,
 - the "Fixed Internal 8X DVD+/-RW Tray Load Drive", so not the BlueRay drive,
 - no bluetooth,
 - the "Intel Pro Wireless WI-FI 5100 (802.11a/g/Draft-n) MiniCard, European", which was not the default, at least when I bought the laptop. The wireless, too, works fine without any configuration with both WEP and WPA.
I'm sorry to answer so late and hope my post helps somewhat, nonetheless.

---

### Post by Vesperatus on 2009-08-23
Can you post the result of lspci.

I will see If I have the same sound card than you on my 1720.

---

### Post by dimoftheyard on 2009-08-23
lspci says: 
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                                  
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)                                                                              
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                                
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                                
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)Thank you for looking at this.

---

### Post by Vesperatus on 2009-08-23
> **dimoftheyard said:**
> lspci says: 
Thank you for looking at this.

I'll post my spec tomorrow morning when I start my laptop. I'm just too lazy to open my bag tonight :oops:

---

### Post by Vesperatus on 2009-08-24
I think we have the same thing.

Can your add the version of alsa you are using. 

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

```

```
phil@phil-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.

```

```
phil@phil-laptop:~$ uname -r
2.6.28-15-generic

```

---

### Post by dimoftheyard on 2009-08-24
I am using the server kernel, because I have 4 GB of Ram:
```
$ uname -r
2.6.28-13-server

```My Alsa version still is 1.0.18, which is exactly my problem. I installed alsa-base and alsa-utils from karmic, which has version 1.0.20. But even after a reboot it still says 1.0.18.

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
```

---

### Post by Vesperatus on 2009-08-24
> **dimoftheyard said:**
> I am using the server kernel, because I have 4 GB of Ram:
```
$ uname -r
2.6.28-13-server

```My Alsa version still is 1.0.18, which is exactly my problem. I installed alsa-base and alsa-utils from karmic, which has version 1.0.20. But even after a reboot it still says 1.0.18.

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
```


I know you said you do not want to compile you alsa drivers but if you follow these instructions, everthing should go smoothly : [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)


I you have some issues, just go in the 3 compilation folder and do make uninstall

Tadam. Alsa works.

---

### Post by dimoftheyard on 2009-08-24
Ok, that would work. I know that compiling is mostly not a problem, in this case it seems to work quite easily. I just thougt that having the package manager do the job is a much cleaner solution, and since the karmic packages had no critical dependencies... Anyway, thank you for yor quick help! I'll try it out, or post here if I find out how to do it with the packages.

---

### Post by Vesperatus on 2009-08-24
> **dimoftheyard said:**
> Ok, that would work. I know that compiling is mostly not a problem, in this case it seems to work quite easily. I just thougt that having the package manager do the job is a much cleaner solution, and since the karmic packages had no critical dependencies... Anyway, thank you for yor quick help! I'll try it out, or post here if I find out how to do it with the packages.

Let us know how it went. 

By the way, each time a new kernel is going to be install, you will have to redo the make, make install.

I think it would be the same with the packages.

---

### Post by dimoftheyard on 2009-08-26
I did not yet try the compilation, and I wouldn't recommend following the howto exactly. One could at least have the sources in /usr/local/src, as I thought this was exactly what /usr/local/ was for. Also the file INSTALL in alsa-driver-1.0.20/ says
> If you have already a system with ALSA init script, you should install just only modules via 'make install-modules' so that the existing init script won't be replaced.

Anyway, I got it working with packages from karmic, although this is not as easy as I had hoped. I installed libasound2 from karmic and after it still did not work I (finally) figured I needed the kernel from karmic. I am not entirely sure this is the only way, but it works with the generic-pae kernel from karmic (support for 32bit server kernels has been dropped, but generic-pae is exactly what I need). I tried various things (including installing from the alsa-source package with module-assistant) before but my alsa version never changed.

The new kernel from karmic has other problems, though. Currently it does not seem to detect my wireless card. But I still have to look into this problem, there should be a solution for it. Hopefully... :)

Anyway, thank you for your help. I must admit, that you probably were right and compiling from the sources is the easiest way to update alsa ;)

---

### Post by Vesperatus on 2009-08-26
> **dimoftheyard said:**
> 
Anyway, thank you for your help. I must admit, that you probably were right and compiling from the sources is the easiest way to update alsa ;)

Glad you got it working.

But did I understand right and you managed to get sound but lost wireless ? :lolflag:


Compiling would have been easier indeed :P

---

### Post by deymious on 2009-09-07
I've been having trouble with my 1520, which I think may be related to this. It seems every so often Grub crashes on load, so I can't get up to the selection screen. I read elsewhere this can be caused by bad keyboard input on boot. It seems that maybe this keyboard/touchpad problem may be more than an inconvenience. When this happens to me I can't do much other than reinstall to rewrite Grub.

---

### Post by Vesperatus on 2009-09-07
> **deymious said:**
> I've been having trouble with my 1520, which I think may be related to this. It seems every so often Grub crashes on load, so I can't get up to the selection screen. I read elsewhere this can be caused by bad keyboard input on boot. It seems that maybe this keyboard/touchpad problem may be more than an inconvenience. When this happens to me I can't do much other than reinstall to rewrite Grub.

Do you have vista installed on a second partition ? Because I do and it's the fourth time today I have to reinstall grub. Each time is after I boot vista...

---

### Post by TheFlow on 2009-09-14
Hi everybody. To get it out of the way, here are the specs for my vostro 1720:

Intel Core 2 Duo P8600(2,4GHz,1066MHz,3MB)
4 GB of RAM
512 MB NVIDIA GeForce 9600M GS BLACK
INTEL Wi-Fi Link 5300
_NO_ Blue Ray

Everything worked out of the box, but I'm still having trouble with GRUB and the keyboard (sometimes)

GRUB seems to shoot itself in the leg sometimes, especially after booting into Vista (64- Bit Enterprise). It just hangs and restarts the laptop if no other bootable device is found. I correct this every now and then with the GRUB Super Disk, it is fixed in two minutes, so no biggie, but a permanent solution would be nice.

I applied the 'i8042.reset noapic -fix' but the keyboard still won't go to work sometimes. But here is what got my attention: I had a two hour train ride today, and GRUB killed itself again, but I had the GRUB Super Disk with me, so i tried to boot from it and fix GRUB. But my touchpad and my keyboard wouldn't work (even after the fourth reboot), so I postponed that until I got home. At home, I tried it again, again, no touchpad and no keyboard. Then I plugged in the power cable, and voila, keyboard and touchpad were waiting for input.

My worst case scenario would be something like this: meeting with a potential costumer (I'm in WLAN penetration business) and I can't get any OS running.

So, any help would be appreciated.

---

### Post by eshwar_andhavarapu on 2009-11-11
> **nielz said:**
> I just got a Dell Vostro 1720 and installed Ubuntu on it. I'm posting this so others will know what to expect (and I hope to get some help with the remaining issues).

* Installation of Ubuntu hung unless I used safe graphics mode
* The keyboard + touchpad often only works after I've rebooted a couple of times. The keyboard works fine in grub and the bios though.
* When I use the headphone jack the laptop's speakers don't turn off. I think this is due to [Bug 382836]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382836"). (Fixed, but only in karmic).
* My wifi has mysteriously disappeared after working fine for a few days.

My specific config has (I took this from the order confirmation):
* Dell Wireless 1397 Mini Card (802.11 b/g) European
* Intel® Core™2 Duo Processor P8600 (2.4GHz, 1066MHz FSB,3MB L2 cache)
* 512 MB NVIDIA® GeForce™ 9600M GS Graphic Card Black
I've got the same configuration except processor is T5870 and not P8600. I installed Karmic 64-bit and everything works out of the box except graphics card and wireless. the hardware drivers need to be enabled for this. After the hardware drivers are enabled, everything works. It seems the card reader is not working but that's a small issue i suppose. Not sure why people having problems with jaunty

---

### Post by eshwar_andhavarapu on 2009-11-11
just forgot to mention there. the laptop seems to run a littlle hotter in ubuntu compared to windows. seems the fan speed control is different. the fan does run so atleast nothing to worry about.

---

### Post by LordDelta on 2010-01-25
Just installed Ubuntu 9.10 on a Vostro 1720 recently.

Nearly everything worked out of the box, except the wireless and graphics. Graphics were an easy fix, just install the drivers, however wireless continues to be elusive.

Not absolutely essential that I have the wireless, I am dual booting with Windows 7 and can virtualize the Ubuntu if I need to, getting wireless that way, however it would be nice to get the wireless working natively.

I've tried the WifiDocs, I have a driver, the driver is installed, the device is present, but it doesn't seem to be enabled. When I get to step 4.3 here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection)

I am missing the wireless device.

Help would be appreciated, I realise wireless is an iffy subject on Linux.

---

### Post by cmreigrut on 2010-01-26
Which wireless card did you get with your 1720? I've had no problems at all with Ubuntu recognizing mine...

---

### Post by LordDelta on 2010-01-26
It's a Dell wireless 1510 wireless-n wlan card, which as far as I can tell is the Broadcom 4322 chipset, which is about what Ubuntu told me.

Its not that the drivers aren't loaded, however no Wireless networks show up (I know there are about 4 different ones in my area), and using other wireless programs as well as the command line, no wireless devices show up. I have a switch to turn the card on or off on the side of the laptop, however I am pretty sure it is not off, due to the light on the chasis being on, as well as it working in Windows 7.

---

### Post by Danilo Cunha on 2010-03-08
Hello, I just got a Vostro 1720. I am using Ubuntu 9.10. For now every thing is working fine except for the webcam. Neither skype or cheese recognized the webcam. I am a beginner in the linux world. Any help is welcome. Thanks.

---

### Post by chandra on 2010-04-10
> **LordDelta said:**
> 

Not absolutely essential that I have the wireless, I am dual booting with Windows 7 and can virtualize the Ubuntu if I need to, getting wireless that way, however it would be nice to get the wireless working natively.

I've tried the WifiDocs, I have a driver, the driver is installed, the device is present, but it doesn't seem to be enabled. When I get to step 4.3 here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection)

I am missing the wireless device.

Help would be appreciated, I realise wireless is an iffy subject on Linux.

Have you tried installing wicd? ```
sudo apt-get install wicd
```It replaces the default networking manager.

It has helped me with my desktop which now works flawlessly using the wired connection when it exists, and wireless when there is no wired connection, switching automatically.

Although I have no laptop experience, I think trying out wicd on your laptop might help solve your problem.

HTH.

---

### Post by asamios on 2013-03-16
Hello,

I have a dell vostro 1720 with windowns vista bussiness and with virtualbox i installed ubuntu 12.10 version. i have problems with graphics and sounds. it works very slow. I'm very new with linux software and i'm asking you what can i do or how can i update the drivers for the graphics.

---

### Post by overdrank on 2013-03-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

