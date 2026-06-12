---
title: "nForce 610i : audio and nVidia graphic drivers How-to"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by djopino on 2008-03-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/195139](https://bugs.launchpad.net/ubuntu/+bug/195139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Euréka!

Here's and HOW-TO make work audio, video proprietary drivers for the motherboard GA-73VM-S2 that has nforce 610i chipet with GeForce 7050 graphic card. Maybe this will work for other motherboards that has nforce 610i.

**AUDIO**

First, with the fresh install of download ubuntu 7.10, the audio did not work. I made all the updates of ubuntu over internet and after I did the code proposed by Temüjin :
```
sudo update-pciids
```

I also ran the scripts proposed by Temüjin:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
I'm not sure what of these did fix my audio but know it works!

**GRAPHICS**

After that, I had a problem to set the native resolution. I have a wide screen monitor that runs with 1440x900 but with the vesa graphic driver, when I tried to set to 1440x900, it did not work. When I tried to install the restricted driver with the graphical utility in System/Administration/Restricted Drivers Manager the display manager did not work. So here's how to make nVidia drivers work :

First uninstall the nVidia drivers provided by the Restricted Drivers Manager.

After go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Select Linux IA32 latest version if you have 32bits distribution or AMD64 if you have ubuntu AMD64. Download and save it on your desktop.

Go where you saved the file and right click on it, select propreties. Go into permissions and mark the box "Allow executing file as a program".

Now you have to close your display manager. Close all you programs, log out and press ctrl+alt+F1. You will enter in a console that is not on the display manager. Log with your normal user and password. 

First close your display manager. Type :
```
killall gdm
```
replace gdm by kdm for KDE display manager.

Go to the directory where you saved the nVidia driver for linux. Type :
```
cd Desktop
```
and then
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```
verify the version that is written. If the version is different, change it on the command above. To see the files you have in the directory you are, type "dir".

Now follow the step by step installer. At the end it is asked if you want to configure your xorg.conf. Say yes, this will select the nvidia driver. Now nVidia driver is installed!

When you return to the console type:
```
sudo gdm
```

You should see the nVidia logo before the login screen.

Enjoy!


NOTE: the new nVidia drivers from their web site were uploaded by nVidia on the February 26, 2008.

---

### Post by pt123 on 2008-03-22
But does it recognise your surround sound channels with that?

---

