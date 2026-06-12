---
title: "HP dv7 - no sound"
date: 2009-07-19
forum: Hardware
---

### Post by PedalOn on 2009-07-19
I just installed Jaunty 9.04 on my brand new HP dv7, and I have no sound (works fine using Vista).

I've tried just about everything that I've come across, inluding the "options snd-hda-intel enable_msi=1", to no avail

some potentially helpful stuff:

Codec: IDT 92HD75B3X

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3624
        Flags: bus master, fast devsel, latency 0, IRQ 2295
        Memory at da100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

Any ideas would be much apprediated, thanks!

PS definitely a linux novice, please be gentle

---

### Post by antou on 2009-07-20
hi, 
i'm having the same problem on hp dv7 2070 ef, except my codec is IDT IT 7603.
apparently some people managed to get sound from a clean install (and then using the *option snd-hda-intel enable_msi=1* tip before doing anything else).
take also a  look at [this]("http://ubuntuforums.org/showthread.php?t=1073090&highlight=dv7+2070+ef"), i don't know if it works for dv7 series (i did not try yet) so good luck !

---

### Post by PedalOn on 2009-07-20
I hadn't seen that fix anywhere yet, but it was a winner!  I can only get sound from the built in speakers (not the headphone jack), but I'm assuming that is some mixer setting that I just need to dig up.

thanks alot!

---

### Post by b3n0 on 2010-04-24
Hey there,

I'm also having the same problem. I have the HP dv7-3105tx, it has a small sub on the bottom (don't get excited, it's only 4cm big) and two speakers on the top. I can only get sound through the sub, and not the main speakers on the top. The audio jacks don't work also.

Any ideas? I see this problem has been around for a while... any news of when the hardware drivers are due to be released?

Any help will be much appreciated. 

B3N0

---

### Post by lidex on 2010-04-24
See this thread:
[http://ubuntuforums.org/showthread.php?t=1461405]("http://ubuntuforums.org/showthread.php?t=1461405")
For karmic you can install the backports as referenced there. For jaunty, update alsa via the alsa-upgrade-script link in my sig. My Dv7 running jaunty required the upgrade and alsa-base options.

---

### Post by b3n0 on 2010-04-24
These lines of command fixes most of the problems!

```
cd
mkdir src
cd src
mkdir alsa
cd alsa
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar -xvpf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure
sudo make
sudo make install-modules
```

However, if you use the front audio jacks; the audio will still play through the laptop speakers. But it's a start...

---

