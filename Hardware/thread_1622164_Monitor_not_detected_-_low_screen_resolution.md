---
title: "Monitor not detected - low screen resolution"
date: 2010-11-15
forum: Hardware
---

### Post by shaunthesheep on 2010-11-15
I have a 19 inch iiyama HM903DTA Vision Master Pro 454 CRT monitor that is not detected and I am stuck with a highest screen resolution of 1024 x 768. I would prefer a higher resolution. 

I am using Ubuntu Studio 10.10 and I have an Nvidia Geforce2 GTS/Pro card.

The following info about it is reported using the command :

**lshw -c display**

*-display               
       description: VGA compatible controller
       product: NV15 [GeForce2 GTS/Pro]
       vendor: nVidia Corporation
       physical id: 0

       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resour

[B]
2010-11-15 19:30:02 (278 KB/s) - `compiz-check' saved [28360/28360][/B]

$ chmod +x compiz-check
$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)
 Driver in use:         nouveau
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N)

**The contents of xorg.conf is as follows**:

# Minimal xorg.conf for the Nouveau driver

Section "Device"
    Identifier    "Default screen"
          Driver        "nouveau"
EndSection

xorg.conf is not located in directory etc/X11 but in /usr/share/doc/xserver-xorg-video-nouveau

I have been searching the forum and found a few threads on the subject  but I am still not sure how to proceed. Any help would be appreciated.

---

### Post by shaunthesheep on 2010-11-21
Any any ideas people?

---

