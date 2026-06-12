---
title: "Focusrite Scarlett 8i6"
date: 2013-12-18
forum: Hardware
---

### Post by cemercelik on 2013-12-18
Hi, 
After i see MuseScore supports choral writing, I thought move my whole system to ubuntu is best idea. I want to use ubuntu but my sound card doesnt supported. I cant hear or record anything.
[COLOR=#333333][FONT=Lucida Grande]Here some infos[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]aplay -l[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]card 1: USB [Scarlett 8i6 USB], device 0: USB Audio [USB Audio][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Subdevice #0: subdevice #0[/FONT][/COLOR]


[COLOR=#333333][FONT=Lucida Grande]cat /proc/asound/cards[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]0 [NVidia ]: HDA-Intel - HDA NVidia[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]HDA NVidia at 0xd3000000 irq 17[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]1 [USB ]: USB-Audio - Scarlett 8i6 USB[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Focusrite Scarlett 8i6 USB at usb-0000:00:1d.7-1, high speed[/FONT][/COLOR]


[COLOR=#333333][FONT=Lucida Grande]cat /proc/asound/devices[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]1: : sequencer[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]2: [ 1- 0]: digital audio playback[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]3: [ 1- 0]: digital audio capture[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]4: [ 1] : control[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]5: [ 1- 0]: raw midi[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]6: [ 0- 9]: digital audio playback[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]7: [ 0- 8]: digital audio playback[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]8: [ 0- 7]: digital audio playback[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]9: [ 0- 3]: digital audio playback[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]10: [ 0- 3]: hardware dependent[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]11: [ 0- 2]: hardware dependent[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]12: [ 0- 1]: hardware dependent[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]13: [ 0- 0]: hardware dependent[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]14: [ 0] : control[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]33: : timer[/FONT][/COLOR]


[COLOR=#333333][FONT=Lucida Grande]lsusb[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 002 Device 002: ID 1235:8002 Novation EMS [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 006 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 005 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 004 Device 002: ID 04e8:3268 Samsung Electronics Co., Ltd ML-1610 Mono Laser Printer[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Could you please help?[/FONT][/COLOR]

---

### Post by cemercelik on 2013-12-19
With the latest update of Jack, the problem solved. everything works just fine except skype :D who cares skype :D

---

