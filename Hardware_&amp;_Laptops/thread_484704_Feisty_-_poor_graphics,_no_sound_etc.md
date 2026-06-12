---
title: "Feisty - poor graphics, no sound etc"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by pablo88 on 2007-06-26
Hi -

I have had Feisty on a laptop running well. This is a newish machine (9 months old) with 2 Gb of ram, an intel 1.8ghz M processor, 80gb sata drive, wide screen.

However, the lack of sound (for some reason I could not record sound at all) led me to reinstall Feisty from scratch. So far this looks like a bad move; I am in need of some sound advice to correct the following problems:

1) The graphics are now so bad as to make the machine unusable. How do I find out what video driver I need and where do I get it from? (This is odd as screen rendering before was excellent). Currently the screen res is set at 1024 x 768 and refresh shows at 60hz (with no option to change either of these). I am sure the refresh rate was higher in the previous install. I installed Envy to upload the appropriate ATI or Nvidia drivers, but the result came back that my machine uses neither of ATI or Nvidia - so which one and where do I get and install the best driver for it?

2) I have installed Msttcorefonts but need to add Tahoma. How is this done? I did it 5 months ago easily (when the machine was running 6.06 prior to upgrading to 7.04) but cannot for the life of me figure out how to do it this time around. Before, I just lobbed the Tahoma.ttf files into the fonts folder. But I cant find that folder on 7.04 and even if I did, it probably wouldn't work. Befuddled.

3) I need to use Audacity to record stuff for podcasts. This was the problem that caused me to reinstall 7.04 in the first place. How do I get this audio aspect to work? I have a desktop on which I also run 7.04 and I cannot record sound in Audacity or Sound device there either. It's a puzzle.

Any sage advice welcome. My confusion is in danger of becoming despair.

-- Pablo

Mt lspci shows:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by CompactDestruction on 2007-06-26
You have an Intel integrated graphics chipset.

---

### Post by pablo88 on 2007-06-26
Yes, my dim brain is beginning to see that. Thanks.

Do you have any pointers as to why it is soooo bad, whereas before it was v good ?  And what I might be able to do to make it render properly again ?

-- Pablo

---

### Post by PaulFr on 2007-06-26
From my reply to your earlier post:

1. For your display resolution problem, you have an Intel 915 graphics controller, so the ATI / NVidia drivers will not work. One convenient way to fix it is to look at this blog post: **[http://roland-lopez.blogspot.com/200...ution-fix.html](http://roland-lopez.blogspot.com/200...ution-fix.html)[** which is linked to from **[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)**.

2. For your font problem, take a look at the "Manually" section of **[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)**.

3. For your sound recording problem, I am on shakier grounds - but a simple suggestion: did you try running **alsamixer -V** capture in a terminal ? This will show you the levels of the audio capture devices (use left and right arrows to move between capture devices, Tab to show playback/all devices). You may need to adjust the levels of the capture devices. More sources of audio problems and how to fix can be found at: **[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)**.

Hope these help.

---

### Post by pablo88 on 2007-06-26
Many thanks for those pointers. I'm on it and will post back here afterwards.

-- pablo

---

### Post by Maxtorm on 2007-06-26
Another, perhaps easier, solution to the fonts problem is to let Automatix do it for you ([www.getautomatix.com](www.getautomatix.com)).

---

### Post by pablo88 on 2007-06-26
Well thanks for the help and pointers here. By following them I've managed to get all the fonts installed and working (including the pesky Tahoma) and, more importantly, fixed the screen resolution issue - the laptop looks proper again.

However . . . 

The sound issue is a pain. I've followed the instructions as given here

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

as far a the last bit where it says -

START
Manually specify which model you are using. If your sound still doesn't work after installing the latest alsa, it is likely that alsa was unable to autodetect your model. To solve this:

Edit the file /etc/modprobe.d/alsa-base

gksudo gedit /etc/modprobe.d/alsa-base

Add the following line to the file, replacing '3stack' with your model (see below)

options snd-hda-intel model=3stack

 Reboot

Choosing your model

The full list of models is available in ALSA-Configuration.txt in the subdirectory /alsa-kernel/Documentation/ of the alsa-driver-1.0.14rc4 directory you created. Note that this list is ordered on modules and codec chips. To find your codec use this command from a terminal:

cat /proc/asound/card0/codec\#*
END

I cannot figure out what my model is. This is what I get when I enter cat /proc/asound/card0/codec\#*:

Codec: Motorola Si3054
Address: 0
Vendor Id: 0x10573055
Subsystem Id: 0x10573055
Revision Id: 0x100700
Codec: Realtek ALC880
Address: 1
Vendor Id: 0x10ec0880
Subsystem Id: 0x8800000
Revision Id: 0x100800


But this sure is a messy way to just get sound on a laptop.

Maybe I'm missing something obvious. Any pointers then I'd be glad to hear them.

-- Pablo

---

### Post by speaker219 on 2007-06-26
--

---

### Post by PaulFr on 2007-06-27
Your module is snd-hda-intel and your model name is one of the entries under ALC880 (search for ALC880 in ALSA-Configuration.txt) - these will depend on which laptop / desktop you have and on your jack configuration.

I hope you have downloaded the latest driver and utils (1.0.14) and library (1.0.14a) since there are a number of fixes for Realtek cards. Good luck.

---

### Post by pablo88 on 2007-06-27
Thanks PaulFr, but I'm still stuck with the models and modules stuff. The info I get for ALC880 is as follows:

**-START-**

Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

	  Model name	Description
	  ----------    -----------
	ALC880
	  3stack : 3-jack in back and a headphone out
	  3stack-digout :      3-jack in back, a HP out and a SPDIF out
	  5stack :                 5-jack in back, 2-jack in front
	  5stack-digout :      5-jack in back, 2-jack in front, a SPDIF out
	  6stack :                 6-jack in back, 2-jack in front
	  6stack-digout :      6-jack with a SPDIF out
	  w810 :                   3-jack
	  z71v :                   3-jack (HP shared SPDIF)
	  asus :                   3-jack (ASUS Mobo)
	  asus-w1v :           ASUS W1V
	  asus-dig :             ASUS with SPDIF out
	  asus-dig2 :           ASUS with SPDIF out (using GPIO2)
	  uniwill :                 3-jack
	  fujitsu :                Fujitsu Laptops (Pi1536)
	  F1734 :                2-jack
	  lg :                       LG laptop (m1 express dual)
	  lg-lw :                  LG LW20/LW25 laptop
	  tcl :                     TCL S700
	  clevo :                 Clevo laptops (m520G, m665n)
	  test :                  for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto :                 auto-config reading BIOS (default)

**-END-**

What do I put where it says:

Add the following line to the file, replacing '3stack' with your model (see below)

options snd-hda-intel model=3stack

I don't know what it means when it says "force the model name" next to model as shown above.

I have alsa-utils 1.0.14 and alsa-lib 1.0.14a installed under usr > src > alsa  , having followed the install instructions for this on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).

Many thanks for the help up to press. Hope I can get this working.

-- Pablo

---

### Post by PaulFr on 2007-06-28
Please check **[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)** - maybe you can find suggestions there for your brand or model of laptop. Even if you do not have an exact match for your model, you may want to try out the suggestions for the brand (like I did for my laptop).

---

### Post by Saghaulor on 2007-07-04
I know that this particular issue has been resolved, but I wanted to post my problem and solution since it is a related problem.

Problem: Screen Resolution 680x400 only.

Solution: 

After much research in other forums, I found the solution. The xorg.conf file needed the exact specs of my monitor in order to be able to utilize all of its resolution settings.

This required me to manually edit the xorg.conf file, but first I had to research my monitor specs.

I have a 19" Dell M990.

So I opened terminal, and keyed the following:

sudo nano /etc/X11/xorg.conf
Then under the monitor section I added my monitor settings, including:
ModelName, Horizsync, VertSync.

After that I keyed: 
ctrl-x, then I saved my changes. 

Then I opened the system menu, the preferences submenu, and opened the Screen Resolution preferences. 

Badda Bing, it now recognizes my other resolution modes.

I suggest you make a backup of the xorg.conf file in the event you biff it up.

---

