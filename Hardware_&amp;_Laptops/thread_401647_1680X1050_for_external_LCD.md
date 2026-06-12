---
title: "1680X1050 for external LCD"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by villindesign on 2007-04-04
Hello - I know there are tons of post related to external monitors. I have a dell 700m and I am using the 915 package to get 1280x800 on my notebook's LCD. I connected a Samsung 206bw to the VGA and use Fn+F8 to direct the output to the external screen. I changed the resolution to 1024x768 so that the external monitor would display something readable, but the native resolution is 1680x1050. I don't know how to modify my xorg.conf file to get an option of running just the external monitor at 1680x1050. 

I am not trying to run both screens at one, each with its own resolution (though that would be nice). If anyone knows how to do this, or knows of a good description on how to modify the xorg config file, I would be happy to hear from you. Thanks.

---

### Post by villindesign on 2007-04-04
by the way, my ddcprobe output is:
```
britt@britt-laptop:~$ sudo ddcprobe
Password:
vbe: VESA 3.0 detected.
oem: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)852GM/852GME/855GM/855GME Graphics Controller Hardware Version 0.0
memory: 16192kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 027c
eisa: SAM027c
serial: 4d453230
manufacture: 2 2007
input: separate sync, composite sync, sync on green, analog signal.
screensize: 43 27
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1680x1680@60
ctiming: 1280x1024@60
ctiming: 1280x960@60
ctiming: 1152x864@75
dtiming: 1680x1050@59
monitorrange: 30-81, 56-75
monitorname: SyncMaster
monitorserial: HVFP102683

```
The first monitor is the LCD attached to the notebook and the second is the external monitor. As you can see, 'dtiming: 1680x1050@59' is listed.

---

### Post by villindesign on 2007-04-05
I reinstalled 915 resolution and now I have the option of 1600 x 1200, 1280 x 1024 and a few others. on 1600 X 1200, I have to scroll the screen to see everything. 1280 x 1024 works OK. Any way to get it up to native resolution (1680 x 1050)?

---

### Post by Angry penguin on 2007-04-23
try this thread:

[http://ubuntuforums.org/showthread.php?t=406100&highlight=1680+x+1050](http://ubuntuforums.org/showthread.php?t=406100&highlight=1680+x+1050)

---

