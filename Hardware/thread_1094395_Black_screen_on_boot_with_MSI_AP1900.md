---
title: "Black screen on boot with MSI AP1900"
date: 2009-03-12
forum: Hardware
---

### Post by markba on 2009-03-12
The MSI Neton AP1900 is an all-in-one PC: [http://global.msi.com.tw/index.php?func=proddesc&maincat_no=654&prod_no=1732](http://global.msi.com.tw/index.php?func=proddesc&maincat_no=654&prod_no=1732)

It consist of an Atom-processor, combined with an integrated video chipset, 945GM:

```
lspci | grep -i display

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

After boot (Intrepid), the normal status bar appears, but as soon as the login window is entered, the screen goes black. The PC boots normal (login sound can be heard, SSH is possible, etc.), but only with a black screen. However, when started in safe mode, I have a screen, but only on 800x600 (or 640x480).

I've tried several versions of Ubuntu (8.04, 8.10, 9.04) and even Fedora 10), all with the same result: only safe mode (with a reduced resolution) works.

Attached is my /etc/X11/xorg.conf file when started in safe mode. Note the vesa-driver, probably causing the low resolution. When manually change the vesa-driver into "intel" or "i810", I'm greeted again with a black screen. :(

Tried several solutions:

From bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/233787](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/233787)
```
1) Add
        Option "monitor-LVDS" "LVDS"
in Device section
2)
Section "Monitor"
        Identifier "LVDS"
        Option "Ignore" "True"
EndSection
```
-> at startup, a config screen appears: none of the possibilities works (with the test button)

Force i810-driver (only on Hardy, i810-driver is deleted from Intrepid repos):
```
dpkg -l xserver-xorg-video-i*
sudo apt-get remove xserver-xorg-video-intel
```
-> at startup, a config screen appears: none of the possibilities works (with the test button)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
-> no go

Several solutions from [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Added to Section "Screen":

```
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```
-> no higher res then 800x600 (same)

While in vesa-mode (800x600):
```
xrandr --addmode default 1024x600
```
-> cannot find mode "1024x600"

```
xrandr --addmode default 800x600
```
-> OK, but useless

Solutions from [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Add to your monitor section line
```
Option "DDC" "False"
```

-> screen (non-vesa), but max res 800x600

```
xresprobe vesa | intel | i810
```
-> no usefull output

Only on Hardy, package is removed from Intrepid:
```
sudo apt-get install 915resolution
```
-> Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets.

Best result I can get so far is in vesa-mode: 800x600, while the monitor can do 1366x768.

I've read several postings and wiki's:
[http://ubuntuforums.org/showthread.php?t=964689](http://ubuntuforums.org/showthread.php?t=964689)
[http://ubuntuforums.org/archive/index.php/t-975908.html](http://ubuntuforums.org/archive/index.php/t-975908.html)
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950) 
.... but none seem to have a solution.

It seems like the Intel 945GM Display adapter has two channels: LVDS and VGA. My guess is that the wrong channel, the one with no screen attached has been chosen, hence a black screen on the real monitor. But because the MSI no external VGA, there's no way to test the other channel. Otherwise, how to debug this?

Another possibility is that the specs of the attached monitor (resolution, hsync, vsync, etc.) is not configured correctly, but how to change that?

I'm clueless right now.

---

### Post by copycat on 2009-04-02
Not good... I have the same issue with my Shuttle mediacenter with mythbuntu.

And I planned to buy this one... now I'm going to wait.

---

### Post by Tipped OuT on 2009-04-02
I'm guessing it's just driver issues. Sadly, not all computers are able to work  with Linux due to drivers. I suggest messing around with it more, or just trying another distro and see if you get the same results. If so, I'm sorry friend. If you have a desktop computer, then you could just buy compatible parts for it. But if you're on a laptop, looks like you have no choice but to buy another one.:icon_frown:

---

### Post by copycat on 2009-04-02
We can not say that markba did no investigation

---

### Post by markba on 2009-04-02
Soon after, I found the problem was indeed in the driver and a (temporarely) workaround:

> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119/comments/78](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119/comments/78)

Solution for me (MSI Neton AP1900 with Intel 945GM Display Adpater) was the following:
- using vesa-driver
- modified /etc/X11/xorg.log
```
    Section "Monitor"
            Identifier "Configured Monitor"
            HorizSync 30-100
            VertRefresh 30-100
    EndSection
```

I used the xorg.conf from Eric Griffis (thanks!): [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119/comments/17](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119/comments/17)

No 3D (so no compiz), but resolution is correct now and the PC is in a usable state, but this is only a temporary solution.

My guess, the 'magical' point is this (from /var/log/Xorg.0.log):
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.

For this, I compared a working configuration with the same display chipset (Samsung NC10 Netbook): /var/log/Xorg.0.log did not have any of those lines. Probably, the internal screen is connected to the LVDS channel, but because it is removed, hence not working, logically the screen does not have input so stays black.

I tried Jaunty Alpha 5, but the problem still exists, despite status of this bug "Fix released".

Sadly, but my comment was the last in line, so no definitive solution yet.


> **Tipped OuT said:**
> If you have a desktop computer, then you could just buy compatible parts for it. 

It is a desktop model, but the MSI Neton AP1900 is a all-in-one model (screen, PC, etc. integrated), so it is not possible to swap parts. :mad:

---

### Post by copycat on 2009-04-03
Thanks Markba for the update.

Is the netop fast with Ubuntu?
I deliverid it only to one customer with XP and it was fast.

---

### Post by markba on 2009-04-03
The MSI is fast enough for normal usage (browse, mail, document editing, etc.) because it's equipped with an Atom processor (1.6 GHz), just as most of the netbooks like Asus EEE do.

---

### Post by copycat on 2009-04-03
Are you sure that Compiz isn't working now?  You nee to install compiz-settings-manager. And the backend config.
But I'm sure you know this :-)

---

### Post by markba on 2009-04-03
> **copycat said:**
> But I'm sure you know this :-)

Yes I know :-)

Apart from the missing 3D-effects (I'm not really missing them, though), is the fact that playing a movie in Totem or VLC is in fact unusable (lagging enormously). Watching movies in Flash (Youtube) is OK.

So my solution is workable, but only hardly. I'm trying all versions of Jaunty, in the hope this regression is solved.

---

### Post by copycat on 2009-04-03
Just installed Jaunty on a old p4 3.2 with cheap nvidia agp card...

works fine.  Strange that my MSI Nvidia PCI-X card is'n working fine with the restricted drivers

---

### Post by markba on 2009-04-03
The MSI has an integrated video chipset, Intel 945GM. 

The ironic fact was that I had to gamble: I could not test the machine with a live-CD, because it was only available from webshops, but my guess was that with Intel components, I had nothing to fear. I was proved wrong, sadly.

---

### Post by gpremuda on 2009-05-25
Partial solution:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Unknown-1"
EndSection

Section "Monitor"
	Identifier	"LVDS"
        Option    	"Ignore"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Unknown-1"
	Device		"Configured Video Device"
EndSection

```
After restarting X you need to set the correct resolution in System -> Preferences -> Screen resolution
The gdm login screen is still a bit garbled, but it works.

---

### Post by markba on 2009-05-25
OK, thanks, I'll give it a go...

---

