---
title: "Sound Config - Would like to FORCE only bluetooth headset to be playback"
date: 2016-01-02
forum: Hardware
---

### Post by Elishasmantle on 2016-01-02
Noob Alert! ( Just Sayin')

Hello,

Ok, I have ( After Hours of Reading ) my laptop internal audio working correctly on every reboot.

I also ( although not happy about it have I think every Alsa and Pulse Audio) app, widget, snap-in, driver, etc... known to man installed on my system. I prefer to have only bare minimum needed installed to get my bluetooth headset working.

The thing is, I do not use my internal audio on my laptop. I do not have external speakers and the sound from laptop is: 1) Poor , 2) Not loud enough.

**I Only want my Logitech H800 Headphones/Headset to sink on every reboot. **This is what I really want to accomplish is my linux to see the headphones as the Top level highest priority device and use it / sink it as the default sound playback device, especially when streaming any content.
I also want to make sure it works via streaming Youtube, Crackle, Netflix, etc... as that is what it is almost exclusively used for.

I do not have the skills to know what is actually controlling the bluetooth sink, what app, or where to get those config file info to post here on forum,
I have posted what I think you may need to help me:

1) PulseAudio system tray is the app I currently have showing and sinking my bluetooth headset. I was not able to figure out how to use any Alsa app to get my headphones to sink properly.
2) inxi -Axx
```
 inxi -Axx
Audio:     Card-1: Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:293e 
           Card-2: Logitech driver: USB Audio usb-ID: 002-004 chip-ID: 046d:0a29 
           Sound: Advanced Linux Sound Architecture ver: k4.2.0-21-generic

```
3) pacmd
```
>>> list-cards 
2 card(s) available.
    index: 0
        name: <alsa_card.pci-0000_00_1b.0>
        driver: <module-alsa-card.c>
        owner module: 5
        properties:
                alsa.card = "7"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xf6adc000 irq 31"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card7"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "293e"
                device.product.name = "82801I (ICH9 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "7"
                device.description = "Built-in Audio"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
                output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
                output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
                output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
                output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5460, available: unknown)
                output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: unknown)
                output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (priority 360, available: unknown)
                off: Off (priority 0, available: unknown)
        active profile: <output:analog-stereo>
        sinks:
                alsa_output.pci-0000_00_1b.0.analog-stereo/#0: Built-in Audio Analog Stereo
        sources:
                alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo
        ports:
                analog-input-microphone-internal: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-microphone-dock: Dock Microphone (priority 7800, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-microphone: Microphone (priority 8700, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-speakers"
                analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-headphones"
                hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "video-display"
    index: 1
        name: <alsa_card.usb-Logitech_Logitech_Wireless_Headset_000d44b82d40-00-Headset>
        driver: <module-alsa-card.c>
        owner module: 6
        properties:
                alsa.card = "0"
                alsa.card_name = "Logitech Wireless Headset"
                alsa.long_card_name = "Logitech Logitech Wireless Headset at usb-0000:00:1d.7-1.2, full speed"
                alsa.driver_name = "snd_usb_audio"
                device.bus_path = "pci-0000:00:1d.7-usb-0:1.2:1.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0/sound/card0"
                udev.id = "usb-Logitech_Logitech_Wireless_Headset_000d44b82d40-00-Headset"
                device.bus = "usb"
                device.vendor.id = "046d"
                device.vendor.name = "Logitech, Inc."
                device.product.id = "0a29"
                device.product.name = "Logitech Wireless Headset"
                device.serial = "Logitech_Logitech_Wireless_Headset_000d44b82d40"
                device.form_factor = "headset"
                device.string = "0"
                device.description = "Logitech Wireless Headset"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-headset-usb"
                device.intended_roles = "phone"
        profiles:
                input:analog-mono: Analog Mono Input (priority 1, available: unknown)
                output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
                output:analog-stereo+input:analog-mono: Analog Stereo Output + Analog Mono Input (priority 6001, available: unknown)
                off: Off (priority 0, available: unknown)
        active profile: <output:analog-stereo>
        sinks:
                alsa_output.usb-Logitech_Logitech_Wireless_Headset_000d44b82d40-00-Headset.analog-stereo/#1: Logitech Wireless Headset Analog Stereo
        sources:
                alsa_output.usb-Logitech_Logitech_Wireless_Headset_000d44b82d40-00-Headset.analog-stereo.monitor/#1: Monitor of Logitech Wireless Headset Analog Stereo
        ports:
                analog-input-microphone: Microphone (priority 8700, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
                        properties:

```

4) lsusb
```
lsusb
Bus 002 Device 003: ID 413c:8171 Dell Computer Corp. Gobi Wireless Modem (QDL mode)
Bus 002 Device 006: ID 0480:0212 Toshiba America Info. Systems, Inc. 
Bus 002 Device 005: ID 046d:c534 Logitech, Inc. 
Bus 002 Device 004: ID 046d:0a29 Logitech, Inc. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Sorry if I have used multiple utils for gathering the info. I'm just mimmicking info like a parrot from reading others peoples posts.

Thank You,

Elishasmantle

For a wee bit more clarification. The reason I want to do this is because on every reboot, whetheer it is a user error or a device / config issue it takes me 5-30 minutes after each reboot to try to get my headphones to work properly. and I am totally frustrated by this.

I am seeing some bug reports on firefox and "*CubebUtils*" issues with others having sound and volume issues as well and I do not know how much that may be present in my issue as well , if any.

I'm not opposed to using a different browser, I just want my streaming videos and sound to work more easily than it has been up to this point.

Thank You,

elishasmantle

Hello,

I love linux, but I will give linux an "F" on new user experience on configuring sound devices.

The issue is RESOLVED.

I hate the fact that after such frustration I am not entirely sure what the exact fix was.

I do know that I have put the below entries in end of my alsa-base.conf file

options snd-usb-audio index=2 vid=0x046d pid=0x0a29
options snd-hda-intel model=auto

I have my Logitech USB Headphones/set H800 automatically connecting on boot it they are on.
I do not use the actual bluetoothe unless really needed,
And the built-in audio is work on boot as well.

When streaming and I think using firefox there is an app/plugin called CubeBUtils. It seems it only show up when video is being streamed ( Just FYI) and if a user clicks on volume indicator near system tray ,right clicks on the cubebutils icon>move to> (and then selects the sound device: Internal audio, headphones, etc...) it directs the stream audio to that device.

All is working.
2 urls I gleaned info to fix issue are:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

Thank You,

Elishasmantle

---

