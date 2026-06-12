---
title: "Ubuntu 10.10 on ASUS A52F: Another Sound Problems Thread"
date: 2010-10-29
forum: Hardware
---

### Post by Anjruu on 2010-10-29
Hey all,

I know that there have been several billion of these threads, but I've looked at all I could find, and they don't seem to have helped me (unless I've gone deaf and didn't notice).

I recently installed Ubuntu 10.10 on my new ASUS A52F laptop, and the sound doesn't work, as in no sound from speakers, no sound from headphones. nada. I've checked, and I'm pretty sure that the sound is not muted (hitting the volume-up key on my keyboard shows a volume bar that is full and on).

When I load up the Sound configuration manager, there are no hardware devices listed. When I try to run "alsamixer" I get the error message:

```
cannot open mixer: No such file or directory
```

Running aplay -l gives

```
aplay: device_list:235: no soundcards found...

```

Running lspci -v gives a long list of PCI devices, one of which is 

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 13f3
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d5400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```


Purging and reinstalling alsa-base, alsa-utils, and linux-sound-base (and then restarting my laptop) also doesn't help.

I also don't have a /proc/asound directory. Some of the solutions that have worked for other people involved looking at a file found under that directory, so I'd thought I'd include that info.

Aaaaannnnddddd at this point I don't know what to do. My system finds my sound card, but is denied access to it? Is the problem something with drivers? Any help would be greatly appreciated.

EDIT:
I forgot to mention that I found a post on this forum that has a bunch of troubleshooting for this model laptop. It suggested I run the following sequence of commands: 
wget [http://www.linuxant.com/alsa-driver/....0_all.deb.zip](http://www.linuxant.com/alsa-driver/....0_all.deb.zip)
unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip
gdebi-gtk alsa-driver-linuxant_1.0.23.0_all.deb

Doing this gives me a build error for alsa-driver-..._all.deb. The error log is some 300 lines, but the last few define the error, which is:

```

/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/pcm_native.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [compile] Error 2

```

I can post any other lines, but I'm not sure what are good lines to show. I imagine all 300 lines probably isn't so useful...


Edit2:
Sort of fixed the problem! I didn't have the kernel sound modules installed, so booting up synaptic and installing linux-backports-modules-alsa-maverick-generic-pae fixed some of the problems. Of course, now the headphones don't work... but that's another problem. Anywho, I'm marking this guy as solved, I suppose. 

Thanks!
anjruu

---

