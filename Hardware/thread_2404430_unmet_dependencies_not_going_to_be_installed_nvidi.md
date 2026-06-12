---
title: "unmet dependencies not going to be installed nvidia graphics"
date: 2018-10-24
forum: Hardware
---

### Post by josdh149 on 2018-10-24
Can someone help me to get a workaround this:
```
sudo apt install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
 nvidia-current : Depends: nvidia-304 but it is not going to be installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.87-0ubuntu0~gpu18.04.1) but it is not going to be installed
                     Recommends: libnvidia-gl-390:i386 (= 390.87-0ubuntu0~gpu18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Everytime I'm trying to install one of these drivers it seems to be I am in some kind of loop.

---

### Post by kc1di on 2018-10-24
Did you try what it told you to do ```
'apt --fix-broken install'
``` ?

---

### Post by josdh149 on 2018-10-24
> **kc1di said:**
> Did you try what it told you to do ```
'apt --fix-broken install'
``` ?

Yes, but that does not work.

It gives me a output similar as this one:
```
sudo apt install -f
[sudo] password for jos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 101 not upgraded.
4 not fully installed or removed.
Need to get 0 B/29,1 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 285988 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by kc1di on 2018-10-24
what happen when you enter this command in a terminal?
```
sudo dpkg --configure -a
```

---

### Post by josdh149 on 2018-10-24
> **kc1di said:**
> what happen when you enter this command in a terminal?
```
sudo dpkg --configure -a
```

It seems to be a similar output as before:
```
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on libnvidia-gl-390 (= 390.87-0ubuntu0~gpu18.04.1); however:
  Package libnvidia-gl-390:amd64 is not installed.

dpkg: error processing package nvidia-driver-390 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-390:
 nvidia-390 depends on nvidia-driver-390; however:
  Package nvidia-driver-390 is not configured yet.

dpkg: error processing package nvidia-390 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-390:amd64:
 libnvidia-ifr1-390:amd64 depends on libnvidia-gl-390; however:
  Package libnvidia-gl-390:amd64 is not installed.

dpkg: error processing package libnvidia-ifr1-390:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-390:i386:
 libnvidia-ifr1-390:i386 depends on libnvidia-gl-390; however:
  Package libnvidia-gl-390:i386 is not installed.

dpkg: error processing package libnvidia-ifr1-390:i386 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 nvidia-driver-390
 nvidia-390
 libnvidia-ifr1-390:amd64
 libnvidia-ifr1-390:i386

```

---

### Post by kc1di on 2018-10-24
Which version of ubuntu are you using?  Which kernel?
it would be helpful if you could install inxi ```
sudo apt install inxi 
```
and run this from a terminal ```
inxi -Fxz
``` and post the output here.

There is definitely a dependency problem.

---

### Post by josdh149 on 2018-10-24
> **kc1di said:**
> Which version of ubuntu are you using?  Which kernel?
Ubuntu 18.04 LTS
Kernel 4.15.0-36-generic obtained from uname -r

> it would be helpful if you could install inxi ```
sudo apt install inxi 
```
it gives me the same dependency problem, i cannot install this

---

### Post by kc1di on 2018-10-24
Ok lets do this and try again.
in the terminal type ```
rm /var/cache/apt/archives
```
then
```
sudo apt update
sudo apt install inxi
```

---

### Post by josdh149 on 2018-10-24
> **kc1di said:**
> Ok lets do this and try again.
in the terminal type ```
rm /var/cache/apt/archives
```
then
```
sudo apt update
sudo apt install inxi
```

I obtained the following results from this:
```
jos@jos-ThinkPad-W520:/var/cache/apt$ sudo rmdir archives
jos@jos-ThinkPad-W520:/var/cache/apt$ sudo apt update
Hit:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                            
Hit:3 http://security.ubuntu.com/ubuntu bionic-security InRelease                                       
Hit:4 http://nl.archive.ubuntu.com/ubuntu bionic InRelease                                              
Hit:5 http://linux.teamviewer.com/deb stable InRelease                                                  
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                                              
Hit:7 http://linux.teamviewer.com/deb preview InRelease                                                 
Hit:8 http://nl.archive.ubuntu.com/ubuntu bionic-updates InRelease                                      
Ign:9 https://dl.bintray.com/hawkeye116477/waterfox-deb release InRelease                               
Hit:10 http://nl.archive.ubuntu.com/ubuntu bionic-backports InRelease                                   
Hit:11 https://dl.bintray.com/hawkeye116477/waterfox-deb release Release                                
Hit:12 https://repo.nordvpn.com/deb/nordvpn/debian stable InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
102 packages can be upgraded. Run 'apt list --upgradable' to see them.
jos@jos-ThinkPad-W520:/var/cache/apt$ sudo apt install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 inxi : Depends: gawk
        Recommends: hddtemp but it is not going to be installed
        Recommends: mesa-utils but it is not going to be installed
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.87-0ubuntu0~gpu18.04.1) but it is not going to be installed
                     Recommends: libnvidia-gl-390:i386 (= 390.87-0ubuntu0~gpu18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

---

### Post by kc1di on 2018-10-24
Ok you have 102 packages that can be ugrade to so do this ```
sudo apt upgrade
```
Also you never said which version of ubuntu you installed?

---

### Post by josdh149 on 2018-10-24
> **kc1di said:**
>  Also you never said which version of ubuntu you installed?
> **josdh149 said:**
> Ubuntu 18.04 LTS
Kernel 4.15.0-36-generic obtained from uname -r
I guess I mentioned my version?

> **kc1di said:**
> Ok you have 102 packages that can be ugrade to so do this ```
sudo apt upgrade
```
This gives the following output:
```
$ sudo apt upgrade
[sudo] password for jos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.87-0ubuntu0~gpu18.04.1) but it is not installed
                     Recommends: libnvidia-gl-390:i386 (= 390.87-0ubuntu0~gpu18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```

---

### Post by #&amp;thj^% on 2018-10-24
This is just a stab in the dark >>But try and run:
```

LC_MESSAGES=C dpkg-divert --list '*nvidia-340*' | sed -nre 's/^diversion of (.*) to .*/\1/p' | xargs -rd'\n' -n1 -- sudo dpkg-divert --remove
sudo apt --fix-broken install
```

---

### Post by josdh149 on 2018-10-25
> **1fallen said:**
> This is just a stab in the dark >>But try and run:
```

LC_MESSAGES=C dpkg-divert --list '*nvidia-340*' | sed -nre 's/^diversion of (.*) to .*/\1/p' | xargs -rd'\n' -n1 -- sudo dpkg-divert --remove
sudo apt --fix-broken install
```

This actually worked out for me! The stop sign disappeared and I was able to fix broken. After that I was also able to run
```
sudo apt upgrade
```
successfully. However, now coming back to the origin of the problem:
I am still not able to start nvidia settings. Therefore, I cannot select my graphical card. Currently it is using intel graphics (which accepts external monitors but somehow cannot get my original screen resolution higher than 960*540).
I took a look at my nvidia drivers and it says that the device is using an alternate driver: [https://ibb.co/mwmj8A](https://ibb.co/mwmj8A)

I figured out this might have something to do with the problem. What do you guys think? Do you also know how to get my display resolution normal again. At the login screen it is still normal....weird enough.

---

### Post by kc1di on 2018-10-25
I'm not sure but this [page ]("https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu")may be of help.

---

### Post by josdh149 on 2018-10-25
> **kc1di said:**
> I'm not sure but this [page ]("https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu")may be of help.
The page you referred to resulted in:
**step 1**:
```
$ lspci -k | grep -A 2 -i "VGA"
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Lenovo 2nd Generation Core Processor Family Integrated Graphics Controller
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [Quadro 1000M] (rev a1)
    Subsystem: Lenovo GF108GLM [Quadro 1000M]
    Kernel driver in use: nouveau

```
**step 2**: Intel® Sandybridge Mobile
**step 3**:
```
$ sudo ubuntu-drivers devices
[sudo] password for jos: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000DFAsv000017AAsd000021D1bc03sc00i00
vendor   : NVIDIA Corporation
model    : GF108GLM [Quadro 1000M]
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-390 - third-party free recommended
driver   : nvidia-304 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin

```
For which I already have selected the recommended one in [I]Software & Updates 
[/I]and verified by trying to install which results in the message I already installed it.
```
$ sudo apt-get install nvidia-390
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-390 is already the newest version (390.87-0ubuntu0~gpu18.04.1).
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-34 linux-headers-4.15.0-34-generic linux-image-4.15.0-34-generic
  linux-modules-4.15.0-34-generic linux-modules-extra-4.15.0-34-generic qtdeclarative5-qtquick2-plugin
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```
Now I should be able to select it and in *Software & Updates* it should show a green bubble, well...it does not.

The weird thing is that in step one it says I use the nouveau driver whereas in *Software & Updates *the recommended nvidia-390 is selected. However, it keeps telling me that I am using an alternate driver.

---

### Post by #&amp;thj^% on 2018-10-25
If your machine is equipped with a Nvidia gpu and you want to make use of it to the fullest, you need to install the "proprietary" Nvidia drivers. 
But lets have a look at: (Please use code tags to keep the format intact)
```
cat /var/log/Xorg.0.log
```
Also show us what this returns:
```
apt policy nvidia-prime && apt policy nvidia-390
``` 
This can be a tedious process so hang in there with us. :)

---

### Post by josdh149 on 2018-10-26
> **1fallen said:**
> If your machine is equipped with a Nvidia gpu and you want to make use of it to the fullest, you need to install the "proprietary" Nvidia drivers. 
But lets have a look at: (Please use code tags to keep the format intact)
```
cat /var/log/Xorg.0.log
```
Also show us what this returns:
```
apt policy nvidia-prime && apt policy nvidia-390
``` 
This can be a tedious process so hang in there with us. :)

I get the following outputs:
First: [https://paste.ubuntu.com/p/vH7bXtMg5d/](https://paste.ubuntu.com/p/vH7bXtMg5d/)
Second: [https://paste.ubuntu.com/p/Tc8fjhNFQy/](https://paste.ubuntu.com/p/Tc8fjhNFQy/)

---

### Post by #&amp;thj^% on 2018-10-26
Hmmm? outside a few common warnings this install should work...:o

lets give this a shot>>edit this file via:
```
sudoedit /etc/gdm3/custom.conf
```
 and uncomment the line
```

#WaylandEnable=false
```
 by removing the # in front.
So it would now look like:
```
WaylandEnable=false
```

Save the file and then reboot.
Also i would like to know if you have yet tried if possible in the bios disabling the intel gpu?

---

### Post by josdh149 on 2018-10-26
> **1fallen said:**
> Hmmm? outside a few common warnings this install should work...:o

lets give this a shot>>edit this file via:
```
sudoedit /etc/gdm3/custom.conf
```
 and uncomment the line
```

#WaylandEnable=false
```
 by removing the # in front.
So it would now look like:
```
WaylandEnable=false
```
Save the file and then reboot.
I tried this: the laptop booted but now also had a 960*540 resolution before logging in. Normally this was only the case after logging in. As I proceeded I found out this resolution was still the maximum possible option while I do have a 1600*900 screen. The iGPU did not work yet, only intel graphics. I tried to select a propietary driver in *Software & Updates* but it snaps back to the nvidia-390 (not propietary) while mentioning this card is using an alternative driver. Maybe it also helps out mentioning my laptop does have a functioning vga output on max resolution of the external screen. The DP does not work.
> **1fallen said:**
> Also i would like to know if you have yet tried if possible in the bios disabling the intel gpu?
I have not tried this yet. However, I make use of a dual boot with grub. I also have windows 10 which I normally boot at home with an eGPU and the internal nvidia disabled (disabled in windows device manager). I don't know if this might influence the behavior in ubuntu but I don't think so since windows device manager disables this device and chooses my eGPU. It would also be nice to use this on ubuntu, but when I'm anywhere else then home I use ubuntu with intel graphics but prefer my internal nvidia.

And I like to get my original resolution of my internal screen back of course ;)

---

### Post by #&amp;thj^% on 2018-10-26
> the internal nvidia disabled (disabled in windows device manager). 
Yes that could be an important factor here>>>Is secure boot enabled?
But check in your bios to see if you can switch between the two GPU's, I would check this first. :)

---

### Post by josdh149 on 2018-10-27
> **1fallen said:**
> Yes that could be an important factor here>>>Is secure boot enabled?
But check in your bios to see if you can switch between the two GPU's, I would check this first. :)

I cannot seem to find secure boot so I’m not sure about that. Regarding the switching it seems this is possible. I attached some screenshots so you can check it out. It seems that I already selected the Nvidia. This also has to do with the fact that I needed to do this for my windows configuration.

[https://ibb.co/d0khyA](https://ibb.co/d0khyA)
[https://ibb.co/cVe9dA](https://ibb.co/cVe9dA)

Maybe it is also worth mentioning that my Ubuntu used to work fine with the integrated graphics. Good resolution and external display over vga.

---

### Post by josdh149 on 2018-10-27
> **1fallen said:**
> Yes that could be an important factor here>>>Is secure boot enabled?
But check in your bios to see if you can switch between the two GPU's, I would check this first. :)
You can see my reply on this in the post above. But additionally I thought it also might be useful to share the following:
```

$ sudo gedit /etc/X11/xorg.conf# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 390.87  (buildmeister@swio-display-x64-rhel04-14)  Tue Aug 21 17:33:38 PDT 2018

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
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

```

---

### Post by josdh149 on 2018-10-28
As this problem used to only influence my account I thought there might be some config file affecting the possibility to run Nvidia settings and being able to properly set the resolution.
As I was looking at some hidden files in my home folder I found .nvidia-settings-rc containing the following code:
```
#
# /home/jos/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Tue Oct 16 12:06:19 2018
#

# ConfigProperties:

RcFileLocale = C
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Memory_Used_(GPU_0),Yes,3000

# Attributes:

0/SyncToVBlank=1
0/LogAniso=0
0/FSAA=0
0/GammaCorrectedAALines=0
0/TextureClamping=1
0/FXAA=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/GammaCorrectedAALinesValue=16
[DPY:LVDS-0]/Dithering=0
[DPY:LVDS-0]/DitheringMode=0
[DPY:LVDS-0]/DitheringDepth=0
[DPY:LVDS-0]/ColorSpace=0
[DPY:LVDS-0]/ColorRange=0
[DPY:LVDS-0]/SynchronousPaletteUpdates=0
[DPY:DP-0]/Dithering=0
[DPY:DP-0]/DitheringMode=0
[DPY:DP-0]/DitheringDepth=0
[DPY:DP-0]/ColorSpace=0
[DPY:DP-0]/ColorRange=0
[DPY:DP-0]/SynchronousPaletteUpdates=0
[DPY:DP-1]/Dithering=0
[DPY:DP-1]/DitheringMode=0
[DPY:DP-1]/DitheringDepth=0
[DPY:DP-1]/ColorSpace=0
[DPY:DP-1]/ColorRange=0
[DPY:DP-1]/SynchronousPaletteUpdates=0
[DPY:DP-2]/Dithering=0
[DPY:DP-2]/DitheringMode=0
[DPY:DP-2]/DitheringDepth=0
[DPY:DP-2]/ColorSpace=0
[DPY:DP-2]/ColorRange=0
[DPY:DP-2]/SynchronousPaletteUpdates=0
[DPY:DP-3]/Dithering=0
[DPY:DP-3]/DitheringMode=0
[DPY:DP-3]/DitheringDepth=0
[DPY:DP-3]/ColorSpace=0
[DPY:DP-3]/ColorRange=0
[DPY:DP-3]/SynchronousPaletteUpdates=0
[DPY:DP-4]/Dithering=0
[DPY:DP-4]/DitheringMode=0
[DPY:DP-4]/DitheringDepth=0
[DPY:DP-4]/ColorSpace=0
[DPY:DP-4]/ColorRange=0
[DPY:DP-4]/SynchronousPaletteUpdates=0
[DPY:DP-5]/Dithering=0
[DPY:DP-5]/DitheringMode=0
[DPY:DP-5]/DitheringDepth=0
[DPY:DP-5]/ColorSpace=0
[DPY:DP-5]/ColorRange=0
[DPY:DP-5]/SynchronousPaletteUpdates=0
```

Does this help out?

---

### Post by #&amp;thj^% on 2018-10-28
Basically secure boot may prevent you from loading some driver's (special drivers for their wireless card, video card, or specialty hardware. These drivers are normally unsigned, as they can come from a number of different sources. If secure boot is enabled, and the drivers are not signed, these drivers will not load. In order for them to load, each driver must be "signed". This process of signing the drivers is not extremely difficult, but it can be a hassle... especially if you change/update the driver, or change/update the kernel software that is a part of Ubuntu. Each change will require that you resign the driver. ) you installed which can be quite frustrating. I have been through this myself: the driver installed correctly, everything seemed to be good to go, but it just didn't work. Took me some time to find it was secure boot's preventing the OS from loading it. 

Secure boot is used to prevent anything that isn't signed with a certified key to boot. This in "theory" helps to prevent malware from booting on your system. Many question it's usefulness and many don't even think twice before disabling it. (Myself included!)
Maybe just maybe in the distant future we may need secure boot, but I do not turn it on for now. And if needed you can re-enable it.

And you say you don't know if secure boot is enabled or not, I'm going to assume that it is  due to fact you dual boot with windows 10.

So there you have it. Here is a concise description of how to do that: [https://askubuntu.com/a/768310/134479](https://askubuntu.com/a/768310/134479)

---

### Post by josdh149 on 2018-10-28
> **1fallen said:**
> Basically secure boot may prevent you from loading some driver's (special drivers for their wireless card, video card, or specialty hardware. These drivers are normally unsigned, as they can come from a number of different sources. If secure boot is enabled, and the drivers are not signed, these drivers will not load. In order for them to load, each driver must be "signed". This process of signing the drivers is not extremely difficult, but it can be a hassle... especially if you change/update the driver, or change/update the kernel software that is a part of Ubuntu. Each change will require that you resign the driver. ) you installed which can be quite frustrating. I have been through this myself: the driver installed correctly, everything seemed to be good to go, but it just didn't work. Took me some time to find it was secure boot's preventing the OS from loading it. 

Secure boot is used to prevent anything that isn't signed with a certified key to boot. This in "theory" helps to prevent malware from booting on your system. Many question it's usefulness and many don't even think twice before disabling it. (Myself included!)
Maybe just maybe in the distant future we may need secure boot, but I do not turn it on for now. And if needed you can re-enable it.

And you say you don't know if secure boot is enabled or not, I'm going to assume that it is  due to fact you dual boot with windows 10.

So there you have it. Here is a concise description of how to do that: [https://askubuntu.com/a/768310/134479](https://askubuntu.com/a/768310/134479)

Well, first of all thanks a lot for your explanation! I really appreciate it and it helps me out. As I consider this what you said, and the fact that I am mostly using my ubuntu on the go: Is it possible to make it properly work again? On intel graphics? As for now the resolution max is 960x540 which is really annoying.

---

### Post by lordboltar on 2018-10-28
To add the Proprietary GPU Drivers PPA in Ubuntu and update the software sources, use the following commands:

sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt update

Close terminal then open Software and Updates click on Additional Drivers and install latest nVidia drivers

---

### Post by josdh149 on 2018-10-29
As I'm trying to get back my original resolution of my laptop screen I ran into the following:
```
$ xrandr
Screen 0: minimum 8 x 8, current 960 x 540, maximum 32767 x 32767
LVDS1 connected primary 960x540+0+0 (normal left inverted right x axis y axis) 340mm x 190mm
   960x540       59.82* 
   864x486       60.00    59.92    59.57  
   800x450       60.00  
   640x480       59.94  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
It looks like it does not detect that my screen has a maximum resolution of 1600*900 and that there is not any displayport. That is weird right?

---

### Post by josdh149 on 2018-10-29
> **1fallen said:**
> Hmmm? outside a few common warnings this install should work...:o

lets give this a shot>>edit this file via:
```
sudoedit /etc/gdm3/custom.conf
```
 and uncomment the line
```

#WaylandEnable=false
```
 by removing the # in front.
So it would now look like:
```
WaylandEnable=false
```

Save the file and then reboot.
Also i would like to know if you have yet tried if possible in the bios disabling the intel gpu?

As I have mentioned yesterday I would just like to change back to intel graphics and having my laptop just initially work on its normal 1600*900 resolution. For now, I have to manually add the resolution with xrandr --newmode --addmode. As this is a bit complex I would like to have it initially go to the normal resolution when I boot. Then I remembered that before applying the above it used to boot in its normal resolution up to its login screen before switching to a low resolution. Now, after the application of this it also booted low res. So, I can change this back but I do not know if this helps. Furthermore, within xrandr it says VGA1 is disconnected also when I plugin a cable and it does not even show my displayport. Any thoughts on this?

---

### Post by #&amp;thj^% on 2018-11-01
My work schedule has increased,  leaving me little time to help out on forums lately. (Sorry for not responding in a timely manner)
If you want to try to undo the Wayland option>>>
```
sudoedit /etc/gdm3/custom.conf
```
Now just re-add the comment>>"#" so it will now read exactly like:
```
#WaylandEnable=false
```
And save the file before closing the terminal, now after a reboot should leave you just as you were prior to the change.
And if you are going to just use your intel GPU, you can safely un-install the nvidia driver with:
```
sudo apt remove --purge nvidia*
```
Again a reboot is needed to see the change.

---

### Post by josdh149 on 2018-11-05
> **1fallen said:**
> My work schedule has increased,  leaving me little time to help out on forums lately. (Sorry for not responding in a timely manner)
If you want to try to undo the Wayland option>>>
```
sudoedit /etc/gdm3/custom.conf
```
Now just re-add the comment>>"#" so it will now read exactly like:
```
#WaylandEnable=false
```
And save the file before closing the terminal, now after a reboot should leave you just as you were prior to the change.
And if you are going to just use your intel GPU, you can safely un-install the nvidia driver with:
```
sudo apt remove --purge nvidia*
```
Again a reboot is needed to see the change.

Yes these are the exact steps I did. However, as my computer now boots correctly at the correct resolution, after the login it seems to have forgotten the resolution. It switches to 960*540 which is the highest possible. I have to manually add a new mode with xrandr. This is not a big struggle, however, the biggest problem is that it does not recognize external display. A big pain in the ass as I work a lot with external monitors. In wayland this works but in some way my mouse is lagging in wayland.

---

### Post by josdh149 on 2018-11-15
> **1fallen said:**
> My work schedule has increased,  leaving me little time to help out on forums lately. (Sorry for not responding in a timely manner)
If you want to try to undo the Wayland option>>>
```
sudoedit /etc/gdm3/custom.conf
```
Now just re-add the comment>>"#" so it will now read exactly like:
```
#WaylandEnable=false
```
And save the file before closing the terminal, now after a reboot should leave you just as you were prior to the change.
And if you are going to just use your intel GPU, you can safely un-install the nvidia driver with:
```
sudo apt remove --purge nvidia*
```
Again a reboot is needed to see the change.

I still am wondering if you could come up with something...

---

### Post by josdh149 on 2018-12-03
I guess no one has any solutions anymore for this?

---

