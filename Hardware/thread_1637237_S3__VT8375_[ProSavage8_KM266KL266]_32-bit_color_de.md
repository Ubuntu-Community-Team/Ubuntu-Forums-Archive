---
title: "S3  VT8375 [ProSavage8 KM266/KL266] 32-bit color depth"
date: 2010-12-04
forum: Hardware
---

### Post by eesh on 2010-12-04
Hi,

I need to set my display dolor depth to 32 bit, but Ubuntu 10.10 doesn't seem to recognize my display adapter. It's an old PC with an on-board S3 VT8375 [ProSavage8 KM266/KL266].

I have the xserver-xorg-video-savage and xserver-xorg-video-openchrome packages installed. It's a basic Ubuntu 10.10 installation, fully updated, with a few irrelevant additions (VLC, SSH, winbind and samba).

Here are a few command outputs that may help troubleshoot:
```
root@pc:~# lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=4
       resources: memory:ed000000-ed07ffff memory:e0000000-e7ffffff memory:ec000000-ec00ffff
root@pc:~# lsmod
Module                  Size  Used by
savage                 29276  3
drm                   168054  4 savage
binfmt_misc             6599  1
snd_via82xx            20140  3
gameport                9327  1 snd_via82xx
snd_ac97_codec         99227  1 snd_via82xx
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_via82xx,snd_ac97_codec
snd_page_alloc          7120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5661  1 snd_via82xx
snd_seq_midi            4588  0
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i2c_viapro              5777  0
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
via_ircc               21469  0
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
irda                  178906  1 via_ircc
snd                    49006  13 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               1351  1 irda
via_agp                 5322  1
soundcore                880  1 snd
agpgart                32011  2 drm,via_agp
shpchp                 29886  0
ppdev                   5556  0
parport_pc             26058  1
psmouse                59033  0
serio_raw               4022  0
lp                      7342  0
parport                31492  3 ppdev,parport_pc,lp
joydev                  8735  0
usbhid                 36882  0
via_rhine              19038  0
floppy                 54311  0
pata_via                7332  2
mii                     4425  1 via_rhine
hid                    67742  1 usbhid
```

Thank you! :)

---

