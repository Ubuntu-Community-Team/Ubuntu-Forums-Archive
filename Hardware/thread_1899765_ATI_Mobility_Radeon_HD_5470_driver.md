---
title: "ATI Mobility Radeon HD 5470 driver"
date: 2011-12-24
forum: Hardware
---

### Post by delsus on 2011-12-24
I have recently installed Ubuntu 11.10 on my HP Pavilion dv6-3182 laptop and when I install the propriotory driver the OS finds it doesn't seem to be working, and when I install the post release version I get this error:

> Sorry the installation of this driver failed.

Please have a look at the log file for the details: /var/log/jockey.log 

If anyone knows a driver that is compatible with the ATI Mobility Radeon HD 5470 could you please post it, if you need the contents on jockey.log lemme know and i'll post it, seems kinda long.

Thanks for any help.

---

### Post by BC59 on 2011-12-24
You could try install the driver from Synaptic. If you don't have it already installed, do it through Software Center. Then open it and search fro FGLRX. Install it from there.

---

### Post by collisionystm on 2011-12-24
> **delsus said:**
> I have recently installed Ubuntu 11.10 on my HP Pavilion dv6-3182 laptop and when I install the propriotory driver the OS finds it doesn't seem to be working, and when I install the post release version I get this error:



If anyone knows a driver that is compatible with the ATI Mobility Radeon HD 5470 could you please post it, if you need the contents on jockey.log lemme know and i'll post it, seems kinda long.

Thanks for any help.


Open a terminal

sudo apt-get install fglrx-updates

install compiz-config-settings-manager

reboot

open compiz config manager

click on openGL, change texture filter to fast, UNCHECK sync to vblank

open amd catalyst admin program

enable tear free 

log out and back on

you will be running smooth.

I have a 6380G and I had to figure all this out.

---

### Post by delsus on 2011-12-24
> **collisionystm said:**
> Open a terminal

sudo apt-get install fglrx-updates

install compiz-config-settings-manager

reboot

open compiz config manager

click on openGL, change texture filter to fast, UNCHECK sync to vblank

open amd catalyst admin program

enable tear free 

log out and back on

you will be running smooth.

I have a 6380G and I had to figure all this out.

When I try to open CCC I get this error:

> There was a problem initializing Catalyst Control Center Linux Edititon. It could be caused by the following:

No AMD driver installed or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for your AMD hardware or configure using aticonfig

---

### Post by BC59 on 2011-12-24
Why don't you trying install the driver through Synaptic?

---

### Post by delsus on 2011-12-24
> **BC59 said:**
> Why don't you trying install the driver through Synaptic?

Sorry I did biu get the same error as in my previous post when I try to check CCC, also when I try to run aticonfig with sh aticonfig in the usr/bin folder it says "aticonfig: 1: Syntax error: "(" unexpected" is there anything else i need to install to run aticonfig?

---

### Post by BC59 on 2011-12-24
Look here if you can find a solution:
[https://bitcointalk.org/index.php?action=printpage;topic=28028.0](https://bitcointalk.org/index.php?action=printpage;topic=28028.0)

---

### Post by delsus on 2011-12-25
Ok I managed to get aticonfig running, seemed to work after I installed the JDK, I was wondering if anyone knows the aticonfig commands to get my card working properly, and allow me to open CCC.

Thanks again, once I have got this sorted out I should be ok.

---

### Post by collisionystm on 2011-12-27
> **delsus said:**
> Ok I managed to get aticonfig running, seemed to work after I installed the JDK, I was wondering if anyone knows the aticonfig commands to get my card working properly, and allow me to open CCC.

Thanks again, once I have got this sorted out I should be ok.



aticonfig --initial -f

reboot

---

### Post by delsus on 2011-12-27
> **collisionystm said:**
> aticonfig --initial -f

reboot

I did that and it wrote the new xorg.conf, however now my ubuntu will not boot, I just get a screen with some options and [ok] or [fail] next to them, I think it is because of the new xorg.conf (because that is all I changed).


One thing that occured to me is that my laptop uses switchable graphics, could that be causing problems, and if so how would I overcome it?

EDIT: restored my origanal xorg.conf from live cd running nautilus through gksudo,

Here is the xorg.conf that stopped my laptop booting if it helps.

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
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


---

### Post by delsus on 2011-12-28
Ok I know for certain that the problem is that the system is defaulting to my integrated GPU, with ATI drivers disabled I can configure vgaswitcheroo to change to my discreet GPU if I queue it for the next login and I log out then back in again because the xserver has restarted.

However everytime I reboot it defaults to the integrated GPU again, and to make it worse when I reinstall the FGLRX driver the vgaswitcheroo folder in /sys/kernel./debug folder disapears I therefore cannot change the GPU after the FGLRX driver is installed.

I also have a suspicion that if I run aticonfig --initial -f it will not boot, I have looked the boot script to switch the cards here [https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup](https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup)

and it says to use this command:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,IGD,OFF"

in the /etc/default/grub file then update grub which will enable all GPUs, then switch to the integrated GPU then switch the discreet GPU off. I have tried modifying that command to read 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,DIS,OFF" and 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=0 hybridopts=ON,DIS,OFF" but it still defaults to the integrated GPU.

So onto my question finally, either modifying this command or another command how will I set the default GPU to discreet rather than the integrated one from boot? and that should solve my problems.

Thanks for any help you can be.

---

