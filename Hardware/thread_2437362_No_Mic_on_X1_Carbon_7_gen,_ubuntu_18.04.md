---
title: "No Mic on X1 Carbon 7 gen, ubuntu 18.04"
date: 2020-02-22
forum: Hardware
---

### Post by senuketo on 2020-02-22
Hey,
  Spent last 2 days trying to make the mics work - no success.  

Last thing I tried was: [https://bbs.archlinux.org/viewtopic.php?id=249900](https://bbs.archlinux.org/viewtopic.php?id=249900)
After I do the first post + #9 comment modifications, arecord -l returns "no soundcards found"

arecord -l <without mods>
```

card 0: PCH [HDA Intel PCH], device 0: ALC285 Analog [ALC285 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Without modifications I was using my earbuds with mic - both working perfectly.
Another temporary decision could be a super small usb mic: [https://www.aliexpress.com/item/32973953613.html](https://www.aliexpress.com/item/32973953613.html)


Do you think I should persue trying the mic to work at all on:
```

Linux 5.3.0-40-generic #32~18.04.1-Ubuntu SMP x86_64 x86_64 x86_64 GNU/Linux
x1 carbon 7 gen - 10th Gen Intel® Core™ i7-10710U

```


This is my first Linux experience, probably won't be able to do the witchcraft you guys do here - custom kernels and stuff.


lspci
```

00:00.0 Host bridge: Intel Corporation Device 9b51
00:02.0 VGA compatible controller: Intel Corporation Device 9bca (rev 04)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Device 02f9
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:14.3 Network controller: Intel Corporation Device 02f0
00:15.0 Serial bus controller [0c80]: Intel Corporation Device 02e8
00:15.1 Serial bus controller [0c80]: Intel Corporation Device 02e9
00:16.0 Communication controller: Intel Corporation Device 02e0
00:1d.0 PCI bridge: Intel Corporation Device 02b0 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 02b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Audio device: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 02a4
00:1f.6 Ethernet controller: Intel Corporation Device 0d4f
03:00.0 Non-Volatile memory controller: Intel Corporation SSD Pro 7600p/760p/E 6100p Series (rev 03)
05:00.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
06:00.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
06:01.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
06:02.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
06:04.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
07:00.0 System peripheral: Intel Corporation JHL6540 Thunderbolt 3 NHI (C step) [Alpine Ridge 4C 2016] (rev 02)
2d:00.0 USB controller: Intel Corporation JHL6540 Thunderbolt 3 USB Controller (C step) [Alpine Ridge 4C 2016] (rev 02)

```


when I l look in dmesg result at the end I can find:
```

[   25.382012] sof-audio-pci 0000:00:1f.3: error: load fw failed ret: -110
[   25.382035] sof-audio-pci 0000:00:1f.3: error: status = 0x0000002c panic = 0x00000000
[   25.382042] sof-audio-pci 0000:00:1f.3: error: failed to reset DSP
[   25.382043] sof-audio-pci 0000:00:1f.3: error: failed to boot DSP firmware -110
[   25.382044] sof-audio-pci 0000:00:1f.3: error: sof_probe_work failed err: -110

```
dmesg|grep sof
```

[    1.918246] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.918248] software IO TLB: mapped [mem 0x41f74000-0x45f74000] (64MB)
[   22.113587] uvcvideo 1-8:1.2: Entity type for entity Microsoft Extended Controls Uni was not initialized!
[   22.258847] sof-audio-pci 0000:00:1f.3: warning: No matching ASoC machine driver found
[   22.258853] sof-audio-pci 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040380
[   22.258977] sof-audio-pci 0000:00:1f.3: use msi interrupt mode
[   22.263433] sof-audio-pci 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   22.267673] sof-audio-pci 0000:00:1f.3: hda codecs found, mask 5
[   22.267674] sof-audio-pci 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
[   22.313875] sof-audio-pci 0000:00:1f.3: unexpected ipc interrupt raised!
[   22.313877] sof-audio-pci 0000:00:1f.3: error: no reply expected, received 0x0
[   25.382012] sof-audio-pci 0000:00:1f.3: error: load fw failed ret: -110
[   25.382035] sof-audio-pci 0000:00:1f.3: error: status = 0x0000002c panic = 0x00000000
[   25.382042] sof-audio-pci 0000:00:1f.3: error: failed to reset DSP
[   25.382043] sof-audio-pci 0000:00:1f.3: error: failed to boot DSP firmware -110
[   25.382044] sof-audio-pci 0000:00:1f.3: error: sof_probe_work failed err: -110

```

Cheers

---

### Post by senuketo on 2020-02-22
Other things I tried was run the script from here: [https://gist.github.com/hamidzr/dd81e429dc86f4327ded7a2030e7d7d9](https://gist.github.com/hamidzr/dd81e429dc86f4327ded7a2030e7d7d9)
Went through the comments but I lack knowledge to understand it well enough.

Also went through: [https://forums.lenovo.com/t5/Ubuntu/Guide-X1-Carbon-7th-Generation-Ubuntu-compatability/td-p/4489823?page=1](https://forums.lenovo.com/t5/Ubuntu/Guide-X1-Carbon-7th-Generation-Ubuntu-compatability/td-p/4489823?page=1)

---

### Post by him610 on 2020-02-22
Not familiar with > X1 Carbon 7
This is the audio device from* lspci*, ```
00:1f.3 Audio device: Intel Corporation Device 02c8 
```
You have not said what version of Ubuntu you are on. Please show the results between the code tags....
```

inxi -Fxz

```
Normally the audio drivers get installed and just work.

---

### Post by senuketo on 2020-02-22
I've posted above: 
Linux 5.3.0-40-generic #32~18.04.1-Ubuntu

Here's command you requested.
inxi -Fxz
```
System:    Host: xxxxx Kernel: 5.3.0-40-generic x86_64 bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Audio:     Card Intel Device 02c8 driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k5.3.0-40-generic

```

Somewhere read that the audio card(02c8) and the 4 inbuilt microphones were different devices.

Also from what I read:
1. SOF driver had to be used
2. Custom kernel (some kernals disabled SOR because of SST conflicts)
3. blocking of legacy intel drivers
4. modifications to a couple of files

but not stable as it breaks after updates..

Somewhere else I read that putting the latest firmware fixed most of the stuff. 
But "fwupdmgr update" says I'm on the latest available.

A bit confused if I should pursue this or wait for some update.

---

### Post by him610 on 2020-02-22
So you have a laptop; with four(?) builtin microphones. 
They must be on a bus other than the PCI bus. Could you please show the output of *lsusb*?
If you had your working before then it is probably just improperly configured.
> Somewhere read that the audio card(02c8) and the 4 inbuilt microphones were different devices.
That is true, but all of the audio probably gets processed through the Intel Corporation Device 02c8 (I may be wrong on this).
Have you tried using *alsamixer* from a terminal?

---

### Post by senuketo on 2020-02-23
ye 4 mics - crazy...

 lsubs
```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 06cb:00bd Synaptics, Inc. 
Bus 001 Device 002: ID 04f2:b67c Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 8087:0aaa Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Haven't tried alsamixer. From threads I can see people use it to modify the strength of the sound after installing SOF, kernels and stuff.

Thanks for your time!

---

### Post by senuketo on 2020-02-23
Tried again this script because I messed up the default audio which worked: [https://gist.github.com/hamidzr/dd81e429dc86f4327ded7a2030e7d7d9](https://gist.github.com/hamidzr/dd81e429dc86f4327ded7a2030e7d7d9)
Tried **alsamixer** as described at the end and chose sof-skl_hda_card. But it's not working. When I choose default in alsamixer I have audio output.

dmesg | grep sof
```

[    1.913793] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.913795] software IO TLB: mapped [mem 0x41f74000-0x45f74000] (64MB)
[   14.091676] uvcvideo 1-8:1.2: Entity type for entity Microsoft Extended Controls Uni was not initialized!
[   14.300419] sof-audio-pci 0000:00:1f.3: warning: No matching ASoC machine driver found
[   14.300425] sof-audio-pci 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040380
[   14.300593] sof-audio-pci 0000:00:1f.3: use msi interrupt mode
[   14.308923] sof-audio-pci 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   14.315228] sof-audio-pci 0000:00:1f.3: hda codecs found, mask 5
[   14.315229] sof-audio-pci 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
[   14.373250] sof-audio-pci 0000:00:1f.3: unexpected ipc interrupt raised!
[   14.373252] sof-audio-pci 0000:00:1f.3: error: no reply expected, received 0x0
[   14.457661] sof-audio-pci 0000:00:1f.3: Firmware info: version 1:1:0-fcf6c
[   14.457663] sof-audio-pci 0000:00:1f.3: Firmware: ABI 3:11:0 Kernel ABI 3:8:0
[   14.457663] sof-audio-pci 0000:00:1f.3: warn: FW ABI is more recent than kernel
[   14.457918] sof-audio-pci 0000:00:1f.3: firmware boot complete
[   14.460546] sof-audio-pci 0000:00:1f.3: Topology: ABI 3:7:0 Kernel ABI 3:8:0
[   14.460550] sof-audio-pci 0000:00:1f.3: warning: widget type 7 name iDisp3 Tx not handled
[   14.461175] sof-audio-pci 0000:00:1f.3: warning: widget type 0 name codec0_in not handled
[   14.461177] sof-audio-pci 0000:00:1f.3: warning: widget type 7 name iDisp2 Tx not handled
[   14.461826] sof-audio-pci 0000:00:1f.3: warning: widget type 0 name codec1_in not handled
[   14.461828] sof-audio-pci 0000:00:1f.3: warning: widget type 7 name iDisp1 Tx not handled
[   14.462643] sof-audio-pci 0000:00:1f.3: warning: widget type 1 name codec0_out not handled
[   14.462645] sof-audio-pci 0000:00:1f.3: warning: widget type 7 name Analog CPU Playback not handled
[   14.463826] sof-audio-pci 0000:00:1f.3: warning: widget type 1 name codec1_out not handled
[   14.463827] sof-audio-pci 0000:00:1f.3: warning: widget type 7 name Digital CPU Playback not handled
[   14.463828] sof-audio-pci 0000:00:1f.3: warning: widget type 0 name codec2_in not handled
[   14.463829] sof-audio-pci 0000:00:1f.3: warning: widget type 7 name Alt Analog CPU Playback not handled
[   14.463830] sof-audio-pci 0000:00:1f.3: warning: widget type 1 name codec2_out not handled
[   14.463831] sof-audio-pci 0000:00:1f.3: warning: widget type 0 name Analog CPU Capture not handled
[   14.466323] sof-audio-pci 0000:00:1f.3: warning: widget type 1 name iDisp1_out not handled
[   14.466325] sof-audio-pci 0000:00:1f.3: warning: widget type 0 name Digital CPU Capture not handled
[   14.467492] sof-audio-pci 0000:00:1f.3: warning: widget type 1 name iDisp2_out not handled
[   14.467494] sof-audio-pci 0000:00:1f.3: warning: widget type 0 name Alt Analog CPU Capture not handled
[   14.468843] sof-audio-pci 0000:00:1f.3: warning: widget type 1 name iDisp3_out not handled
[   14.474251] sof-audio-pci 0000:00:1f.3: ASoC: Parent card not yet available, widget card binding deferred
[   14.555585] input: sof-skl_hda_card Mic as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input17
[   14.555628] input: sof-skl_hda_card Headphone as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input18
[   14.555668] input: sof-skl_hda_card HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input19
[   14.555743] input: sof-skl_hda_card HDMI/DP,pcm=4 as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input20
[   14.555884] input: sof-skl_hda_card HDMI/DP,pcm=5 as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input21
[   36.626290] sof-audio-pci 0000:00:1f.3: error: no reply expected, received 0x0
[   36.720496] sof-audio-pci 0000:00:1f.3: firmware boot complete

```

---

### Post by him610 on 2020-02-23
> When I choose default in alsamixer I have audio output. 
Do you have **input** through any of your microphones? The input level of the Front Mics and Rear Mics can be adjusted using the plus(+) and minus(-) keys.
This may have some bearing on your issue, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1848490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1848490")

---

### Post by senuketo on 2020-02-24
Internal microphones are all not recognized, only getting my earbud's mic to work when I plug them in the stereo jack.

Looks like the same issue. Will do some testing.

Thanks, him610!

---

### Post by aktiwers on 2020-03-18
Did you find a solution to this? 

I found that it all worked perfectly on 19.10 fresh install - but all breaks after upgrading alle packages. I suspect it to be the firmware-linux package that breaks things.

---

### Post by senuketo on 2020-04-03
Nice to hear that aktiwers!
Stopped chasing this as I'm a complete noob and already invested too much time into it.

I lost all my audio after an 18.04 upgrade. What I found out was reverting to the previous kernel fixed things.

I've set the grub config to load the last chosen kernel. 
[B]sudo nano /etc/default/grub
[/B]> GRUB_SAVEDEFAULT=true
GRUB_DEFAULT=saved

On reboot (Esc or Shift) to go into the Grub menu -> Advanced -> choose kernel
This way I can more easily switch between them to test.

---

### Post by senuketo on 2020-04-04
Just installed HWE kernel support and 5.3.0-46-generic kernel.
Now the mic is recognised: 
> Multichannel input - sof-skl_hda_card
But it's not working. Maybe I need some drivers.
At least when I plug headphones with a mic it's working.

Also sound got bad (maybe subwoofer not working).
WiFi, bluetooth got broken. Managed to fix the WiFi.

---

