---
title: "dell venue 11 pro 7140 tablet keys not working correct"
date: 2020-09-06
forum: Hardware
---

### Post by sz3bbyla on 2020-09-06
I have an dell venue pro 11 7140 with slim keyboard
I use xfce4

this tablet have an windows button on it and volume up and down keys(keys hardware on tablet)
if I attach keyboard on tablet this keys are working
if tablet is detached from keyboard this keys not working anymore but there events from this keys

I installed evtest and I can capture button keys

No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:    Lid Switch
/dev/input/event1:    Power Button
/dev/input/event2:    AT Translated Set 2 keyboard
/dev/input/event3:    Video Bus
/dev/input/event4:    HDA Intel HDMI HDMI/DP,pcm=3
/dev/input/event5:    HDA Intel HDMI HDMI/DP,pcm=7
/dev/input/event6:    Intel Virtual Button driver
/dev/input/event7:    HDA Intel HDMI HDMI/DP,pcm=8
/dev/input/event8:    HDA Intel HDMI HDMI/DP,pcm=9
/dev/input/event9:    HDA Intel HDMI HDMI/DP,pcm=10
/dev/input/event10:    SYNA7500:00 06CB:780C
/dev/input/event11:    SYNA7500:00 06CB:780C
/dev/input/event12:    Dell WMI hotkeys
/dev/input/event13:    broadwell-rt286 Headset
/dev/input/event14:    Integrated_Webcam_FHD: Integrat
/dev/input/event15:    Integrated_Webcam_8M: Rear Inte
/dev/input/event16:    Synaptics T Pad V 01.31 Mouse
/dev/input/event17:    Synaptics T Pad V 01.31 Touchpad
/dev/input/event18:    Synaptics T Pad V 01.31
/dev/input/event19:    Synaptics T Pad V 01.31 Consumer Control
/dev/input/event20:    Synaptics T Pad V 01.31
/dev/input/event21:    Synaptics T Pad V 01.31 Wireless Radio Control
/dev/input/event22:    Logitech M185/M225

select event2
and 

Event: time 1599426042.177238, type 4 (EV_MSC), code 4 (MSC_SCAN), value b0
Event: time 1599426042.177238, type 1 (EV_KEY), code 115 (KEY_VOLUMEUP), value 1
Event: time 1599426042.177238, -------------- SYN_REPORT ------------
Event: time 1599426042.681225, type 4 (EV_MSC), code 4 (MSC_SCAN), value b0
Event: time 1599426042.681225, type 1 (EV_KEY), code 115 (KEY_VOLUMEUP), value 0
Event: time 1599426042.681225, -------------- SYN_REPORT ------------
Event: time 1599426044.806383, type 4 (EV_MSC), code 4 (MSC_SCAN), value ae
Event: time 1599426044.806383, type 1 (EV_KEY), code 114 (KEY_VOLUMEDOWN), value 1
Event: time 1599426044.806383, -------------- SYN_REPORT ------------
Event: time 1599426045.309224, type 4 (EV_MSC), code 4 (MSC_SCAN), value ae
Event: time 1599426045.309224, type 1 (EV_KEY), code 114 (KEY_VOLUMEDOWN), value 0
Event: time 1599426045.309224, -------------- SYN_REPORT ------------
Event: time 1599426058.628238, type 4 (EV_MSC), code 4 (MSC_SCAN), value db
Event: time 1599426058.628238, type 1 (EV_KEY), code 125 (KEY_LEFTMETA), value 1
Event: time 1599426058.628238, -------------- SYN_REPORT ------------
Event: time 1599426058.628475, type 4 (EV_MSC), code 4 (MSC_SCAN), value db
Event: time 1599426058.628475, type 1 (EV_KEY), code 125 (KEY_LEFTMETA), value 0
Event: time 1599426058.628475, -------------- SYN_REPORT ------------


there is any chance to use this keys (hardware on tablet) to working only in tablet mode without keyboard and mouse  ?
[B]
if I add this keys in keyboard shortcuts they working only if keyboard is attached on tablet !!!!


[/B]

---

