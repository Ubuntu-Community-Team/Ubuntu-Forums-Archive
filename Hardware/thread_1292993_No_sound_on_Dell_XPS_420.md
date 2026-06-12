---
title: "No sound on Dell XPS 420"
date: 2009-10-16
forum: Hardware
---

### Post by schwim on 2009-10-16
Hi there everyone,

I've got a brand new install of ubu on a Dell XPS 420. Dell lists my audio device as:

> Card, Multi-Meldia, Audio       Creative Sound Blaster X-FI   Windows Vista Os I'm dualbooting with Vista in which the sound works.  When I boot into Ubu, no ports generate sound during testing and only a single channel is available to me under volume control and the output device is listed as Null Output (PulseAudio Mixer), which leads me to believe that it's not recognizing my audio output device. The device dropdown does not offer another choice.

Could someone help me figure out how to get it working?

thanks,
json

---

### Post by schwim on 2009-10-16
I followed the instructions found [here]("http://here") and determined that the soundcard is detected:

> 
04:04.0 Audio device: Creative Labs SB X-Fi
        Subsystem: Creative Labs Device 6002
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f7ef8000 (32-bit, non-prefetchable) [size=16K]
        Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]
        Memory at f0000000 (64-bit, non-prefetchable) [size=64M]
        I/O ports at cce0 [size=32]
        Capabilities: <access denied>
which leads me to believe that I am missing the driver for it. Soundblaster has some linux drivers for the x-fi series cards [here]("http://opensource.creative.com/soundcard.html") but I'm not sure how to go about installing this driver.

My alsa computer profile is [here]("http://www.alsa-project.org/db/?f=cebbd6efe0405b5a08ef4893d5dc8bc1111e00ba").

I've gotten to the point to where I am browsing the Git repository and to be completely honest, this is too much for me.  I'm hoping that I'm overthinking this and I just need to install the previously linked driver.

Help please?

---

### Post by schwim on 2009-10-16
I found [this thread](http://ubuntuforums.org/showthread.php?t=870001) stating that the card would work in 9.10 with the kernel 2.6.31.X and am wondering if it's feasible to upgrade 9.04 to 9.10 to get working audio?

I'm not willing to install audio drivers every time there is a kernel update as I'm a strong believer that the hardware should work without repetitive intervention.

thanks,
json

---

### Post by schwim on 2009-10-16
Issue was resolved by upgrading to 9.10.

Thanks for all the help.
json

---

