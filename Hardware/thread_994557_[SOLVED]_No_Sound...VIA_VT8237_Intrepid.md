---
title: "[SOLVED] No Sound...VIA VT8237 Intrepid"
date: 2008-11-26
forum: Hardware
---

### Post by wlm on 2008-11-26
New Intrepid install...AMD   NO sound whatsoever!
will@wlm:~$ sudo hwinfo --sound
15: PCI 11.5: 0401 Multimedia audio controller                  
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3059
  Unique ID: Ssy1.ZasLFjFiMAB
  SysFS ID: /devices/pci0000:00/0000:00:11.5
  SysFS BusID: 0000:00:11.5
  Hardware Class: sound
  Model: "VIA VT8233/A/8235/8237 AC97 Audio Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3059 "VT8233/A/8235/8237 AC97 Audio Controller"
  SubVendor: pci 0x16f3 "Jetway Information Co., Ltd."
  SubDevice: pci 0x4170 
  Revision: 0x60
  Driver: "VIA 82xx Audio"
  Driver Modules: "snd_via82xx"
  I/O Ports: 0xe500-0xe5ff (rw)
  IRQ: 22 (1601 events)
  Module Alias: "pci:v00001106d00003059sv000016F3sd00004170bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_via82xx is active
    Driver Activation Cmd: "modprobe snd_via82xx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
will@wlm:~$ lsmod |grep snd
snd_via82xx            32536  3 
gameport               19468  1 snd_via82xx
snd_ac97_codec        111652  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15360  1 snd_via82xx
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
will@wlm:~$

Following this thread solved it...[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by tayroni on 2009-04-03
What you did to solve?

---

