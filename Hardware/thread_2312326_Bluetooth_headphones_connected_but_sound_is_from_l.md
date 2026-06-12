---
title: "Bluetooth headphones connected but sound is from laptop"
date: 2016-02-03
forum: Hardware
---

### Post by dibo on 2016-02-03
Hi,

I searched this forum for similar problems but nothing helps.
So. When I pair headphones then everything seems to be fine (in headphones I hear "pair" sound). Kubuntu notify me with message that sound device with higher priority was detected and switched sound to this device but sound is still from laptop:
[ATTACH=CONFIG]267100[/ATTACH]
So I tried to force use this device as output device:
[ATTACH=CONFIG]267101[/ATTACH]
"Save" works but when back to this window then there is default device:
[ATTACH=CONFIG]267102[/ATTACH]
... which in fact is not my default device. This HDMI device is my external display. Even if I change to analog device and save, then it back to HDMI too. Maybe there is a problem? Do I need root permission or something?

Note that I also have USB speakers. When I connect then sound automatically switch to them and music is playing from USB spearks.

**Kubuntu 14.04 64 bit**

Regards

> pactl load-module module-bluetooth-discover this return "Failure: Module initialisation failed"

```
pacmd list-cards
```
> >>> 3 card(s) available.    index: 0
        name: <alsa_card.pci-0000_00_03.0>
        driver: <module-alsa-card.c>
        owner module: 5
        properties:
                alsa.card = "0"
                alsa.card_name = "HDA Intel HDMI"
                alsa.long_card_name = "HDA Intel HDMI at 0xf7e34000 irq 64"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:03.0"
                sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "0a0c"
                device.form_factor = "internal"
                device.string = "0"
                device.description = "Wbudowany d&#378;wi&#281;k"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                output:hdmi-stereo: Wyj&#347;cie Digital Stereo (HDMI) (priority 5400, available: unknown)
                output:hdmi-surround: Wyj&#347;cie Digital Surround 5.1 (HDMI) (priority 300, available: unknown)
                output:hdmi-stereo-extra1: Wyj&#347;cie Digital Stereo (HDMI) (priority 5200, available: unknown)
                output:hdmi-surround-extra1: Wyj&#347;cie Digital Surround 5.1 (HDMI) (priority 100, available: unknown)
                output:hdmi-stereo-extra2: Wyj&#347;cie Digital Stereo (HDMI) (priority 5200, available: unknown)
                output:hdmi-surround-extra2: Wyj&#347;cie Digital Surround 5.1 (HDMI) (priority 100, available: unknown)
                off: Wy&#322;&#261;czone (priority 0, available: unknown)
        active profile: <output:hdmi-stereo>
        sinks:
                alsa_output.pci-0000_00_03.0.hdmi-stereo/#0: Wbudowany d&#378;wi&#281;k Digital Stereo (HDMI)
        sources:
                alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor/#0: Monitor of Wbudowany d&#378;wi&#281;k Digital Stereo (HDMI)
        ports:
                hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "video-display"
                hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "video-display"
                hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "video-display"
    index: 1
        name: <alsa_card.pci-0000_00_1b.0>
        driver: <module-alsa-card.c>
        owner module: 6
        properties:
                alsa.card = "1"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xf7e30000 irq 65"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "9c20"
                device.product.name = "Lynx Point-LP HD Audio Controller"
                device.form_factor = "internal"
                device.string = "1"
                device.description = "Wbudowany d&#378;wi&#281;k"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                input:analog-stereo: Wej&#347;cie Analogowe stereo (priority 60, available: unknown)
                output:analog-stereo: Wyj&#347;cie Analogowe stereo (priority 6000, available: unknown)
                output:analog-stereo+input:analog-stereo: Analogowy dupleks stereo (priority 6060, available: unknown)
                off: Wy&#322;&#261;czone (priority 0, available: unknown)
        active profile: <output:analog-stereo+input:analog-stereo>
        sinks:
                alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Wbudowany d&#378;wi&#281;k Analogowe stereo
        sources:
                alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#1: Monitor of Wbudowany d&#378;wi&#281;k Analogowe stereo
                alsa_input.pci-0000_00_1b.0.analog-stereo/#2: Wbudowany d&#378;wi&#281;k Analogowe stereo
        ports:
                analog-input-microphone-internal: Wewn&#281;trzny mikrofon (priority 8900, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-microphone-dock: Mikrofon stacji dokuj&#261;cej (priority 7800, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-microphone-headset: Mikrofon na s&#322;uchawkach (priority 8700, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-output-speaker: G&#322;o&#347;niki (priority 10000, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-speakers"
                analog-output-headphones: S&#322;uchawki (priority 9000, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-headphones"
    index: 5
        name: <bluez_card.BD_6A_C9_39_09_96>
        driver: <module-bluetooth-device.c>
        owner module: 30
        properties:
                device.description = "Mini503"
                device.string = "BD:6A:C9:39:09:96"
                device.api = "bluez"
                device.class = "sound"
                device.bus = "bluetooth"
                device.form_factor = "headset"
                bluez.path = "/org/bluez/1123/hci0/dev_BD_6A_C9_39_09_96"
                bluez.class = "0x240404"
                bluez.name = "Mini503"
                device.icon_name = "audio-headset-bluetooth"
                device.intended_roles = "phone"
        profiles:
                hsp: Duplex telefoniczny (HSP/HFP) (priority 20, available: unknown)
                a2dp: Odtwarzanie o wysokiej dok&#322;adno&#347;ci (A2DP) (priority 10, available: no)
                off: Wy&#322;&#261;czone (priority 0, available: yes)
        active profile: <hsp>
        sinks:
                bluez_sink.BD_6A_C9_39_09_96/#5: Mini503
        sources:
                bluez_sink.BD_6A_C9_39_09_96.monitor/#9: Monitor of Mini503
                bluez_source.BD_6A_C9_39_09_96/#10: Mini503
        ports:
                headset-output: S&#322;uchawki z mikrofonem (priority 0, latency offset 0 usec, available: unknown)
                        properties:


                headset-input: S&#322;uchawki z mikrofonem (priority 0, latency offset 0 usec, available: unknown)
                        properties:


Tried run phonon as root:
```
sudo kcmshell4 kcm_phonon
```
... and force output device. Same result, when reopen phonon HDMI device is as default. Weird...

---

### Post by Vladlenin5000 on 2016-02-03
Your BT headset admits two different profiles. I noticed in one of your screenshots you had selected the "hands free" profile (mono+mic) which usually works for specific apps only. Have you tried the other one, A2DP (Stereo HD Audio, no mic)?

---

### Post by dibo on 2016-02-03
Ok. I have progress. Seems like these headphones are not detected as "Music" category. Had to move order to the top on other categories (games, etc.) and now when they pair, laptop sound is off but I don't hear anything on headphones :( . Changed main channel to this volume and it is max. When connecting to smartphone then everything is fine. They have Bluetooth v4.0 + EDR (which is weird because on e-shop where I bought them description is V2.1 + EDR). My laptop is Dell Latitude E7440. Does it mean that Kubuntu may don't have support for v4 or there is problem between my laptop bluetooth and v4.0?

---

### Post by dibo on 2016-02-03
Tried change to A2DP but still everything is muted

---

### Post by dibo on 2016-02-03
Solved! But actually I don't know what I did. Just played with phonon configuration. I also moved this device on top in "Sound recording" section (comunication, recording, control). But this didn't help (on each change I'm reconnecting headphones to be sure). Finally I noticed that main node "Sound recording" also contain this device but on bottom while all subnodes have it on top. So I moved it to top too. Instead of check this with reconnect only, I also removed device from "known" devices and added it again to bluetooth authorized devices. First try: still nothing hear, spontaneously changed profile to A2DP(tried this many times before) and immediately headphones started playing even without saving changes :popcorn:. So finally don't know what did the trick, removing and adding headphones in authorized bluetooth list? Is it possible that it cached audio configuration for headphones and I reset it?

**So if someone have bluetooth headphones(with microphone) dedicated especially for smartphones, here is what I did:**
[LIST]
[*]Move your device to the top in ALL categories (music, games, communication, etc)
[*]Move it also for "recording" section
[*]Don't forget check main sections, they may contain your device on bottom while categories have it on top
[*]Do not test changes with reconnecting only(turn off - turn on). REMOVE DEVICE FROM BLUETOOTH AUTHORIZED DEVICES ON EACH CHANGE!
[/LIST]

Thanks @[COLOR=#000000]Vladlenin5000 for pointing to A2DP. My headphones are working only on this profile.

Regards[/COLOR]

---

### Post by Vladlenin5000 on 2016-02-03
You're welcome and I'm glad you solved so quickly :p
I had nothing else to offer. Kubuntu/KDE has its own software ecosystem and my personal experience with it is close to zero.
You can also use the thread tool to mark it as solved.

---

