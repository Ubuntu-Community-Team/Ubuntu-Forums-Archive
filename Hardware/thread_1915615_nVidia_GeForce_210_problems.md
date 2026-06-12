---
title: "nVidia GeForce 210 problems"
date: 2012-01-26
forum: Hardware
---

### Post by MichaelGld on 2012-01-26
I replaced my GeForce 7300GS recently because it died.  When I booted into 10.04 (32-bit) with the new GeForce 210, the screen looked good. My Conky even recognized it. It was short lived, however. After a short while, the screen froze and the system was locked up. 

My system is dual-boot, so I ran Windows XP and successfully installed the driver for the new card. Then I started searching these forums for a solution.  I went to nVidia's web site and downloaded the Linux driver, NVIDIA-Linux-x86-290.10.run.  I followed these directions found here. [http://ubuntuforums.org/showthread.php?t=1617393&highlight=graphics+card+problems](http://ubuntuforums.org/showthread.php?t=1617393&highlight=graphics+card+problems)


                                [I]  **Re: new graphics card problems**             
                                                                Hi,

Go to the nvidia site and get the latest driver for your card, keep the download in a handy location, /home[/I] [I]

Open a terminal and stop the gdm(GraphicDisplayManager) with:[/I] [I]

sudo gdm-stop[/I] [I]

A black screen will be presented with terminal access, type in:[/I] [I]

telinit 3[/I] [I]

another black screen will be presented,now cd to the downloaded driver and start it like this:[/I] [I]

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you  have, be precise as errors will result in "no such file"[/I] [I]

Note: If you get an error message like this "Unable to find kernel source tree", do this:[/I] [I]
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again[/I]  [I]  Follow the onscreen guide from Nvidia and when done

[/I] [I]  Start GDM

sudo service gdm start[/I] [I]
 
Regards, Ellgor.
      
[/I] 
I got an error when running this:

```
The distribution provided pre-install script failed. Continue anyway?
```I answered yes and the install finished. When I reboot into Ubuntu, Conky tells me the driver is in use and the screen looks great. However, after a few minutes of use the screen suddenly goes ugly and I have a total lockup again. I repeat the process with the same affect.

Then I went back to nVidia's web site and downloaded the older driver: NVIDIA-Linux-x86-285.05.09.run. I repeat the process as above with the same results. 

My Xorg.conf.

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```I'd be very grateful for any assistance.

---

