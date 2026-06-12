---
title: "Restarting USB modules"
date: 2009-06-28
forum: Hardware
---

### Post by itsjareds on 2009-06-28
Hi, I have a problem with my wireless adapter (Netgear WPN111) and it won't be disconnected by Ubuntu when I restart my computer. The device still blinks during a reboot, and Ubuntu sees the adapter as "busy" if it's blinking during boot up. The only fix to this is to manually unplug/replug my device to force it to stop working.

I was wondering, is there a way to virtually unplug all of my usb modules so that I can simulate an unplug/replug of a device? This would be a great help. I'll show you my USB devices and loaded modules:

```
jared@jared-desktop:~$ lsusb
Bus 001 Device 002: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 004: ID 04b3:3025 IBM Corp. 
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jared@jared-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   65668  2 
drm                    96296  3 i915
vboxnetflt             91016  0 
vboxdrv               117544  1 vboxnetflt
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
ppdev                  15620  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
psmouse                61972  0 
parport_pc             40100  0 
serio_raw              13316  0 
parport                42220  3 lp,ppdev,parport_pc
ndiswrapper           193308  0 
usbhid                 42336  0 
floppy                 64324  0 
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache
```

Thanks!

---

### Post by itsjareds on 2009-06-29
Bump.. #-o

---

### Post by itsjareds on 2009-06-29
Bump..

---

### Post by cenwesi on 2009-07-06
I too would like to know this... My external Mybook will not reconnect unless i unplug and replug it back in upon reboot.

---

### Post by deankovell on 2009-07-07
please help this guy. I have the same adapter. same issues. thank you.

---

