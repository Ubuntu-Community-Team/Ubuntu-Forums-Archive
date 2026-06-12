---
title: "How to have both nvidia propitiatory drivers, and intel drivers at the same time?"
date: 2011-04-01
forum: Hardware
---

### Post by Meow27 on 2011-04-01
It has come to my understanding that ubuntu 10.10 uses noveau drivers, and they are not compatible with the propiatary nvidia drivers without screwing around with your system.

The way I understand it is that if you manage to install nvidia drivers, your machine will only be able to function on that gfx card because all other display services had to be deleted


Here is what I'm interested in: I want to use my intel card when Im _away from home_,
then restart my machine, with nvidia graphics when I'm _at home_.

**Can someone tell me how i can do this?** Im running a thinkpad t410 with nvidia optimus. Through the BIOS, I have the ability to physically switch to use optimus, nvidia only, or intel only.


search has given me very vague results and at this point, i need somebody to tell me.

thanks in advance.
-meow

EDIT: the card is an nvidia quadro NVS 3100m

2ND EDIT: i want to use the latest nvidia drivers.

---

### Post by fela on 2011-04-01
[http://sixteennet.co.uk/google/linux%20optimus](http://sixteennet.co.uk/google/linux%20optimus)

NVIDIA seem to be saying that they have no plans for Linux support on Optimus.

Seems like the end of NVIDIA/Linux compatibility.

---

### Post by beew on 2011-04-01
I don't know, uninstall the Nvidia driver when you are not using it? 

I had a similar question a while back.
[http://ubuntuforums.org/showthread.php?t=1559432]("http://ubuntuforums.org/showthread.php?t=1559432")

Maybe you would find some useful hint in mhgsys's post (#6) It was far above my level (and still is)

---

### Post by beew on 2011-04-01
> **fela said:**
> [http://sixteennet.co.uk/google/linux%20optimus](http://sixteennet.co.uk/google/linux%20optimus)

NVIDIA seem to be saying that they have no plans for Linux support on Optimus.

Seems like the end of NVIDIA/Linux compatibility.

Lucky guy has a T410 and he CAN use either card with a BIOS switch. 

There will still be compatibility if you 1) don't use Nvidia on laptops or 2) buy a really high end one which costs a lot $$$ (Nvidia cards which are 3d -vision capable apparently don't use Optimus, but 3d -vision is not supported for Linux unless you get a Quadro card) 3) Get a laptop with a BIO switch like the Thinkpads. 

But it really sucks, please write to Nvidia
[http://ubuntuforums.org/showthread.php?t=1712278]("http://ubuntuforums.org/showthread.php?t=1712278")

---

### Post by Meow27 on 2011-04-01
> **beew said:**
> I don't know, uninstall the Nvidia driver when you are not using it? 

I had a similar question a while back.
[http://ubuntuforums.org/showthread.php?t=1559432]("http://ubuntuforums.org/showthread.php?t=1559432")

Maybe you would find some useful hint in mhgsys's post (#6) It was far above my level (and still is)

from the looks of it, i have to spend 5 minutes just to switch it every time. this isn't a solution, its a hassle.

> **beew said:**
> Lucky guy has a T410 and he CAN use either card with a BIOS switch. 


yup ^^

---

### Post by beew on 2011-04-01
> **Meow27 said:**
> from the looks of it, i have to spend 5 minutes just to switch it every time. this isn't a solution, its a hassle.



yup ^^

It is a hassle if you go back and forth a lot(that's why I ended up not doing it. :)) But if you are doing the switch only between trips then it is not so bad. You can remove the Nvidia driver from Synaptic and reinstall it with jockey, takes lot less than 5 minutes. :) I have tried that. :)

You don't need to kill the Intel driver, it is the Nvidia one that gives the hassle.

---

### Post by Meow27 on 2011-04-01
> **beew said:**
> It is a hassle if you go back and forth a lot(that's why I ended up not doing it. :)) But if you are doing the switch only between trips then it is not so bad. You can remove the Nvidia driver from Synaptic and reinstall it with jockey, takes lot less than 5 minutes. :) I have tried that. :)

You don't need to kill the Intel driver, it is the Nvidia one that gives the hassle.

but you are talking about the supplied drivers. i want the up to date ones... maybe i should have mentioned that.

---

### Post by beew on 2011-04-01
> **Meow27 said:**
> but you are talking about the supplied drivers. i want the up to date ones... maybe i should have mentioned that.

I got mine from the xswat ppa, it is updated enough yet still stable (I am runing 270.XX beta as it is on 10.10, don't want anything more 'updated"!). Otherwise you can get it from xorg-edger ppa which is even more up to date but it may break your machine. I don't install from Nvidia, too much troubles and it is a real hassle to have to reinstall after each kernel update.

---

### Post by oldfred on 2011-04-02
Someone posted this, I have not used it:

Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

### Post by Meow27 on 2011-04-02
> **oldfred said:**
> Someone posted this, I have not used it:

Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

Ok so I tried installing the nvidia driver and my fears have come true. my intel driver no longer works correctly. This isn't a problem since i loaded off ubuntu off my external disk, but as a test i still need to continue

I made the /etc/rc2.d/S01nvidia-xconfig file like this (and yes its executable)
```
#!/bin/bash
# copy appropriate xorg.conf for your videocard
cp /etc/X11/default.conf /etc/X11/xorg.conf
if lspci | grep "VGA compatible controller: nVidia" 
then
	# nVidia card
	nvidia-xconfig
fi
if lspci | grep "VGA compatible controller: ATI Technologies" 
then
	# ATI card, loading opensource ati driver
	cp /etc/X11/ati.conf /etc/X11/xorg.conf
fi

if lspci | grep "VGA compatible controller: Intel Corporation" 
then
	# Intel Card loading driver
#	cp /etc/X11/ati.conf /etc/X11/xorg.conf [COLOR="Blue"]// this isn't where the intel driver is located :'([/COLOR]
fi
```

From where do I take intel xorg configs and place em into xorg.conf?

---

### Post by oldfred on 2011-04-02
ON my Intel 945 chip I have no xorg at all. So you just rename the xorg to some other name so there is no xorg. Or you can just put out a generic xorg with little or no settings.

---

### Post by Meow27 on 2011-04-02
> **oldfred said:**
> ON my Intel 945 chip I have no xorg at all. So you just rename the xorg to some other name so there is no xorg. Or you can just put out a generic xorg with little or no settings.

alas compiz (and i fear everything 3D related) doesn't work at all without an xorg.conf. the generic one that was automatically made did not do anything either. (Xorg -configure gave me completely messed up results)

**I need something that will make my intel card work as it did before I installed the nvidia driver.**

---

### Post by Meow27 on 2011-04-02
So i did some tweaking, I CAN switch graphics cards without screwing over too hard (meaning no additional commands)
[B][SIZE="3"]
but i still cant run compiz on my intel card![/SIZE][/B]

```
#!/bin/bash

if lspci | grep "VGA compatible controller: nVidia" 
then
	# nVidia card
	nvidia-xconfig
fi

if lspci | grep "VGA compatible controller: Intel Corporation" 
then
	 #Intel card doesnt use xorg, so kill it.
	rm /etc/X11/xorg.conf
fi

``` (/etc/rc2.d/S01nvidia-xconfig)

---

### Post by Meow27 on 2011-04-02
In suspicion that the swat-ppa screwed with the system too much, I made a new install and tested installing the nvidia driver directly. Apparently nvidia finally included a script to disable noveau drivers, so the nvidia binaries are usable again! :D

but to my disappointment, I lost control over my brightness switcher (with the nvidia driver), and was no longer able to adjust it via gnome or my lappy. :/


when i switched to the intel card again, i had the same problem; compiz no longer worked.

how do i fix the intel issue :'( ?????

---

### Post by oldfred on 2011-04-03
I have not had problems with my nVidia recently. But early it was suggested to blacklist nouveau.

Perhaps the scripts are automatically blacklisting drives that may conflict and you have to undo that?

Check status of 
sudo nano /etc/modprobe.d/blacklist.conf

---

### Post by Meow27 on 2011-04-03
> **oldfred said:**
> I have not had problems with my nVidia recently. But early it was suggested to blacklist nouveau.

Perhaps the scripts are automatically blacklisting drives that may conflict and you have to undo that?

Check status of 
sudo nano /etc/modprobe.d/blacklist.conf

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

the nvidia driver said something about disabling the noveau drivers. ill look into where that was.

---

### Post by C.S.Cameron on 2011-04-03
There is a program in the repositories named "switchconf".
It can be used to switch between xorg.conf at startup.
This was handy back when xorg.conf loaded video drivers.
You could choose to load Nvidia drivers or not.

---

### Post by Meow27 on 2011-04-03
> **C.S.Cameron said:**
> There is a program in the repositories named "switchconf".
It can be used to switch between xorg.conf at startup.
This was handy back when xorg.conf loaded video drivers.
You could choose to load Nvidia drivers or not.

my concern is specifically how to get intel gfx working again.



as for the brightness issue, i fixed it with a custom xorg.conf

---

### Post by Meow27 on 2011-04-03
> **oldfred said:**
> I have not had problems with my nVidia recently. But early it was suggested to blacklist nouveau.

Perhaps the scripts are automatically blacklisting drives that may conflict and you have to undo that?

Check status of 
sudo nano /etc/modprobe.d/blacklist.conf

ok so i did a reinstall on a seperate drive and found where the file is. its in 
/etc/modprobe.d/nvidia-installer-disable-nouveau.conf
its contents are ```
# generated by nvidia-installer
blacklist nouveau
options nouveau modeset=0
```



so... what does noveau have to do with intel?

---

### Post by Meow27 on 2011-04-04
ok I'm on my intel card and i have tried to the following
remove xorg.conf
remove /etc/modprobe.d/nvidia-installer-disable-nouveau.conf (described above)

Compiz will STILL not work on the intel card. I am baffled as to why this would be.

---

### Post by C.S.Cameron on 2011-04-04
> **Meow27 said:**
> ok I'm on my intel card and i have tried to the following
remove xorg.conf
remove /etc/modprobe.d/nvidia-installer-disable-nouveau.conf (described above)

Compiz will STILL not work on the intel card. I am baffled as to why this would be.

As mentioned above, xorg.conf no longer loads video drivers, If it did you could use switchconf to load, not load video drivers.

Edit:
With a Live USB you need to load compiz each time you boot, go to startup and make a startup named compiz.

---

### Post by Meow27 on 2011-04-04
> **C.S.Cameron said:**
> As mentioned above, xorg.conf no longer loads video drivers, If it did you could use switchconf to load, not load video drivers.

Edit:
With a Live USB you need to load compiz each time you boot, go to startup and make a startup named compiz.

but i already did that, removing the xorg.conf file and the noveau blacklist technically should revert the system back to normal. are you saying otherwise?


also, with liveCDs, intel compiz already works

---

### Post by Meow27 on 2011-04-05
bump.....

---

### Post by C.S.Cameron on 2011-04-05
> **Meow27 said:**
> bump.....

In versions after 8.04 xorg.conf is not used to load video drivers, they are loader before xorg.conf is read, I think.

---

### Post by Meow27 on 2011-04-05
> **C.S.Cameron said:**
> In versions after 8.04 xorg.conf is not used to load video drivers, they are loader before xorg.conf is read, I think.

Ive already said i deleted xorg.conf

---

### Post by oldfred on 2011-04-06
Have you tried booting recovery mode and reconfigure graphics? That may reinstall something, not sure.

---

### Post by Meow27 on 2011-04-06
> **oldfred said:**
> Have you tried booting recovery mode and reconfigure graphics? That may reinstall something, not sure.

how would i do this?

---

### Post by oldfred on 2011-04-06
Can you boot at all?

If so at grub menu, choose recovery mode and it gives some choices on recovery.

If you do not get menu because you have only one system you have to hold shift key down from BIOS boot until menu appears.

---

### Post by Meow27 on 2011-04-08
> **oldfred said:**
> Can you boot at all?

If so at grub menu, choose recovery mode and it gives some choices on recovery.

If you do not get menu because you have only one system you have to hold shift key down from BIOS boot until menu appears.

ill try doing this, but this doesnt look like a solution.

my objective is to get both cards working :(

ill get back to you guys

---

### Post by Yellow Pasque on 2011-04-08
The problem with Compiz on intel is with the proprietary versions of libgl and libglx used by the nvidia driver. You have to change those in addition to xorg.conf. Maybe this will give you some ideas: [http://phoronix.com/forums/showthread.php?41337-PowerXpress-Support-Notebooks-Under-Linux&p=189617#post189617](http://phoronix.com/forums/showthread.php?41337-PowerXpress-Support-Notebooks-Under-Linux&p=189617#post189617)

---

### Post by Meow27 on 2011-04-09
ok so i tried doing that above commands, but they havent worked at all. instead i had trouble logging into X :/

i even tried placing the code into this file to see if it would solve the problem after multiple restarts. it didn't.

recovery mode also did not make compiz work.

so TL;DR intel still doesn't work, however nvidia does

/etc/rc2.d/S01Nvidia-xconfig (executable)
```
#!/bin/bash

if lspci | grep "VGA compatible controller: nVidia" 
then
	# nVidia card
	cp /home/username/xorg.conf.good.nvidia /etc/X11/xorg.conf
	cp /home/username/nvidia-installer-disable-nouveau.conf.bak /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
fi

if lspci | grep "VGA compatible controller: Intel Corporation" 
then
	 #Intel card doesnt use xorg, so kill it.
	rm /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
	rm /etc/X11/xorg.conf
	update-alternatives --config gl_conf
	update-initramfs -utk all
	ldconfig

fi
```

---

### Post by Meow27 on 2011-04-17
still no avail :(

---

