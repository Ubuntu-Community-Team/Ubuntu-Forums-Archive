---
title: "No sound on Kubuntu 7.04"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by maddom on 2007-09-08
Hello,
i've got a very big problem with my  sound card and Kubuntu 7.04. Sound doesn't work. I've tried everything (installing new alsa driver-utils-lib; using alsaconf; putting options snd-hda-intel index=0 model=3stack into /etc/modprobe.d/options) but nothing to do. It's very strange because when i reboot my laptop and run aplay uxc.wav sound works for the first time only; I think it's something about kde because with gnome system it works without problems.
This is my lspci:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
03:00.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
03:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Thank you very much.

---

### Post by maddom on 2007-09-10
Is it possible that nobody can help me?
It seems that something is stopping my audio because the sound card seems correctly configured and the speakers are working, but no sound.
However this is the link for my ALSA information: [http://pastebin.ca/690286](http://pastebin.ca/690286)

---

### Post by fdetweiler on 2007-09-11
i am a newbie, it took me a couple of days to find the volume button on the top of the ubuntu screen just to the left of the date, mine said master:muted

---

### Post by maddom on 2007-09-11
Mine said master is unmuted.

---

### Post by dabl on 2007-09-11
I have that same Intel 82801 controller chip.  Make sure you have the alsa packages installed:

alsa-base
alsa-utils
alsamixergui
alsa-oss

Then, in your Kmixer, make sure on the "Switches" tab that you have a non-muted device.  Mine says "IEC958" -- I have no idea how that relates to my STAC92xx chip or so-called Intel HDA integrated sound system.

Obviously, the "Output" channels need to be un-muted as well.  :)

---

