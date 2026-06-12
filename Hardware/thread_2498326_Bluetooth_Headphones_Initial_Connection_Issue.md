---
title: "Bluetooth Headphones Initial Connection Issue"
date: 2024-06-09
forum: Hardware
---

### Post by chrisrid on 2024-06-09
Hi guys! This is my first post on the forums, so let me know if this is in the right place / if there's anything else needed. I'd be grateful if anyone could help me with a potential bug when connecting my Bluetooth headphones.

_What's Happening_
When I startup Ubuntu, I log in and then switch on my Bluetooth headphones which say "Connecting" (vocally in the earpiece) but they never actually connect - they don't play any audio, and don't confirm the connection by saying "connected" (vocally as they normally would). When I check the Bluetooth settings menu, it shows my headphones and Ubuntu says they are actually connected and working fine despite the connection process being incomplete. It almost seems like an incomplete initial handshake or something?

_The Workaround_
A workaround that I have been using so far, is when I'm at the stage above, I would manually disconnect the headphones from the Bluetooth settings menu and wait a second before manually connecting them again - which works perfectly. The headphones then say "connected" (vocally as you'd expect) and they can then play audio. But I have to do this on each boot.

_Side-Note - Bluetooth Battery Status_
I'm not sure if this is related at all, but I noticed that Ubuntu doesn't show the Bluetooth battery status, but can do using the terminal, but not consistently. I checked to see if this information was available to the OS by using "pactl list sinks | grep bluetooth.battery" in a terminal, and sure enough it returned a percentage. For convenience I just put this command into a bash file in my home directory, so I could quickly run "bash bat.sh" to check it every so often - but I've come to find that the battery information is not always there and sometimes it doesn't return anything. On the occasions when it doesn't return anything, I run "pactl list sinks" and sure enough I can see all of the other info of the headphones, other than the battery status? Not a big deal, but wondered if it had anything to do with the overall communication between Ubuntu and the Headphones?

_Headphones Information_
The headphones I bought are Rebocico 6S Wireless Headphones, which seem to be pretty popular (Amazon link below):
[https://www.amazon.co.uk/gp/product/B0BG89CJDB/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B0BG89CJDB/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)

_System Information_
OS Name: Ubuntu 22.04.4 LTS
OS Type: 64-bit
GNOME Version: 42.9
Windowing System: X11

_Sinks Info (pactl list sinks)_
Sinks 1 & 2 are actually a HyperX Quadcast S microphone, so I have suspended both of them
Sink #3
    State: RUNNING
    Name: bluez_sink.F8_4C_92_25_91_D2.a2dp_sink
    Description: 6S
    Driver: module-bluez5-device.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 25
    Mute: no
    Volume: front-left: 27866 /  43% / -22.28 dB,   front-right: 27866 /  43% / -22.28 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor Source: bluez_sink.F8_4C_92_25_91_D2.a2dp_sink.monitor
    Latency: 48038 usec, configured 39512 usec
    Flags: HARDWARE HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        bluetooth.protocol = "a2dp_sink"
        bluetooth.codec = "sbc"
        device.description = "6S"
        device.string = "F8:4C:92:25:91:D2"
        device.api = "bluez"
        device.class = "sound"
        device.bus = "bluetooth"
        device.form_factor = "headset"
        bluez.path = "/org/bluez/hci0/dev_F8_4C_92_25_91_D2"
        bluez.class = "0x240404"
        bluez.alias = "6S"
        device.icon_name = "audio-headset-bluetooth"
        device.intended_roles = "phone"
    Ports:
        headset-output: Headset (type: Headset, priority: 0, available)
    Active Port: headset-output
    Formats:
        pcm

---

