---
title: "karmic: nvidia brightness and power management"
date: 2009-12-17
forum: Hardware
---

### Post by zyron72 on 2009-12-17
Brightness control via System Settings->Power Management doesn't work anymore when I install the NVIDIA proprietary driver, it does work with the 'nv' driver. I have a tool nvclock that I can use to control the brightness, can this be integrated into the Power Management tool? Another problem is that the Fn+BrightnessUp and Fn+BrightnessDown buttons don't work. When I press them I can see the (blue) progressbar going to 0% or 100% at once, brightness itself is not changed. Any ideas how to get this working properly?

Next are details of my hardware:
1) Kubuntu 9.10 Karmic Koala
2) Samsung Q210 Laptop
3) NVidia
4) GeForce 9200M GS

---

### Post by zyron72 on 2009-12-18
No feedback at all?

---

### Post by serkan_ on 2009-12-29
Also i have the brightness problem :(

I'm using ubuntu 9.10 carmic 64 bit (fresh install)
LG laptop with VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)

Brightness not changing. My function keys stuck at 100% to 90%.

I tried gnome applet, it says cannot get laptop panel brightness
At Power management, brightness setting has no affect.

Editting  /etc/default/grub adding GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor" no change in the brightness 

Any suggestions :confused:

---

### Post by michal.tv on 2009-12-30
I've just installed Karmic on my new and shiny Dell Inspiron 13z (with NVidia GeForce G 105M) and am experiencing exactly the same problems:

- the brightness buttons seem to be received by Ubuntu, but the indicator is stuck
- power settings changes (like dim display on battery power) don't make any difference
- the display is constantly dimmed
- after sleep / wakeup / logout or any X server reload/refresh the screen starts flickering in an odd way

Not sure whether the issues are with the NVidia driver itself or maybe it's a BIOS thing? 

Any help would be more than appreciated.

---

### Post by serkan_ on 2009-12-31
Not a solution but behalf of our eyes

system --> administration --> hardware drivers --> activate the nvidia driver (there is only 185v, so i chose that)

after reboot

system --> administration --> Nvidia  x server settings

Under X server 0, x server color correction drop the brightness level confirm the current change. (Every boot you have to click Nvidia  x server settings to recall your adjustments )

I hope someone post, the proper solution for that.

---

### Post by skelli928 on 2010-01-03
Try downloading the newest nvidia driver 195, from nvidias website.

---

### Post by serkan_ on 2010-01-04
Updated to nvidia's latest driver 190.53, brightness not changing by the function keys. 

Brightness only changes from nvidia x server settings.

---

### Post by realzippy on 2010-01-04
> **serkan_ said:**
> Not a solution but behalf of our eyes

system --> administration --> hardware drivers --> activate the nvidia driver (there is only 185v, so i chose that)

after reboot

system --> administration --> Nvidia  x server settings

Under X server 0, x server color correction drop the brightness level confirm the current change. ([COLOR="Red"]Every boot you have to click Nvidia  x server settings to recall your adjustments[/COLOR] )

I hope someone post, the proper solution for that.

you have to run the nvidiatool with root privileges to make changes permanent:

[B]gksudo nvidia-settings
[/B]
change,apply,save to x configuration file

---

### Post by michal.tv on 2010-01-06
I have installed the NVIDIA beta driver (195.30), but it has not solved my problem. I'm wondering whether the issues are related to the BIOS version, rather than graphics card itself. I'm not sure. 

In my case (Dell Inspiron 13z) I think I'm gonna have to talk to Dell to get a response. Unfortunately at this stage they don't seem to have any BIOS updates for my model. They also (surprisingly) don't support Linux on this model...

---

### Post by luk156 on 2010-01-07
I've the same problem! Dell 13z + karmic

---

### Post by rjklindsay on 2010-01-17
Hi,

I have the same problemm, and a partial solution:
The Fn+Up/Down keys show the brightness bar, but the brightness does not change and the keyboard locks up.
The keyboard lock can be released by pressing Ctrl+F3, followed by Ctrl+F7.

Brightness can only be adjusted from the terminal, using smartdimmer.  I think the command is:
smartdimmer -s 50

My laptop:
Ubuntu 9.10 Karmic,
Samsung R560 laptop,
NVidia GeForce 9600M GT

---

### Post by luk156 on 2010-01-19
Don't work with dell 13z:

smartdimmer -s 50
Unable to shadow the video bios
Error!
Smartdimmer is only supported on certain (HP/SamsungSony/Zepto) laptops using a Geforce 6200/7x00Go/8x00Go. If you want support on your laptop contact the author.

:(

---

### Post by serkan_ on 2010-01-19
Don't work with LG either

sudo smartdimmer -s 50

Error!
Smartdimmer is only supported on certain (HP/SamsungSony/Zepto) laptops using a Geforce 6200/7x00Go/8x00Go. If you want support on your laptop contact the author.

---

### Post by annavp on 2010-02-11
smartdimmer -s 50 works for me
thanks, I only need this when on battery
anna

---

### Post by luk156 on 2010-04-21
I solved!
Add this to yours xorg.conf in section Device:
Option "RegistryDwords" "EnableBrightnessControl=1"

---

