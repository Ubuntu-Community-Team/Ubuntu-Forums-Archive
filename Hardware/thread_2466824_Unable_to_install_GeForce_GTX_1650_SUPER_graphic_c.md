---
title: "Unable to install GeForce GTX 1650 SUPER graphic card"
date: 2021-09-07
forum: Hardware
---

### Post by satimis on 2021-09-07
Hi all,

Ubuntu 20.04

$ lspci | grep VGA```

01:00.0 VGA compatible controller: NVIDIA Corporation TU116 [GeForce GTX 1650 SUPER] (rev a1)

```

Download NVIDIA-Linux-x86_64-440.82.run

on;
Download NVidia GeForce GTX 1650 SUPER Driver v.440.82 for Linux x86_*64
[https://driverscollection.com/_52493112111aaf4e5d0b9c19d5d/Download-NVidia-GeForce-GTX-1650-SUPER-Driver-v.440.82-for-Linux-x86_64-free](https://driverscollection.com/_52493112111aaf4e5d0b9c19d5d/Download-NVidia-GeForce-GTX-1650-SUPER-Driver-v.440.82-for-Linux-x86_64-free)

On Terminal run;
1)
$ sudo chmod +x NVIDIA-Linux-x86_64-440.82.run

2)
$ sudo ./NVIDIA-Linux-x86_64-440.82.run

Warning```

ERROR: An NVIDIA kernel module 'nvidia-drm' appears to already be loaded in your kernel.  This may be because    
         it is in use (for example, by an X server, a CUDA program, or the NVIDIA Persistence Daemon), but this    
         may also happen if your kernel was configured without support for module unloading.  Please be sure to    
         exit any programs that may be using the GPU(s) before attempting to upgrade your driver.  If no           
         GPU-based programs are running, you know that your kernel supports module unloading, and you still        
         receive this message, then an error may have occured that has corrupted an NVIDIA kernel module's usage   
         count, for which the simplest remedy is to reboot your computer.     

```

Unable to proceed further.  Please help.  Thanks

Regards

---

### Post by mastablasta on 2021-09-07
you are doing it the hard way. why?

just run the Additional Drivers application, select the driver you want and click install. done.

here are 3 methods: [https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu](https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu)

here is another article that includes a bit information about post install setup: [https://linuxize.com/post/how-to-nvidia-drivers-on-ubuntu-20-04/](https://linuxize.com/post/how-to-nvidia-drivers-on-ubuntu-20-04/)

---

### Post by satimis on 2021-09-07
> **mastablasta said:**
> you are doing it the hard way. why?

just run the Additional Drivers application, select the driver you want and click install. done.

here are 3 methods: [https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu](https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu)

here is another article that includes a bit information about post install setup: [https://linuxize.com/post/how-to-nvidia-drivers-on-ubuntu-20-04/](https://linuxize.com/post/how-to-nvidia-drivers-on-ubuntu-20-04/)
Hi,

Thanks for your advice.

I have tried several times before posting
-> Software & Updates -> Additional Drivers
unable to install the proprietary driver there
Always complained

Until finally on Terminal running something like
$ sudo dpkg --purge -a (sorry I couldn't recall exactly)

-> reboot PC
Then I can install the proprietary driver there.

But
-> Settings -> Display
still showing
1920x1080 resolution

Not
3840x2160 resolution


[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]

Problem solved.  I made a mistake on selecting a wrong display.

This PC is connected to 2 Displays
Display-1 - Samsung 24" display, 1920x1080 resolution - connected to HDMI port of MSI Graphic card
Display-2 - Dell 32" 4K display, 3840x2160 resolution - connected to Display port of MSI Graphic card

During installation, Display-1 is off

On -> Settings -> Display - select Display-1
Resolution showing 1920x1080 

On -> Settings -> Display - select Display-2
Resolution showing 3480x2160

Regards

---

### Post by mastablasta on 2021-09-07
i don't know why nvidia does this. on my old card monitor is on VGA and TV is on DVI-D. eventhough i installed and said that primary display is on VGA it would still switch to TV at boot. ridiculous.

my kid has GTX 1650 and when i fist installed i couldn't even get the new HDMI monitor display to appear. it was obviously sending information to another port. but only i replaced the cabel it is suddenly recognised. i moved the original cable back and it's like nothing happened.

i never saw this kind of behaviour on AMD.

---

