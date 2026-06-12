---
title: "help with DAC"
date: 2018-05-16
forum: Hardware
---

### Post by ramonet on 2018-05-16
Hi to all!
First, forgiveme me poor english.
I've bought a DAC and I connect to port USB. Ubuntu recognize and it sounds. But the volume control affects to signal, so I think that PC not send the bit flow directly to USB. Perhaps Pulseaudio is doing some conversion before send the bit flow.

aplay -L response with

hw:CARD=DAC,DEV=0
    Liberty DAC, USB Audio
    Direct hardware device without any conversions
plughw:CARD=DAC,DEV=0
    Liberty DAC, USB Audio
    Hardware device with all software conversions

so I'm interested in send bits without any conversion.

And the audio parameters Secction presents two devices

Digital Output (S/PDIF) - Liberty DAC  (select)
Analogic Output - Liberty DAC

But Volume control always is active.

Any idea?

Thanks to all!

---

