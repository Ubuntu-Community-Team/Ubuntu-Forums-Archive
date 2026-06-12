---
title: "Ubuntu 10.04 LTS: How to boot into command line"
date: 2010-09-07
forum: Hardware
---

### Post by Welly Wu on 2010-09-07
Hello! I have a new ASUS N61JV-X2 which I recently purchased from Amazon and I installed both Microsoft Windows 7 Ultimate x64 bit Edition and Ubuntu 10.04 Lucid Lynx AMD_x64 bit LTS in a dual boot configuration.

I would like to know how I can boot into the command line so that I can install the proprietary NVIDIA Geforce GT 325M drivers. This means that I will get into a TTY screen and stop GDM from loading along with the X Server.

When I finish working on the installation, I also would like to know how I can change the configuration back to its default which is to say that I want the X Server and GDM to start as per the normal boot process.

I would appreciate detailed step-by-step instructions. I consider my level of understanding of GNU/Linux to be above average so I will not be afraid of getting into the nitty gritty details.

Thank you.

---

### Post by jocko on 2010-09-07
Is there any particular reason you don't want to use the nvidia driver that comes packaged for ubuntu in the repos?
To install it, simply go to System-->Administration-->Hardware drivers and follow the very simple instructions.

If you really need to install it with nvidia's installer, just go to a virtual terminal (Ctrl+Alt+F1), login and stop gdm:
```
sudo service gdm stop
```Then run the installer:
```
sudo sh [COLOR=Red]nameofnvidiasinstallerfile.run[/COLOR]
```And restart gdm:
```
sudo service gdm start
```Or reboot:
```
sudo reboot
```But remember: if you install the driver manually from nvidia, you'll have to remember to run the installer again every time there is a kernel update. If you install the one from the repos, it will be automatically rebuilt when needed.

---

### Post by ellgor on 2010-09-07
Hi,

To get into a command line at boot as soon as the comp posts press the tab-bar key, or keep it pressed, a screen will appear with the different options to play with, as to the Nvidia thing I found this guide that works a treat (it appears that the nvidia drivers somehow don't load in correctly when done normally):

) Download Newest Nvidia drivers from their website (one's for your card)
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor

---

### Post by shreepads on 2010-09-07
Welly I had put together something that you may find useful when I did the same thing at this post:
[http://ubuntuforums.org/showthread.php?p=9676616#post9676616](http://ubuntuforums.org/showthread.php?p=9676616#post9676616)

Only thing, I'm running 32 bit so YMMV...

---

### Post by Welly Wu on 2010-09-07
I tried all of these possible solutions and others for my ASUS N61JV-X2 notebook PC, but I always get a Black Screen of Death (BSOD) when I try to open up a TTY or temporarily stop GDM. This requires me to utilize the CTRL+ALT+DEL combination to reboot my Ubuntu OS.

I remember reading in an AnandTech article which reviewed my specific laptop that the Intel IGP is compatible with Nouveau and the NVIDIA Optimus 325 M GPU is not yet fully supported by the manufacturer at this time. In fact, NVIDIA has no estimated time frame as to if they will issue the correct driver package to allow for seamless switching that utilizes the Optimus technology in a Linux environment.

Thank you for your detailed solutions. Unfortunately, I am going to settle with the default configuration that uses Nouveau because it consistently works on my laptop.

---

