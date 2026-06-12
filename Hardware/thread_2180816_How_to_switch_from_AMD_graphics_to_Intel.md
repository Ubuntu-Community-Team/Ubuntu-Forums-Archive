---
title: "How to switch from AMD graphics to Intel"
date: 2013-10-14
forum: Hardware
---

### Post by cem2 on 2013-10-14
Hi everyone. I am a pretty new linux user. So please be as descriptive as possible.

I have Ubuntu 12.04 with Radeon HD 5650 on my laptop. I can easily switch between these two in Windows. I want to be able to switch to Intel HD graphics because AMD causes heating problem and fan runs very noisy. In addition, it is my work computer and i won't be needing any graphics acceleration.

I have a problem with Catalyst driver. When I activate it, I get the error message "running in low graphics mode" on startup. Then I have to switch to the generic driver. I was working on this issue for weeks. I tried many things from the forums but I got nothing. I purged the driver and installed it from AMD website. I caused Linux to crash several times and re-installed it. So that I really don't want to deal with it much. I want to stay on the safe side. So please be sure that it is safe before posting. 

I tried:
```

sudo su -
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```



and I got:
```

-su: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

```

And there is no option about it in the BIOS. What should I do to switch to intel HD graphics?

---

### Post by cem2 on 2013-10-15
up! please help

---

### Post by Bashing-om on 2013-10-15
cem2; Hi !

Sorry, I do not run switchable graphics, so not any direct help.
These links should provide ya the means you seek:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by cem2 on 2013-10-15
Hi Bashing-om

Thanks for your help. First link seems helpful. I will try it tomorrow and comment about the result. There are still many things too complicated for me but I'm trying to get used to.

---

### Post by Bashing-om on 2013-10-15
cem2; Hey .
That "are still many things too complicated for me but I'm trying to get used to" is an ongoing story. No one person knows everything about this wonderful, complex operating system. It is indeed a process of learning, asking the right questions at the right place gets the right answers.

Me ? 

[INDENT][INDENT]I know a little about a few things, continuing to learn and too share
[/INDENT][/INDENT]

---

### Post by cem2 on 2013-10-16
```

>sudo su
    
>grep -i switcheroo /boot/config-*
     /boot/config-3.8.0-29-generic:CONFIG_VGA_SWITCHEROO=y
     /boot/config-3.8.0-31-generic:CONFIG_VGA_SWITCHEROO=y
    
>ls -l /sys/kernel/debug/vgaswitcheroo/
     ls: cannot access /sys/kernel/debug/vgaswitcheroo/: No such file or directory
```


Any suggestions? I have been searching for it. There seems to be nothing really fixes it. All solutions include installing fglrx driver which my pc doesn't like.

---

### Post by Bashing-om on 2013-10-16
cem2; Hey .

this to me:
> 
>ls -l /sys/kernel/debug/vgaswitcheroo/
     ls: cannot access /sys/kernel/debug/vgaswitcheroo/: No such file or directory

indicates that both the cards are NOT powered on. Maybe one of them are turned off in bios ?
Let's see if we can finger out what is not going on.
Terminal codes:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga 

```

Here is one solution, old one but should still apply for the situation that you want to be able to do.

> 
source ->MAFoElffen
Explaination- By turning off the discreet chipset (ATI), it then uses the Intel GPU (physically)... which with the Xorg.conf file still there pointing to the ATI GPU (now switched off), it gets confused.

Solution- If that's what you want to do, after turning off the ATI GPU- rename /etc/X11/Xorg.conf to something else, so that XServer can ID the active GPU (your case Intel) and select a generic driver for it.

What I usually suggest to people is that they make a copy/backup of the Xorg.conf files- One for the installed ATI and one generic pointing to the xorg Intel Driver in the device section... then copying the appropriate one into place when needed.

Mind you I do not know if there presently exist the "/etc/X11/Xorg.conf". so let's look:
```

ls -la /etc/X11/Xorg.conf
##and if that files is in exotence, what does it contain ?
cat /etc/X11/Xorg.conf

```
There may now-a-days exist more elegant solutions, but this at least will give you a working condition.

Until those of greater knowledge notice this thread. I am ->

[INDENT][INDENT]doing what I can to help
[/INDENT][/INDENT]

---

### Post by cem2 on 2013-10-16
no Xorg.conf file


When I open Additional Drivers from "System Settings" it says:


##########
No proprietary drivers are in use on this system. 
ATI/AMD proprietary FGLRX graphics driver (**experimental**beta)
This driver is activated but not currently in use.
##########


> >sudo lshw -C display

```
  *-display               
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:c0000000-cfffffff memory:e6400000-e641ffff ioport:5000(size=256) memory:e6440000-e645ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:6050(size=8)

```

> >lspci | grep VGA

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]

```

> >lspci -nnk | grep -iA3 vga


```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: COMPAL Electronics Inc Device [14c0:004d]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1]
    Subsystem: COMPAL Electronics Inc Mobility Radeon HD 5650 [14c0:004d]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_13, radeon

```



> >ls -la /etc/X11/Xorg.conf


```
ls: cannot access /etc/X11/Xorg.conf: No such file or directory

```



> >/etc/X11# ls


```
app-defaults             xinit                          Xreset.d
cursors                  xkb                            Xresources
default-display-manager  xorg.conf.10152013             Xsession
fonts                    xorg.conf-backup-131015003432  Xsession.d
rgb.txt                  xorg.conf.failsafe             Xsession.options
X                        Xreset                         Xwrapper.config

```



> >cat /etc/X11/xorg.conf.10152013 

```
# Warning: This file is autogenerated by fglrx-pxpress. All changes to this file will be lost.


Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option      "VendorName" "ATI Proprietary Driver"
    Option      "ModelName" "Generic Autodetecting Monitor"
    Option      "DPMS" "true"
EndSection


Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection


Section "Device"
    Identifier  "intel"
    Driver      "intel"
    Option      "AccelMethod" "uxa"
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by Bashing-om on 2013-10-16
cem2; Hey,

Hold my horses ! These say I need to re-arrange my thinking:
[http://linux-hybrid-graphics.blogspot.com/2012/01/improved-support-for-amd-hybrid.html](http://linux-hybrid-graphics.blogspot.com/2012/01/improved-support-for-amd-hybrid.html)
[http://ubuntuforums.org/showthread.php?t=1924347](http://ubuntuforums.org/showthread.php?t=1924347)

So ->
[INDENT][INDENT]I be look'n to learn
[/INDENT][/INDENT]

---

### Post by niniendowarrior on 2013-10-17
> **cem2 said:**
> up! please help

I never tried it when I used fglrx, but from what I noticed in the drivers.  You should be able to switch via running amdcccle with sudo.  The option to change from Intel to AMD GPUs and vice-versa should be there.

You should check this guide out as it specifies scripts on how to switch between hybrid GPUs.
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

---

