---
title: "Dell Inspiron 1520 NVIDIA Grapics Card Help Needed"
date: 2008-06-01
forum: Hardware
---

### Post by Will240 on 2008-06-01
What is the best way for me to install a driver for my graphics card on Ubuntu 8.04 Hardy Heron. I have already tried doing the following but if you think I did it wrong let me know and I will give it a second shot.

[LIST=1]
[*]I tried going System > Administrator > Hardware Drivers and enabling it. After restarting my screen goes a funny gray color with a dark gray strip down the center, I login from memory and it turns different shades of gray with a dark gray strip down the center and then stops.

[*]I tried downloading the latest Linux driver from NVIDIA's webpage and it results in exactly the same after installing it.

[*]Also tried a few other ways but forgot them now. They resulted in the same.
[/LIST]


**Hardware Stats:**

[FONT="Arial"]
Processor
Intel® Centrino® Processor Technology - Intel® Core™ 2 Duo Processor T7250 (2.0GHz/ 800 FSB/ 2MB Cache)

Memory
3GB Dual-channel 667MHz DDR2 SDRAM

Harddrive
250GB 5400RPM SATA Hard Drive

Monitor	
15.4" Widescreen WXGA (1280x800) TFT Display with TrueLife™

Graphic Card
128MB NVIDIA® GeForce® 8400M GS

Optical Device
8X max DVD+/-RW Drive with DVD+R double layer write capability

Wireless Network Card	
Intel® 3945 802.11a/g Mini-card[/FONT]

---

### Post by cforput on 2008-06-07
I'm a newbie so I hopefully I don't point you in the wrong direction. I also use Gutsy and not Hardy.

I had to add the driver to the restricted driver manager for nVidia (I have a Gforce7 version). Then make sure it is checked as activated. Then I had to go into System > Administration > Screens and Graphics and click on the graphics card tab. Then I searched for nVidia as the driver. 

I know it isn't much to go on but maybe it will be enough for you.

Good luck.

---

### Post by taghawi on 2008-06-11
UBUNTU 9.4:

downloaded the newes dirver at:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")


ctrl-alt-F1 to go to bash   (ctrl-alt-F7 to come back)
login
sudo killall gdm
sudo sh NVIDIA-Linux- ... .run


OLDER UBUNTUS (e.g. 8.4)

In habe a geforce 8400, I did the following:

1) Ensured that your system meets the following requirements:

    * development tools like make and gcc are installed
      (use synaptic in the Administration menu)
    * the linux-headers package matching the installed Linux kernel is installed (probably thats OK, if you dont know what it means ignore it)
    * the pkg-config and xserver-xorg-dev packages are installed
      (use synaptic in the Administration menu)
    * the nvidia-glx package has been uninstalled with the --purge option 
      (sudo apt-get purge nvidia-glx)
and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

2)  
downloaded this [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)
3)
ctrl-alt-F1 to go to bash   (ctrl-alt-F7 to come back)
login
sudo killall gdm
sudo sh NVIDIA-Linux-x86-180.22.pkg1.run
4)
restart, ubuntu and select the recovery in the boot menu
select fix x
5)
sudo gedit /etc/X11/xorg.conf

find 
section Section "Device"
	Identifier	"Configured Video Device"
EndSection

change it to 
section Section "Device"
	Identifier	"Configured Video Device"
	Driver "nvidia"
EndSection

6)and restart.

There might be a better version. Some steps might be superfluous, but this works.

Additional comment: for  using two monitors via dual monitor or Xinerama use Applications -> System Tools -> NVIDIA xserver settings 
or in  the Terminal nvidia-settings


Davoud

---

