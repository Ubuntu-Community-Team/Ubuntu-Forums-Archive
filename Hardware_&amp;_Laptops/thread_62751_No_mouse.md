---
title: "No mouse"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by chuckd on 2005-09-05
I wanted to try linux so I obtained a copy of Ubuntu version 5.04.  I installed the software, but the mouse doesn't work.  The mouse works fine under Windows.  The mouse is an optical mouse and I notice that after Ubuntu booted that the red  light on the mouse was off.  I rebooted and noted the light was on until the  "loading modules" was displayed then the red mouse light turned off.  This is an  older computer PIII 600 Mhz and the mouse plugged into the PS/2 port.  So did I do something wrong during the installation?   Is there  a easy way to fix it?   Since  I'm not a linux user I will need explicit step by step instructions.

chuck

---

### Post by s_p_a_r_k_y on 2005-09-05
hi chuck, can you post the output of the following two commands?

cat /etc/modules

and 

dmesg

and paste them in here so we can take a looksie

---

### Post by chuckd on 2005-09-06
cat /etc/modules

#/etc/modules: kernel modules to load at boot time.
#
#This file contains the names of kernal ....
#at boot time ....

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse


Well that part wasn't too hard as I could just type it in.  The dmesg command outputs a lot of text.  I can redirect the output to a file, but don't know how to transfer the information to Windows to paste it here as you suggest.  Sorry, I'm really not very well versed in linux.  I did look through the output and found this info for the mouse

mice: PS/2 mouse device common for all mice
input: ImExPS/2 Generic Exp;orer Mouse on isa 0060/serio1

If you can tell me how to get the output file from linux to windows I'd would be more than happy to post it here.

I appreciate you taking your time to try and help me.

chuck

---

### Post by chuckd on 2005-09-09
I sort of figured out my problem.  I download simplyMepis and tried it.  It offer to boot using the 2.4 kernal for older hardware and 2.6 for new hardware.  If I use the 2.6 version the mouse doesn't work.  If I use the 2.4 verison the mouse works fine.  Since the ubuntu 5.04 uses the 2.6 kernal (I think), suspect that is my problem.  Thanks for trying to help.

chuck

---

### Post by MeanRoy on 2005-09-09
I have Ubuntu 5.04 installed, works fine with an old "no name" mouse.
However, The old mouse (and I mean REALLY old) doesn't work very well, sticky even after cleaning. 

I purchased a GE optical mouse. It's just a "cheapie" but works fine with Win2K.

Ubuntu does not apparently recognise it. No mouse at the login screen.

I looked around to see if I could, perhaps, find a driver for it. Nothing so far.

Do any of you experienced guys think that this problem can be resolved or am I going to be wasteing my time?

If it is just a big time waster, does anyone know of an optical mouse that will work?

Thanks,

Roy.

---

### Post by chuckd on 2005-09-10
That is interesting.  I had just replaced the mouse on that computer with a GE optical mouse.  Perhaps the problem is with the mouse itself rather than the OS.

chuck

---

### Post by Granji on 2005-09-10
Okay, so I have an Aopen USB mouse...with optional PS/2 adapter, which has long since been lost...I'm getting aggravated again, because not only now is ubuntu not recognizing my video card, but it no longer allows me to use my usb mouse...which was configured on an fglrxconfig run through as being /dev/input/mice..which worked before...help me please.

---

### Post by chuckd on 2005-09-11
I went out an purchased a cheap non-optical PS/2 mouse and it worked just fine. 

chuck

---

### Post by greenwom on 2005-11-03
The GE mouse is Optical and PS/2.  The xorg.conf file needs to be changed so the mouse is properly recognized.  

I've tried a couple of different settings to get my GE mouse to work but no luck, it still dies at boot.  If you get a PS/2 to usb adapter the mouse will run properly as a USB devcice.  I'm trying to use the PS/2 port.  (if I used my back panel USB for a mouse I'll run out of ports.)

If anyone has found the right option entry for thier GE optical mouse post it !!!! please.

---

