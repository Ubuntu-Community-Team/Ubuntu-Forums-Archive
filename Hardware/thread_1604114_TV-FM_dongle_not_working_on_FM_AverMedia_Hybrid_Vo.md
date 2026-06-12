---
title: "TV-FM dongle not working on FM: AverMedia Hybrid Volar Max"
date: 2010-10-23
forum: Hardware
---

### Post by vandamme on 2010-10-23
Got this dongle working with Kaffeine and the driver from AverMedia (model H826). But I've been trying to get the FM tuner working...Gnomeradio claims there's no /dev/radio so I figure that the driver from AverMedia doesn't work on FM. The driver on their website is 0.1 beta (sheesh) which is dated Dec 2009 and claims to work through Ubuntu 9.10. I'm running 10.10. The instructions say mplayer should work but there's no FM radio support in mplayer. Ideas?

:-({|=

---

### Post by maatthc on 2010-10-26
It's not working for me either. I have a USB AverTvHybrid Volar HX and I'm using the AVERMEDIA-Linux-x86-H826D-0.10-beta driver. The TV works just fine and apparently the radio device is active:

[ 9050.217816] AVerMedia USB Wrapper for H826D version 0.28 loaded
[ 9050.250338] h826d: module license 'AVerMedia TECHNOLOGIES, Inc.' taints kernel.
[ 9050.250347] Disabling lock debugging due to kernel taint
[ 9050.410783] AVerTV Volar HX AX MAX version 0.10 loaded
[ 9050.736914] A827 registered V4L2 device video1[video]
[ 9050.737034] A827 registered V4L2 device vbi0[vbi]
**[COLOR=SeaGreen][ 9050.737271] A827 registered V4L2 device radio0[radio][/COLOR]**
[ 9050.737691] A827 registered ALSA sound card 1
[ 9050.737707] DVB: registering new adapter (A827[0] DVB-T)
[ 9050.737712] A827[0] DVB-T registered DVB adapter 0
[ 9050.738196] DVB: registering adapter 0 frontend 0 (A827[0] DVB-T)...
[ 9050.738318] usbcore: registered new interface driver AVerTV Volar HX AX MAX
[ 9721.911444] usb 1-5: USB disconnect, address 8
[ 9726.120083] usb 1-5: new high speed USB device using ehci_hcd and address 9
[ 9727.160670] A827 registered V4L2 device video1[video]
[ 9727.160751] A827 registered V4L2 device vbi0[vbi]
**[COLOR=SeaGreen][ 9727.160822] A827 registered V4L2 device radio0[radio][/COLOR]**
[ 9727.161111] A827 registered ALSA sound card 1
[ 9727.161127] DVB: registering new adapter (A827[0] DVB-T)
[ 9727.161132] A827[0] DVB-T registered DVB adapter 0
[ 9727.161646] DVB: registering adapter 0 frontend 0 (A827[0] DVB-T)...

---

### Post by vandamme on 2010-10-26
Quoth AVerMedia USA: 

"It should be able to get FM  stations if you are using a program with the ability to pick up FM stations. You  will need to check with the Linux open source community to see if there are  applications available that supports FM for the AVerTV Hybrid Volar  Max."

Have a nice day, and don't let the door hit you. 

maatthc, sounds like your radio is active (eek! radio active??) but the tuner app is not seeing it... what front-end proggie are you trying to use? Distro?

---

### Post by maatthc on 2010-10-27
Hi vandamme,
I'm sorry for my poor English skills..
But I'm using Gnomeradio as well as you..Ubuntu 10.10

Regards,
Alexandre

---

### Post by vandamme on 2010-10-27
OK, Gnomeradio isn't loading the mixer ("could not open /dev/mixer") and there's no way to select the mixer as a source under gnomeradio preferences. I'm using Kaffeine for TV, and that works...EXCEPT not when I have gnomeradio running (TV works again when I shut off gnomeradio). So that probably means that gnomeradio is seeing and controlling the radio?? I changed the radio device in the preferences from the default /dev/radio to /dev/radio0. 

I haven't found any other app that runs a radio. 

Alexandre, your english is better than most people in New York.

---

