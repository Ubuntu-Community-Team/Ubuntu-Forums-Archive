---
title: "Pulseaudio doesn't detect external speakers"
date: 2019-06-30
forum: Hardware
---

### Post by cisarro on 2019-06-30
Hi there!

I just installed Lubuntu 19.04 (64 bits). I am using a HDMI monitor and external speakers (plugged in the back jack). Pulseaudio detects the HDMI DisplayPort and sound is working fine. I would like to use the external speakers but Pulseaudio doesn't detect them.

```

pacmd list-cards

1 card(s) available.
    index: 0
        name: <alsa_card.pci-0000_07_00.1>
        driver: <module-alsa-card.c>
        owner module: 7
        properties:
                alsa.card = "0"
                alsa.card_name = "HD-Audio Generic"
                alsa.long_card_name = "HD-Audio Generic at 0xfcc88000 irq 55"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:07:00.1"
                sysfs.path = "/devices/pci0000:00/0000:00:08.1/0000:07:00.1/sound/card0"
                device.bus = "pci"
                device.vendor.id = "1002"
                device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
                device.product.id = "15de"
                device.string = "0"
                device.description = "HD-Audio Generic"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                output:hdmi-stereo: Digital Stereo (HDMI) Salida (priority 5900, available: unknown)
                off: Apagado (priority 0, available: unknown)
        active profile: <output:hdmi-stereo>
        sinks:
                alsa_output.pci-0000_07_00.1.hdmi-stereo/#0: HD-Audio Generic Digital Stereo (HDMI)
        sources:
                alsa_output.pci-0000_07_00.1.hdmi-stereo.monitor/#0: Monitor of HD-Audio Generic Digital Stereo (HDMI)
        ports:
                hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "video-display"
                                device.product.name = "LED MONITOR"

```

What should I check or updgrade to get speakers working?

---

### Post by tea for one on 2019-06-30
> **cisarro said:**
>  I am using a HDMI monitor and external speakers (plugged in the back jack). Pulseaudio detects the HDMI DisplayPort and sound is working fine. I would like to use the external speakers but Pulseaudio doesn't detect them. 

Are your speakers plugged in to the PC or the monitor?

---

### Post by cisarro on 2019-06-30
> **tea for one said:**
> Are your speakers plugged in to the PC or the monitor?

I tried both: monitor and PC (back and front).

---

### Post by tea for one on 2019-06-30
> **cisarro said:**
> I tried both: monitor and PC (back and front).

You tried audio jacks in both your PC and your monitor yet pulse audio does not recognise either source?

However, in your original post, you mentioned that ** Pulseaudio detects the HDMI DisplayPort and sound is working fine.** - Can you kindly add some clarification?

---

### Post by cisarro on 2019-06-30
> **tea for one said:**
> You tried audio jacks in both your PC and your monitor yet pulse audio does not recognise either source?

However, in your original post, you mentioned that ** Pulseaudio detects the HDMI DisplayPort and sound is working fine.** - Can you kindly add some clarification?

Oh, I am sorry... When I plug the monitor through an HDMI cable, Pulseaudio recognise it as audio output device so I got sound from the monitor with built-in speakers. But if I plug my external speakers or headphones (with 3.5mm jack) in to the PC, Pulseaudio doesn't detect them.

---

### Post by tea for one on 2019-06-30
As your monitor speakers function OK via HDMI then it must be something to do with the connection or performance of the speakers?

Please plug your speakers into the **audio out** jack of your monitor.

Then navigate to Pulseaudio > Configuration and select **Digital Stereo (HDMI) Output + Analogue Stereo Input**

I am assuming that your speakers are receiving sufficient power?

---

### Post by cisarro on 2019-06-30
> **tea for one said:**
> As your monitor speakers function OK via HDMI then it must be something to do with the connection or performance of the speakers?

Please plug your speakers into the **audio out** jack of your monitor.

Then navigate to Pulseaudio > Configuration and select **Digital Stereo (HDMI) Output + Analogue Stereo Input**

I am assuming that your speakers are receiving sufficient power?

The quality of the sound from the monitor speakers is not good (I would tag it "decent" but not really "good"), that's why I want to use external speakers.

I also plugged the speakers into the audio jack of the monitor, but Pulseaudio only shows **Digital Stereo (HDMI) Output** to select.

And yes... the speakers are receiving enough power.

I guess there is something about the drivers because Pulseaudio doesn't detect the microphone neither does Alsamixer.

---

### Post by CatKiller on 2019-06-30
> **cisarro said:**
> I also plugged the speakers into the audio jack of the monitor, but Pulseaudio only shows **Digital Stereo (HDMI) Output** to select.

That's entirely to be expected. The * monitor* is the audio device. Whether the analogue signal goes to the monitor's speakers, or your external speakers, or a rubber band on a margarine tub, after that is entirely down to the monitor.

It's exactly the same when you're using your computer's own audio device. *That* is what you'd select with PulseAudio. Your speakers don't factor into it at all. Some ports that are intended for headphones have a feature called "presence detect" to identify when something's plugged into them to help with routing, but ports intended for speakers generally don't.

So far, you're looking at some combination of

[list][*]Your speakers being turned off, turned down, or not working at all.

[*]Your monitor's external analogue output being turned off, turned down or muted.

[*]Your computer's audio device being turned off, turned down, muted, not plugged in, not configured, or not selected.[/list] 

Those are the things that you need to identify.

---

