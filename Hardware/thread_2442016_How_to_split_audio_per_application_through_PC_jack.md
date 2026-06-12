---
title: "How to split audio per application through PC jack ports of front and back panels"
date: 2020-04-28
forum: Hardware
---

### Post by xu-guillaume on 2020-04-28
Hello,

My use case is this: getting audio for say, Firefox & Audacity on headphones wired to the front panel's jack port, while my better half hears the sound of a VLC video playing on another screen, thanks to speakers wired to the back panel's jack port.

Right now I've got Pulseaudio running on Xubuntu 18.04. I've ran alsamixer but I can't see any way to separate the audio. I've installed and read some of JACK's documentation, but can't figure it out this way either.

Here's more info on my setup:
[http://alsa-project.org/db/?f=32c00fb1f45f7b6a3c39a7fd94649830fcc075ae](http://alsa-project.org/db/?f=32c00fb1f45f7b6a3c39a7fd94649830fcc075ae) 

Would love to have a distinction for the physical jack ports in Pulseaudio's volume control, the way it already presents audio per application.

Thanks in advance for any pointers!

(Please bear with me if this post doesn't meet these boards' standards, I'm new here. :)

---

### Post by CatKiller on 2020-04-28
> **xu-guillaume said:**
> ,My use case is this: getting audio for say, Firefox & Audacity on headphones wired to the front panel's jack port, while my better half hears the sound of a VLC video playing on another screen, thanks to speakers wired to the back panel's jack port.

That's standard PulseAudio functionality; it directs an audio stream from a source to a sink, mixing streams together if necessary. No need to faff about with ALSA or JACK.

The defaults are to move all streams to a new sink when it appears or is selected, since that's what most people generally want, but you can move them around however you like. In KDE it's just accessed through the volume control widget (along with having different classes of audio using different default sinks, and so on). It *used* to be the case that the volume widget in Gnome could do the same, but they took out that function in their quest to make Gnome difficult to customise. You can still install other things to manipulate PulseAudio streams, though, or do it from the command line if you get desperate. I have no idea what volume widgets Xubuntu comes with by default - probably the same as Gnome's - but the same things apply: you can just move audio streams about as you like.

---

### Post by Holger_Gehrke on 2020-04-28
I don't think this is possible in the way you describe because normal on-board audio circuitry has only one digital-analog converter which then sends the audio to the selected port.

My work-around for such situations is to either use an USB sound-dongle - those can be had for less than 10 Euro or to use the digital audio channel on the HDMI port my second display (which has a headphone jack for this purpose) is connected to. In either case you can send select on a per application basis to which soundcard to send the audio.

Holger

---

### Post by CatKiller on 2020-04-28
That's a good point: you'd need each output to be exposed as a different sink, which isn't necessarily the case with cheap onboard hardware.

---

### Post by xu-guillaume on 2020-04-29
Thank you both.
> **CatKiller said:**
>  I have no idea what volume widgets Xubuntu comes with by default
I believe it's Pavucontrol, but for now I can't see any separated sinks there. If I click the lock next to an app volume, I can change front and right volumes, but that applies both to the "rear panel" and "front panel" audio.

Do you know how I can determine whether the front and back panel are physically separated?

EDIT: running "pactl list sinks" gives me this:
```
Destination #0
    État : RUNNING
    Nom : alsa_output.pci-0000_00_1b.0.analog-stereo
    Description : Audio interne Stéréo analogique
    Pilote : module-alsa-card.c
    Spécification de l'échantillon : s16le 2ch 44100Hz
    Plan des canaux : front-left,front-right
    Module du propriétaire : 8
    Sourdine : non
    Volume : front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    Volume de base : 65536 / 100% / 0,00 dB
    Source du moniteur : alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    Latence : 7725 usec, configuré 8000 usec
    Marqueurs : HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Propriétés :
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC887-VD Analog"
        alsa.id = "ALC887-VD Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7d10000 irq 29"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "8 Series/C220 Series Chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Stéréo analogique"
        device.description = "Audio interne Stéréo analogique"
        alsa.mixer_name = "Realtek ALC887-VD"
        alsa.components = "HDA:10ec0887,1458a002,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports :
        analog-output-lineout: Sortie ligne (priority: 9900, available)
        analog-output-headphones: Casque audio (priority: 9000)
    Port actif : analog-output-headphones
    Formats :
        pcm
```
Does having both *analog-output-lineout* and *analog-output-headphones* mean I will indeed be able to separate the streams?

Otherwise, could the front panel microphone jack be turned into an output instead of an input? This way the two outputs would be wired separately. Could that be a first step?

---

### Post by xu-guillaume on 2020-04-29
In Pavucontrol, I can see only one output device, called "Built-in Audio Analog Stereo", but I can select one of two ports:
- "Line Out (plugged in)"
- "Headphones"
Can I assume it means there is one sink per port, and that I should be able to redirect them the way I want?

I noticed that the automatic detection of whether a cable is plugged into the jack ports only works for the Line Out.
Also, choosing "Line Out" cuts audio for the front panel jack. On the contrary, choosing "Headphones" doesn't cut audio for the back panel jack. I get audio on both sides.

Thank you!

---

### Post by CatKiller on 2020-04-30
> **xu-guillaume said:**
> Can I assume it means there is one sink per port, and that I should be able to redirect them the way I want?

Maybe? It's been a while since I played with this. 

*pacmd* and *pactl* are the command line tools for PulseAudio if the GUI tools won't easily do what you want.

---

### Post by Holger_Gehrke on 2020-04-30
If you do a 'pacmd list-sinks' you'll probably find (like I do on my system) that the output-part of the sound card is one sink and has a list of ports and **one** active port. So the ports are a property of the sink and only one can be active at a time.

Holger

---

### Post by xu-guillaume on 2020-04-30
pacmd list-sinks gives me this:
```
1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9039
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stéréo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 8
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC887-VD Analog"
        alsa.id = "ALC887-VD Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7d10000 irq 29"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "8 Series/C220 Series Chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Stéréo analogique"
        device.description = "Audio interne Stéréo analogique"
        alsa.mixer_name = "Realtek ALC887-VD"
        alsa.components = "HDA:10ec0887,1458a002,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-lineout: Sortie ligne (priority 9900, latency offset 0 usec, available: yes)
            properties:
                
        analog-output-headphones: Casque audio (priority 9000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-headphones>
```
Can I therefore assume that I can't "divide" the output playing with sinks, as only one is available, or because only one port can be active at the same time?

If this is true, could it be an alternative to turn the input from the front panel microphone jack into an output?

Thanks!

---

### Post by Holger_Gehrke on 2020-05-01
Looking up the data on the chips involved (HDA Intel PCH and Realtek's ALC887) I see that the combination of these should be capable of sound output up to 7.1 (8 channels; centre, front left, front right, left, right, back left, back right and base). Depending on how things are wired up to those chips it could be possible to set the card to some multichannel mode using the ALSA configuration and then set Pulse to use that mode and have some virtual sinks into which programs send their (stereo) sound to get mixed into a multichannel output (4.0 is probably what you want). Then you'd connect the speakers and headphones to the outputs for the front and back speakers.

You can use 'aplay -L' to get a list of soundcard(s) and modes and then use 'speaker-test' to see what channels are connected to which ports. See the manual pages for both programs for details. For configuration of Pulseaudio and virtual sinks you'll want to read the documentation for pulse at [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/) especially the part on modules.

Again, this depends on how things are connected on the soundboard or the main board if this is integrated audio. On my laptop the sound chips are capable of 7.1 sound but only front-left and front-right are connected so I can't use it.

Holger

---

### Post by xu-guillaume on 2020-05-05
Even though I don't have any HDMI-capable monitor at the moment, I  enabled the HDMI audio output in the Configuration panel of Pavucontrol. Then I had two  output devices instead of one, and saw how it should work. Pavucontrol then offers which output device to use per application, as described in your workaround:
> **Holger_Gehrke said:**
> My work-around for such situations is to either use an USB sound-dongle - those can be had for less than 10 Euro or to use the digital audio channel on the HDMI port my second display (which has a headphone jack for this purpose) is connected to. In either case you can send select on a per application basis to which soundcard to send the audio.
I tried messing with PulseAudio's commands and also installed HDAJackRetask, to try and reassign jack ports. But one way or the other, I wasn't able to create a new device output.

My GA-B85M-HD3 R4 motherboard's [manual]("https://download.gigabyte.com/FileList/Manual/mb_manual_ga-b85m-hd3-r4_e.pdf") states, about the front panel audio header:
> Audio signals will be present on both of the front and back panel audio connections simultaneously.
Some chassis provide a front panel audio module that has separated connectors on each wire instead of a single plug. For information about connecting the front panel audio module that has different wire assignments, please contact the chassis manufacturer.

My Zalman T5 chassis's laconic [manual]("https://www.zalman.com/cmm/fms/FileDown.do?atchFileId=FILE_000000000003808&fileSn=0") states:
> To connect power and I/O ports please refer to your motherboard manual.
But there is indeed just one plug instead of separated connectors.

I feel like it's taking me hours of reading over the internet to grasp sentences in your posts one after the other...
The motherboard manual also states, about the Realtek ALC887 codec:
> To configure 7.1-channel audio, you have to use an HD front panel audio module and enable the multi-channel audio feature through the audio driver.
I don't know how I could tell whether my front panel audio module is 'HD'. I figure I'll read your latest post again and dig into the ALSA configuration and speaker tests.

Do you think the manuals excerpts I quoted point to the limitations you mentioned?
> **Holger_Gehrke said:**
> Again, this depends on how things are connected on the soundboard or the main board if this is integrated audio.
Thank you.

---

