---
title: "On hybrid laptop/tablet detect when keyboard is disabled."
date: 2013-12-28
forum: Hardware
---

### Post by ferguson.stewart on 2013-12-28
My new laptop (Dell XPS 12) has a screen which flips around.  When that screen flips, the keyboard is disabled. I want to detect when this happens.  I want to do this because I was to enable "Onboard" (on-screen keyboard) on my touchscreen when I am in tablet mode.  I know the hardware must support this because it worked in Windows 8 before I wiped the machine.  This is my dmesg | grep input: 
```
stew@kronos:~$ dmesg | grep input 
[    0.866859] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0 
[    0.866887] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1 
[    0.866924] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[    1.141775] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3 
[    2.066627] input: Dell WMI hotkeys as /devices/virtual/input/input4 
[    2.089640] input: ATML1000:00 03EB:842F as /devices/pci0000:00/INT33C3:00/i2c-0/0-004b/input/input5 
[    2.093280] input: DLL05E3:01 06CB:2734 as /devices/pci0000:00/INT33C3:00/i2c-0/0-002c/input/input6 
[    2.154271] input: Integrated Webcam as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input7 
[    3.728237] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8 
[    3.751526] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9 
[    3.751600] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10 
[    3.751657] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11 
[    3.761875] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12 
[   16.761124] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input13
```  

I've tried  
```
stew@kronos:/dev/input$ ls 
by-id    event0  event10  event12  event2  event4  event6  event8  mice    mouse1 
by-path  event1  event11  event13  event3  event5  event7  event9  mouse0  mouse2 
stew@kronos:/dev/input$ sudo cat event0
```  

I'm able to get keyboard events, mouse events, touchpad inputs, but I haven't found an event that gives me an output when my screen unlatches.  Any advice is welcome!

---

### Post by ferguson.stewart on 2013-12-30
Not sure if "bumps" are disapproved here, but I do need some help.

---

### Post by Toz on 2013-12-30
> **ferguson.stewart said:**
> Not sure if "bumps" are disapproved here, but I do need some help.
We're okay with bumping as long as you give it 24 hours before bumps.

There was a HOWTO written back in February that might be useful. See [here]("http://ubuntuforums.org/showthread.php?t=2116275").

---

### Post by ferguson.stewart on 2014-01-03
Thanks, I tried this out, but Magic rotate didn't run on my system.  It looks like my Dell BIOS is not supported by the MagickExtras packages provided.

---

