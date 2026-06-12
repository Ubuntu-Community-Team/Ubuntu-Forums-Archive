---
title: "Ubuntu 14.04 &amp; Nvidia GTX 960"
date: 2015-01-31
forum: Hardware
---

### Post by jempa333 on 2015-01-31
I have Ubuntu 14.04 64bit and NVIDIA Geforce GTX 960 that caused me a lot of problems to install. Hopefully this can help somebody:

 
in terminal write
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get install build-essential && sudo apt-get install linux-source && sudo apt-get install linux-headers-generic 
sudo gedit [COLOR=#000000]/etc/default/grub[/COLOR] *#change line "GRUB_CMDLINE_LINUX_DEFAULT..."-line to *
**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1     quiet splash nomodeset"** *#(forces low-level graphics to ensure putty does     not give black screen)*
sudo update-grub2
sudo apt-get remove nvidia* && sudo apt-get autoremove *#ensures no former installation clashes with new install*
sudo reboot 

After reboot get correct nvidia-driver (chose graphic-card and OS) at &#8220;[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)" (or search webb with &#8220;nvidia download&#8221;). Right-click on downloaded file and change if to executable. 
sudo gedit /etc/modprobe.d/blacklist.conf [I]#add these lines at the end:
 blacklist vga16fb[/I]
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveua
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off 

Open a putty-terminal with Ctrl + Alt     + F1       
sudo service lightdm stop *#stops graphic session to enable nvidiainstallation*
cd Downloads *#(or wherever you downloaded your nvidia-file)*
sudo ./{***the downloadedfilename***.run} *#follow installation-instructions (normally yes to all)sudo nvidia-xconfig #(if you did not chose &#8220;yes&#8221; to this in the installation&#8221; *
sudo nano [COLOR=#000000]/etc/default/grub[/COLOR] *# change the "GRUB_CMBLINE_LINUX_DEFAULT..."-line to below:*
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset&#8221;
sudo update-grub2 #update grub!
 sudo reboot
 

 hopefully it works for you now as it did for me...

---

### Post by Bradley_Pirtle on 2015-02-08
[COLOR=#000000]Ago[/COLOR]
[COLOR=#000000]Jempa333, I just finished installing drivers for my [/COLOR][COLOR=#000000]Geforce GTX 970. Thanks for the helpful post!

-Brad[/COLOR]

---

### Post by dat789 on 2015-02-11
I will try this out soon as I am facing the same problem after a recently purchas of the GTX 960 graphics card.
Symptom currently facing -- black screen after grub.

---

### Post by jempa333 on 2015-02-13
Glad to help!

---

### Post by Ignacio_Tiraboschi on 2015-02-25
I F****** LOVE YOU!
This is just great! Works perfectly, had a black screen rigth after grub, now it works perfectly :)
Thanks a lot!

---

### Post by o-phil on 2015-03-10
Hi. After completing the last step, and rebooting I'm stuck with 800 x 600. Any ideas? Thanks.

---

### Post by olp1 on 2015-03-19
Hi folks,
just registered to say "Thanks sooo much" to jempa! Great job! This helped a lot!

But I think in the end you forgot ro mention, to update Grub again.

This might fix:
> **o-phil said:**
> Hi. After completing the last step, and rebooting I'm stuck with 800 x 600. Any ideas? Thanks.

So the last steps are:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset” #change grub settings
sudo update-grub2 #update grub!
sudo reboot #restart
```

I hope that help's ;)

---

### Post by alan56 on 2015-03-20
When i goto put in the driver file name it says file directory doesnt exist. I put it in several times to make sure it was correct but it doesnt find the driver file no matter what i do. (im kinda new to linux any help would be amazing,)

---

### Post by jempa333 on 2015-03-26
Hi alan56,

Try:
cd /home/'***yourusername'***/Downloads #instead of the original line stated above "cd Downloads *#(or wherever you downloaded your nvidia-file*"

...and/or ensure you move the file to this location after you downloaded it and before you run th "sudo ./"-command ...

If this does not work please let me know

---

### Post by jempa333 on 2015-03-26
olp1
Thanks, I edited the post.
jempa333

---

### Post by matthias12 on 2015-03-27
Thanks very much Jempa! You helped me a lot!

Cheers,
Matthias

---

### Post by CliveMcCarthy on 2015-04-04
Thank you so much for this post. Getting the 960 to work was getting tough, especially when Ctrl-Alt-F1 was lost.

I'm running a 4k display on Mint17 with the gtx960.

---

### Post by member-e on 2015-04-06
Perfect solution. Thanks. I think you have a typo . "[FONT=courier new]blacklist lbm-nouveua[/FONT]" is rather "[FONT=courier new]blacklist lbm-nouveau[/FONT]"

---

### Post by rrobb on 2015-04-06
Thank you so much.

Worked great in 14.04.2 with a GTX970 and 346.47.




Cory

---

### Post by miska-paloposki on 2015-04-17
> **jempa333 said:**
> 
in terminal write
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get install build-essential && sudo apt-get install linux-source && sudo apt-get install linux-headers-generic....

Where you open terminal? If I try to install ubuntu I get black screen. Adding nomodeset on boot settings helps to pass black screen. After installation reboot I got stuck on black screen again but if I press shift on reboot I can get to grub menu. So again, where and how you open terminal? CTRL + ALT + F1 doesn't work.

---

### Post by dotang76 on 2015-04-24
works perfect on 14.10 fresh install on gtx 960....grattitude for great post!

---

### Post by zkneebone on 2015-04-25
after upgrade to 15.04 I had all kinds of problems with the NVIDIA driver update.
first issue: stopping lightdm no longer kills x on my install
I had to perform the installation from a root terminal which was recommended by NVIDIA installation instructions.
Get to root terminal: reboot, hit [ESC] during boot, select [recovery] mode from grub menu, enter root shell
NVIDIA*.run said it could not access the /tmp folder. I then had to remount the filesystem with

sudo mount -a

second issue: the NVIDIA*.run file kept saying there is an error in initializing
turns out there was a script at /usr/lib/nvidia/pre-install
the content is this

> #!/bin/sh


# Trigger an error exit status to prevent the installer from overwriting
# Ubuntu's nvidia packages.


exit 1

changing the 1 to 0 enabled the nvidia install script to run

third issue: the installer didn't like the new kernel but I was able to recompile it with the new kernel
./NVIDIA*.run --add-this-kernel
which output a different script NVIDIA*-custom.run which was successful
This was a big help but I want to post my additional steps here for others who are having trouble.

---

### Post by pi6502 on 2015-04-28
Hi there,

I've ordered a Gtx960 and will do a fresh 14.04 LTS after mounting it (I'm currently 12.04 LTS with an ATI 4890 HD).
When/how shall I enter those commands, since I presume the screen will go black after rebooting, i.e. finishing the installation process?

One more thing: The procedure to have steam running on ubuntu 12.04 LTS was a little cumbersome. I had to install first the open video driver, then steam, and then install the proprietary one, otherwise I would get errors. Is this the same with the nvidia proprietary driver, steam and 14.04 LTS?

---

### Post by m.xander on 2015-05-22
Thanks Jempa333 for this extremely useful post. Gigabyte GeForce GTX 960 WindForce OC 4GB successfully set up with multiple monitors on Ubuntu Studio 14.04.

---

### Post by tjeremiah on 2015-05-24
> **jempa333 said:**
> I have Ubuntu 14.04 64bit and NVIDIA Geforce GTX 960 that caused me a lot of problems to install. Hopefully this can help somebody:

 
in terminal write
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get install build-essential && sudo apt-get install linux-source && sudo apt-get install linux-headers-generic 
sudo gedit [COLOR=#000000]/etc/default/grub[/COLOR] *#change line "GRUB_CMDLINE_LINUX_DEFAULT..."-line to *
**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1     quiet splash nomodeset"** *#(forces low-level graphics to ensure putty does     not give black screen)*
sudo update-grub2
sudo apt-get remove nvidia* && sudo apt-get autoremove *#ensures no former installation clashes with new install*
sudo reboot 

After reboot get correct nvidia-driver (chose graphic-card and OS) at “[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)" (or search webb with “nvidia download”). Right-click on downloaded file and change if to executable. 
sudo gedit /etc/modprobe.d/blacklist.conf [I]#add these lines at the end:
 blacklist vga16fb[/I]
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveua
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off 

Open a putty-terminal with Ctrl + Alt     + F1       
sudo service lightdm stop *#stops graphic session to enable nvidiainstallation*
cd Downloads *#(or wherever you downloaded your nvidia-file)*
sudo ./{***the downloadedfilename***.run} *#follow installation-instructions (normally yes to all)sudo nvidia-xconfig #(if you did not chose “yes” to this in the installation” *
sudo nano [COLOR=#000000]/etc/default/grub[/COLOR] *# change the "GRUB_CMBLINE_LINUX_DEFAULT..."-line to below:*
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset”
sudo update-grub2 #update grub!
 sudo reboot
 

 hopefully it works for you now as it did for me...

Thanks you so much! Works well with my gtx 960.

---

### Post by Death_Frost on 2015-07-18
very helpful indeed. Worling perfectly on ubuntu 14.04 LTS with my MSI GTX960 2gd5t oc graphic card.

---

### Post by timbergetter2 on 2015-07-24
Thank you jempa333 for your detailed and accurate post which worked perfectly for me.
My video card is Gigabyte GV-NX96T1GHP (Geforce 9600 GT)

---

### Post by newyawker on 2015-07-25
This worked for me as well. THANKS!

GPU: Nvidia GTX 745

---

### Post by xmjsilverx on 2015-08-01
I am having trouble getting a terminal open to even try this.  Is it possible to reinstall the old graphics card and download the drivers and then switch to the new card?  If so what lines can I run before installing the new card?

---

### Post by fbnaia2 on 2015-08-10
I am using evga GeForce GTX 960 SSC, and i was getting a blank/black screen when installing the drivers. I found that nvidia-xconfig was not detecting my currently connected monitor correctly.

To fix it, i used "nvidia-xconfig --query-gpu-info" to get the list of detected monitors and used "nvidia-xconfig --use-display-device=DISPLAY-DEVICE" to generate a xorg.conf file with the correct monitor settings.

---

### Post by Steve_Miller on 2015-08-13
I just wanted to say a MASSIVE thank you to jempa33 for posting this.
This fixed it for me after countless reading of god knows how many other forum posts.
It's been emotional!

I had problems where as soon as I tried to switch to the (recommended/tested) proprietary NVIDIA driver, I'd just get a black screen.
And the reason I was trying to use a proprietary driver was to get multiple monitors working - The Nouveau driver just resulted in black/flashing screen on primary monitor as soon as I tried hooking up a second display.

System: Ubuntu 14.04.3 LTS
Graphics card: ASUS NVIDIA GeForce GTX 750 Ti

Three bits of info for other novices:
i) [FONT=arial]Ctrl + Alt + F7[/FONT] gets you back out of the putty-terminal/console should you need it (and if you mess up and have to drop back out of console you'll want [FONT=arial]sudo service lightdm[/FONT] start to re-enable your graphics) 
ii) 5 minute tutorial on using [FONT=arial]nano[/FONT] editor [https://www.youtube.com/watch?v=45KO4KO2DTo](https://www.youtube.com/watch?v=45KO4KO2DTo)
iii) To make the download executable.  Right click on it in Nautilus > Properties >Permissions tab - Check the 'Execute' box

Thanks again!

---

### Post by david430 on 2015-09-03
hi guys !
i just registered here to give a *huge* thanks to **jempa333 !!** luckily i found the post quickly, i bet it saved me a lot of time...
this worked for me on debian 8.1 Jessie, with a GTX 960
i strictly followed the guide, but removed the "nouveau" driver instead of disabling it ; idk if i made a mistake there but it looks good right now :)
thanks again for the help !

---

### Post by ziq on 2015-09-17
After following suggested solution, I got the system working but no acceleration since the nvidia driver doesn't seem no recognize the gtx 960. Any suggestion?

Here the log file:

> [    31.878] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    31.878] X Protocol Version 11, Revision 0
[    31.878] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    31.878] Current Operating System: Linux MiK7 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
[    31.878] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4eec5ceb-2bb4-4d25-a66b-67b8b5af5b26 ro nouveau.blacklist=1 nomodeset
[    31.878] Build Date: 12 February 2015  02:49:29PM
[    31.878] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    31.878] Current version of pixman: 0.30.2
[    31.878]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    31.878] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.878] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 17 07:26:20 2015
[    31.878] (==) Using config file: "/etc/X11/xorg.conf"
[    31.878] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.879] (==) ServerLayout "Layout0"
[    31.879] (**) |-->Screen "Screen0" (0)
[    31.879] (**) |   |-->Monitor "Monitor0"
[    31.879] (**) |   |-->Device "Device0"
[    31.879] (**) |-->Input Device "Keyboard0"
[    31.879] (**) |-->Input Device "Mouse0"
[    31.879] (==) Automatically adding devices
[    31.879] (==) Automatically enabling devices
[    31.879] (==) Automatically adding GPU devices
[    31.879] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.879]     Entry deleted from font path.
[    31.879] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.879]     Entry deleted from font path.
[    31.879] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.879]     Entry deleted from font path.
[    31.879] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.879]     Entry deleted from font path.
[    31.879] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.879]     Entry deleted from font path.
[    31.879] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    31.879] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.879] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    31.879] (WW) Disabling Keyboard0
[    31.879] (WW) Disabling Mouse0
[    31.879] (II) Loader magic: 0x7fe8ea93dd40
[    31.879] (II) Module ABI versions:
[    31.879]     X.Org ANSI C Emulation: 0.4
[    31.879]     X.Org Video Driver: 15.0
[    31.879]     X.Org XInput driver : 20.0
[    31.879]     X.Org Server Extension : 8.0
[    31.879] (II) xfree86: Adding drm device (/dev/dri/card0)
[    31.880] (--) PCI:*(0:0:2:0) 8086:0412:1458:d000 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    31.880] (--) PCI: (0:1:0:0) 10de:1401:1043:8520 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    31.880] Initializing built-in extension Generic Event Extension
[    31.880] Initializing built-in extension SHAPE
[    31.880] Initializing built-in extension MIT-SHM
[    31.880] Initializing built-in extension XInputExtension
[    31.880] Initializing built-in extension XTEST
[    31.880] Initializing built-in extension BIG-REQUESTS
[    31.880] Initializing built-in extension SYNC
[    31.880] Initializing built-in extension XKEYBOARD
[    31.880] Initializing built-in extension XC-MISC
[    31.880] Initializing built-in extension SECURITY
[    31.880] Initializing built-in extension XINERAMA
[    31.880] Initializing built-in extension XFIXES
[    31.880] Initializing built-in extension RENDER
[    31.880] Initializing built-in extension RANDR
[    31.880] Initializing built-in extension COMPOSITE
[    31.880] Initializing built-in extension DAMAGE
[    31.880] Initializing built-in extension MIT-SCREEN-SAVER
[    31.880] Initializing built-in extension DOUBLE-BUFFER
[    31.880] Initializing built-in extension RECORD
[    31.880] Initializing built-in extension DPMS
[    31.880] Initializing built-in extension Present
[    31.880] Initializing built-in extension DRI3
[    31.880] Initializing built-in extension X-Resource
[    31.880] Initializing built-in extension XVideo
[    31.880] Initializing built-in extension XVideo-MotionCompensation
[    31.880] Initializing built-in extension SELinux
[    31.880] Initializing built-in extension XFree86-VidModeExtension
[    31.880] Initializing built-in extension XFree86-DGA
[    31.880] Initializing built-in extension XFree86-DRI
[    31.880] Initializing built-in extension DRI2
[    31.880] (II) LoadModule: "glx"
[    31.881] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.942] (II) Module glx: vendor="NVIDIA Corporation"
[    31.942]     compiled for 4.0.2, module version = 1.0.0
[    31.942]     Module class: X.Org Server Extension
[    31.943] (II) NVIDIA GLX Module  355.11  Wed Aug 26 16:02:11 PDT 2015
[    31.943] Loading extension GLX
[    31.944] (II) LoadModule: "nvidia"
[    31.944] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    31.952] (II) Module nvidia: vendor="NVIDIA Corporation"
[    31.952]     compiled for 4.0.2, module version = 1.0.0
[    31.952]     Module class: X.Org Video Driver
[    31.952] (II) NVIDIA dlloader X Driver  355.11  Wed Aug 26 15:38:55 PDT 2015
[    31.952] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    31.953] (++) using VT number 8


[    32.302] (EE) No devices detected.
[    32.302] (==) Matched nvidia as autoconfigured driver 0
[    32.302] (==) Matched nouveau as autoconfigured driver 1
[    32.302] (==) Matched intel as autoconfigured driver 2
[    32.302] (==) Matched modesetting as autoconfigured driver 3
[    32.302] (==) Matched fbdev as autoconfigured driver 4
[    32.302] (==) Matched vesa as autoconfigured driver 5
[    32.302] (==) Assigned the driver to the xf86ConfigLayout
[    32.302] (II) LoadModule: "nvidia"
[    32.302] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    32.302] (II) Module nvidia: vendor="NVIDIA Corporation"
[    32.303]     compiled for 4.0.2, module version = 1.0.0
[    32.303]     Module class: X.Org Video Driver
[    32.303] (II) UnloadModule: "nvidia"
[    32.303] (II) Unloading nvidia
[    32.303] (II) Failed to load module "nvidia" (already loaded, 32744)
[    32.303] (II) LoadModule: "nouveau"
[    32.303] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    32.303] (II) Module nouveau: vendor="X.Org Foundation"
[    32.303]     compiled for 1.15.0, module version = 1.0.10
[    32.303]     Module class: X.Org Video Driver
[    32.303]     ABI class: X.Org Video Driver, version 15.0
[    32.303] (II) LoadModule: "intel"
[    32.303] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    32.305] (II) Module intel: vendor="X.Org Foundation"
[    32.305]     compiled for 1.15.1, module version = 2.99.910
[    32.305]     Module class: X.Org Video Driver
[    32.305]     ABI class: X.Org Video Driver, version 15.0
[    32.305] (II) LoadModule: "modesetting"
[    32.305] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    32.305] (II) Module modesetting: vendor="X.Org Foundation"
[    32.305]     compiled for 1.15.0, module version = 0.8.1
[    32.305]     Module class: X.Org Video Driver
[    32.305]     ABI class: X.Org Video Driver, version 15.0
[    32.305] (II) LoadModule: "fbdev"
[    32.305] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.305] (II) Module fbdev: vendor="X.Org Foundation"
[    32.305]     compiled for 1.15.0, module version = 0.4.4
[    32.305]     Module class: X.Org Video Driver
[    32.305]     ABI class: X.Org Video Driver, version 15.0
[    32.305] (II) LoadModule: "vesa"
[    32.305] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.305] (II) Module vesa: vendor="X.Org Foundation"
[    32.305]     compiled for 1.15.0, module version = 2.3.3
[    32.305]     Module class: X.Org Video Driver
[    32.305]     ABI class: X.Org Video Driver, version 15.0
[    32.305] (II) NVIDIA dlloader X Driver  355.11  Wed Aug 26 15:38:55 PDT 2015
[    32.305] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    32.305] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    32.305] (II) NOUVEAU driver for NVIDIA chipset families :
[    32.305]     RIVA TNT        (NV04)
[    32.305]     RIVA TNT2       (NV05)
[    32.305]     GeForce 256     (NV10)
[    32.305]     GeForce 2       (NV11, NV15)
[    32.306]     GeForce 4MX     (NV17, NV18)
[    32.306]     GeForce 3       (NV20)
[    32.306]     GeForce 4Ti     (NV25, NV28)
[    32.306]     GeForce FX      (NV3x)
[    32.306]     GeForce 6       (NV4x)
[    32.306]     GeForce 7       (G7x)
[    32.306]     GeForce 8       (G8x)
[    32.306]     GeForce GTX 200 (NVA0)
[    32.306]     GeForce GTX 400 (NVC0)
[    32.306] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    32.306] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    32.306] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    32.306] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    32.306] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    32.306] (II) FBDEV: driver for framebuffer: fbdev
[    32.306] (II) VESA: driver for VESA chipsets: vesa
[    32.306] (++) using VT number 8


[    32.306] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    32.306] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    32.306] (EE) [drm] KMS not enabled
[    32.306] (EE) [drm] KMS not enabled
[    32.313] (WW) Falling back to old probe method for modesetting
[    32.313] (II) Loading sub module "fbdevhw"
[    32.313] (II) LoadModule: "fbdevhw"
[    32.313] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.313] (II) Module fbdevhw: vendor="X.Org Foundation"
[    32.313]     compiled for 1.15.1, module version = 0.0.2
[    32.313]     ABI class: X.Org Video Driver, version 15.0
[    32.313] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    32.313] (II) FBDEV(1): using default device
[    32.313] (WW) Falling back to old probe method for vesa
[    32.313] (EE) Screen 0 deleted because of no matching config section.
[    32.313] (II) UnloadModule: "modesetting"
[    32.313] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[    32.313] (==) FBDEV(0): RGB weight 888
[    32.313] (==) FBDEV(0): Default visual is TrueColor
[    32.313] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.313] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[    32.313] (II) FBDEV(0): checking modes against framebuffer device...
[    32.313] (II) FBDEV(0): checking modes against monitor...
[    32.313] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    32.313] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    32.313] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[    32.313] (==) FBDEV(0): DPI set to (96, 96)
[    32.313] (II) Loading sub module "fb"
[    32.313] (II) LoadModule: "fb"
[    32.314] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.314] (II) Module fb: vendor="X.Org Foundation"
[    32.314]     compiled for 1.15.1, module version = 1.0.0
[    32.314]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.314] (**) FBDEV(0): using shadow framebuffer
[    32.314] (II) Loading sub module "shadow"
[    32.314] (II) LoadModule: "shadow"
[    32.314] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    32.314] (II) Module shadow: vendor="X.Org Foundation"
[    32.314]     compiled for 1.15.1, module version = 1.1.0
[    32.314]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.314] (II) UnloadModule: "nvidia"
[    32.314] (II) Unloading nvidia
[    32.314] (II) UnloadModule: "vesa"
[    32.314] (II) Unloading vesa
[    32.314] (==) Depth 24 pixmap format is 32 bpp
[    32.314] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    32.314] (==) FBDEV(0): Backing store enabled
[    32.314] (**) FBDEV(0): DPMS enabled
[    32.314] (==) RandR enabled
[    32.318] (II) SELinux: Disabled on system
[    32.319] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    32.326] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.328] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    32.328] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.328] (**) Power Button: Applying InputClass "Logitech G5"
[    32.328] (II) LoadModule: "evdev"
[    32.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.329] (II) Module evdev: vendor="X.Org Foundation"
[    32.329]     compiled for 1.15.0, module version = 2.8.2
[    32.329]     Module class: X.Org XInput Driver
[    32.329]     ABI class: X.Org XInput driver, version 20.0
[    32.329] (II) Using input driver 'evdev' for 'Power Button'
[    32.329] (**) Power Button: always reports core events
[    32.329] (**) evdev: Power Button: Device: "/dev/input/event1"
[    32.329] (**) evdev: Power Button: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[    32.329] (--) evdev: Power Button: Vendor 0 Product 0x1
[    32.329] (--) evdev: Power Button: Found keys
[    32.329] (II) evdev: Power Button: Configuring as keyboard
[    32.329] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    32.329] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    32.329] (**) Option "xkb_rules" "evdev"
[    32.329] (**) Option "xkb_model" "pc105"
[    32.329] (**) Option "xkb_layout" "es"
[    32.330] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    32.330] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    32.330] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.330] (**) Power Button: Applying InputClass "Logitech G5"
[    32.330] (II) Using input driver 'evdev' for 'Power Button'
[    32.330] (**) Power Button: always reports core events
[    32.330] (**) evdev: Power Button: Device: "/dev/input/event0"
[    32.330] (**) evdev: Power Button: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[    32.330] (--) evdev: Power Button: Vendor 0 Product 0x1
[    32.330] (--) evdev: Power Button: Found keys
[    32.330] (II) evdev: Power Button: Configuring as keyboard
[    32.330] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    32.330] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    32.330] (**) Option "xkb_rules" "evdev"
[    32.331] (**) Option "xkb_model" "pc105"
[    32.331] (**) Option "xkb_layout" "es"
[    32.331] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[    32.331] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    32.331] (II) config/udev: Adding input device HDA NVidia HDMI (/dev/input/event18)
[    32.331] (**) HDA NVidia HDMI: Applying InputClass "Logitech G5"
[    32.331] (II) No input driver specified, ignoring this device.
[    32.331] (II) This device may have been added with another device file.
[    32.331] (II) config/udev: Adding input device HDA NVidia HDMI (/dev/input/event17)
[    32.331] (**) HDA NVidia HDMI: Applying InputClass "Logitech G5"
[    32.331] (II) No input driver specified, ignoring this device.
[    32.331] (II) This device may have been added with another device file.
[    32.331] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[    32.331] (**) HDA Intel HDMI HDMI/DP,pcm=7: Applying InputClass "Logitech G5"
[    32.331] (II) No input driver specified, ignoring this device.
[    32.331] (II) This device may have been added with another device file.
[    32.331] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event6)
[    32.331] (**) HDA Intel HDMI HDMI/DP,pcm=8: Applying InputClass "Logitech G5"
[    32.331] (II) No input driver specified, ignoring this device.
[    32.331] (II) This device may have been added with another device file.
[    32.332] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[    32.332] (**) HDA Intel HDMI HDMI/DP,pcm=3: Applying InputClass "Logitech G5"
[    32.332] (II) No input driver specified, ignoring this device.
[    32.332] (II) This device may have been added with another device file.
[    32.332] (II) config/udev: Adding input device Logitech Logitech Gaming Keyboard (/dev/input/event2)
[    32.332] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    32.332] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "Logitech G5"
[    32.332] (II) Using input driver 'evdev' for 'Logitech Logitech Gaming Keyboard'
[    32.332] (**) Logitech Logitech Gaming Keyboard: always reports core events
[    32.332] (**) evdev: Logitech Logitech Gaming Keyboard: Device: "/dev/input/event2"
[    32.332] (**) evdev: Logitech Logitech Gaming Keyboard: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[    32.332] (--) evdev: Logitech Logitech Gaming Keyboard: Vendor 0x46d Product 0xc221
[    32.332] (--) evdev: Logitech Logitech Gaming Keyboard: Found keys
[    32.332] (II) evdev: Logitech Logitech Gaming Keyboard: Configuring as keyboard
[    32.332] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.1/3-3.1:1.0/input/input5/event2"
[    32.332] (II) XINPUT: Adding extended input device "Logitech Logitech Gaming Keyboard" (type: KEYBOARD, id 8)
[    32.332] (**) Option "xkb_rules" "evdev"
[    32.332] (**) Option "xkb_model" "pc105"
[    32.332] (**) Option "xkb_layout" "es"
[    32.332] (II) config/udev: Adding input device Logitech Logitech Gaming Keyboard (/dev/input/event3)
[    32.332] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    32.332] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "Logitech G5"
[    32.332] (II) Using input driver 'evdev' for 'Logitech Logitech Gaming Keyboard'
[    32.332] (**) Logitech Logitech Gaming Keyboard: always reports core events
[    32.332] (**) evdev: Logitech Logitech Gaming Keyboard: Device: "/dev/input/event3"
[    32.332] (**) evdev: Logitech Logitech Gaming Keyboard: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[    32.332] (--) evdev: Logitech Logitech Gaming Keyboard: Vendor 0x46d Product 0xc221
[    32.332] (--) evdev: Logitech Logitech Gaming Keyboard: Found keys
[    32.332] (II) evdev: Logitech Logitech Gaming Keyboard: Configuring as keyboard
[    32.332] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.1/3-3.1:1.1/input/input6/event3"
[    32.332] (II) XINPUT: Adding extended input device "Logitech Logitech Gaming Keyboard" (type: KEYBOARD, id 9)
[    32.332] (**) Option "xkb_rules" "evdev"
[    32.332] (**) Option "xkb_model" "pc105"
[    32.332] (**) Option "xkb_layout" "es"
[    32.333] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event4)
[    32.333] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[    32.333] (**) Logitech USB Gaming Mouse: Applying InputClass "Logitech G5"
[    32.333] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[    32.333] (**) Logitech USB Gaming Mouse: always reports core events
[    32.333] (**) evdev: Logitech USB Gaming Mouse: Device: "/dev/input/event4"
[    32.333] (**) evdev: Logitech USB Gaming Mouse: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[    32.333] (--) evdev: Logitech USB Gaming Mouse: Vendor 0x46d Product 0xc041
[    32.333] (--) evdev: Logitech USB Gaming Mouse: Found 20 mouse buttons
[    32.333] (--) evdev: Logitech USB Gaming Mouse: Found scroll wheel(s)
[    32.333] (--) evdev: Logitech USB Gaming Mouse: Found relative axes
[    32.333] (--) evdev: Logitech USB Gaming Mouse: Found x and y relative axes
[    32.333] (II) evdev: Logitech USB Gaming Mouse: Configuring as mouse
[    32.333] (II) evdev: Logitech USB Gaming Mouse: Adding scrollwheel support
[    32.333] (**) evdev: Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[    32.333] (**) evdev: Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    32.333] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.2/3-3.2:1.0/input/input7/event4"
[    32.333] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE, id 10)
[    32.333] (II) evdev: Logitech USB Gaming Mouse: initialized for relative axes.
[    32.333] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[    32.333] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[    32.333] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[    32.333] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[    32.333] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[    32.333] (**) Logitech USB Gaming Mouse: Applying InputClass "Logitech G5"
[    32.333] (II) No input driver specified, ignoring this device.
[    32.333] (II) This device may have been added with another device file.
[    32.333] (II) config/udev: Adding input device G15 Keyboard G15 Keyboard (/dev/input/event5)
[    32.333] (**) G15 Keyboard G15 Keyboard: Applying InputClass "evdev keyboard catchall"
[    32.333] (**) G15 Keyboard G15 Keyboard: Applying InputClass "Logitech G5"
[    32.333] (II) Using input driver 'evdev' for 'G15 Keyboard G15 Keyboard'
[    32.333] (**) G15 Keyboard G15 Keyboard: always reports core events
[    32.333] (**) evdev: G15 Keyboard G15 Keyboard: Device: "/dev/input/event5"
[    32.333] (**) evdev: G15 Keyboard G15 Keyboard: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[    32.333] (--) evdev: G15 Keyboard G15 Keyboard: Vendor 0x46d Product 0xc222
[    32.333] (--) evdev: G15 Keyboard G15 Keyboard: Found keys
[    32.333] (II) evdev: G15 Keyboard G15 Keyboard: Configuring as keyboard
[    32.333] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.4/3-3.4:1.0/input/input8/event5"
[    32.333] (II) XINPUT: Adding extended input device "G15 Keyboard G15 Keyboard" (type: KEYBOARD, id 11)
[    32.333] (**) Option "xkb_rules" "evdev"
[    32.333] (**) Option "xkb_model" "pc105"
[    32.333] (**) Option "xkb_layout" "es"
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event16)
[    32.334] (**) HDA Intel PCH Front Mic: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event15)
[    32.334] (**) HDA Intel PCH Rear Mic: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[    32.334] (**) HDA Intel PCH Line: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event13)
[    32.334] (**) HDA Intel PCH Line Out Front: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event12)
[    32.334] (**) HDA Intel PCH Line Out Surround: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event11)
[    32.334] (**) HDA Intel PCH Line Out CLFE: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.334] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event10)
[    32.334] (**) HDA Intel PCH Line Out Side: Applying InputClass "Logitech G5"
[    32.334] (II) No input driver specified, ignoring this device.
[    32.334] (II) This device may have been added with another device file.
[    32.335] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    32.335] (**) HDA Intel PCH Front Headphone: Applying InputClass "Logitech G5"
[    32.335] (II) No input driver specified, ignoring this device.
[    32.335] (II) This device may have been added with another device file.
[    32.337] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   101.034] (II) XKB: reuse xkmfile /var/lib/xkb/server-4968D24C59EB905E8B3DE6B1AD4DB0BD19C330FF.xkm
[  1974.441] (II) config/udev: Adding input device Cypress Sem PS2/USB Browser Combo Mouse (/dev/input/mouse1)
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: Applying InputClass "Logitech G5"
[  1974.441] (II) No input driver specified, ignoring this device.
[  1974.441] (II) This device may have been added with another device file.
[  1974.441] (II) config/udev: Adding input device Cypress Sem PS2/USB Browser Combo Mouse (/dev/input/event19)
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: Applying InputClass "evdev pointer catchall"
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: Applying InputClass "Logitech G5"
[  1974.441] (II) Using input driver 'evdev' for 'Cypress Sem PS2/USB Browser Combo Mouse'
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: always reports core events
[  1974.441] (**) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Device: "/dev/input/event19"
[  1974.441] (**) evdev: Cypress Sem PS2/USB Browser Combo Mouse: ButtonMapping '1 2 3 4 5 6 7 2 9 10 11 12 13 14 15 2 17 18 19 20 21 22 23 24'
[  1974.441] (--) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Vendor 0x5fe Product 0x11
[  1974.441] (--) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Found 9 mouse buttons
[  1974.441] (--) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Found scroll wheel(s)
[  1974.441] (--) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Found relative axes
[  1974.441] (--) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Found x and y relative axes
[  1974.441] (II) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Configuring as mouse
[  1974.441] (II) evdev: Cypress Sem PS2/USB Browser Combo Mouse: Adding scrollwheel support
[  1974.441] (**) evdev: Cypress Sem PS2/USB Browser Combo Mouse: YAxisMapping: buttons 4 and 5
[  1974.441] (**) evdev: Cypress Sem PS2/USB Browser Combo Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1974.441] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.0/input/input22/event19"
[  1974.441] (II) XINPUT: Adding extended input device "Cypress Sem PS2/USB Browser Combo Mouse" (type: MOUSE, id 12)
[  1974.441] (II) evdev: Cypress Sem PS2/USB Browser Combo Mouse: initialized for relative axes.
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) keeping acceleration scheme 1
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) acceleration profile 0
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) acceleration factor: 2.000
[  1974.441] (**) Cypress Sem PS2/USB Browser Combo Mouse: (accel) acceleration threshold: 4




---

### Post by ziq on 2015-09-21
> **ziq said:**
> After following suggested solution, I got the system working but no acceleration since the nvidia driver doesn't seem no recognize the gtx 960. Any suggestion?

Here the log file:

Looks like the problem was related to the inboard graphic card. Disabling it in the BIOS did the trick.

---

### Post by koray2 on 2015-09-21
Hello,

I have a MSI PE60 2QE computer which has nvidia gtx960m graphic card inside. I installed ubuntu 14.04 and walked through the steps for installing the nvidia drivers. I didn't get any serious errors during installation except for the failure of pre-install script which I saw is not very important .
But after reboot, I stuck in the login screen of ubuntu(Normally, the login feature was assigned to auto-login, and was not seeing it.). 
After I login with my password, I see the desktop just for a glimpse and go back to greeter screen again immediately.
With guest account, same scenario.
I understand there is a problem with X server, may be with the configuration of xconfig. But couldn't figure out what it is . 
Any ideas ?

---

### Post by ziq on 2015-09-22
> **koray2 said:**
> Hello,

I have a MSI PE60 2QE computer which has nvidia gtx960m graphic card inside. I installed ubuntu 14.04 and walked through the steps for installing the nvidia drivers. I didn't get any serious errors during installation except for the failure of pre-install script which I saw is not very important .
But after reboot, I stuck in the login screen of ubuntu(Normally, the login feature was assigned to auto-login, and was not seeing it.). 
After I login with my password, I see the desktop just for a glimpse and go back to greeter screen again immediately.
With guest account, same scenario.
I understand there is a problem with X server, may be with the configuration of xconfig. But couldn't figure out what it is . 
Any ideas ?

Can you login en text mode (ctrl+alt+f1) and take a look at the logs file? If it's a X problem, "less /var/log/xorg.0.log" could give some clue.

---

### Post by 3muzel on 2015-10-11
Thaank you jempa333 for posting, you saved me a ton of headache.
For anyone interested, I used the"nano" command instead of the "gedit" in case it didn't work like in my case
Also, I used the proprietary drivers (using Kodibuntu) instead of the official one on the Nvidia website, as the proprietary has the latest drivers for Linux afaik "355"
```

[FONT=monospace]**sudo apt-get install** python-software-properties pkg-config[/FONT]
[FONT=monospace]**sudo** add-apt-repository ppa:graphics-drivers**/**ppa[/FONT]
[FONT=monospace]**sudo apt-get update**[/FONT]
[FONT=monospace]**sudoapt-get install** nvidia-XXX nvidia-settings libvdpau1 #**(**XXX being the selected driver version, 355 the latest as of today**)**[/FONT]
```
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by goodbyefacebook2011 on 2015-10-13
I have followed your instructions to the letter but once I get to

sudo ./{mydriver}

it says command not found.
I am currently in the putty terminal and in my downloads folder, I have checked to make sure this is correct several times so I'm still not sure what I'm doing wrong here.  Please help as I have been searching to make this work for at least 24 combined hours and your solution seems like it would work from a newbie perspective :)

Edit: Well I figured it out lol  I didn't see the part about making the file executable, so I did that by right clicking the file and going to permissions.  Afterwards I was including the {} brackets in the line above.  Upon taking those out everything seems to work fine.  

THANK YOU SOOOOOO MUCH!!!  I am a newbie to Linux and hoping to reformat my last windows drive soon and because of this post that is much closer than I thought it could be :-)

---

### Post by harve2000 on 2015-11-01
Anyone know how to change the default audio out from the DisplayPort to HDMI?  Currently, it's set to go out my DisplayPort instead of my HDMI port.  (Using a DisplayPort to HDMI adapter to get sound now.)

System:
Ubuntu 14.04 LTS
ASUS Strix GeForce GTX 960 (3 DisplayPorts and 1 HDMI)
3.13.0-66-generic #108-Ubuntu SMP  Wed Oct 7 15:20:27 UTC 2015 kernel
NVIDIA Drivers 352.55

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: ID 72 Digital [ID 72 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech F540 Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by harve2000 on 2015-11-01
Just in case anybody else can't get HDMI sound after upgrading from a GTX750ti to a GTX960, it seems even though I ran nvidia-xconfig to detect the new settings after installing the new Nvidia binary, it basically kept all the GTX750ti settings in /etc/X11/xorg.conf.  Ended up just deleting the xorg.conf  (after making a backup) and ran nvidia-xconfig again and rebooted.  I now have sound through the HDMI port.
A diff on the files:
<     BoardName      "GeForce GTX 750 Ti"
---
>     BoardName      "GeForce GTX 960"
60,61c58,59
<     Option         "nvidiaXineramaInfoOrder" "DFP-0"
<     Option         "metamodes" "DVI-I-1: nvidia-auto-select +0+0, HDMI-0: nvidia-auto-select +0+0"
---
>     Option         "nvidiaXineramaInfoOrder" "DFP-5"
>     Option         "metamodes" "nvidia-auto-select +0+0"

---

### Post by chuck_taylor on 2015-11-10
Thanks so much for the help in this thread.  I was able to get everything running correctly on a gtx 750 ti using these instructions.  

However, the next time my system did an automatic update, the kernel updated and now the computer is black screen'ing again immediately after boot.  

Does anyone know how to recover from this situation, or what I should have done to avoid this if I have to wipe the system and re-install?

Thanks for your help.

---

### Post by daniii10 on 2015-11-10
Thanks for the guide but I also have a serious problem with Nvidia driver.

[U][B]My Machine:

[/B][/U]Dell Inspiron 5720
GeForce 630M integrated with Intel graphic card
Dual boot with windows
Currently running Ubuntu 15.10

_**My Problem:**_

First I installed Nvidia driver from Nvidia website (352 version) but than it ruined my Ubuntu completely. I searched the web a lot and everything I tried didn't help (purge Nvidia etc...).
I gave up and installed Ubuntu again fresh install. Than i installed Nvidia proprietary driver from Ubuntu additional drivers (v340.93) and tried to activate Nvidia graphic card with bumblebee. 
This also didn't work and every time when i tried optirun there was an error. Next I installed Nvidia Prime and finally it worked. I changed back to Intel to save battery, so far it seems that everything works this time.
But then I changed back prime select to Nvidia log out and back again and here the black screen is back. I purge Nvidia and reboot. The login screen worked but after login i had desktop only, no dash, no panel, and no icons.
I found a solution by installing Compiz Manager and enable unity plug-in, so now i have a working desktop with Nvidia proprietary driver with prime (because i thought it might bring back my desktop) but if I'll change back prime select to Intel I won't be able to use my Nvidia card again (it will bring back the black screen if I'll try) 
I'm afraid to install Nvidia driver from Nvidia website last time it ruined my Ubuntu.

Please if anyone can help me to get a working Nvidia card I'm really frustrated I'll be so grateful.
Let me now if you need more information.

Sorry for my English.

---

### Post by daniii10 on 2015-11-10
> **chuck_taylor said:**
> Thanks so much for the help in this thread.  I was able to get everything running correctly on a gtx 750 ti using these instructions.  

However, the next time my system did an automatic update, the kernel updated and now the computer is black screen'ing again immediately after boot.  

Does anyone know how to recover from this situation, or what I should have done to avoid this if I have to wipe the system and re-install?

Thanks for your help.

When I got the black screen I purged Nvidia driver read my comment above.

---

### Post by chuck_taylor on 2015-11-10
Do you mean use apt-get purge?  

I'm not sure what package you mean that I should purge.  

I used the nvidia binary .run file to set up the graphics driver as detailed in the first post in the thread, so I'm operating under the assumption that the packaging system doesn't really have much control over the graphics driver at this point.

---

### Post by daniii10 on 2015-11-10
I meant apt-get purge nvidia-*
On login screen go to tty1 and purge nvidia proprietary driver. Installing nvidia driver from nvidia website can cause serous problems like i had.
Read here [http://ubuntuforums.org/showthread.php?t=2302341](http://ubuntuforums.org/showthread.php?t=2302341) the guy explain the differences of nvidia drivers

---

### Post by chuck_taylor on 2015-11-10
Ok, but I did install the nvidia drivers via the website since when I tried to use the xorg-edgers PPA, this resulted in my system black-screen'ing after rebooting.  

It sounds like your suggestion is to re-install and then use the graphics-drivers ppa?

---

### Post by daniii10 on 2015-11-10
I think first step to get your desktop back is to purge the nvidia driver you have installed.
About what driver to install i don't know exactly i suggest you to get help with this from someone more experienced than me. I just happen to get the black screen the same as you, and by completely remove the nvidia driver i got my desktop back.

---

### Post by that_guy2 on 2015-11-10
> **jempa333 said:**
> 
After reboot get correct nvidia-driver (chose graphic-card and OS) at “[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)" (or search webb with “nvidia download”). Right-click on downloaded file and change if to executable. 
sudo gedit /etc/modprobe.d/blacklist.conf [I]#add these lines at the end:
 blacklist vga16fb[/I]
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveua
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off 

Open a putty-terminal with Ctrl + Alt     + F1       
sudo service lightdm stop *#stops graphic session to enable nvidiainstallation*
cd Downloads *#(or wherever you downloaded your nvidia-file)*
sudo ./{***the downloadedfilename***.run} *#follow installation-instructions (normally yes to all)sudo nvidia-xconfig #(if you did not chose “yes” to this in the installation” *
sudo nano [COLOR=#000000]/etc/default/grub[/COLOR] *# change the "GRUB_CMBLINE_LINUX_DEFAULT..."-line to below:*
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset”
sudo update-grub2 #update grub!
 sudo reboot


Sorry but I'm new and still learning linux. I recently bought a 950 and have been battling all day everday for the past week to get the driver to work. At one point I did, but then was locked with a 800x600 resolution, so I reinstalled ubuntu and started over for the millionth time lol.

Ok so I got to the part of changing the file to an excutable and don't understand the rest. Do I go ahead and run the nvidia installer? Or do I just open terminal and enter sudo gedit /etc/modprobe.d/blacklist.conf? And how do I *#add these lines at the end? *I'm also not sure what a putty-terminal is compared to the regular terminal.

Sorry again for all the questions. Any help would be soooo greatly appreciated.

---

### Post by chuck_taylor on 2015-11-10
I was able to fix the problem I mentioned farther up by trying to boot into recovery mode (i.e., hold shift during startup) and then the bios let me boot with the old kernel as one of the 'advanced options' shown by grub for ubuntu. 

Everything looked fine with the 352 drivers once I was booting with the old kernel again.  

Since I don't want to have to boot into an old kernel every time, I ran the 352 binary install again with the --uninstall option to get rid of that driver and then installed the 'nvidia-346' package through synaptic's main menu.  (i.e., didn't use any PPA's / the additional driver tab of synaptic)

It's booting fine now & the nvidia-settings gui is showing that it's using the 346.96 driver.  

I'm not sure why this worked when the PPA's had blown up my system in the past, but it appears to be working, so fingers crossed.  I'm using the 32-bit version of 14.04 since the 64-bit nvidia drivers weren't working with steam, so that may be it...

Hope that someone out there finds this useful.

---

### Post by caisara on 2015-11-23
very thank you. I just install my gtx 750 driver with your tutorial and it works great.

---

### Post by Blue1922 on 2015-12-22
tried everything still doesn't work

---

### Post by Blue1922 on 2015-12-22
it doesn't find my file

---

### Post by alex_4 on 2016-01-16
I've followed the guide at the start of this thread and another one which sounds like the same problem as me here... [http://ubuntuforums.org/showthread.php?t=2289167](http://ubuntuforums.org/showthread.php?t=2289167)

However I still have issues...

[COLOR=#262626][FONT=Arial]I've installed a new GTX960 into my TS140 running Ubuntu 14.04 and ive got issues booting up from a video perspective. The machine boots up as i can still use putty into the terminal but I get some weird visuals. [/FONT][/COLOR]
[COLOR=#262626][FONT=Arial] [/FONT][/COLOR]
[COLOR=#262626][FONT=Arial]Firstly it doesn't beep on post?.... then when the lenovo splashscreen shows up its surrounded by white lines.

[/FONT][/COLOR]
[COLOR=#262626]As it moves onto the Ubuntu boot screen loads of fuzzy white lines gltch and then eventually it freezes with the boot process listed in the background. On occasion it loads with flashing colours but it hasn't done that in a while.[/COLOR]
[COLOR=#262626][FONT=Arial] [/FONT][/COLOR]
[COLOR=#262626][FONT=Arial]Weirdly I can boot up onto the live CD and get to the desktop but theres a lot of white line glitching.[/FONT][/COLOR]
[COLOR=#262626][FONT=Arial] [/FONT][/COLOR]
[COLOR=#262626]Does this sound like an ubuntu problem or is it possibly to do with power... I've got a 450w psu which is more than the recommended 400w[/COLOR]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]

---

### Post by rexen on 2016-01-26
The exact recipe in the first post didn't work for me exactly, but I finally got it working. An included bonus is that I could do it with the driver in the package manager, thus without the manual install from the ".run"-file.
This is what I did:

* Connect a monitor to the DVI-port.
* Fresh install of Ubuntu 15.10
* Set boot option "nomodeset" using the program boot-repair.
* Set blacklist.conf according to the first post. This included fixing the typo "nouveua".

    blacklist vga16fb
    blacklist nouveau
    blacklist rivafb
    blacklist nvidiafb
    blacklist rivatv
    blacklist lbm-nouveau
    options nouveau modeset=0
    alias nouveau off
    alias lbm-nouveau off 

* Switch to non-graphical terminal: ctrl+alt+F1
* Kill GUI: sudo service lightdm stop
* sudo apt-get install nvidia-352
* nvidia-xconfig
* Start GUI again: sudo service lightdm start

And then it worked! 

I think having the monitor connected to the DVI-port while installing the driver is important. My previous attempts used the DP-port while installing the driver. Switching to DVI after driver install did not help.
I connected two additional monitors to DP-ports, and my desktop was extended flawlessly. So it's not that DP doesn't work, but it may be a requirement of at least one DVI monitor to get it set up correctly.

---

### Post by brandon_2 on 2016-02-14
Works! 

I'm gonna create a small script throw it on github to automate this for the noobs. 

I had to install and do the first bit with onboard video, then switch to my gtx960 after the first chunk was accomplished.

---

### Post by adriandelarco on 2016-03-02
Hello, please I need some help.

I have a MSI GE62 2QD computer which has nvidia gtx960m graphic card  inside. I installed ubuntu 14.04 and walked through the steps for  installing the nvidia drivers.

 I didn't get any serious errors during  installation except for the failure of pre-install script which I saw is  not very important.

But after reboot, I stuck in the login screen of Ubuntu(Normally, the  login feature was assigned to auto-login, and was not seeing it.).

After I login with my password, I see the desktop just for a glimpse and go back to greeter screen again immediately.

With guest account, same scenario.

I understand there is a problem with X server, may be with the configuration of xconfig. But couldn't figure out what it is . 

I tried everything, and nothing works... Delete Xauthority, Install Gnome Desktop, update kernel.. 

When I install the NVIDIA drivers I always get a login loop. I'nm using the last BIOS available, Ubuntu 14.04, I tried with driver 361 355 352 352-updates with the same result.

Thank so much

---

### Post by wojciech9 on 2016-03-08
Hi
@adriandelarco I'v got similar problem. Its look like this is not a nvidia driver problem but kernel. 
My PC: MSI PE70 6QE ( with i7 6700HQ)
You can try add "nomodeset" boot parameter
Take a look here: [https://bugzilla.kernel.org/show_bug.cgi?id=109081](https://bugzilla.kernel.org/show_bug.cgi?id=109081)
What i do:
1. Download Ubuntu 16.04 from daily build ( i try 14.04 and got working with kernel 4.4.4  )
1. Boot install with acpi=off ( without this gui install freez) 
   Boot option acpi=off turn off my touchpad and probably other stuff 
2. Install
3. Boot Ubuntu with intel_idle.max_cstate=7 (remove acpi=off)
4. Edit grub replace acpi=off with intel_idle.max_cstate=7 - for next auto boot
5. Install nvidia driver from ***ppa:graphics-drivers/ppa***


But...
I'v got problem with HDMI/DP. Ubuntu works, graphic card too with nvidia driver, but not working with external monitor - i'm still looking solution.
Sorry for my English. Hope this help.

---

### Post by Victor_Lubchuk on 2016-04-14
> **jempa333 said:**
> I have Ubuntu 14.04 64bit and NVIDIA Geforce GTX 960 that caused me a lot of problems to install. Hopefully this can help somebody:

 
in terminal write
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get install build-essential && sudo apt-get install linux-source && sudo apt-get install linux-headers-generic 
sudo gedit [COLOR=#000000]/etc/default/grub[/COLOR] *#change line "GRUB_CMDLINE_LINUX_DEFAULT..."-line to *
**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1     quiet splash nomodeset"** *#(forces low-level graphics to ensure putty does     not give black screen)*
sudo update-grub2
sudo apt-get remove nvidia* && sudo apt-get autoremove *#ensures no former installation clashes with new install*
sudo reboot 

After reboot get correct nvidia-driver (chose graphic-card and OS) at “[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)" (or search webb with “nvidia download”). Right-click on downloaded file and change if to executable. 
sudo gedit /etc/modprobe.d/blacklist.conf [I]#add these lines at the end:
 blacklist vga16fb[/I]
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveua
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off 

Open a putty-terminal with Ctrl + Alt     + F1       
sudo service lightdm stop *#stops graphic session to enable nvidiainstallation*
cd Downloads *#(or wherever you downloaded your nvidia-file)*
sudo ./{***the downloadedfilename***.run} *#follow installation-instructions (normally yes to all)sudo nvidia-xconfig #(if you did not chose “yes” to this in the installation” *
sudo nano [COLOR=#000000]/etc/default/grub[/COLOR] *# change the "GRUB_CMBLINE_LINUX_DEFAULT..."-line to below:*
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset”
sudo update-grub2 #update grub!
 sudo reboot
 

 hopefully it works for you now as it did for me...

Hey. I just by lenovo ideapad Y700 with geforce gtx 960.
I try to use your code to install geforce gtx960 video driver  361 version and your code not working.
after that i following your steps i'm stuck on login screen and can't login to desktop. always when i'm enter user and password in login screen, i'm returning to the same login screen and can't enter to the desktop.
can you tell me why this happend? what can be a reason of this?

---

### Post by fintanboyle on 2016-04-30
> **Victor_Lubchuk said:**
> Hey. I just by lenovo ideapad Y700 with geforce gtx 960.
I try to use your code to install geforce gtx960 video driver  361 version and your code not working.
after that i following your steps i'm stuck on login screen and can't login to desktop. always when i'm enter user and password in login screen, i'm returning to the same login screen and can't enter to the desktop.
can you tell me why this happend? what can be a reason of this?

Here's some instructions on how to edit grub on startup to restore to what you had  [http://askubuntu.com/a/38834](http://askubuntu.com/a/38834) .  It doesn't save the edits but allows you to boot with these edits applied.  To save changes you'll need to gksudo gedit /etc/default/grub in the terminal once you're logged in.

I followed these instructions for installing the driver for my gtx 960 on Ubuntu 16.04 and it worked for me;

[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

---

### Post by bozhidar2 on 2016-06-01
Hello I have Lenovo Y700 with GTX 960 and I have the same black screen problem when istalling NVIDIA drivers. I followed your instructions and after last reboot I get bounced on log in screen. I type my log in password and then I get bouced back to log in screen. Any help would be appreciated...

---

### Post by coffeecat on 2016-06-02
Old thread closed to prevent further necromancy. If anyone needs help with a similar problem, please start your own thread.

---

