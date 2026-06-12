---
title: "Cirrus Logic Crystal CS4281 PCI Audio compile drivers"
date: 2009-02-04
forum: Hardware
---

### Post by volkswagner on 2009-02-04
Hi all,

I am trying to setup a headless jukebox with Jinzora, Ubuntu Server 8.04.2, LAMP, MPD all via an old Toshiba Laptop model 1735.  I want the sound directed to the laptop sound card.

```
lspci -v
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at fc010000 (32-bit, non-prefetchable) [size=4K]
        Memory at fc000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```
  
```
dan@Jukebox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS4281 [Cirrus Logic CS4281], device 0: CS4281 [CS4281]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dan@Jukebox:~$ aplay -L
default:CARD=CS4281
    Cirrus Logic CS4281, CS4281
    Default Audio Device
null
    Discard all samples (playback) or generate zero samples (capture)
```

Following the comprehensive sound guide I have landed at compile drivers.  I tried with "Using-Alsa-Source" with no joy.  Modprobe still resulted in no such module.

I am stuck on the compilation from source.  I have attached the output of

```
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=cs4281 --with-oss=yes

```

When checking dmesg I still see the same two items as prior to doing any changes.

```
[  917.458568] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  926.793601] gameport: CS4281 Gameport is pci0000:00:08.0/gameport0, speed 2294kHz
```

Does this mean that the card is not detected as an output device?

Any suggestions?

SideNote:  Why is the UbuntuForum Upload of text files limited to ~19Kb?  A 21KB files creates a 152KB file.

I guess I need to research pastebin?

---

### Post by volkswagner on 2009-02-05
Anyone have any idea?

I am not sure if it helps, but the sound works out of the box with Slax5 live CD.

---

