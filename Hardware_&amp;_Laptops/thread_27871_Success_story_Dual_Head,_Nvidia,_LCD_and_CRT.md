---
title: "Success story: Dual Head, Nvidia, LCD and CRT"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by GrumpySmurf on 2005-04-18
Setting up dual head displays on X is one of the most challenging aspects of configuring a Linux workstation in my experience. I hope this helps other users running into problems.

First, my hardware:

Nvidia Geforce 6800GT
CRT: Samsung Syncmaster 1200NF
LCD: Samsung Syncmaster 172x

I have been configuring various dual head systems on Linux using my laptop and a CRT at work and that hasn't posed too much trouble once I figured out multiple screen settings, layout options, etc.  This particular configuration above is on my gaming system at home, and presented new issues.

Basically, the specified HorizSync and VertRefresh from the manufacturer don't work!  I couldn't get 1280x1024 as a "Validated display mode".  I won't go into the details of my unsuccessful configuration attempts, but suffice to say, I bumped up the values and now it works like a champ.  Here's the relevant bits from my xorg.conf, followed by a brief explanation.

```

Section "Device"
        Identifier      "GF6800"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Screen          0
        Option          "TwinView"
        Option          "HorizSync" "CRT-1: 30-121; DFP-0: 30-80"
        Option          "VertRefresh" "CRT-1: 50-185; DFP-0: 60-75"
        Option          "MetaModes" "CRT-1: 1600x1200, DFP-0: 1280x1024"
        Option          "TwinViewOrientation" "CRT-1 LeftOf DFP-0"
        Option          "RenderAccel"
        Option          "IgnoreEDID" "true"
EndSection

Section "Monitor"
        Identifier      "DFP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "GF6800"
        Monitor         "DFP"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

TwinView keeps all its configuration in the device section and doesn't require specific settings under seperate monitor sections like standard Xinerama setups.  After watching the Xorg log, I determined that the detected monitors were CRT-1 and DFP-0, so those are used here.

The LCD specifications from Samsung for HorizSync and VertRefresh are 30-63 and 56-75, respectively.  These settings did not allow me to set the resolution to 1280x1024.  I bumped the HorizSync to 30-80 and VertRefresh to 60-75 and was able to use my desired resolution.  This was the key to getting my configuration as I wanted it.

The ability to specify the monitor settings on one Option line for the Device are a great advantage from using TwinView instead of classic Xinerama.  Multiple monitor, device and screen sections are very confusing, and I'm glad Nvidia makes it all easier.

I hope this helps someone having difficulty configuring a dual head setup.  Good luck!  Feel free to PM me with any questions.

---

### Post by TravisNewman on 2005-04-18
I've never seen it spelled out so well :) Makes me wish I had a twinview!

---

### Post by GrumpySmurf on 2005-04-18
[QUOTE=panickedthumb]I've never seen it spelled out so well :) Makes me wish I had a twinview![/QUOTE]
 It's not spelled out that well... If I had more time I would have taken notes while I tweaked the configuration and posted something with more detail.

But its not a HOWTO, so I guess thats all good.

---

### Post by AnGeLiX on 2005-04-18
If anyone is going to setup a Twin-View or Dual Head Display HE MUST READ [THIS](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt)  (ReadMe file of the nvidia drivers)

---

### Post by airtonix on 2007-11-28
do you need the binary drivers or can you use the 'nv' one that comes installed with fiesty?

---

