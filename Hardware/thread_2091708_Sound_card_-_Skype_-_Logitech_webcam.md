---
title: "Sound card - Skype - Logitech webcam"
date: 2012-12-05
forum: Hardware
---

### Post by dkolars on 2012-12-05
Once again, the shortcomings of Linux sound management have visited my household...  I use Skype 1x/week for an on-line lesson.  The first time I tried it, I found that Xubuntu had set the input volume to zero.  OK, so easy fix for that.  Have used the camera weekly for 3 weeks before tonight.  Tonight, the person on the other end could not hear me.  Volume is set right where I left it.  Ended up using laptop, not nearly as nice!!

So, my PulseAudio volume control says:
Input Devices: 
1) Built-in Audio Analog Stereo.  Port:  Front Microphone
2) QuickCam E 3500 Analog Mono.  Port:  Microphone

What's up with sound on this OS?  I have had trouble of some sort with every Ubuntu/Xubuntu version I've had, on 2 different computers!!    Grrr....

I've changed NOTHING other than to install the upgrades to the sytem, and all other sound functions work fine... 

Skype test call does not record sound.

Unplugged/replugged camera, re-booted, etc. etc.  to no avail.

Here's my lspci:
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper XT [AMD Radeon HD 6000 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
02:00.1 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller (rev a0)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:07.0 SCSI storage controller: Adaptec AIC-7850 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by BertN45 on 2012-12-05
Do you use PulseAudio Volume Control, if not install it from the Software Center. Use Skype test call and open the recording tab of PA Volume Control. Wait for the part where you have to talk and select the input source that has the signal and leave it there. From now on Skype should work.

If you have two audio sources you need PA Volume Control to select the right one. You could do the same for any other application, if needed and Pulse Audio will remember those settings.

---

### Post by dkolars on 2012-12-06
Yes, I'm using PA Volume Control.  Had never looked at the Recording tab... When I do a test call, the Recording tab shows "Monitor of Built-in Audio Analog Stereo.

So, I go to Input Devices tab, and it shows 
*Built-in Audio Analog Stereo
*QuickCam E 3500 Analog Mono

Under Built-in Audio Analog Stereo, I have 3 choices for Port:  Front Microphone, Rear Microphone, Line In.

Under QuickCam E 3500 Analog Mono, I have Port:  Microphone

None of those work.  Last week, it all worked.  

In the Configuration Tab, I have many choices for Built-in Audio:
[LIST]
[*]Analog Stereo Duplex
[*]Analog Stereo Output
[*]Digital Stereo(IED958) Output + Analog Stereo Input
[*]Digital Stereo(IED958) Output
[*]Analog Surround 5.1 Output + Analog Stereo Input
[*]Analog Surround 4.1 Output + Analog Stereo Input
[*]Analog Surround 5.1 Output
[*]Analog Surround 4.1 Output
[*]Analog Surround 7.1 Output + Analog Stereo Input
[*]Analog Surround 5.0 Output + Analog Stereo Input
[*]Analog Surround 4.0 Output + Analog Stereo Input
[*]Analog Surround 7.1 Output
[*]Analog Surround 5.0 Output
[*]Analog Surround 4.0 Output
[*]Analog Stereo Input
[*]Off
[/LIST]

So, I changed the setting to Analog Stereo Duplex, knowing full well that it will create echo, hiss, and totally unusable sound!  Cancelled test call when I heard that, set it back to Analog Stereo Output, and NOW it works... WTH???  I really do not like the way Linux deals with sound!!  But, I guess (?) it's fixed... for now?  Why do settings not stay "set"?  Thanks...

---

### Post by dkolars on 2012-12-08
:confused:

Well, it's NOT fixed...  I can see the video just fine, but the sound is not there... When I plug in the USB for the camera, the indicator bar moves from the background noise (humidifier) in the house, and when I talk it moves as it should... then it freezes, wherever it happens to be, after about 4 seconds.  

Thinking that the camera might be the problem (it's an old, cheap Logitech ball model), I got a new camera, Logitech 525...  great picture!!  But no sound.

Same behavior... plug it in, it responds to sounds for a few seconds, then freezes.  All settings in the pauvcontrol are where they should be... system sounds, sound files & movies on HDD play fine, YouTube plays fine, etc.

NO sound from webcam in Skype or VLC.  LOTS of noise on VLC, nothing on Skype.

So, any sound alternatives to PulseAudio?  I didn't like it so much on Ubuntu and now I'm not liking it so much on Xubuntu either!!

Soundcard is: AMD nee ATI Juniper HDMI Audio (Raedeon HD 5700 Series)

Should this continue, I'll be forced to install Virtual Box and load a copy of Windows so I can be able to use Skype!!

---

