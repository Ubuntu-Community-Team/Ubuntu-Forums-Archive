---
title: "ATI drivers cause black screen (didn't on 9.04)"
date: 2009-11-24
forum: Hardware
---

### Post by hleather on 2009-11-24
Hi,

   I have an Alienware M17-R1 which worked well under 9.04.  It's got two ATI 3850 graphics cards in it.  

   I recently upgraded to 9.10 but had to do this through safe mode.  If I use the ATI drivers, I get a black screen after the glowing ubuntu logo.  I've tried the latest drivers from ATI, without joy.

   Can anyone help me?  Has anyone else found this or fixed it?

   Thanks in advance,

   Hugh.

---

### Post by hleather on 2009-11-26
Can anyone help?

---

### Post by nelfin on 2009-11-26
You don't see the login screen at all?

This may be a similar problem, apparently there's a known issue when doing an upgrade (as opposed to a clean install) on a system that uses restricted drivers:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/451252](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/451252)

---

### Post by hleather on 2009-11-26
Hi,

   Thanks for responding :-)

   I don't get a log in screen.  Just blackness after the glowing logo.  I do hear the 'ubuntu is starting' chime.  And it was a fresh install.  Any ideas?

   Cheers,

   Hugh.

---

### Post by nelfin on 2009-11-26
Well, I have a HD 4870 for which I use ATi's restricted driver and it works fine. Seeing as you have two cards, I presume they're in CrossFire. Maybe try taking one out and see if that has any effect?

Other than that, try temporarily changing your boot options (whack Esc a few times just after POST if you don't have a timeout on your grub menu. Select your kernel, probably the one highlighted, press 'e', then get rid of the words "quiet splash". Then boot, see if the last few lines before it halts are useful (try posting them, I'm sure someone in here would have a better idea))

---

### Post by hleather on 2009-11-27
Hi,

    Crossfire sounds familiar.  I'm not confident to take out one of the cards on my laptop.

    There doesn't seem to be anything in the last few lines of the output.  It doesn't actually halt, it goes black directly after, as if Ubuntu is booting normally but just doesn't realise the screen has gone black.

    Sorry to be a pain.

    Hugh.

---

### Post by hleather on 2009-11-29
Hi,

Can anyone help?

---

### Post by nelfin on 2009-11-29
Back again,

I didn't check up enough obviously, otherwise I would have realised that your computer is in fact a laptop. To be sure, is your card a HD 3850 X2, or are there actually two HD 3850 cards in there? Your laptop would have to be pretty beastly to warrant two graphics cards (the HD xxxx X2 range of Radeons and Mobility Radeons have two GPUs on the same die).

Does anything display on an externally connected monitor (providing you have one available) after the whole boot up spiel? (almost) all laptops should have a VGA out for connecting to monitors and projectors. Probably on the spine, or on the sides near the hinge of the screen.

Try logging into a tty (it might work that you can press Ctrl+Alt+F1 after the chime plays and the screen goes black, but changing your boot options (like with getting rid of "quiet splash") to include "text" at the end should bypass X and take you to a terminal). I don't know how much terminal experience you have, so we'll keep it simple.

Make a copy of your xorg.conf file (Just in case):
```
cp /etc/X11/xorg.conf ~/xorg.conf.bak
```

Edit the original so we can use the VESA driver:
```
sudo nano /etc/X11/xorg.conf
```

Change the Device section to resemble:
```
Section "Device"
    Identifier      "Configured Video Device"
    Driver          "vesa"
EndSection
```

Save & Restart. Hopefully your laptop will be in a useable state, where we have our lovely X back (at something like 640x480).

Try and grab a copy of /var/log/xorg.0.log
Open it up and read through to see if there are any problems; lines that start with (EE) are errors.

If it is the driver, there's the open source alternative, which runs faster on 2D, but doesn't support 3D in the newer chipsets (basically anything in the HD 3000/4000/5000 range). You have to completely remove the ATI driver to use that one, instructions for all of that are here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

See if anything in [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen) helps if that doesn't.

Good luck

---

### Post by asdrc on 2009-11-29
Go to recovery mode when booting, & select "try to fix graphics problems " or some thing like that.

---

### Post by hleather on 2009-11-30
Hi,

   I can boot with the vesa driver, but the resolution is 1600x1200 not 1920x1200 as my screen supports.  Also I can't suspend or hibernate because the colours go crazy and I can't make head nor tail out of the screen.

   I've tried doing the things suggested in the link - still blackness :-( 

   I've attached my Xorg.0.log.  I'm not really sure whether it's a happy log or not.

   Here's my xorg.conf

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    BusID        "PCI:3:0:0"
    Option        "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Radeon 9600"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1920x1200"
    EndSubSection
EndSection

Section "DRI"
    Mode        0666
EndSection

Section "Extensions"
    Option    "Composite" "Enable"
EndSection

---

### Post by nelfin on 2009-11-30
Try changing your Monitor section in your xorg.conf to:
```
Section "Monitor"
     Identifier "Configured Monitor"
     Option "ReducedBlanking"
EndSection
```

From your Xorg.0.log:
```
...
(II) RADEON(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
...
```

---

### Post by hleather on 2009-12-01
Hi Nelfin,

Thank you very much for your help, btw.  It is very much appreciated.

I changed that and had the same results :-(  It didn't seem to change the log file very much - which I've attached.  A diff shows only this:

15c15
< (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 30 10:01:24 2009
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  1 08:21:51 2009
19a20
> (**) Option "ReducedBlanking"
371a373,376
> (II) RADEON(0): Default Engine Clock: 660000
> (II) RADEON(0): Default Memory Clock: 850000
> (II) RADEON(0): Calling ASIC Init
> (II) RADEON(0): ASIC_INIT Successful
373d377
< drmOpenDevice: open result is 9, (OK)
595,597c599,601
< (II) RADEON(0): [pci] 32768 kB allocated with handle 0x1186e900
< (II) RADEON(0): [pci] ring handle = 0x2b7ff000
< (II) RADEON(0): [pci] Ring mapped at 0x7f7450fe6000
---
> (II) RADEON(0): [pci] 32768 kB allocated with handle 0x1188e900
> (II) RADEON(0): [pci] ring handle = 0x2b800000
> (II) RADEON(0): [pci] Ring mapped at 0x7f339ac94000
599,600c603,604
< (II) RADEON(0): [pci] ring read ptr handle = 0x1b800000
< (II) RADEON(0): [pci] Ring read ptr mapped at 0x7f7450fe5000
---
> (II) RADEON(0): [pci] ring read ptr handle = 0x1b7ff000
> (II) RADEON(0): [pci] Ring read ptr mapped at 0x7f339ac93000
602,603c606,607
< (II) RADEON(0): [pci] vertex/indirect buffers handle = 0x2b800000
< (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0x7f743c8c4000
---
> (II) RADEON(0): [pci] vertex/indirect buffers handle = 0x2b801000
> (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0x7f3386572000
605,606c609,610
< (II) RADEON(0): [pci] GART texture map handle = 0x2b801000
< (II) RADEON(0): [pci] GART Texture map mapped at 0x7f743ac44000
---
> (II) RADEON(0): [pci] GART texture map handle = 0x2b802000
> (II) RADEON(0): [pci] GART Texture map mapped at 0x7f33848f2000
1080c1084
< (II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0x1b7ff000 at 0x7f74510e7000
---
> (II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0x2b7ff000 at 0x7f339ad95000


Can you think of anything else that might help?

Thank you,

Hugh.

---

### Post by nelfin on 2009-12-01
Hey Hugh,

Don't worry about it. I figure that just because I have practically no experience troubleshooting stuff in ubuntu doesn't mean that I should sit by and do nothing because "someone else out there should help him, as they'll know more than me".

After reading your logs through and the entire xorg.conf man page (not forgetting a lot of help from Google), I've got yet another suggestion. Drawing your attention to lines 403-408 in your Xorg.0.log (doesn't matter which one, they're the same in both) it appears that that X is applying your monitor layout to your VGA out, not LVDS (your laptop's screen). As an aside, I thought at one point you said that you were using the fglrx one from ATI? There is a wiki page on problems relating to fglrx bits interfering with the radeon driver [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) but those symptoms don't seem to apply here.

Lets try editing your xorg.conf once more:

Comment out the Option "ReducedBlanking" in the "Configured Monitor" Monitor section.

Add this section
```
Section "Monitor"
    Identifier "LVDS"
    #Option "ReducedBlanking" # Shouldn't be needed, but uncomment it if it doesn't detect this
EndSection
```

Add
```
    Option "monitor-LVDS" "LVDS"
```
to your Device section

And change your Screen section to reflect this, i.e.
```

Section "Screen"
    Identifier "Default Screen"
    Monitor "LVDS"
    ...
```

Hope it works. The man page for xorg.conf is a beast.

---

### Post by hleather on 2009-12-02
Hi Nelfin,

Still no joy.  I think maybe I should revert back to 9.04 :-(

Thanks for your help!

Cheers,

Hugh.

---

### Post by nelfin on 2009-12-02
Unfortunately, unless someone else has some form of solution magic, I guess switching back to Jaunty is best for now.

---

