---
title: "Higher resolution in Dell Optiplex cx240"
date: 2009-12-22
forum: Hardware
---

### Post by shivchal on 2009-12-22
Hi.
      I'm using an old Dell Optiplex 240 system; 512MB RAM; 40GB HDD; P4 1.6GHz; don't know the chipset; 
        System is connected to my 32" Sharp Aquos LCD TV (LC-32A33M). I'm getting a resolution of 800x600 though it is capable of much more. I tried reading many posts regarding "How to change resolution?". I tried many methods from changing xorg.conf, installing Nvidia display driver etc. But only had to re-install Ubuntu, as some configuration changes resulted in startup failure. 
        I'll be extremely glad and thankful, if anybody can help me out.

Cheers
Shivchal

---

### Post by Grenage on 2009-12-22
First, chech you are running the proprietary drivers (System/Administration/Hardware Drivers).

Then install the nvidia panel:

```
sudo app-get install nvidia-settings
```

Run it:

```
gksu nvidia-settings
```

Make your changes there, save it and reboot.  If that screws your display, just log into the terminal and:

```
sudo rm /etc/X11/xorg.conf
```

If all else fails, post your monitor make and model, along with the results of:

```
lspci | grep VGA
```

---

### Post by madnessjack on 2009-12-22
All my resolution troubles are EDID related. This post has fixed them all for me [http://ubuntuforums.org/showthread.php?t=316985](http://ubuntuforums.org/showthread.php?t=316985)

And yes, I do use silly TV panels for monitors on occasion :P

---

### Post by shivchal on 2009-12-23
> **Grenage said:**
> First, chech you are running the proprietary drivers (System/Administration/Hardware Drivers).

Then install the nvidia panel:

```
sudo apt-get install nvidia-settings
```


Hi Grenage. 
First. Thanks for your inputs. I checked for the "proprietary drivers" and I couldn't find any installed. I went ahead installing nvidia-settings. When I tried to run the the next step

```
gksu nvidia-settings
```

I get an error 

```
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "
```

When I try running `nvidia-xconfig`, I get invalid command error.

This is the output of "lspci | grep VGA"

```
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF 
```

BTW, I use LCD  32" Sharp Aquos LCD TV (LC-32A33M).

And below is the /etc/X11/xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Shivchal

---

### Post by Grenage on 2009-12-23
Ah, so you have an ATI card, not an Nvidia. First off remove nvidia-settings:

```
sudo apt-get remove nvidia-settings
```

Than take a look here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by shivchal on 2009-12-24
I'm using Ubuntu 9.04 & not Ubuntu 9.10. Is it wise to use the repositories of Ubuntu 9.10?

Shivchal

---

### Post by Grenage on 2009-12-24
You should be able to get it from your current repos, try this:

```
sudo apt-get install fglrx-driver
```

---

