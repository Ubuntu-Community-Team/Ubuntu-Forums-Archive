---
title: "Optiplex 580 - no sound"
date: 2010-08-12
forum: Hardware
---

### Post by lykwydchykyn on 2010-08-12
Just got a new Optiplex 580, installed (k)ubuntu 64 bit 10.04 on it.

I can't get sound from any output.

It looks like it recognizes the hardware, kmix and alsamixer are both showing the card and channels.  

Here's what I've tried:
 - with or without pulseaudio installed
 - unmuting and turning up everything in alsamixer
 - installing backported alsa modules
 
Some output:

```

$ dmesg |grep hda
[   17.190885] hda_codec: ALC269: SKU not ready 0x411111f0
[   17.190966] hda_codec: ALC259: BIOS auto-probing.

```

```

$ lspci |grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```

```

$ sudo lshw -class multimedia
  *-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:f9ff0000-f9ff3fff

```

any advice?

---

### Post by lykwydchykyn on 2010-08-12
Sometimes I think I only post here because it virtually guarantees I'll solve the problem on my own within an hour or two.

I got it working now, just had to do three things:

 - follow these directions to update my alsa-modules: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

 - Reboot

 - Run alsamixer and turn up the newly-added PCM channel.

Phew!

---

