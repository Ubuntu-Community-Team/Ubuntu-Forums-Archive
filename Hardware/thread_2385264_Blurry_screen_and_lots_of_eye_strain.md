---
title: "Blurry screen and lots of eye strain"
date: 2018-02-18
forum: Hardware
---

### Post by xzenon on 2018-02-18
Hi Guys.
I have been off and on ubuntu no for some time. The reason i go off it is i have never been able to make the screen sharp and it gives me lots of eye strain.
But now i have started to really hate windows 10 and im thinking on staying on ubuntu a while longer. So i would like to have your help with my blurry screen.

when i type sudo lshw -c video i get

```
  *-display                 
       beskrivning: VGA compatible controller
       produkt: GT216 [GeForce GT 220]
       tillverkare: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       bredd: 64 bits
       klocka: 33MHz
       förmågor: pm msi pciexpress vga_controller bus_master cap_list rom
       konfiguration: driver=nvidia latency=0
       resurser: irq:27 memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:cc00(storlek=128) memory:c0000-dffff

```

Yea i know its an old nividia card. Im using the NIVIDA binary drivers - version 340.104 from nividia-340. I hope i got all the information you need to help me out if there is something pls ask. 

So pls help me out here

---

### Post by thehipho on 2018-02-18
You tried the Nouveau driver for your nVidia card, they may make the screen sharper for older cards.

---

### Post by xzenon on 2018-02-18
Yea but it doesn't get mutch sharper.

---

### Post by cruzer001 on 2018-02-18
> I have been off and on ubuntu no for some time.

Maybe its time for a version upgrade.  Please post:

```
lsb_release -a && uname -r
```

---

### Post by xzenon on 2018-02-18
This is what i get typing in lsb_release -a && uname -r
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful
4.13.0-32-generic

---

### Post by cruzer001 on 2018-02-19
Ok, your on the latest release.

Are you given any choice of monitor refresh rate?
```
xrandr
```
[https://askubuntu.com/questions/147580/how-to-see-change-screen-refresh-rate-or-monitor-frequency/155351#155351](https://askubuntu.com/questions/147580/how-to-see-change-screen-refresh-rate-or-monitor-frequency/155351#155351)

Have you tried 16.04?  The download links below use a different kernel that can make a difference.

[64-bit PC desktop image]("http://old-releases.ubuntu.com/releases/16.04.1/ubuntu-16.04.1-desktop-amd64.iso")

[32-bit PC desktop image]("http://old-releases.ubuntu.com/releases/16.04.1/ubuntu-16.04.1-desktop-i386.iso")

And might as well post your system specs.
```
inxi -b
```

---

### Post by thehipho on 2018-02-19
> **xzenon said:**
> Yea but it doesn't get mutch sharper.

Did you make sure Nouveau driver, was not previously blacklisted by nvidia driver?

---

### Post by xzenon on 2018-02-19
Yea i tried 16.04 its the same and the version before it. Both 32 and 64 bits. 

When i type xrandr
> Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
XWAYLAND0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 380mm x 310mm
   1280x1024     74.90*+

And inxi -b
> 
System:    Host: xzenon-Aspire-M5810 Kernel: 4.13.0-32-generic x86_64
           bits: 64
           Desktop: Gnome 3.26.2 Distro: Ubuntu 17.10
Machine:   Device: desktop System: Acer product: Aspire M5810 serial: N/A
           Mobo: Acer model: FMP55 serial: N/A
           BIOS: American Megatrends v: P01-B2C0 date: 03/29/2010
CPU:       Dual core Intel Core i3 530 (-HT-MCP-) speed/max: 1200/2933 MHz
Graphics:  Card: NVIDIA GT216 [GeForce GT 220]
           Display Server: wayland (X.Org 1.19.5 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1280x1024@74.90hz
           OpenGL: renderer: NVA5 version: 3.3 Mesa 17.2.8
Network:   Card: Intel 82578DC Gigabit Network Connection driver: e1000e
Drives:    HDD Total Size: 1160.2GB (25.6% used)
Info:      Processes: 204 Uptime: 2:44 Memory: 1366.8/5952.1MB
           Client: Shell (bash) inxi: 2.3.37 

				 				 					 						 	[**[COLOR=#000000]thehipho i dont know what you mean. Its either [/COLOR]**Nouveau or Nividia and i tried them both and both are blurry,]("https://ubuntuforums.org/member.php?u=798314")

---

### Post by cruzer001 on 2018-02-19
I don't expect to see a change, but I think better to switch from wayland to xorg.

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

### Post by thehipho on 2018-02-19
>  i dont know what you mean. Its either Nouveau or Nividia and i tried them both and both are blurry,


To check nouveau wasn't blacklisted:
```
ls /etc/modprobe.d/
```

---

### Post by xzenon on 2018-02-19
[**[COLOR=#000000]thehipho[/COLOR]**]("https://ubuntuforums.org/member.php?u=798314") i got this. I have no idea what it is.

> alsa-base.conf              blacklist-oss.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf
blacklist.conf              dkms.conf
blacklist-firewire.conf     intel-microcode-blacklist.conf
blacklist-framebuffer.conf  iwlwifi.conf
blacklist-modem.conf        mlx4.conf

[**[COLOR=#000000]cruzer001[/COLOR]**]("https://ubuntuforums.org/member.php?u=2084993")
I dont think it would help to switch to xorg because this blurryness is like the old versions of ubuntu i tried in the past.

---

### Post by thehipho on 2018-02-19
From terminal you can check these files:
```
cat /etc/modprobe.d/blacklist.conf
```

And if found, remove blacklist nouveau:
```
sudo nano /etc/modprobe.d/blacklist.conf
```

---

### Post by xzenon on 2018-02-19
i couldent find blacklist nouveau in blacklist.conf.

---

### Post by thehipho on 2018-02-19
Which driver do you have currently installed?
```
lshw -c video | grep 'configuration'
```

---

### Post by 1clue on 2018-02-19
Is it possible you're using an analog monitor and/or video cable? Or that your resolution chosen is not native to the monitor?

I can't recall ever seeing blurry displays on an all-digital card/cable/monitor combination.

---

### Post by xzenon on 2018-02-19
[**[COLOR=#000000]thehipho[/COLOR]**]("https://ubuntuforums.org/member.php?u=798314")
when i type in lshw -c video | grep 'configuration' nothing shows up.

                                                                                    [URL="https://ubuntuforums.org/member.php?u=799622"][B][COLOR=#000000]1clue
I am using this monitor [/COLOR][/B][/URL][B][COLOR=#000000][http://mobilespecs.net/monitor/Samsung/Samsung_Samtron_91S.html](http://mobilespecs.net/monitor/Samsung/Samsung_Samtron_91S.html)
[/COLOR][/B]

---

### Post by 1clue on 2018-02-20
What cable are you using? Does it use an old-style D-sub connector on either end?

---

### Post by xzenon on 2018-02-20
yea im using an old-style D-sub connector cable.

---

### Post by 1clue on 2018-02-21
So going out on a limb here, I suspect that since you're going from digital (the computer end of your graphics card) to analog (that cable) and then back to digital again (the LCD matrix) there is probably noise/distortion in the chain somewhere, and because of that the blurriness.

IMO if you get a completely digital signal path you're unlikely to have blurriness. Also making sure that the video card is sending out the same resolution as the monitor supports in native mode will help.

---

### Post by xzenon on 2018-02-21
Ok. make sense. But i cant understand why i have never hade any problems like this on windows.

---

### Post by 1clue on 2018-02-22
When you use an analog signal path, the video card can try any resolution and if the monitor can show it you can use it, within limits.

With a CRT monitor, there is an electron beam that hits paint on the inside of your CRT tube, and then the paint glows. The resolution of the monitor depends on the size of those paint particles, the width of the electron beam and the accuracy of the analog controls on the electron beam. There is no exact resolution on those old monitors, but there was a list of supported resolutions. Using some other resolution could possibly damage the monitor because it might cause a signal outside of the capability of the electron gun.

LCD panels have specific cells which are activated in a grid. There is no ambiguity about the native resolution. Alternate resolutions can be had by an algorithm supported by the monitor's firmware, but it's not like a CRT monitor. Often the screen has black edges all around a pretty tiny image, or maybe if the resolution being used is small enough they may treat a 2x2 sqare of pixels as a single pixel to magnify the image. It's possible they may also go to 3x3 or 4x4 and so on.

With a MODERN LCD monitor, the whole thing is digital and you have a digital-only cable. The video card produces a digital signal. The monitor tells the card what the supported resolutions are, and will only accept those resolutions.

With older LCD monitors, they had an analog input. Some types of DVI cables even support analog. So there's this circuit taking an analog signal from your cable, and trying to figure out which pixel to light up how much. The affect is somewhat like having a big grid of, let's say you had a huge egg carton that holds hundreds of eggs. And you have a spray paint gun where the color changes frequently. You're going from left to right and this gun is spraying, and you're trying to hit each hole in the egg carton. The color is supposed to change and be correct for each cell, but there's likely to be some over-spray because you aren't a very good shot and your timing may be off. So one pixel was supposed to be white and the next black, but because of your aim and the simple fact of it being spray paint there's 2 gray cells instead of a white and a black. So the electron beam is like the spray gun. It's not like a laser, more like the spray paint. The center area is  full coverage, the edges get kind of faded out, and there's some over-spray on the edges where there shouldn't be any paint at all.

The analog amplifier is going to be doing the same thing. Every step in an analog signal path adds noise, even your cables. If the noise is insignificant then the digital circuits on the other end give a pretty good representation on your LCD screen. If there's too much noise, or the video card is not using the native resolution supported by the monitor, then you get this over-spray effect.

My guess is that your video card settings on Windows are different from the settings on Linux. There's frequency and resolution that could be off. If you can tweak those items you may get a better picture. I don't know if Linux still supports that sort of thing because I haven't used an analog video component for ... at least 10 years I think. I got on the wagon right away.

---

