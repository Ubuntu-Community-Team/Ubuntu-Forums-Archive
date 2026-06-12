---
title: "display brighter than in Win7 when at minimal position"
date: 2011-08-07
forum: Hardware
---

### Post by dag0bert on 2011-08-07
Hello!

I have a HP pavilion g6 with ubuntu 10.04. When putting the displaybrightness at minimum position it appears somewhat brighter than in Win7, I think also brighter in maximum position. I would like to have it darker, especially when using the batterie. I also have only 3 steps of brightness regulation with ubuntu - somewhat more with Windows.  Is there a way to change this? 

bye,
dag0bert

---

### Post by dag0bert on 2011-08-07
I just noticed, that the screen gets brighter just before the gdm-logon screen appears? I am not able to reduce it after logon.

---

### Post by Toz on 2011-08-07
Exactly what model version of G6 do you have? Open a terminal window, type in the following command, and post back the results (in code blocks, if you don't mind):
```
sudo dmidecode -s system-product-name
```

What model video card do you have?
```
lspci | grep VGA
```

What modules are running?
```
lsmod
```

Anything interesting in your startup messages related to acpi?
```
dmesg | grep acpi
```

And finally, have you tried booting with the
[LIST]
[*]**acpi_backlight=vendor** _or_
[*]**acpi_osi=\"Linux\"** [/LIST]
kernel parameters? 
For instructions on how to test them, see: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

---

### Post by dag0bert on 2011-08-08
With **acpi_osi=\"Linux\" **its darker now, thanks! But still I have only 4 (did I say 3 before:rolleyes:) steps of brightness regulation with the 4th step beeing much bigger than the others before. Thats not the main problem, but do you have a solution for that too? 

```
root@patrice-laptop:/home/patrice# sudo dmidecode -s system-product-name
HP Pavilion g6 Notebook PC
root@patrice-laptop:/home/patrice# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6760
root@patrice-laptop:/home/patrice# lsmod
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26907  1 aes_i586
binfmt_misc             6586  1 
ppdev                   5245  0 
arc4                    1133  2 
snd_hda_codec_hdmi     23042  1 
ath9k                  97285  0 
mac80211              245343  1 ath9k
i915                  393076  3 
ath9k_common            2611  1 ath9k
snd_hda_codec_idt      57428  1 
snd_hda_intel          24332  2 
ath9k_hw              268126  2 ath9k,ath9k_common
snd_hda_codec          86476  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
drm_kms_helper         31609  1 i915
snd_hwdep               5181  1 snd_hda_codec
snd_pcm                75543  2 snd_hda_intel,snd_hda_codec
drm                   176972  4 i915,drm_kms_helper
ath                    13849  2 ath9k,ath9k_hw
max6650                 6304  0 
snd_seq_midi            4786  0 
intel_agp               9913  1 i915
cfg80211              144533  3 ath9k,mac80211,ath
joydev                  9423  0 
i2c_algo_bit            4910  1 i915
snd_rawmidi            17763  1 snd_seq_midi
lp                      7400  0 
intel_gtt              13287  3 i915,intel_agp
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
agpgart                32238  3 drm,intel_agp,intel_gtt
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
parport                32560  2 ppdev,lp
hp_wmi                  5525  0 
intel_ips              12115  0 
shpchp                 25357  0 
video                  12975  1 i915
output                  1851  1 video
snd                    49949  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               58581  0 
videodev               68263  1 uvcvideo
v4l1_compat            13912  2 uvcvideo,videodev
sparse_keymap           3431  1 hp_wmi
psmouse                58014  0 
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_hda_intel,snd_pcm
serio_raw               4062  0 
usbhid                 36648  0 
hid                    67454  1 usbhid
ahci                   19176  1 
r8169                  37619  0 
libahci                20139  1 ahci
mii                     4169  1 r8169
root@patrice-laptop:/home/patrice# dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    1.903734] ACPI: acpi_idle yielding to intel_idle
[   16.480657] acpi device:02: registered as cooling_device4
[   16.502704] acpi device:14: registered as cooling_device5
[   16.508095] acpi device:15: registered as cooling_device6
root@patrice-laptop:/home/patrice# 

```

---

### Post by dag0bert on 2011-08-08
Its a Pavilion G6-1009sg. With **acpi_backlight=vendor **I have no brightness regulation. Just compared: With **acpi_backlight=vendor **darker than before, but still much brighter than with Win7.

---

### Post by Toz on 2011-08-08
Looks like you have one of those optimus notebooks with the dual video cards. Have you disabled one (ATI) in the bios? 

Since the i915 module is loaded and running, I'm going to assume that its using the intel driver. Have a look at Kamal's intel-specific kernel - its configured to deal specifically with backlight problems on intel-based video cards. URL:[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")

---

### Post by dag0bert on 2011-08-08
These repositories seem to be empty?

[http://kernel.ubuntu.com/git?p=kamal/ubuntu-natty.git;a=commit;h=8b683a54da310d60d52bda2326106b0996c1fe0f](http://kernel.ubuntu.com/git?p=kamal/ubuntu-natty.git;a=commit;h=8b683a54da310d60d52bda2326106b0996c1fe0f)

[http://kernel.ubuntu.com/git?p=kamal/ubuntu-maverick.git;a=commit;h=ffc3acd96bfbd55847ad44c5b09b6011e2e6044e](http://kernel.ubuntu.com/git?p=kamal/ubuntu-maverick.git;a=commit;h=ffc3acd96bfbd55847ad44c5b09b6011e2e6044e)

---

### Post by Toz on 2011-08-08
You could try this one: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri") (though its no longer supported).

Two other things you could try (from a terminal window):

1. Using setpci:
```
sudo setpci -s 00:02.0 F4.B=DF
sudo setpci -s 00:02.0 F4.B=BF
sudo setpci -s 00:02.0 F4.B=9F
sudo setpci -s 00:02.0 F4.B=7F
```

2. Using xbacklight:
```
sudo apt-get install xbacklight
```
...then
```
xbacklight -set 90
xbacklight -set 80
xbacklight -set 70
...etc, in decrements of 10
```

Any difference?

---

### Post by dag0bert on 2011-08-08
Thanks, but neither 1. or 2. make any difference! :(  Kamals Kernels are for non-functional brightness fn-keys (mines do work), bur I will have a look at his repository. 2.6.32 is rather old.

---

