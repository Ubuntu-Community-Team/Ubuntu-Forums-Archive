---
title: "Sound only works when screen goes to sleep"
date: 2016-09-25
forum: Hardware
---

### Post by Herber on 2016-09-25
Hope someone can help. I have searched the forums and found other references to problems with sound and ALC889A but have been unable to fix the problem. The analog stereo out works fine in windows (dual boot machine) but in 16.4 and 16.10 beta (64bit) no sound but occasional pop and crackle. The mute is not on, the output selection is correct, volume at 100.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0 

I recently learned that when the screen goes to sleep and turns off then sound will come out of the analog out and work fine.  However as soon as I move the mouse or touch the keyboard to wake the screen the sound turns off again.  I am suspicious that it may have to do with the video card which is attached to my screen via a DVI to HDMI converter and then enters the screen as an HDMI input.  The video card does not have an HDMI out, it has two DVI and 1 s-video out.  My guess is that the video card is somehow taking the audio when the screen is awake but the motherboard gets the audio when the screen goes to sleep.  maybe I need another driver for my video card?  System specs. below:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
[COLOR="#FF0000"]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
[COLOR="#FF0000"]01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 8800 GT] (rev a2)[/COLOR]
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)

Maybe I need a different driver?

---

### Post by Herber on 2016-09-26
The driver for my GeForce 8800 was the problem and a switch to the available proprietary driver solved the issue.

---

