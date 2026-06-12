---
title: "How to get Nvidia-drivers to work on Asus X52J"
date: 2011-01-26
forum: Hardware
---

### Post by ImNoTree on 2011-01-26
Hi!

I recently bought an Asus X52J-laptop and I wish to install Nvidia Drivers, so I can play Heroes of Newerth and use that epic Burg-bootloader.

My Specs:

CPU: Intel Core i3-370M, 2.4 GHz
Graphic card: nVidia GeForce 310M (Cuda, 1GB)

I don't that the other specs are needed for this?
I have searched google about 10 times, and tried different workarounds, with no good result. Either I get the black screen instead of splash /login-screen, or it just says "(EE) No device found, system will be run in low-graphics mode".

I've tried:
* Remove nouveau and nvidia-*, stopping gdm, installing a downloaded driver as root, then starting gdm.
* Blacklisting nouveau and doing the same as above.
* Blacklisting nouveau, remove nvidia-*, installing driver by "sudo apt-get install nvidia-current". 
* Extracting EDID from windows, putting it in /etc/x11 and linking xorg.conf to it, then installing.
* Installing from System->Administration->Hardware Drivers

Probably also a bit of them all mixed together.

None of these have worked for me, is there any way of doing this I haven't tried, or what should i do?

Best regards, ImNoTree

---

### Post by cascade9 on 2011-01-26
Optimus....again. This is getting so common that I'm cut and pasting my response. :( 

At the moment, if there isnt a way to force the nvidia GPU or disable the intel video chip in the BIOS, then no, there is nothing you can do to get the nvidia card going.

---

### Post by ImNoTree on 2011-01-26
That sucks :/

I guess I'll just have to use Windows 7 to play games then...

---

### Post by realzippy on 2011-01-26
> **cascade9 said:**
> Optimus....again. This is getting so common that I'm cut and pasting my response. :( 

At the moment, if there isnt a way to force the nvidia GPU or disable the intel video chip in the BIOS, then no, there is nothing you can do to get the nvidia card going.

Yep,optimus sucks.
Jockey should not offer nvidia-drivers when *lspci grep VGA* returns
nvidia and intel...could not be so hard.

---

### Post by cascade9 on 2011-01-27
> **realzippy said:**
> Yep,optimus sucks.
Jockey should not offer nvidia-drivers when *lspci grep VGA* returns
nvidia and intel...could not be so hard.

It probably should. Or at least give some sort of 'possible issues' warning.

---

### Post by realzippy on 2011-01-27
In fact it is a bug.
Jockey installs wrong driver.
Report?

---

