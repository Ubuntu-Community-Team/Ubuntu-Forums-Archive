---
title: "Ubuntu Server does not recognize onboard graphic cards (Intel HD Graphics)"
date: 2015-09-11
forum: Hardware
---

### Post by kfir2 on 2015-09-11
[COLOR=#111111][FONT=Ubuntu]I've purchased the Intel NUC5PPYH in order to make it a chrome kiosk. The CPU is Intel Pentium N3700 which has Intel HD Graphics built in. The kiosk is built on top of [/FONT][/COLOR]**Ubuntu Server 14.04.3**[COLOR=#111111][FONT=Ubuntu] with [/FONT][/COLOR]**xorg[COLOR=#111111][FONT=Ubuntu], [/FONT][/COLOR]openbox[COLOR=#111111][FONT=Ubuntu] and [/FONT][/COLOR]google-chrome-stable**[COLOR=#111111][FONT=Ubuntu]**.**

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I got the kiosk running with the following script:[/FONT][/COLOR]
```

#!/bin/bash

xset -dpms
xset s off
openbox-session & 

while true; do
    rm -rf ~/.{config,cache}/google-chrome
    google-chrome  —-disable-translate \
    —-disable-infobars \
    —-disable-suggestions-service \
    —-disable-save-password-bubble \
    —-disable-restore-background-contents \
    —-disable-vertical-tabs \
    —-disable-answers-in-suggests \
    —-disable-extensions \
    —-disable-new-kiosk-ui \
    —-disable-notifications \
    —-disable-plugin-power-saver \
    —-kiosk —-no-first-run ‘somewebsite.com‘
done
```

[COLOR=#111111][FONT=Ubuntu]I also have a conf file in the init.d directory, /etc/init.d/kiosk.conf:[/FONT][/COLOR]
```

start on (filesystem and stopped udevtrigger)
stop on runlevel [06]

console output
emits starting-x

respawn

exec sudo -u USERNAME startx /etc/X11/Xsession /opt/kiosk.sh —-
```

[COLOR=#111111][FONT=Ubuntu]Until this point everything worked exactly as expected. When the chrome browser is launching and I go to[/FONT][/COLOR]**chrome://gpu**[COLOR=#111111][FONT=Ubuntu] I can see that almost every option has the [/FONT][/COLOR]Software only, hardware acceleration unavailable[COLOR=#111111][FONT=Ubuntu] near it. I browsed to [/FONT][/COLOR]**chrome://settings**[COLOR=#111111][FONT=Ubuntu]and ensured that the hardware acceleration is checked. Also, I browsed to [/FONT][/COLOR]**chrome://flags**[COLOR=#111111][FONT=Ubuntu] and made sure to enable the [/FONT][/COLOR]Override software rendering list[COLOR=#111111][FONT=Ubuntu]. Unfortunately, it didn't work. I still see the [/FONT][/COLOR]Software only, hardware acceleration unavailable[COLOR=#111111][FONT=Ubuntu] message.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I tried to google around and look for a solution for this but no avail. I have some suspicious that the Intel HD Graphics driver isn't installed or at-least isn't installed correctly. When I run the command [/FONT][/COLOR]**lspci | grep VGA**[COLOR=#111111][FONT=Ubuntu] I see

[/FONT][/COLOR]```
VGA compatible controller: Intel Corporation Device 22b1 (rev 21)
```[COLOR=#111111][FONT=Ubuntu]

When I run the command:

```
sudo lshw -C video
```

I get

```

*-display:
    description: VGA compatible controller
    product: Intel Corporation
    vendor: Intel Corporation
    physical id: 2
    bus info: pci@0000:00:02.0
    version: 21
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi vga_controller bus_master cap_list rome 
    configuration: driver=i915_bpo latency=0
    resources: irq:312 memory:80000000-80ffffff ioport:f000(size=64)

```

It seems like it says that the clock speed is 33MHz when t[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]he onboard GPU should have 400MHz base speed and burst to 700MHz, which leads me to think that the onboard GPU wasn't recognized. I'm not sure if this has anything to do with the fact that I don't get hardware acceleration.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I would like someone to shine some light on this issue and tell me what I'm doing wrong [/FONT][/COLOR]

---

### Post by Yellow Pasque on 2015-09-11
Some info might be helpful:
link to ALSA info - [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
contents of /var/log/Xorg.0.log (pastebin it or use code tags because it's a lot of text)

> When I run the command lspci | grep VGA I see
That's because your hardware is newer than Trusty's copy of the PCI ID database of names. Run this (once, with internet connection on) to update to the most current database of PCI/USB device names, and then run lspci again:
```
sudo update-pciids
sudo update-usbids
```

> It seems like it says that the clock speed is 33MHz
lshw isn't showing the speed of the GPU, but rather the PCI-e interface. (I forget why it shows 33MHz for PCI-e.) Don't worry about it though. It's not an issue.

---

### Post by afremont on 2015-09-23
To get VAAPI acceleration working in 14.40, I had to add a repository and do an apt-get dist-upgrade after installing a 4.2 kernel.  The kernel was to get rid of assorted dmesg errors and get the wifi working.

What is the output of a vainfo command?  Mine gave me an error after install the required libraries by doing:
sudo apt-get install i965-va-driver libva-intel-vaapi-driver vainfo

This is the developer's page for the repository I had to add to get VAAPI working:
[https://launchpad.net/~wsnipex/+archive/ubuntu/vaapi](https://launchpad.net/~wsnipex/+archive/ubuntu/vaapi)

Here is the command to issue to add it:
sudo apt-add-repository ppa:wsnipex/vaapi

After that, do this:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apg-get install libva1  (for some reason this was being "held back" from auto installing)

After that, the vainfo command gave me all the output that I was expecting instead of an error message.  This made mythv and kodi happy and made the playback look a lot better.  In mythtv, you have to use the opengl painter and not qt, otherwise you get an error when trying to play video or live TV.

I'm going to pen up a HOWTO on getting mythbuntu and kodi working on the NUC Braswell as there are some serious problems with the out-of-the-box software on that hardware.

BTW, you have to install a 4.2 kernel and download wifi firmware from Intel to get things working there.  I got my kernel from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2.1-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2.1-unstable/)
and I got the wifi firmware from here: (AC 3165)
[http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)

---

### Post by adrhc on 2016-02-20
I have a N3150 cpu (Asrock N3150DC-ITX board) with the same problem on ubuntu 15.10.
Linux xxx-desktop 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux.

This is the result after doing/installing every package suggested above (aside of kernel):

xxx-desktop:~$ vainfo
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns -1
libva error: va_getDriverName() failed with unknown libva error,driver_name=(null)
vaInitialize failed with error code -1 (unknown libva error),exit

xxx-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)

xxx-desktop:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:122 memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(size=64)

PS: I'm running XFCE over RDC (remote desktop connection) from windows 7

---

### Post by adrhc on 2016-02-20
[https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0) -> does this has anything to do with our problem ? I installed it (has support for braswell) but nothing changed.

---

### Post by adrhc on 2016-02-21
> **adrhc said:**
> [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0) -> does this has anything to do with our problem ? I installed it (has support for braswell) but nothing changed.
Well, I notice no change when using XFCE with remote desktop from windows 7. But when using directly ubuntu-unity I get in chrome://gpu/:
[h=3]Graphics Feature Status[/h]
[LIST]
[*]Canvas: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Multiple Raster Threads: [COLOR=#008000]Force enabled[/COLOR]
[*]Rasterization: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video Decode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Video Encode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]

---

