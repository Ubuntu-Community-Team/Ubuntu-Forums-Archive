---
title: "Monitor Resolution Issues"
date: 2018-03-03
forum: Hardware
---

### Post by uzzo23 on 2018-03-03
About every eight or ten startups I get this error and was wondering if anyone has had the same problem and how to go about fixing it. I've been just restarting it and it'll be fine until about another eight or ten bootups and it does it again. So I thought I'd try and find a solution to it if I could.

---

### Post by cruzer001 on 2018-03-04
Please post your system specs:
```
inxi -b
```
You may have to install it:
```
sudo apt-get install inxi
```
also post
```
xrandr
```

---

### Post by uzzo23 on 2018-03-04
> **cruzer001 said:**
> Please post your system specs:
```
inxi -b
```
You may have to install it:
```
sudo apt-get install inxi
```
also post
```
xrandr
```

```
System:    Host: phillip-OptiPlex-360 Kernel: 4.4.0-67-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: OptiPlex 360
           Mobo: Dell model: 0T656F v: A02 Bios: Dell v: A02 date: 07/02/2009
CPU:       Dual core Intel Core2 Duo E7500 (-MCP-) speed: 2925 MHz (max)
Graphics:  Card: Intel 82G33/G31 Express Integrated Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel G33 GLX Version: 1.4 Mesa 17.2.8
Network:   Card-1: Broadcom NetLink BCM5784M Gigabit Ethernet PCIe driver: tg3
           Card-2: Realtek RTL8169 PCI Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 500.1GB (5.7% used)
Info:      Processes: 188 Uptime: 6:58 Memory: 2496.3/3876.3MB
           Client: Shell (bash) inxi: 2.2.35 

```

```
Screen 0: minimum 8 x 8, current 1440 x 900, maximum 32767 x 32767
VGA1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900      59.89*+
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by cruzer001 on 2018-03-04
> Resolution: 1440x900@59.89hz
So your running a 17" monitor?

Your kernel is seriously out dated, maybe all you need is a update.  Try that first.
```
sudo apt update && sudo apt full-upgrade && reboot
```

```
uname -r
```
That should change it from xxxx.67 to something like xxxx.118

Run the new kernel for a while.  If still giving you trouble, post back.

---

### Post by uzzo23 on 2018-03-04
> **cruzer001 said:**
> So your running a 17" monitor?

Your kernel is seriously out dated, maybe all you need is a update.  Try that first.
```
sudo apt update && sudo apt full-upgrade && reboot
```

```
uname -r
```
That should change it from xxxx.67 to something like xxxx.118

Run the new kernel for a while.  If still giving you trouble, post back.

It's a 19 inch monitor. I went ahead and did the update which I do pretty frequently anyway. It's still showing the same kernel version.

```
phillip@phillip-OptiPlex-360:~$ uname -r
4.4.0-67-generic

```

---

### Post by cruzer001 on 2018-03-04
> It's still showing the same kernel version.
Odd

Please post the output of:
```
apt policy linux-generic linux-headers-generic linux-image-generic
```
and
```
ls /boot
```

---

### Post by deadflowr on 2018-03-05
Was the 1440x900 resolution something that came with it or did you set that up?
It's kind of an oddball/out-of-place resolution.

I would expect several res sizes in between it and the standard 1024x768 res.

---

### Post by uzzo23 on 2018-03-05
> **deadflowr said:**
> Was the 1440x900 resolution something that came with it or did you set that up?
It's kind of an oddball/out-of-place resolution.

I would expect several res sizes in between it and the standard 1024x768 res.

I didn't set it up so I'm assuming it either came that way or ubuntu automatically configured it if that's possible.

---

### Post by uzzo23 on 2018-03-05
> **cruzer001 said:**
> Odd

Please post the output of:
```
apt policy linux-generic linux-headers-generic linux-image-generic
```
and
```
ls /boot
```

```
phillip@phillip-OptiPlex-360:~$ apt policy linux-generic linux-headers-generic linux-image-generic
linux-generic:
  Installed: (none)
  Candidate: 4.4.0.116.122
  Version table:
     4.4.0.116.122 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     4.4.0.21.22 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
linux-headers-generic:
  Installed: (none)
  Candidate: 4.4.0.116.122
  Version table:
     4.4.0.116.122 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     4.4.0.21.22 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
linux-image-generic:
  Installed: (none)
  Candidate: 4.4.0.116.122
  Version table:
     4.4.0.116.122 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     4.4.0.21.22 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

```
phillip@phillip-OptiPlex-360:~$ ls /boot
abi-4.4.0-67-generic         memtest86+.elf
config-4.4.0-67-generic      memtest86+_multiboot.bin
grub                         System.map-4.4.0-67-generic
initrd.img-4.4.0-67-generic  vmlinuz-4.4.0-67-generic
memtest86+.bin

```

---

### Post by cruzer001 on 2018-03-05
Your missing the upgrade packages.
```
sudo apt install linux-generic linux-headers-generic linux-image-generic
```
Followed with:
```
sudo apt update && sudo apt full-upgrade && reboot
```
Now you have a long needed kernel upgrade :)
```
uname -r
```

---

### Post by uzzo23 on 2018-03-05
> **cruzer001 said:**
> Your missing the upgrade packages.
```
sudo apt install linux-generic linux-headers-generic linux-image-generic
```
Followed with:
```
sudo apt update && sudo apt full-upgrade && reboot
```
Now you have a long needed kernel upgrade :)
```
uname -r
```

```
phillip@phillip-OptiPlex-360:~$ uname -r
4.4.0-116-generic

```

Thank you so much! Hopefully that will take care of my monitor resolution issue as well.

---

### Post by cruzer001 on 2018-03-05
> **uzzo23 said:**
> ```
phillip@phillip-OptiPlex-360:~$ uname -r
4.4.0-116-generic

```

Thank you so much! Hopefully that will take care of my monitor resolution issue as well.

That's what I suspect too.  Time will tell.

---

### Post by uzzo23 on 2018-04-13
Well I almost marked this solved last week and forgot about it. I had a  pretty good run this time but my original problem reared its head again  this morning.
[ATTACH=CONFIG]279277[/ATTACH]

---

### Post by cruzer001 on 2018-04-13
Well nuts
Same exact output too

What sort of driver choices do you have?  In terminal:

```
software-properties-gtk
```

Go to the "driver" tab and maybe post a pic of that.

---

### Post by uzzo23 on 2018-04-13
> **cruzer001 said:**
> Well nuts
Same exact output too

What sort of driver choices do you have?  In terminal:

```
software-properties-gtk
```

Go to the "driver" tab and maybe post a pic of that.
Hopefully I'm wrong, but this doesn't look very good to me.

[ATTACH=CONFIG]279286[/ATTACH]

---

### Post by cruzer001 on 2018-04-13
That means there are no proprietary drivers available for your graphics.  The printout in post #3 says your running an intel driver and I assumed there were options.  So that means you should be running xserver-xorg-video-intel.  Please verify that in terminal.

```
sudo lshw -c video | grep 'configuration'
```

and check the kernel

```
lspci -nnk | grep -i vga -A3
```

---

### Post by uzzo23 on 2018-04-14
I'll tell you what, I sure am glad that there are people here that are a lot smarter than me when it comes to this kind of stuff.:D

```
phillip@phillip-OptiPlex-360:~$ sudo lshw -c video | grep 'configuration'
[sudo] password for phillip: 
       configuration: driver=i915 latency=0
       configuration: latency=0

```


```
phillip@phillip-OptiPlex-360:~$ lspci -nnk | grep -i vga -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 0a)
    Subsystem: Dell 82G33/G31 Express Integrated Graphics Controller [1028:0294]
    Kernel driver in use: i915
    Kernel modules: i915

```

---

### Post by Yellow Pasque on 2018-04-14
I think the file in question is ~/.config/monitors.xml , so maybe you want to compare one from a bad boot and a good boot and figure out what's different and what's modifying that file (unity-settings-daemon?).

You may also want to save the /var/log/Xorg.0.log from a bad start and compare it with a good one.

---

### Post by uzzo23 on 2018-04-15
> **Temüjin said:**
> I think the file in question is ~/.config/monitors.xml , so maybe you want to compare one from a bad boot and a good boot and figure out what's different and what's modifying that file (unity-settings-daemon?).

You may also want to save the /var/log/Xorg.0.log from a bad start and compare it with a good one.

I'll certainly try. Can you tell me how to access those files? I found the Xorg.0.log file but I can't seem to find the other one.

---

### Post by Yellow Pasque on 2018-04-15
.config is a hidden directory in your home folder. I don't use Unity/Gnome, so I don't know how to show hidden files in nautilus. Here in xfce/Thunar, Ctrl+H does the trick. Or you could just use the command line:
```
cd ~/
cp .config/monitors.xml goodboot.xml
```

---

