---
title: "Can't Install Nvidia GeForce 6600 AGP on Ubuntu8.04.1 64Bit"
date: 2008-08-15
forum: Hardware
---

### Post by extruct on 2008-08-15
Hello, I've Installed Ubuntu 8.04.1 Desktop AMD64it Edition on my Pentium 4 3.0Ghz 64bit HT and tried to install Inno3D Nvidia GeForce 6600 256MB AGP driver in the following ways:
Using Driver Hardware
Using EnvyNG
Using Driver from nvidia site
All of them gave me black screen after rebooting and was fixed using recovery mode xfix, or trough recovery mode root console changing Driver "nvidia" to Driver "nv" in xorg.conf.
I reinstalled the system 4 times, I dug the forum tried everything I found here and on the net, nothing helped.
I don't know what to do...
I'm not on fresh Ubuntu installed all the updates and don't know what to do now.
BTW My monitor is LG flatron l1760tr LCD connected trough DVI.
Please help me!

---

### Post by overdrank on 2008-08-15
> **extruct said:**
> Hello, I've Installed Ubuntu 8.04.1 Desktop AMD64it Edition on my Pentium 4 3.0Ghz 64bit HT and tried to install Inno3D Nvidia GeForce 6600 256MB AGP driver in the following ways:
Using Driver Hardware
Using EnvyNG
Using Driver from nvidia site
All of them gave me black screen after rebooting and was fixed using recovery mode xfix, or trough recovery mode root console changing Driver "nvidia" to Driver "nv" in xorg.conf.
I reinstalled the system 4 times, I dug the forum tried everything I found here and on the net, nothing helped.
I don't know what to do...
I'm not on fresh Ubuntu installed all the updates and don't know what to do now.
BTW My monitor is LG flatron l1760tr LCD connected trough DVI.
Please help me!

Hi and after you install the drivers and receive the black screen are you able to reach the virtual terminal with the keys ctrl, alt, F1. If so try and configure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then sudo reboot. Hopefully this will return you to the desktop with the nvidia drivers working. If not you may look here and try this 
PmDematagoda
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

---

### Post by extruct on 2008-08-15
Hi, well few things:
1. I'm not able to do something during the black screen its just freezing and don't act on key pressed or something else, I can boot in recovery mode and using root console.
2. Well now I'm on fresh Ubuntu, what drivers should I install? System->Administration->Hardware drivers?
Or using EnvyNG? or from nvidia site?

Thanks again.

---

### Post by overdrank on 2008-08-15
> **extruct said:**
> Hi, well few things:
1. I'm not able to do something during the black screen its just freezing and don't act on key pressed or something else, I can boot in recovery mode and using root console.
2. Well now I'm on fresh Ubuntu, what drivers should I install? System->Administration->Hardware drivers?
Or using EnvyNG? or from nvidia site?

Thanks again.

Hi and yes I would try and use the hardware drivers. Then like I posted try and reach the command line with the ctrl, atl, F1 keys all at the same time.

---

### Post by extruct on 2008-08-15
Nop. Nothing, I can log into X but seems like the driver isn't running
```

skwee@dpc:~$ more /var/log/Xorg.0.log | grep "(EE)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
skwee@dpc:~$ 

```

Seems like there are no nvidia kernel module:
```

skwee@dpc:~$ sudo displayconfig-gtk 
on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-KUJX6F8193/xauthority
Got pid 8215
(0, 0)
checkpoint 1
None
False
Sorry, this configuration video card driver
and monitor doesn't appear to work:

Messages from the X server:
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:


```

---

