---
title: "Install NVidia GTX 460"
date: 2011-04-16
forum: Hardware
---

### Post by Ventai on 2011-04-16
I'm running Ubuntu (Studio) 10.04 (Lucid) and need to try and get the video output from my motherboard to hook up to my monitor. 

This stems from an earlier attempt to get my NVidia GTX460 to work, it was with installing the community version of the driver (which seemed like, and I was advised was the best option). Essentially, I couldn't access my system after installation. I eventually managed to get a really bad default driver working. 

To install the official NVidia driver was a VERY convoluted process last time I checked, logging out of X-Windows, and a whole bunch of other stuff I haven't got time for right now. 


Further to this, I thought I give this a go:- 

[http://ubuntuforums.org/showthread.php?t=1604741](http://ubuntuforums.org/showthread.php?t=1604741) 

I installed nvidia-current. 

Which then gave me a message I seem to recall:- 

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.Which I did for a 2nd time and got the following: -

> system@ubuntu:~$ sudo nvidia-xconfig
[sudo] password for system: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/QUOTE]

Which then gave me the same error I seem to recall getting previously:- 

> The following error was encountered. You may need to update your configuration to solve this. 

(EE) NVidia: Failed to load the NVidia kernel module.
You may need to 
(EE) NVidia: check the system's kernel logs for additional errors 
(EE) Failed to load module 'NVidia' (module-specific error,0)
(EE) No drivers available Any help would be greatly appreciated . .

---

### Post by Yellow Pasque on 2011-04-16
So what does dmesg say about it, or try and load it manually:
```
sudo modprobe -v nvidia.ko
```

I'm not sure whether the nvidia driver in lucid had support for your card yet, but you can get a recent driver from: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Ventai on 2011-04-17
Upgrading the OS sorted it. . 

Thanks for your time!

---

