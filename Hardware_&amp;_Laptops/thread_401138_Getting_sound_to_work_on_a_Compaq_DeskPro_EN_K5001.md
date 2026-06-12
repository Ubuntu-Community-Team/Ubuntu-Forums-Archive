---
title: "Getting sound to work on a Compaq DeskPro EN K500/10"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by KX36 on 2007-04-04
I have been given this old machine and told to get it working. I removed win98 from it and put ubuntu on. However, I can't work out how to get the sound on it working.

As it is absolutely archaic, there is very little support for it. I don't know what sound it uses, it's on the motherboard not on one of its ISA or PCI slots (it's NLX.. i did say archaic after all ;-) ).

When I try and set the sound devices, I get an "error writing to resource".

When I open it up theres a chip that has "ESS AudioDrive" written on it along with some version numbers etc if thats useful.

Does anyone know what I can do to get audio working?

Thanks

---

### Post by KX36 on 2007-04-06
Ok, it turns out its an ES1869F, so it comes under the es18xx alsa drivers.

I tried using [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) to no avail.
```
$ aplay -l
aplay: device_list:222: no soundcards found...
$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:0f.0 Ethernet controller: Belkin Wireless PCI Card - F5D6001 (rev 20)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
$ sudo modprobe snd-es18xx
...it says it cant find blah/isa/blah/snd-es18xx.ko or something like that here...
$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
...all packages up to date...
$ sudo dpkg-reconfigure alsa-source
...I chose yes, no, es18xx only...
$ sudo module-assistant a-i   alsa-source
...everything seems to go fine...
$ sudo modprobe snd-es18xx
SEGMENTATION FAULT
.. lots of mail messages from the kernel about the segfault..
```

somebody help me :(

---

### Post by Brucevdk on 2007-04-19
I too have a Compaq Deskpro EN SFF with the exact same audio chipset and I managed to get it to work, this post really did help me out. I followed your instructions and then modified it a little bit near the end due to [another very helpful thread I found]("http://www.linuxquestions.org/questions/showthread.php?threadid=234814").

When I used just *modprobe snd-es18xx* it too segfaulted for me and using dmesg it displayed a descriptive error (I'll look the precise message up again later). Anyways in the linked thread they use modprobe and pass IRQ and DMA settings as arguments, which doesn't segfault.

The BIOS mentions the following IRQ/DMA settings:
```

Audio device: 220-22FF, 388-38B, 330-331, IRQ 10, DMA 1, DMA 0

```

So the complete procedure is:
```

$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
$ sudo module-assistant a-i   alsa-source
$ sudo modprobe sb esstype=18xx io=0x220 irq=10 dma=1

```

I added *sb esstype=18xx io=0x220 irq=10 dma=1* to */etc/modules* so the module is loaded on boot.

Sound works but I had to set Amarok to use OSS as output plugin because it wouldn't play using ALSA, which indicates that something is still not working properly. But hey, sound works so it's good enough for now.

Hope this helps you out as much as it did for me.

UPDATE: I searched around a little bit more and turns out there is another thread right here on Ubuntu Forums where this is discussed and [the same solution is brought up]("http://ubuntuforums.org/showthread.php?p=525490#post525490"). The Ubuntu Community Documentation wiki is mentioned there too and has [an article explaining all of this]("https://help.ubuntu.com/community/forum/hardware/OldSoundCard"). However, none of those mention the segfaulting :)

---

