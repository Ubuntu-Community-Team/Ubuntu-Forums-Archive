---
title: "How Intel 82801H Audio started working on my Dell Inspiron 1520"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by maramot on 2008-04-13
A riveting account on
How I managed to get my own Intel 82801H working yesterday evening.

After I installed from the live CD, the day before yesterday, I had no sound at all (and no wireless but that's another story). So, I had tried everything I could find in the help system and in the forums and nothing was working, I had gone through everything applicable that was listed [here]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller"), I had to take the most unwanted method: Install kernel 2.6.23, according to the instructions given in the [linked thread there]("http://ubuntuforums.org/showthread.php?t=311158").

So I went on downloading and compiling the new kernel as per the instructions but while it was compiling I saw at the beginning of the same instructions thread, that the same guy who was writing the guide for kernel update was also writing a program called "Kernel Check" that was supposed to do all the stuff on updating your kernel automatically. I was like "that's exactly what I needed" so I ctrl+c-ed the still compiling kernel, downloaded the program and gave it a go. It gave me an "Unknown error" message right at the beginning of the questions before it starts compiling though, so after this happened twice, I got disappointed and quit the program.

Some time later I restarted for some other reason and, contrary to my hopes, I got some errors in the startup and was left with the command prompt. 

After the initial shock, I launched ubuntu manually by typing *startx* and once I was back on known territory (and supplied with my wireless internet connection, which seems to be the most important thing, since I didn't have any LAN cables around), I went on updating the packages I was expecting I had broken. Without being very certain of what I'm doing, I installed once again **fast-user-switch-applet** and **gdm** since I was getting errors when trying to log out and I remembered I had to have these uninstalled when I was uninstalling **alsa-utils** before the last reboot which had ended with the console screen. I'm mentioning this because the reinstallation of **alsa-utils** (version is 1.0.14-1ubuntu4) might be related to my sound card beginning to function.

Other things I updated were **linux-generic** (2.6.22.14.21) [[COLOR="Red"]restricted[/COLOR]] from the page: [http://packages.ubuntu.com/gutsy/linux-generic]("http://packages.ubuntu.com/gutsy/linux-generic") The file I downloaded is called "linux-generic_2.6.22.14.21_i386.deb"
I also updated **linux-restricted-modules-generic** (2.6.22.14.21) [[COLOR="Red"]restricted[/COLOR]] the link to this is on the page I just linked to for the previous upgrade, or here it is directly - [http://packages.ubuntu.com/gutsy/linux-restricted-modules-generic](http://packages.ubuntu.com/gutsy/linux-restricted-modules-generic)

I just don't remember wether I also updated **linux-image-generic** (the first "dependent" package for **linux-generic** or simply -- [http://packages.ubuntu.com/gutsy/linux-image-generic]("http://packages.ubuntu.com/gutsy/linux-image-generic")).

Anyway, after I rebooted once again, to test wether I'll stop getting errors or maybe I'll be left at ubuntu's door again, I surprisingly discovered that I can now hear sounds.

Currently, in my Synaptic Package Manager I have the following *and nothing else* installed, when I search (in name and in description) for "alsa":

[B]alsa-utils
gstramer0.10-alsa
libesd-alsa0
libpt-plugins-alsa
libsdl1.2debian-alsa
jack-rack
libao2
libasound2
libmikmod2
linux-sound-base[/B]

The result from the *aplay -l* command:
```
maramot@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I checked to tell you the contents of "/etc/modprobe.d/alsa-base" but it turned out I don't even have such a file :D

My laptop spcifications:
Dell Inspiron 1520

Intel Core II Duo 2.4GHz [(designation T8300)]("http://processorfinder.intel.com/details.aspx?sSpec=SLAPA")
2048 MB DDR2 at 667 Mhz
NVIDIA NB8P-GS 256 MB - [GeForce Go 8600M GS]("http://en.wikipedia.org/wiki/Comparison_of_NVIDIA_Graphics_Processing_Units#GeForce_8M_series")
HDD -- TOSHIBA MK2546GS 250 GB

---

