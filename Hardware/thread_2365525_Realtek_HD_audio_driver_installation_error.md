---
title: "Realtek HD audio driver installation error"
date: 2017-07-07
forum: Hardware
---

### Post by parag-93 on 2017-07-07
I wanted to install realtek HD audio driver on ubuntu 14.04 because my sound is too low on default driver. I downloaded the driver from official website of realtek. I found the tutorial from following link-
[http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/](http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/)
I did everything as instructed. Everything goes fine till './configure --with-cards=hda-intel' command. But when I run 'make', it shows me following error at the bottom. I did everything as root.
```
cc1: some warnings being treated as errors
make[3]: *** [/home/parag/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/timer.o] Error 1
make[2]: *** [/home/parag/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore] Error 2
make[1]: *** [_module_/home/parag/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.4.0-83-generic'
make: *** [compile] Error 2
```
Here is the output of 'lspci'.
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330] (rev ff)
07:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
07:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```
Thanks in advance for any help.

---

### Post by CatKiller on 2017-07-07
Why are you trying to compile a driver from source?

Why are you trying to use a Realtek driver when you don't have a Realtek audio device? ```
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
```

---

### Post by Yellow Pasque on 2017-07-07
Realtek hasn't updated their Linux audio driver in years, so it won't build with modern kernels (as you've discovered). It's a dead end.

> Why are you trying to compile a driver from source?

The OP already stated that the default driver has low volume. I would think this would be adjustable in alsamixer.
A better solution for updating the driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
..and use the lts-xenial package if you're running the 4.4 kernel on Trusty.

> Why are you trying to use a Realtek driver when you don't have a Realtek audio device? 
You can't tell what codec is used just from lspci. Alsa info will tell you what codec the user has (and much, much more): [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by CatKiller on 2017-07-07
> **Temüjin said:**
> The OP already stated that the default driver has low volume.

Yeah, no. The OP has stated that his volume is low.

It's a long, long journey from that point to downloading and trying to compile some random source from somewhere on the Internet, designed for hardware the OP may not even have.

There would be all sorts of steps in between, some of which you've already mentioned, like checking the volume settings and identifying the actual hardware. The OP has given no indication of having taken any of those steps.

Instead, it seems likely that the OP has simply gone, "there is some problem with my sound, I'll download some random thing off the Internet," conditioned from using Windows. Taking such a course is universally a Bad Plan, and should be discouraged at every opportunity.

I apologise if this comes across as unnecessarily grumpy. Thinking about what it is that you're trying to achieve and learning the best way to achieve that is an important skill to develop and use.

---

### Post by parag-93 on 2017-07-07
Bad news is there is no sound after trying to install realtek hd audio.
> A better solution for updating the driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
..and use the lts-xenial package if you're running the 4.4 kernel on Trusty.
Then I installed  lts-xenial package you said to install.
But it's not still working. Here is my alsa-info.
[ATTACH=CONFIG]275905[/ATTACH]

---

### Post by efflandt on 2017-07-07
You did not say what hardware you are using to play audio, or what audio source, but laptop speakers are not necessarily all that powerful or may not have full range sound. I just fired up 16.04 on a low end HP laptop and YouTube music videos are not too loud with volume in Firefox and the system at maximum. And some movies have quieter sound and/or wider dynamic range such that they may be difficult to hear at times.

Ubuntu has long supported Realtek and Intel HD video out of the box without having to do anything. But you are not going to get louder or better sound than whatever amplifies or plays it. I can get louder audio connecting the HP laptop with HDMI to the 32" HDTV I normally use as a monitor for my PC. If you do not have that, you might consider headphones or external amplified PC speaker system. I personally use a 2.1 PC speaker system with subwoofer for my PC, since that is better than speakers in the HDTV. And for laptops I have various old PC speakers for analog stereo (3.5 mm jack) from amplified speakers with volume, bass, treble, to some Dell speakers with no controls, but besides 3.5 mm plug have USB to power some amplification.

And do not take offense if this is not your issue, but I know some people who are hard of hearing and do not realize it. When I visit them they have the TV so loud I have to wear earplugs.

Sometimes when you start tampering with things you reach a point where you do not know how to completely undo what you did. In my case I was trying all sorts of things with graphics drivers and had a bunch of mixed up drivers that I did not know how to resolve and ended up reinstalling Ubuntu. I eventually realized that the cheap graphics card was failing when boot logs of the driver showed that graphics hardware was not responding. Never had that problem again with name brand cards.

---

### Post by Yellow Pasque on 2017-07-07
Yes, the Realtek driver often breaks sound.
First, remove the alsa dkms .deb you installed. (If you want, you can try it again after you have the stock kernel sound working)
From the same directory where you tried to run 'sudo make', run:
```
sudo make uninstall
```

Then reinstall kernel image to restore the files modified/removed by custom Realtek driver:
```
sudo apt-get install linux-image-generic-`uname -r`
```
Sound should work as it did before after reboot.

---

### Post by parag-93 on 2017-07-08
> [COLOR=#000000]Then reinstall kernel image to restore the files modified/removed by custom Realtek driver:[/COLOR]
Cannot reinstall the kernel image. This is the output-
```
E: Unable to locate package linux-image-generic-4.4.0-83-generic
E: Couldn't find any package by regex 'linux-image-generic-4.4.0-83-generic'
```

---

