---
title: "Anyone uses ASUS U31JG or MSI FX400?!!"
date: 2011-02-22
forum: Hardware
---

### Post by gunkzmile on 2011-02-22
Is anyone uses ASUS U31JG or MSI FX400?:KS
Would you share your experience of using ubuntu with these laptops. Is everything work okay with ubuntu. Things like touchpad, Fn button, webcam, VGA, wi-fi wireless, hibernate/suspend, etc.

I wanna buy one of these two laptops. But still not sure :confused: about their supportability with OS UBuntu (I prefer using ubuntu lucid-32).

thanks

---

### Post by gunkzmile on 2011-02-25
anyone? please?):P

---

### Post by koleoptera on 2011-03-09
Hey I have an U31F which is the same machine without the nvidia card..
I have installed all ubuntu 32bit-64bit after 10.04..Right now I settled with Maverick 64bit...Most things work quite nice except suspend hibernate..
You can see more here 
[http://ubuntuforums.org/showthread.php?t=1300562&highlight=suspend+hibernate](http://ubuntuforums.org/showthread.php?t=1300562&highlight=suspend+hibernate)

---

### Post by gunkzmile on 2011-03-13
thanks for your reply!

I thought no one is going to reply my thread. I really need this information to help me for making a decision.

btw, about suspend & hibernate. Have you tried the tricks from these links:
[COLOR="Red"][http://wiki.daviddarts.com/Ubuntu_Lucid_on_the_Asus_UL30VT]("http://wiki.daviddarts.com/Ubuntu_Lucid_on_the_Asus_UL30VT")[/COLOR]
[COLOR="red"][http://www.linlap.com/wiki/asus+u35jc]("http://www.linlap.com/wiki/asus+u35jc")[/COLOR]

let me know if it works and solve your problem ^_^

---

### Post by koleoptera on 2011-03-13
> thanks for your reply!

I thought no one is going to reply my thread. I really need this information to help me for making a decision.

btw, about suspend & hibernate. Have you tried the tricks from these links:
[http://wiki.daviddarts.com/Ubuntu_Lu...he_Asus_UL30VT](http://wiki.daviddarts.com/Ubuntu_Lu...he_Asus_UL30VT)
[http://www.linlap.com/wiki/asus+u35jc](http://www.linlap.com/wiki/asus+u35jc)

let me know if it works and solve your problem ^_^

So here it goes:

1) Daviddarts wiki, knew about it and have tried most of the tweaks and workarounds, but suspend did not work..
2) Did not know the asus U35JC thread, used the suspend script and now it works for me...THANKS..

Practically now my machine has 100% functionality..
If you need anything else just tell me..

---

### Post by none0421 on 2011-03-15
I install Ubuntu 10.10 on U31jg. Everything works fine except for the graphic card. I could not switch to Nvidia card. Also I could not watch youtube. Does anyone know solutions?

Thanks!

---

### Post by none0421 on 2011-03-15
To be more specific, there's no nvidia0 in the /dev folder. And ther vga_swicheroo is on in the kernal, but no /sys/kernel/debug/vgaswitcheroo folder ( don't know if it's because there's no nvidia0 in /dev)

---

### Post by koleoptera on 2011-03-16
Well I dont know a lot about the Nvidia card cause mine has only 1 (Intel), but check this guy here

[http://ubuntuforums.org/showpost.php?p=9328344&postcount=110](http://ubuntuforums.org/showpost.php?p=9328344&postcount=110)

,he has done pretty good job and most people have sorted out their problems...

---

### Post by none0421 on 2011-03-21
Thanks for the reply. Actually I check the links above, they are all about turning off nvidia to save battery. For me , I wish to turn on nvidia so I could run some gpu program using cuda. Anyone has an idea how to use nvidia?

---

### Post by zaheridor on 2011-04-16
ASUS u31jg has 'optimus' technology. As I've found out, there's no connection from nvidia
card to the monitor.

So idea was somehow to start X with nvidia drivers and the use VirtualGL to draw the glx stuff out.
I'm to use nvidia card mostly for CUDA computations. so don't use the folliwng xorg.conf.all as the defaulf one. Instead You can start X with the default config and load acpi_call to disable discrete nvidia card (see [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html) )

( I'm using ubuntu 10.10... )

!!!AT YOUR PERSONAL RISK!!! as ever :)

1. I've dowloaded  devdriver_4.0_linux_32_270.40.run
from [http://developer.nvidia.com/cuda-toolkit-40#Linux](http://developer.nvidia.com/cuda-toolkit-40#Linux) (and other toolkits )

2. check that  grep nvi /etc/modprobe.d/* (mb not useful, ignore for the first try )
has 
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb
/etc/modprobe.d/blacklist-local.conf:blacklist nvidia_current

and /etc/default/grub
has 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux rdblacklist=nouveau"

don't forget to make
update-initramfs
update-grub

3. login to console and stop gdm
sudo /etc/init.d/gdm stop

4. install drivers, ignore all, don't create config for X from installer
sudo sh ./devdriver_4.0_linux_32_270.40.run

5. create /etc/X11/xorg.conf.all 

Modified version of the  xorg.conf generated by nvidia-xconfig

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

I've added 
    BusID          "PCI:1:0:0"
    Option "SWCursor" "true"
for nvidia device

glx into Module section
Xinerama to ServerFlags (no virtualgl without this)

added device, monitor, screen section for the intel card and
modified ServerLayout  
so

xorg.conf.all

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen        "Screen1"
    Screen        "Screen0"
#    Screen        "Screen1" Leftof "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
##    HorizSync       28.0 - 33.0
##    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Option         "DefaultModes" "false"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
##    HorizSync       28.0 - 33.0
##    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Option         "DefaultModes" "false"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "intel"
    Option         "UseDisplayDevice" "AUO"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:1:0:0"
#    Option         "CustomEDID" "CRT-0:/etc/X11/edid.custom"
#    Option         "UseDisplayDevice" "CRT-0"
#    Option "HWCursor" "false"
    Option "SWCursor" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

6. download VirtualGL from [www.virtualgl.org](www.virtualgl.org)  and install it
sudo dpkg -i VirtualGL_2.2.1_i386.deb
and configure it 
/opt/VirtualGL/bin/vglserver_config
See configure section [http://www.virtualgl.org/vgldoc/2_2_1/#hd005](http://www.virtualgl.org/vgldoc/2_2_1/#hd005) 
N.b. I've desided to use the most unsecure settings and allow everything to everybody)

7. ( gdm is stopped already, xorg.conf.all in /etc/X11/ )
startx -- -config xorg.conf.all

8. you can check glxinfo 
and run glxgears
but if you want to see anything, use
vglrun glxgears
or even try 
vglrun amoeba -nosound -windowed

9. continue installing CUDA. See [http://ubuntuforums.org/showthread.php?t=1625433](http://ubuntuforums.org/showthread.php?t=1625433) for details.

FINAL NOTE.
IT'S A HACK (but not real).
MOSTLY IT'S TO USE CUDA ( but not games, compiz an so on)
XINERAMA DISABLES RANDR.

comment it and post suggestions

---

