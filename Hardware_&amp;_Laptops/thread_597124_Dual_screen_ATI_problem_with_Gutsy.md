---
title: "Dual screen ATI problem with Gutsy"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by bandad on 2007-10-30
Hi,
I have enjoyed a dual screen setup for a long while. Previously, in non-ubuntu mode I have used xinerama. When I moved to ubuntu 7.04 I spent ages getting it to work and eventually discovered that I needed to use mergedFB mode. Now I have upgraded to Gutsy 7.10 - which is generally great and I love the compiz stuff - and  have lost the dual screen.

lshw looks like this...

```
 *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8

```

The System > Administration > Screen and Graphics tool doesn't help. It has the second screen page, but it will not provide the options for Secondary Screen. It seems that the DVI output (on which I have a DVI-VGA converter) is not being recognised. On start up, both screens display in clone mode as you would expect, so there is no issue with the hardware down stream of the card.

The xorg.conf looks like this

```
Section "Device"
        Identifier      "Radeon9200"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "monitor-DVI-0" "IIyama-1"
        Option          "monitor-VGA-0" "IIyama-0"
EndSection

Section "Monitor"
        Identifier      "IIyama-0"
        Option          "DPMS"
        HorizSync       24-80
        VertRefresh     56-75
        Option          "LeftOf"        "IIyama-1"
EndSection

Section "Monitor"
        Identifier      "IIyama-1"
        Option          "DPMS"
        HorizSync       24-80
        VertRefresh     56-75
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon9200"
        Monitor         "IIyama-0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Virtual         2560 1024
                Modes           "1280x1024" 
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "AIGLX" "true"
EndSection


```

The Xorg.0.log output includes the dreaded line... 
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found


Has anyone solved this problem?
How can I persuade my PC to find the other half of the graphics card?

---

### Post by Cyberapoc on 2007-12-02
I have exactly the same problem in gutsy fluxbuntu. Working with mergedFB won't work. Dual screen works on boot, until the login window appears.

Any help would be very much appreciated.

---

### Post by bandad on 2007-12-07
Cyberapoc,

I haven't cracked this one yet. Have you?
Please help us someone!!!

---

### Post by kolslorr on 2007-12-08
same problem, waiting for someone who will shed the lights pls....

---

### Post by Redenbacher on 2007-12-08
I have the same problem on my laptop that I tried to fix a couple of weeks ago. I found a thread that showed how with a vast amount of xorg.conf editing. Basically you had to set it up so there would be 2 seperate output devices(both the same card with different identifiers) and 2 separate screens and monitors in the xorg.conf. I'll see if I can find the post again... I just remember it being a mess

Found something that might be helpful:
[http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/](http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/)

It seems the old support from feisty was dropped in favor of xrandr, so  this might help as well:
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

