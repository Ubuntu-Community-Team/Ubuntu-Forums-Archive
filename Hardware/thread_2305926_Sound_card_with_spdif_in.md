---
title: "Sound card with spdif in"
date: 2015-12-10
forum: Hardware
---

### Post by two4two on 2015-12-10
My motherboard has on-board sound, but no digital in.  My turntable has a PCM output via cable (not optical).  When I record my records into my computer I'd like to use this digital output rather than the analog output in order to avoid the 60hz ground loop hum, so I'm looking for a sound card, internal via pci or pci-e, or external via USB or firewire, so I can use this PCM output of my turntable as input to my computer.  Does ANYONE know of such a sound card that works in Ubuntu?

---

### Post by two4two on 2015-12-11
BTW, I was reading the docs for the art usb phono plus project series.  It does have SPDIF both optical and co-ax.  And the docs say it doesn't really need a driver because it should work as a USB device.  I don't know if this is an obsolete device and therefore wouldn't be able to find it anywhere, but if I can find it I'd give it a try.  Anyone have tired it yet?

---

### Post by two4two on 2016-02-23
No takers?  Still looking for sound card with S/PDIF input that is supported in Ubuntu.

---

### Post by yoshii on 2016-02-23
I used to have the M-Audio Delta Audiophile 2496 and it has digital coaxial input and output as well as analog inputs and MIDI in/out.  
It's a 24-bit (maximum) 96 kHz PCI (standard) sound card.  From what I remember, it IS supported by Linux but the driver for it is named after the internal hardware and not "M-Audio Delta Audiophile 2496".  I believe instead, you use the "ICE1712" and/or "Envy24" driver support in Linux.  And then you have to be sure and manually turn on all your inputs and outputs and raise the faders with an ALSA utility or similar.  The "ICE1712" or "Envy24" is literally printed on one of the integrated chips of the Audiophile 2496.  I don't have mine any longer so I can't tell you which it is; I forget.  

The M-Audio website also mentions some other resources, but I wasn't able to get those to work.  But I was able to get the above system to work.  At the time I was using Puppy Linux.

---

### Post by yoshii on 2016-02-23
Also, there is this list:  [http://wiki.linuxaudio.org/wiki/hardware_matrix](http://wiki.linuxaudio.org/wiki/hardware_matrix)

---

