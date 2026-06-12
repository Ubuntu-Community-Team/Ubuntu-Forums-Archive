---
title: "HP LaserJet P1102w -- wireless problem"
date: 2010-12-18
forum: Hardware
---

### Post by owkaye on 2010-12-18
I just bought this printer and tried following the instructions in this thread ([http://ubuntuforums.org/showthread.php?t=1479670](http://ubuntuforums.org/showthread.php?t=1479670)) to get it working on my wireless network but even though gcc is installed I'm getting this error when I run HPLIP:

> warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.I'm on Ubuntu 10.10 and I'm wondering why I'm getting this error, and what I can do about it?  I already used Synaptic to reinstall gcc, and when that didn't help I removed gcc them I installed it again, but that didn't help either ... and the only instructions I can find for getting wireless printing working on this printer requires me to use the HPLIP installer script ... which apparently does not recognize that gcc *is* installed.

How do I fix this?

---

### Post by wojto on 2011-08-05
Hi,

I came up with a sort of tutorial to configure the HP Laserjet p1102w wireless(wifi) printer, connected with USB cable, as well over wifi. I am currently usig Ubuntu 11.04, but it shoud work under older distributions too.

**Connecting over USB**

Is no big deal. Just plug and the system should configure it automatically. If not install the newest version of HPLIP```
sudo apt-get install hplip hplip-gui
``` and then siply add a new printer from MENU System > Administration > Printing or with Terminal ```
sudo hp-setup -i 
```**Connecting over wifi = wirelessly**

Wireless printing uder ubuntu is a little tricky. The manufacter mostly supports it for Windows, on the installation CD, but it can work on the Linux the same way. Most of the job is to configure the ad-hoc connection. Turn on your printer and on  and make a sweep for wireless networks. You shoud find something like HP432CBA. Try to connect to it, but if will probably fail. 

Therefore you have to edit this network : Edit connections > Wireless > [choose the network], click Edit and select the IPv4 Settings. Set Method to =Shared to other computers=, Save and try to connect again. It should work now.

Now press the button (x) on your printer for few seconds and wait until it prints the configuration page. Remember the printer cant be in sleep mode, use (I) to wake it. On this configuration page find the IPv4 address. Open your browsver and put the address in there. You should see the printers server page. If yes, it is almost done. 

Now we can add the printer. At first install hplip-gui, if isnt installed on your machine. ```
sudo apt-get install hplip-gui 
``` Then open System > Administration > Printing, click to add a new printer, select =Find network printer=, enter the IPv4 address into the Host column. It would find Jetdirect, click foward, choose or download a proper driver and print a test page.

Hope that it helped.

---

