---
title: "Optical Output on Intel Corporation 82801G (ICH7 Family) High Definition Audio"
date: 2008-12-25
forum: Hardware
---

### Post by JCoster on 2008-12-25
Hi I have just installed Ubuntu 8.10 on a Sony Vaio VGC-RC204.

Everything's working except sound.

I am using the optical output on the onboard controller to output sound to my AV receiver.  

As I am dual-booting Vista I know that the output works using Sigmatel High Defintion Audio Codec drivers so the hardware is not at fault.

However, in Vista the optical light comes on whereas in Ubuntu it remains off.

On doing an lspci, I get the following:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
03:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 02)
04:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
07:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
07:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
07:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

And when I run 'aplay -l':
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And when I run 'cat /dev/sndstat':
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.18a emulation code)
Kernel: Linux jcoster-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xd7200000 irq 22

Audio devices:
0: HDA Generic (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: SigmaTel CXD9872RD/K

```

It may also be worth noting that I get the onboard beep upon error messages also, indicating that no soundcard is installed?

I have played around with the volume mixer settings but I think t's down to a driver problem.

I attempted to install the latest ALSA drivers but in all honesty I have no idea what I'm doing; I've had about a years experience with Ubuntu previously but have never really had problems with hardware until now!

I hope this is enough information for you guys to help me for now...

Cheers,
JC

---

### Post by JCoster on 2008-12-26
Just to add that I've just attempted to reinstall all ALSA related packages via Synaptic and this has not helped... 

I'll keep you posted but if anyone has any ideas let me know.
JC

---

### Post by papill0n on 2008-12-28
I have the RC202 and have the exact same problem as your having. Only way I can get any sound is by adding options snd-hda-intel model=vaio to the bottom of /etc/modprobe.d/alsa-base but its so low it is near unaudible :(

---

### Post by JCoster on 2009-08-31
Right, it's a long time since I first posted this but now I'm trying to get Jaunty working on the same RC-204 after originally giving up with the sound problem and reverting back to Vista, but I'm now devoted to eventually getting this working.

Anyway, the progress I have made is this.

After running 'grep Codec /proc/asound/card0/codec#*' I have determined that I am running the SigmaTel CXD9872RD/K, which after reading the appropriate documentation from ALSA, I have added the line 'options snd-hda-intel model=vaio' to /etc/modprobe.d/aslsa-base.conf.

This has given me a little bit of sound, as mentioned by papill0n above, but it is so quiet even if I pump it all the way up.  This also only gives me an output through the 3.5mm jack and not the optical socket, which is still unilluminated.

If any of you have any further thoughts please let me know, as after fully migrating from Vista>Ubuntu on my laptop I'd love to do the same for my desktop.

Thanks in advance,
JC

---

### Post by JCoster on 2009-09-01
I've just had a thought.
Is it possible that it is being detected as the wrong soundcard?  I can't get my mind around why the optical output won't light-up...

EDIT:
Just noticed, my 'aplay -l' is now:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And I'm not quite sure why.  There should definitely be a digital output there as well.

Under my volume control in Gnome, I have the following options:
- HDA Intel (ALSA Mixer)
- Sigmatel CXD9872RD/K (OSS Mixer) 
- Playback: HDA Intel - STAC92xx Analog (PulseAudio Mixer)
- (two capture options)

I assume the Sigmatel CXD9872RD/K to be the digital mixer, however I have checked and there are no options or switches to switch it to digital?

..just thought I'd give as much information as possible.

---

### Post by JCoster on 2009-09-02
Well I feel as if I've hit a brick wall here and I don't know if anyone is going to be able to help at all, but just in case, bump.

Would you recommend opening a bug on LaunchPad?

---

### Post by ahbart on 2009-09-10
My system:
lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
I'm not sure if that means that it is the same card/chip.

aplay -l
kaart 0: Intel [HDA Intel], apparaat 0: ALC882 Analog [ALC882 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 1: ALC882 Digital [ALC882 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

alsamixer:
Card: HDA Intel
Chip: Realtek ALC882

grep Codec /proc/asound/card0/codec#*
Codec: Realtek ALC882

I'm on karmic now. It's not the same situation, but I never had any problems with optical. (except for some pulseaudio problems now) Are you sure you did check/activate the digital output in alsa?
Normally I do that with gnome alsa mixer. In my case this is the IEC958.

---

### Post by lhrt on 2009-09-10
Do you think its a bug in the kernel?

Try update your kernel or apply the patch mentioned in the thread below
Please see this thread
[http://marc.info/?l=linux-kernel&m=124801208906965&w=2](http://marc.info/?l=linux-kernel&m=124801208906965&w=2)

---

### Post by coldsystem on 2009-11-05
I  had  the  same  issue   ( no sound with  Gnome28 ubunut 9.10),  but now  is  solved  bij following  this link 
 
[http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)
 
Enjoy

---

### Post by vfadool on 2010-02-04
jcoster, 

did you ever get this fixed? I have the EXACT same problem. ubuntu 9.10, vista on one partition, works fine. Ubuntu 9.10 on other partition, works great except for low sound. Sony vaio VBC RB57G, 82801G, codec: sigmatel CXD9872RD/K. I have tried EVERYTHING on all of these forums and nothing has helped.

---

