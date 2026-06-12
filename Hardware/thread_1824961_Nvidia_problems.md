---
title: "Nvidia problems"
date: 2011-08-14
forum: Hardware
---

### Post by littlemissinuka on 2011-08-14
Hello, 

I've read through quite a few threads on here and tried all the suggested solutions but nothing seems to work. 

I have the nVidia additional driver installed and activated, although does say that it's not in use at the bottom, but from reading through the forums that seems to be a bug. 

I then try to go to nVidia settings but I get a dialog box saying: 
> 
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


Then I try to run that in terminal and I get:
> 
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



When I restart after that, the laptop just hangs and does not start X. So I have to go to terminal and replace xorg.conf wiht a backup and I'm back to square one. 

My laptop is a Novatech laptop and everything else on it works perfectly. My graphics card is a NVIDIA GT520M. 

I'm pretty sure this isn't right but all I have in my working xorg.conf file is: 
> 
Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection



I have a few questions:
How do I know if my graphics card is compatible with Linux?
How do I know which nVidia version to use?
How do I know if my nVidia card is really in use or not?

Any help on how to get nVidia working would be great! I'm trying to set up dual monitor but it's all going wrong without it.. 

Thank you!
Inuka.

---

### Post by realzippy on 2011-08-14
You have an optimus laptop?
what does
```
lspci |grep VGA
```

show?

---

### Post by littlemissinuka on 2011-08-14
Thank you for the quick reply! :)

How do I know if my laptop is an optimus laptop?

This is the output I get from lspci |grep VGA:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0ded (rev a1)

---

### Post by realzippy on 2011-08-14
> **littlemissinuka said:**
> 
How do I know if my laptop is an optimus laptop?

Now you know:
> **littlemissinuka said:**
> 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0ded (rev a1)
Read this,then you know the whole story:
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

---

