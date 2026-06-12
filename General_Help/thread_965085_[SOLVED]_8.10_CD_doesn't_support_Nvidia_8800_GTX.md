---
title: "[SOLVED] 8.10 CD doesn't support Nvidia 8800 GTX?"
date: 2008-10-31
forum: General Help
---

### Post by Inwards on 2008-10-31
The 64-bit boot CD can't start X / Ubiquity.  The X.org.log shows that it's trying (and failing) to use VESA.  I've got two Nvidia 8800 GTX's in SLI in my box.  8.04 boot disk works fine.  Does Ubuntu no longer support this card (even unaccelerated) out-of-the-box?

---

### Post by sirchmeister on 2008-10-31
I can report that I installed a completely fresh copy of Ubuntu 8.10 (Desktop/64bit) and upon installing the restricted drivers a reboot brings me to a terminal rather than the gnome environment.

EVGA 680i LT Motherboard
2x 8800 GT (SLI)
C2D E8400 @ 3GHZ

---

### Post by Fatfool on 2008-10-31
odd. I have an 8800GTX as well and I just tested the livecd on the rig. typical config of the era with an EVGA 680i/QX6700 combo.

I could get to the desktop perfectly fine.

not tried to use the restricted drivers or anything (cos I can't connect to my Access point with that rig) but everything else works fine.

note that mine is the i386 livecd though. No intention of actually using ubuntu on that rig.

---

### Post by Inwards on 2008-11-01
I just tried again with the 32 bit desktop CD and still no joy.  I wonder what's going on here?  I'm trying this on a Dell XPS 720:

Core 2 Extreme Q6800 @ 2.9Ghz
Dell nVIDIA nForce 680i SLI BTX motherboard
4 gigs of RAM
NVidia 8800 GTX w/768megs x 2
AGEIA Physx 100 <--- Maybe X thinks this is the video card???

Ideas?

---

### Post by hpstg on 2008-11-01
Exactly the same problem here.
8800GT's in SLI
Asus nForce 680i sli

The live cd boots, installs fine.

When I boot to the installation it works, but after downloading and installing the nVidia drivers and rebooting, all I get is no GDM.

P.S.: WTF? (x64 here).

---

### Post by TeXtonyx on 2008-11-01
nVidia "legacy" video support
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

"The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade." 

My experience with nVidia drives is that they are not installed
automatically. I followed a Howto about downloading the driver
from nVidia. I wound up using envyng after writing the xorg.conf
with nvidia-settings. Your computer probably supports SSE.

---

### Post by Inwards on 2008-11-01
> **hpstg said:**
> Exactly the same problem here.
8800GT's in SLI
Asus nForce 680i sli

The live cd boots, installs fine.

When I boot to the installation it works, but after downloading and installing the nVidia drivers and rebooting, all I get is no GDM.

P.S.: WTF? (x64 here).

You're doing better than me.  I can't even get the livecd to boot to the desktop.

---

### Post by dagrump on 2008-11-01
Some one in their infinite wisdom thought users shouldn't have to edit the xorg.conf file & everything should be automagiclly configured. This is a noble idea, but the hardware people wrote the drivers to work with the existing model in mind, not some sudden change to some other method. It will most likely be fixed sooner or later, but it shouldn't of happened.
Some where buried in the intrepid archives are posts about this issue, you need to designate your primary video in your xorg file, I tried this & had no luck. Good luck, I hate regressions, I just got tired of messing with it & went back to 8.04.1 on the SLI machine. I have 2 machines with SLI setups, I guess I'll be running hardy for the foreseeable future, at least on these 2.

---

### Post by Inwards on 2008-11-02
Okay, I just fixed this.  As dagrump mentioned, the problem is specific to SLI setups.  To get the bootCD to work, wait for the command prompt to come up, then:

- sudo -s
- lspci | grep nV <-- somewhere in there (the last two lines for me) will show your graphics card.  Make a note of the three hex numbers at the beginning of the last line.  They'll be something like 06:00.1.
- vi /etc/X11/xorg.conf
- add the following to the "Device" section of the file:

BusID "XX:YY:Z"

Note that the config file wants two colons, not one colon and a period as lspci will give you.

- save the file
- /etc/init.d/ubiquity start
- complete the installation using the GUI

Addendum

- After the system installed, everything came up okay for me.  I then installed the restricted driver and got no video after rebooting.  So I brought up a terminal (control-alt-f1) and edited the xorg.conf file again.  The fix for me was to change the BusID to the other card's.  Weird, but everything seems happy now.

---

### Post by gamin123 on 2008-11-06
thank you for the tip Inwards. I installed both Ubuntu/Kubuntu 8.10 amd64 editions on my computer (with sli 8800GT), and after downloading the 177.80 drivers, I was unable to return to X. after editing xorg.conf and adding BusID "03:00:0", everything is finally working.

many many thanks for the tips ;)

---

### Post by Benjirii on 2008-11-07
Thanks a lot Inwards. I'd been getting pretty frustrated over not getting the restricted drivers to work. Was able to fix it with the solution you posted!

+1 happy camper.

---

