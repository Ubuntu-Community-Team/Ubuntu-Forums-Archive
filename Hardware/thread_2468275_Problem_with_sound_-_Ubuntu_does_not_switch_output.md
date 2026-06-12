---
title: "Problem with sound - Ubuntu does not switch output device"
date: 2021-10-23
forum: Hardware
---

### Post by chessplayer-dawid on 2021-10-23
Hi!

I'm struggling with Ubuntu on Acer Swift 3 314-42. Due to suspend problems I've upgraded my system to Ubuntu 21.10 (it did not help, I had to downgrade the BIOS :(). Right now I cannot force my Ubuntu to automatically change the audio output device to headphones when I connect them.

Everything works fine when I change the output device in pavucontrol by hand.

```

  *-multimedia:0             
       description: Audio device 
       product: Renoir Radeon High Definition Audio Controller 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0.1 
       bus info: pci@0000:03:00.1 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi bus_master cap_list 
       configuration: driver=snd_hda_intel latency=0 
       resources: irq:83 memory:c06c8000-c06cbfff 
  *-usb:1 
       description: Video 
       product: HD User Facing 
       vendor: SunplusIT Inc 
       physical id: 3 
       bus info: usb@1:3 
       version: 0.02 
       capabilities: usb-2.01 
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s 
  *-multimedia:1 
       description: Multimedia controller 
       product: Raven/Raven2/FireFlight/Renoir Audio Processor 
       vendor: Advanced Micro Devices, Inc. [AMD] 
       physical id: 0.5 
       bus info: pci@0000:03:00.5 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi bus_master cap_list 
       configuration: driver=snd_rn_pci_acp3x latency=0 
       resources: irq:71 memory:c0680000-c06bffff 
  *-multimedia:2 
       description: Audio device 
       product: Family 17h (Models 10h-1fh) HD Audio Controller 
       vendor: Advanced Micro Devices, Inc. [AMD] 
       physical id: 0.6 
       bus info: pci@0000:03:00.6 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi bus_master cap_list 
       configuration: driver=snd_hda_intel latency=0 
       resources: irq:84 memory:c06c0000-c06c7fff

```

---

### Post by TheFu on 2021-10-23
If you expect the sound device to change and can do it using pavucontrol, I'm confused.  Was something else expected?
There is a pulse addon module called ... let me look it up ... **module-switch-on-connect**
To enable that module, run 
```
$ pacmd load-module module-switch-on-connect
```
Does that do what you seek?  I've never tried it. I really hate when a sound subsystem changes things automatically.

---

