---
title: "NVIDIA legacy drivers causing system freeze?"
date: 2008-05-08
forum: Hardware
---

### Post by .haggis on 2008-05-08
Hello!
I'm currently trying to get my NVIDIA GeForce2 MX/MX 400 to work with the binary NVIDIA drivers on Ubuntu (previously using Gutsy, now using Hardy). The problem I'm facing is that everything except the mouse pointer freezes roughly 5 seconds after the desktop has loaded. The only place where it seems to work is on the login screen, where I can fool around by typing in the username box, but if I click the "Options" menu, the system freezes as well.

The driver I'm using is nvidia-glx-legacy, maybe it's the wrong one? I've also tried auto-installing using EnvyNG, but with the same results.

Please, help me solve this! :)

Some information that could be useful (xorg.conf attached)

haggis@wotan:~$ uname -a
Linux wotan 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

haggis@wotan:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

### Post by hermes0710 on 2008-05-08
Is this an agp card? If yes then you must add an option to xorg (I had an agp in the past and i had to add an option like "option NvAGP 0" in the section of the driver)

---

### Post by .haggis on 2008-05-08
I think it's a PCI card (says PCI everywhere), but the fool-proof way would be to open up the case and have a look, so I'll do that :)

So, if the card is not AGP, I should be using "NvAGP" "0", otherwise "NvAGP" "1", right? I will try this out.

Do I have to blacklist anything? I'm reading about NvAGP and AGPGART not working well together, should I blacklist both of them if it's a PCI card? If it's an AGP, should NvAGP be blacklisted?

This looks fine? 

Section "Device"
	Identifier	"Device[0]"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
        Option          "NvAGP" "0"
        Option          "RenderAccel" "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

Thanks!

---

### Post by .haggis on 2008-05-20
Ok, so it's an AGP card. After some fiddling around with the parameters in xorg.conf, I've found that RenderAccel "true" is the culprit. However, while disabling this parameter leads to a stable system, it also leads to slow 2D performance (window resizing is really sluggish)

Is there any way to fix this? How about the Nouveau drivers, anyone with experience of them? I'd gladly sacrifice 3D for snappy 2D performance if neccessary, since I never play games.

---

### Post by Keyper7 on 2008-05-20
If you don't need 3D, wouldn't the nv driver be enough?

It is the driver that was supposed to be used by default after a clean install, if you card was properly detected (sometimes it's not).

nv is supposed to give good 2D performance but no 3D.

---

### Post by .haggis on 2008-05-20
> **Keyper7 said:**
> If you don't need 3D, wouldn't the nv driver be enough?

It is the driver that was supposed to be used by default after a clean install, if you card was properly detected (sometimes it's not).

nv is supposed to give good 2D performance but no 3D.

My experience was that the nv driver (default after a clean install of Hardy as you said) provided no greater 2D performance than what I'm getting now. My reason for installing the nvidia driver was that **it** was supposed to give better 2D performance than nv.

As I forgot to mention, the system is a P4 1.6 GHz with 512 MB RAM.

---

