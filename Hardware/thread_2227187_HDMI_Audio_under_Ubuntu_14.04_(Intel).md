---
title: "HDMI Audio under Ubuntu 14.04 (Intel)"
date: 2014-05-31
forum: Hardware
---

### Post by codingman on 2014-05-31
I have a post on this topic in the Other OS/Distro section of these forums, but that is related to Debian 7.5, and thus I'm posting here in relevance to Ubuntu 14.04.

I currently have a laptop with an Intel HDMI port, and have connected it  to an AVR that has 7.1 channel capabilities (though currently set to  5.1). Earlier this week, it would work properly even with:

```
# pasuspender -- speaker-test -D hdmi -c 8 FL,FC,FR,RR,RRC,RLC,RL,LFE
```

Producing pink noise throughout the room. Now, however it does not work.  I've tried changing the output in the Gnome System Settings, but that  did not help. I tried:

```
# alsactl init
```

Which gives:

```
Found hardware: "HDA-Intel" "Intel IbexPeak HDMI"  "HDA:10ec0269,11790622,00100100 HDA:80862804,11790001,00100000" "0x1179"  "0x0001"
Hardware is initialized using a generic method

``` 

I have also tried unmuting everything in alsamixer, as well as messing around in pavucontrol, but to still no avail. Pavucontrol tells me that the HDMI port is unplugged, despite the fact that the cord is fully connected to the port.

```
# cat /proc/asound/modules
```

Gives me:

```
 0 snd_hda_intel
```

```
# pactl stat
```

Gives me:

```

Currently in use: 1 blocks containing 63.9 KiB bytes total.
Allocated during whole lifetime: 357304 blocks containing 511.3 MiB bytes total.
Sample cache size: 0 B
Server String: unix:/run/user/1000/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 20
Tile Size: 65472
User Name: ________
Host Name: ________
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.hdmi-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: 18c2:d46e

```

Notice the line of the "Default Sink".

```
# lsmod | grep snd
```

Returns:

```

snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd

```

```
# pactl list sinks
```

Gives:

```

Sink #4
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_1b.0.hdmi-stereo
    Description: Built-in Audio Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 5
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: alsa_output.pci-0000_00_1b.0.hdmi-stereo.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "HDA Intel MID"
        alsa.long_card_name = "HDA Intel MID at 0xd4620000 irq 45"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "3b56"
        device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
        device.form_factor = "internal"
        device.string = "hdmi:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Intel IbexPeak HDMI"
        alsa.components = "HDA:10ec0269,11790622,00100100 HDA:80862804,11790001,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, not available)
    Active Port: hdmi-output-0

```

Any suggestions are welcome!

---

### Post by waynesherman on 2014-10-07
I had a similar problem with HDMI audio showing as "not available" and "unplugged" even though HDMI video was plugged in, enabled, and working correctly.  In my case it only happens when I force video on the kernel command line ( video=HDMI-A-1:1280x720-32@60e ). (Intel Baytrail J1900 graphics)

When running "xrandr --verbose", it reported the HDMI "audio" as "auto".  I got it to work by forcing audio "on" with the following command:

```
xrandr --output HDMI1 --set "audio" on
```

I added the command to my startup scripts so it runs at login.

Take care,

ws

---

### Post by webforumthread on 2015-05-04
I have left channel audio only. 
I had all working just a few days ago...


sadly, command below did not work for me.

xrandr --output HDMI1 --set "audio" on

This is the problem I am experiencing:
[http://forums.linuxmint.com/viewtopic.php?f=47&t=172504](http://forums.linuxmint.com/viewtopic.php?f=47&t=172504)

---

