---
title: "USB speakers problem on 11.10"
date: 2012-02-08
forum: Hardware
---

### Post by dargaud on 2012-02-08
Hello all,
I have an external Asus uBoom USB speaker which used to work great on Ubuntu, but since the 11.10 upgrade, there's something wrong.
- when I first connect it, it works fine
- if I disconnect and reconnect, the sound only comes from the front speakers

So let's check:
- I see it in dmesg:
```
usb 3-1: new full speed USB device number 3 using ohci_hcd
input: ASUSTek uBoom Speaker as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.3/input/input9
generic-usb 0003:0B05:178D.0002: input,hidraw0: USB HID v1.00 Device [ASUSTek uBoom Speaker] on usb-0000:00:13.1-1/input3
```

- It's selected as the Kmix master channel
- I see the uBoom volume controller in the Mixer "Playback device"
- In [system settings][Multimedia][Phonon][Device preference], it is MISSING, there's only PulseAudio Sound Server. It was there the 1st time it connected.
- in [Audio Hardware Setup], [Sound Card] is set to "uBoom Speaker" and the speaker testing buttons do work fine.
- [Backend] only has GStreamer

I used to regularly receive warning messages "The audio hardware ...mumble, mumble... has disconnected, do you want to forget about it?" To which I would always reply "No". And I recently selected the "Don't ask again" button. But I think that's not when the problem started but after the 11.10 upgrade.

Any idea ? Thanks.

PS: If I run start-pulseaudio-kde and then select uBoom in [Phonon][Audio Hardware setup][Sound Card], Apply. Then and only then do I get uBoom in the [Device Preference][Audio Playback]. Not very convenient.

---

