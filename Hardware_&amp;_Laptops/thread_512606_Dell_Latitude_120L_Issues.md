---
title: "Dell Latitude 120L Issues"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by sekazi on 2007-07-29
I have have a few issue with Ubuntu 7.04 on my Dell Latitude 120L. I have managed to fix the wireless issue with [this thread]("http://ubuntuforums.org/showthread.php?t=197102") but I am still having problems with the monitor display.

It seems it is stuck at 1024x768 when it should be 1280x800. I have tried dpkg-reconfigure xserver-xorg several times and each time I failed. 

The display supports the following resolutions but it just wont use 1280x800
```
    >> Supported Resolutions
       640 x 400 in  : 256 colours at 60 Hz
       640 x 400 in  : 65536 colours (16-bit) at 60 Hz
       640 x 400 in  : 32-bit at 60 Hz
       640 x 480 in  : 256 colours at 60 Hz
       640 x 480 in  : 65536 colours (16-bit) at 60 Hz
       640 x 480 in  : 32-bit at 60 Hz
       800 x 600 in  : 256 colours at 60 Hz
       800 x 600 in  : 65536 colours (16-bit) at 60 Hz
       800 x 600 in  : 32-bit at 60 Hz
       1024 x 768 in  : 256 colours at 60 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 60 Hz
       1024 x 768 in  : 32-bit at 60 Hz
       1280 x 768 in  : 256 colours at 60 Hz
       1280 x 768 in  : 65536 colours (16-bit) at 60 Hz
       1280 x 768 in  : 32-bit at 60 Hz
       1280 x 800 in  : 256 colours at 60 Hz
       1280 x 800 in  : 65536 colours (16-bit) at 60 Hz
       1280 x 800 in  : 32-bit at 60 Hz
       400 x 640 in  : 256 colours at 60 Hz
       640 x 400 in  : 256 colours at 60 Hz
       400 x 640 in  : 256 colours at 60 Hz
       400 x 640 in  : 65536 colours (16-bit) at 60 Hz
       640 x 400 in  : 65536 colours (16-bit) at 60 Hz
       400 x 640 in  : 65536 colours (16-bit) at 60 Hz
       400 x 640 in  : 32-bit at 60 Hz
       640 x 400 in  : 32-bit at 60 Hz
       400 x 640 in  : 32-bit at 60 Hz
       480 x 640 in  : 256 colours at 60 Hz
       640 x 480 in  : 256 colours at 60 Hz
       480 x 640 in  : 256 colours at 60 Hz
       480 x 640 in  : 65536 colours (16-bit) at 60 Hz
       640 x 480 in  : 65536 colours (16-bit) at 60 Hz
       480 x 640 in  : 65536 colours (16-bit) at 60 Hz
       480 x 640 in  : 32-bit at 60 Hz
       640 x 480 in  : 32-bit at 60 Hz
       480 x 640 in  : 32-bit at 60 Hz
       600 x 800 in  : 256 colours at 60 Hz
       800 x 600 in  : 256 colours at 60 Hz
       600 x 800 in  : 256 colours at 60 Hz
       600 x 800 in  : 65536 colours (16-bit) at 60 Hz
       800 x 600 in  : 65536 colours (16-bit) at 60 Hz
       600 x 800 in  : 65536 colours (16-bit) at 60 Hz
       600 x 800 in  : 32-bit at 60 Hz
       800 x 600 in  : 32-bit at 60 Hz
       600 x 800 in  : 32-bit at 60 Hz
       768 x 1024 in  : 256 colours at 60 Hz
       1024 x 768 in  : 256 colours at 60 Hz
       768 x 1024 in  : 256 colours at 60 Hz
       768 x 1024 in  : 65536 colours (16-bit) at 60 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 60 Hz
       768 x 1024 in  : 65536 colours (16-bit) at 60 Hz
       768 x 1024 in  : 32-bit at 60 Hz
       1024 x 768 in  : 32-bit at 60 Hz
       768 x 1024 in  : 32-bit at 60 Hz
       768 x 1280 in  : 256 colours at 60 Hz
       1280 x 768 in  : 256 colours at 60 Hz
       768 x 1280 in  : 256 colours at 60 Hz
       768 x 1280 in  : 65536 colours (16-bit) at 60 Hz
       1280 x 768 in  : 65536 colours (16-bit) at 60 Hz
       768 x 1280 in  : 65536 colours (16-bit) at 60 Hz
       768 x 1280 in  : 32-bit at 60 Hz
       1280 x 768 in  : 32-bit at 60 Hz
       768 x 1280 in  : 32-bit at 60 Hz
       800 x 1280 in  : 256 colours at 60 Hz
       1280 x 800 in  : 256 colours at 60 Hz
       800 x 1280 in  : 256 colours at 60 Hz
       800 x 1280 in  : 65536 colours (16-bit) at 60 Hz
       1280 x 800 in  : 65536 colours (16-bit) at 60 Hz
       800 x 1280 in  : 65536 colours (16-bit) at 60 Hz
       800 x 1280 in  : 32-bit at 60 Hz
       1280 x 800 in  : 32-bit at 60 Hz
       800 x 1280 in  : 32-bit at 60 Hz
       640 x 480 in  : 16 colours at 1 Hz
       800 x 600 in  : 16 colours at 1 Hz
```

Here is the specs for the monitor and video device

```
    >> Monitor Information #1
      Monitor : Plug and Play Monitor
      Linked on : Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family
      Resolution : 1280x800
      Working desktop : 1280x774
      Main monitor : Yes

  > Monitor Type : Plug and Play Monitor

    >> General Information
      Product ID : QDS0030
      Manufacture : 2005
      Video Input Type : Digital in 0.7/0.3v
      Aspect Ratio : 16:10
      Gamma Factor : 3.55
      DPMS Active-Off : Yes
      DPMS Suspend : Yes
      DPMS Standby : Yes
      EDID version : 1.3     

    >> Features
      Maximum Resolution : 1280 x 800 @ 59 Hz

    >> Video Modes Supported
      Mode : 720 x 400 @ 70 Hz
      Mode : 640 x 480 @ 75 Hz
      Mode : 1024 x 768 @ 87 Hz interlaced

  > Video Card : Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family

    >> General Information
      Manufacturer : Intel Corporation  (Dell Computer Corp)
      Model : 82915GM/GMS, 82910GML Integrated Graphics Device
      Bus Type : PCI
      Total Memory : 128 MB
      Texture Memory : 117 MB
      Processor : Intel(R) 915GM/GMS,910GML Express Chipset
      Converter : Internal
      Refresh Rate (min/max) : 60/60 Hz

    >> GPU Information
      Number of GPU : 1
      Codename : GMA 900 Graphics
      Bus : 64-bit
      Memory Type : DDR
      GPU Frequency : 333 MHz
      Texels : 1332 MTexels/s
      DirectX Support : 9.0
      Pixel Shader Version : 3.0

```

and System Summary

```
<<< System Summary >>>

  > Mainboard : Dell 0RJ272

  > Chipset : Intel i910GML/i915GMS

  > Processor : Intel Pentium M 740 @ 1733 MHz

  > Physical Memory : 512 MB (1 x 512 DDR2-SDRAM )

  > Video Card : Intel Corporation 82915GM/GMS, 82910GML Integrated Graphics Device

  > Hard Disk : FUJITSU (40 GB)

  > DVD-Rom Drive : HL-DT-ST CDRW/DVD GCC4244

  > Network Card : Broadcom Corp BCM440x 100Base-TX Fast Ethernet

  > Network Card : Broadcom Corp BCM4309 802.11a/b/g
```


I hope there is a fix for this because I gave up on Linux for my laptop a few months back when both Wireless and Video did not work. Now that I have wireless working I need the video. I like Ubuntu but these are the kind of issue which make me want to stay away from Linux.

Thanks for the help.

---

### Post by sekazi on 2007-07-29
I no longer need help with the screen resolution. I fix the problem by using 

```
apt-get install xserver-xorg-video-intel
```

It seemed to work perfectly. Now I am able to use 1280x800 without a problem.

Now I can say a Latitude 120L supports Ubuntu. It has Sound, Video, Screen, Touch Pad, Wired & Wireless connection capabilities.

---

### Post by dougfractal on 2007-08-18
> and System Summary

Code:

<<< System Summary >>>

  > Mainboard : Dell 0RJ272

  > Chipset : Intel i910GML/i915GMS

  > Processor : Intel Pentium M 740 @ 1733 MHz

  > Physical Memory : 512 MB (1 x 512 DDR2-SDRAM )

  > Video Card : Intel Corporation 82915GM/GMS, 82910GML Integrated Graphics Device

  > Hard Disk : FUJITSU (40 GB)

  > DVD-Rom Drive : HL-DT-ST CDRW/DVD GCC4244

  > Network Card : Broadcom Corp BCM440x 100Base-TX Fast Ethernet

  > Network Card : Broadcom Corp BCM4309 802.11a/b/g


how did you get this summary?

---

### Post by metyu on 2007-08-18
dell s*cks
this is the only good


[http://s2.gladiatus.hu/game/c.php?uid=17617](http://s2.gladiatus.hu/game/c.php?uid=17617)

---

