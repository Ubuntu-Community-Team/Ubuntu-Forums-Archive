---
title: "proprietary drivers"
date: 2009-04-22
forum: Hardware
---

### Post by gwilkins82 on 2009-04-22
Hi.  A Quick note - been using various Windows platforms my entire life, and was finally pushed over the edge with glitches, crashes, etc.  Been using Ubuntu for a few weeks now, and wish I had tried earlier.  Still very new to the ins and outs, basically know nothing about how it works, but I like that it does.  Been tinkering around with some things, and have a question concerning drivers.  I was messing around w/ desktop visuals, but I cannot load anything except for the 'none' option.  The others will not load.  I hunted around in forums, and all the advice I saw pointed towards restricted drivers.  I went to the hardware drivers tab, and the list is blank, so not really sure what that means.  Could have something to do with the way I wiped my system prior to installing Ubuntu?  Wiped Windows, tried a reinstall that only partially worked, then opted for this new OS.  Not really sure.  Computer is a Gateway M250.  Any advice is great, although nothing serious, since everything else seems to work great.

Graham

---

### Post by coffeecat on 2009-04-22
We need to know what graphics chipset you are using. To use compiz, which is what you get if you click Normal or Extra under Visual Effects, you need hardware acceleration. Different graphics chipset/driver combinations have different abilities. If nothing is showing up under restricted drivers (which is what you need for AMD and NVIDIA cards) it is probably that there is no proprietary driver for your chipset.

Go to Applications > Accessories > Terminal and in the terminal:

```
lspci
```Post the output. That should tell us.

---

### Post by jbdavis52 on 2009-04-22
> **coffeecat said:**
> We need to know what graphics chipset you are using. To use compiz, which is what you get if you click Normal or Extra under Visual Effects, you need hardware acceleration. Different graphics chipset/driver combinations have different abilities. If nothing is showing up under restricted drivers (which is what you need for AMD and NVIDIA cards) it is probably that there is no proprietary driver for your chipset.

Go to Applications > Accessories > Terminal and in the terminal:

```
lspci
```Post the output. That should tell us.
I am having a similar problem. I have a Dell Inspiron 6250 and have switched to Ubuntu after getting a new hard drive installed. Right now I have no access to the ROM BIOS via Dell Setup. Also anytime I try to activate the desktop effects I loose the monitor completely and have to use Grub to fix the problem. Here is the output from lspci:

john@john-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
john@john-laptop:~$

---

### Post by coffeecat on 2009-04-22
> **jbdavis52 said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

My guess is that this graphics chipset is just too old to support compiz. You might want to search the forums for nv11 to see if you can find anything.

Here are links for both yourself and gwilkins82 for compiz-check. You might find it useful.

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

**Edit:** just to add. **gwilkins82** and **jbdavis52**, if you want to run the compiz-check script on each of your setups and post the outputs, that would also be useful. To give you an idea, this is the output I get in Ubuntu Intrepid, which is telling me that for this machine, compiz is fine (which I already knew).

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

---

### Post by gwilkins82 on 2009-04-22
ok, ran that command - although I must admit to not knowing what any of this means.  thanks for the responses though, I'm sure it gets frustrating helping countless noobs such as myself.

G

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:07.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by gwilkins82 on 2009-04-22
also, ran this compiz check deal, and got this in response:

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by coffeecat on 2009-04-22
> **gwilkins82 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

> **gwilkins82 said:**
> Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
 Driver in use:         intel

Well that's very odd. One of my laptops has the Intel 915GM chipset and I don't remember any problems with compiz. It's not the most powerful graphics chipset by any measure, but you should be able to get some of the desktop effects. One thing I noticed after I last posted is that the compiz-check script hasn't been updated in a year. If you look in the script it's hard-coded for releases not later than 8.04. (It gets the Ubuntu 8.10 from your /etc/lsb-release file).

I seem to remember reading about an issue with the intel driver and one of the Intel chipsets, but which chipset and which release I can't remember.

Anyway, I'll bootup that laptop in a couple of hours and check this out and post back. I haven't got Ubuntu 8.10 on it, but I have got Mint6 which is based on Ubuntu 8.10, so any results should be the same.

---

### Post by gwilkins82 on 2009-04-22
Great, appreciate it.  One other thing of note - earlier I am almost positive that the settings were set to 'normal' (as opposed to 'none').  might have done something while messing around w/ various options and what not, although not sure.

---

### Post by coffeecat on 2009-04-22
OK, here I am in Linux Mint 6 on the laptop in question. The most important thing is that I can get all the visual effects - wobbly windows, rotating cube, etc. They're not as smooth as on the nvidia machine, but quite effective nonetheless. The relevant part of lspci:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```...which, apart from an earlier revision number, is the same as yours.

And from compiz-check:

```
Gathering information about your system...

 Distribution:          Linux Mint 
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```So, in theory, your laptop should be as effective as mine.

> **gwilkins82 said:**
> Great, appreciate it.  One other thing of note - earlier I am almost positive that the settings were set to 'normal' (as opposed to 'none').  might have done something while messing around w/ various options and what not, although not sure.

'Normal' is a minimal set of effects but you would have had to have had AIGLX rendering for it. So, if you can remember which options you were messing around with, that might give a clue as to what has gone wrong with compiz. I'm afraid my knowledge of compiz is fairly limited. It's always just worked for me on suitable hardware and I haven't managed to break it yet, so I haven't any experience of mending it. :wink:

---

### Post by gwilkins82 on 2009-04-22
afraid I couldn't say with any certainty, although I'm sure it was something with graphics/visuals settings.  is there a way to reactivate this AiGXL rendering? Again, thanks for the responses.

---

### Post by coffeecat on 2009-04-22
> **gwilkins82 said:**
> afraid I couldn't say with any certainty, although I'm sure it was something with graphics/visuals settings.  is there a way to reactivate this AiGXL rendering? 

I don't know. I was intrigued enough with this issue to have a hunt in the forum, but I couldn't find anything relevant.

Did you, by chance, edit your /etc/X11/xorg.conf file?

---

### Post by gwilkins82 on 2009-04-27
> **coffeecat said:**
> I don't know. I was intrigued enough with this issue to have a hunt in the forum, but I couldn't find anything relevant.

Did you, by chance, edit your /etc/X11/xorg.conf file?


it is possible, although again I am very new at this stuff and am not sure.  i was looking around on various sites and forums for tips and a lot of them involved terminal commands that i did not fullly understand, so maybe - is it possible to find a log somewhere on my system to check for any changes to important system files such as the xorg.conf?  thanks

---

### Post by coffeecat on 2009-04-28
> **gwilkins82 said:**
> is it possible to find a log somewhere on my system to check for any changes to important system files such as the xorg.conf?  thanks

I don't know of such a log. If you made a backup at the time (as some howtos sensibly suggest) that would of course be there. The only other thing would be to check the date/time stamp on your /etc/X11/xorg.conf file. If it's untouched, it will have the date and time of installation.

---

