---
title: "Toshiba Qosmio g40 - NO SOUND through SPEAKERS. Headphones work."
date: 2009-05-08
forum: Hardware
---

### Post by inkashes on 2009-05-08
I'm running Ubuntu 9.04 on my Qosmio g40 Laptop.
Everything works well, except there's no sound from the laptop's speakers (4 speakers + a subwoofer).
The headphones DO work. 

The laptop has Realtek alc262 as one of the sound options. 
On Windows Vista, the sound driver is: Realtek Audio Driver v.6-
On Windows 7, the sound is automatically detected.
   
I get this error in sound preferences when I try to switch "sound playback":
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I've posted the same problem on the Mandriva Forums, without success:
[http://forum.mandriva.com/viewtopic.php?p=671239#671239](http://forum.mandriva.com/viewtopic.php?p=671239#671239)

A recap of some of the things I've tried:
-Disabling Pulseaudio
-Reinstalling ALSA
-Realtek's Linux Driver
-Different Sound Preference settings
-Creating a new user
-Logging in as root
-Adjusting Pulseaudio Preferences
-Alsaconf
-Alsamixer / unmuting
-AUMIX, KMIX, etc.
-and a bunch of other tutorial stuff I found online. 


Any help would be appreciated.
Thanks!

----------------------
In case this helps:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
08:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
08:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by ruien on 2009-12-08
Do this: Put this in rc.local found in /etc 
------------
/sbin/modprobe -r snd-hda-intel && modprobe snd-hda-intel model=auto

exit 0
------------
model can be fujitsu or auto for the G40 . I use auto

---

