---
title: "No sound on Toshiba Satellite A105 on Ubuntu 11.04"
date: 2011-05-26
forum: Hardware
---

### Post by mistu on 2011-05-26
Hi,
I recently installed Ubuntu 11.04 (64 bit) for my friend on a Toshiba Satellite A105. Everything is working fine except that there is no sound. The sound icon shows that the volume is all the way up, whether I turn it down or not. Ubuntu does not detect a soundcard. The sound worked with Windows Vista before the Ubuntu installation. 
I've tried several things, but nothing thus far has worked so I decided to post here. Any suggestions?

It seems that many people have this problem but no one has the solution...

---

### Post by mörgæs on 2011-05-27
How does it work in a live boot of 10.10?

---

### Post by jeritadamsonfourman on 2011-07-20
No sound on Toshiba Satellite L645, Ubuntu 11.04 Natty Narwhal.

No sound for a while running 10.10 Maverick Meercat, then had sound miraculously one day all of a sudden, only to lose sound upon subsequent reboot.

Will keep digging round net, just dropping in to say, "ME, TOO!"

Help?

---

### Post by mörgæs on 2011-07-20
Hi, welcome to the fora.

I guess posting here will help you more:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by James Keating on 2011-10-28
I had the same problem, and for me the solution was surprisingly simple. The correct module was present, but turned off. I am using Lubuntu, which uses Alsa. 

From the command line, I ran alsamixer, pressed F6 to select sound card, and chose HDA Intel. Now sound works, even after rebooting.

Alsamixergui doesn't seem to have the ability to select the sound card. If you are using a different sound system, there should be some equivalent ability to turn on the master.

Before I found the solution, I went through the steps in the sticky Sound Problems Solutions Guide. Following that, I ran 

aplay -l

which told me I had
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]

then

lspci -v

which told me
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Toshiba Satellite A100-796 audio (Realtek ALC861)
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

so I know I need to enable module snd-hda-intel

I tried
sudo modprobe snd-[tab]

but the card wasn't listed.

However, the search
slocate hda-intel

turned up 
/lib/modules/3.0.0-12-generic/kernel/sound/pci/hda/snd-hda-intel.ko

so I knew the module was present.

I thought I would have to add the line snd-hda-intel to /etc/modules and reboot. Perhaps that would work, but for me it's not neccessary.

---

