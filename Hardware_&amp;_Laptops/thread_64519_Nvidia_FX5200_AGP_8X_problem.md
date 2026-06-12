---
title: "Nvidia FX5200 AGP 8X problem"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by bogoliubov on 2005-09-11
Hello there. I have an Nvidia FX5200 card that is supposed to be able to run AGP 8X. The mainboard should support this speed to. But I can't get AGP 8X. Does anyone out there have any idea what I should do to fix this?
Below is the output from the files that I guess are important... :

/proc/driver/nvidia/agp$ cat status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Enabled

/proc/driver/nvidia/agp$ cat card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000e1b:0x1f000301

/proc/driver/nvidia/agp$ cat host-bridge
Host Bridge:     VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000a1f:0x00000b01

This one is edited a bit, since it is a bit large....
$ cat /etc/X11/xorg.conf 
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "L1715S"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "L1715S"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Gezzer on 2005-09-11
via synaptic search for and install
nvidia-glx

once installed open a terminal and write
sudo nvidia-glx-config enable

logout then back in and then check your GPU ...

---

### Post by tseliot on 2005-09-11
First off:

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        [COLOR=Red]#Load    "dri"[/COLOR]
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"

---

### Post by bogoliubov on 2005-09-11
Thank's alot. I'd missed the dri stuff. But, I couldn'r run the nvidia-glx-xonfig; I got this error message:

$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


Any ideas?

---

### Post by bogoliubov on 2005-09-12
I did try to change the md5 sum. Then I could do
$ sudo nvidia-glx-config enable
then I restarted the computer (how do one restart X only?)...

But I still get AGP 4X, not 8....

---

### Post by skoal on 2005-09-12
Bogo, unless you purposefully enabled SBA (side band addressing) in your module config, make sure you have the latest system BIOS update for your VIA/KT400 board.  This is typical on those chipsets trying to use AGP3.0(8x). See the Nvidia README for more information.

\\//_

---

### Post by bogoliubov on 2005-09-12
[QUOTE=skoal]Bogo, unless you purposefully enabled SBA (side band addressing) in your module config, make sure you have the latest system BIOS update for your VIA/KT400 board.  This is typical on those chipsets trying to use AGP3.0(8x). See the Nvidia README for more information.

\\//_[/QUOTE]

Hey, I was reading the Nvidia README and I started to suspect this. I hoped it wouldn't be that, since I've never updated my bios, and I don't know how to do it. Plus of course the fact that it's a bit more dangerous than mucking about with software stuff...  :)

Thank's !!

---

### Post by skoal on 2005-09-12
Yes, sir.  Updating your BIOS is just one option.  You could also recompile the nvidia driver and force the AGP rate in there.  However, by doing so, you more than likely will see why the driver kicks it down to 4x instead, for stability.  All that info is in the README or can be gleaned from the nvnews.net forums (or even google).  Updating a BIOS is easy and straight forward.  All the steps are given on Asus' website (with all the warnings attached to it).

Did you have 8x working in Windows before? Have you checked your BIOS settings (relating to AGP).  Many possibilities here...

\\//_

---

### Post by skoal on 2005-09-12
By the way, bogo, I would try out using the NVIDIA gart interface as well.  It looks like you are using the kernel supplied agpgart.  Just change xorg.conf Option "NvAGP" "1" and add this to /etc/hotplug/blacklist: 

# Nvidia
intel-agp

If you're hesitant to update your BIOS, give that a shot first and/or try a prior Nvidia driver version...

\\//_

---

### Post by bogoliubov on 2005-09-15
Thanks alot! I'll try that as soon as I can; I'm going to Germany for a week tomorrow. Then one week in Italy. I've got a tough job... :)

Anyway, no; I've never used windows with this mainboard/CPU. However I have used the GFX card in Windows and, if I remember correctly, did work at AGP 8X...

Anyway, I don't think I'll recompile the nvidia driver, since I'm not very experienced in Linux (yet!).

Just one question..., What is this blacklist thingy and what does it do?

Cheers!

---

