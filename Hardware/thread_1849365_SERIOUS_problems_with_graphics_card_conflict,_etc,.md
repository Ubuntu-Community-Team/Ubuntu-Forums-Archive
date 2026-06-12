---
title: "SERIOUS problems with graphics card conflict, etc, etc."
date: 2011-09-24
forum: Hardware
---

### Post by MG&amp;TL on 2011-09-24
Just to say-I'm using mint at the moment, but it's very similiar to Ubuntu, and this problem happens in Ubuntu too. In fact the only reason I'm on Mint is this problem.

I have a Dell Dimension 2400, with an integrated Intel graphics card and 512 MB RAM.

Some years, ago, while I was still using Windows, I upgraded to an NVidia GeForce FX 5200. Brilliant card, very few problems.

So I went linux after that. I noticed that I could install the driver for the card (via *jockey*) and it would work fine-in most cases. 3d acceleration-the works.

My problem came when I noticed the "visual effects" tab under "appearance". I tried to enable any level of it, it would fail, with 'visual effects could not be enabled". Problems begin. I realise I am using Metacity, so I run:

```
compiz --replace
```

which starts, then hangs, citing a blacklisted card-the geForce card is not on the list, but the Intel one is. But it's using the geForce card-I know it is, I can run "glxgears" at 1000fps+ now, whereas before enabling the driver, it dawdles around 100.

Is there something I can enable/disable in BIOS/the driver software to only use the geForce? It's not a MAJOR issue, it just nags. Dodging the blacklist on the card works fine, but does not do anything.

Incidentally, Unity will not work either.

Any ideas? 

Thanks, people. I'm only using mint because i thought it would make a difference.

---

### Post by LinuxFan999 on 2011-09-24
Which versions of Ubuntu and Mint are you using?

---

### Post by MG&amp;TL on 2011-09-24
Any; and all. Linux mint, 9, 10 and 11. Ubuntu 10.04, 10.10, 11.04, 11.10beta1, Xubuntu 11.04, Lubuntu 11.04.

---

### Post by MG&amp;TL on 2011-09-25
Here's the linux 'PCI devices' section of the linux mint system information app:

---

### Post by wildmanne39 on 2011-09-25
Hi, I doubt if the computer is very old that unity will run on it. Run this command to see what it says.

Also with 512 ram if it did you would not be able to use effects like the cube it would use up all your ram and cpu.
```
/usr/lib/nux/unity_support_test -p
```
```
lspci | grep VGA
```
```
dmesg | egrep 'nvi|VGA'
```
```
lsmod
```
Also these commands and it will give error messages if any and tell us what drivers are being used.
Thank you

---

### Post by MG&amp;TL on 2011-09-25
VGA:

```
01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Dmesg:
```
[    0.000000] Console: colour VGA+ 80x25
[   13.137589] nvidia: module license 'NVIDIA' taints kernel.
[   13.770723] nvidia 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

```

Modules:
```
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
dm_crypt               11385  0 
nvidia               7088432  24 
snd_intel8x0           25664  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
arc4                    1165  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
rt73usb                22538  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
crc_itu_t               1383  1 rt73usb
psmouse                59033  0 
rt2500usb              18113  0 
rt2x00usb               9779  2 rt73usb,rt2500usb
snd                    49102  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2x00lib              27307  3 rt73usb,rt2500usb,rt2x00usb
shpchp                 29886  0 
serio_raw               4022  0 
led_class               2633  1 rt2x00lib
ppdev                   5556  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
mac80211              231927  2 rt2x00usb,rt2x00lib
lp                      7342  0 
dcdbas                  5402  0 
parport_pc             26058  1 
parport                31492  3 ppdev,lp,parport_pc
cfg80211              144822  2 rt2x00lib,mac80211
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489658  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
b44                    26253  0 
ssb                    39320  1 b44
intel_agp              26566  1 
floppy                 54311  0 
mii                     4425  1 b44
agpgart                32011  2 nvidia,intel_agp

```

I can't run the unity one as I'm using mint at the moment. I can, of course, switch back, but that might take a while. I intend to switch back , I just wanted to see if it was ubuntu-specific.

I'm not especially bothered about compiz or Unity, it's just the lack of anything 3d in my desktop. I have the capability, why can't I have at least *some* of the graphics others have. I'll probably use the LTS when I switch back.

Thanks for answering, wildmanne. Debt owed, again. :)

---

### Post by MG&amp;TL on 2011-09-25
I'm using the 173 drivers, but they cause non-booting, the 96 ones are similiar, and the 'experimental' ones are, experimental. :D

---

### Post by wildmanne39 on 2011-09-25
Hi, I have been researching this but I did not find an answer.

I help someone yesterday get 3d going with the intel he had installed also he was happy but he said it was still buggy, do you still have the intel also? it is belt in right? 

What model is the intel?

You still have the driver loaded it could be conflicting you can blacklist it and see.
```
sudo su
echo "blacklist intel_agp" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by MG&amp;TL on 2011-09-25
The cards conflicting were my initial suspicions. I shall have a look tommorrow morning (~9 hours) , and try the blacklist.

Thanks. Just irritates me if something doesn't work and it should.

---

### Post by wildmanne39 on 2011-09-25
Hi, your welcome! let us know.
Thank you

---

### Post by MG&amp;TL on 2011-09-26
Hm. The intel driver has been blacklisted, but it's still listed in lsmod:

```
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
dm_crypt               11385  0 
arc4                    1165  2 
snd_intel8x0           25664  2 
rt73usb                22538  0 
crc_itu_t               1383  1 rt73usb
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
rt2500usb              18113  0 
rt2x00usb               9779  2 rt73usb,rt2500usb
snd_seq_midi            4588  0 
rt2x00lib              27307  3 rt73usb,rt2500usb,rt2x00usb
nvidia               7088432  24 
snd_rawmidi            17783  1 snd_seq_midi
led_class               2633  1 rt2x00lib
mac80211              231927  2 rt2x00usb,rt2x00lib
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
ppdev                   5556  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144822  2 rt2x00lib,mac80211
dcdbas                  5402  0 
snd                    49102  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489658  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
b44                    26253  0 
intel_agp              26566  1 
ssb                    39320  1 b44
floppy                 54311  0 
mii                     4425  1 b44
agpgart                32011  2 nvidia,intel_agp

```

etc/modprobe.d/blacklist.conf:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist intel_agp


```

I have rebooted. Why is it doing this? Compiz --replace still gives a blacklist warning.

---

### Post by wildmanne39 on 2011-09-26
Hi, I do not know why it is still showing in lsmod.

---

### Post by MG&amp;TL on 2011-09-26
Mh. Never mind, then. It's still perfectly usable. :)

Thanks wildmanne.

---

### Post by wildmanne39 on 2011-09-26
Hi, your welcome! I will do some research and if I found something I will post it here.
Thank you

---

