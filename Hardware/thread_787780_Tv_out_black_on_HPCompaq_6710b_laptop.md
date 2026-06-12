---
title: "Tv out black on HPCompaq 6710b laptop"
date: 2008-05-09
forum: Hardware
---

### Post by mindracer on 2008-05-09
Hi,

I installed Ubuntu Hardy on a Compaq 6710b, so far so good.  Only thing I'm disappointed by is the s-video tv out doesnt work by default, it gives me a black screen.

It detects my TV in Screen Resolutions as an unknown display with 30hz frequency, you see the TV flicker like it should when a computer detects it, but the screen stays black, I tried cloning the screens or putting them next to eachother, still cant get anything on the TV.

Checked the settings in xorg.conf (im a newbie).. Under the device, it doesnt write Intel 965GM (like I have), it writes Default Selected device.. Im thinking the problem is in there, but I dont know exactly what to put in the file for the video card of this laptop

Any ideas?
Thanks in advance

---

### Post by mindracer on 2008-05-09
More info in case someone still wants to help me.. I have an intel 965gm chipset, with X3100 accelerator.

I did a xrandr -q and this is whati get:

saki@saki-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.6*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       30.0* 
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  
saki@saki-laptop:~$ 



Tv is still black :(

---

### Post by mstipanov on 2008-11-03
I have the same problem.

Everithing works fine in windows...

Thanks.

---

### Post by loanrangie on 2009-02-04
> **mindracer said:**
> Hi,

I installed Ubuntu Hardy on a Compaq 6710b, so far so good.  Only thing I'm disappointed by is the s-video tv out doesnt work by default, it gives me a black screen.

It detects my TV in Screen Resolutions as an unknown display with 30hz frequency, you see the TV flicker like it should when a computer detects it, but the screen stays black, I tried cloning the screens or putting them next to eachother, still cant get anything on the TV.

Checked the settings in xorg.conf (im a newbie).. Under the device, it doesnt write Intel 965GM (like I have), it writes Default Selected device.. Im thinking the problem is in there, but I dont know exactly what to put in the file for the video card of this laptop

Any ideas?
Thanks in advance

 How did the install go ? i have my father in laws 6710b and for the life of me i cant load any version of Ubuntu or Kubuntu on it. Just downloading 8.10 and hoping it will load successfully, cant even get XP to install (came with Vista but was wiped prior to purchase).

---

