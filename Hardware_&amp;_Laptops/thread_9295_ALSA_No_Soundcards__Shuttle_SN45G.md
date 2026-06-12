---
title: "ALSA: No Soundcards / Shuttle SN45G"
date: 2004-12-27
forum: Hardware &amp; Laptops
---

### Post by baffled on 2004-12-27
Hey folks,

After installing Ubuntu on my dad's machine, I'm having some trouble with his sound.  It set up perfectly for my AMD64/MSI machine at home with an Envy chipset; however, my dad's Shuttle box is giving me no joy at all.  I'm a wee bit new at all this sound business in Linux, so apologies in advance if this is obvious - it certainly doesn't appear it to me!

First, hardware:

* Shuttle SN45G V3 case/mobo/psu SFF box, Realtek ALC650 sound (AC97)
* ATi Radeon 9600 Pro 256mb (Which I did finally get working)
* 802.11g PCI wireless card, which was picked up fine by the installer.
* 1gb RAM
* Lite-On DVD-Combo drive.
* 120gb Seagate PATA HDD

Next, what I've ascertained:

* Boot message when trying to restore ALSA mixer settings - 1134, no soundcards found.
* NVidia driver package for the nForce package wants to recompile the kernel - this seemed a bit drastic, especially when people seem to be saying it only supports OSS and not ALSA anyway.
* I believe I'm supposed to be using the snd-intel8x0 driver for this chipset.
* Sound hardware is definitely functioning - machine is dual-boot Win2K and it is working 100% on the Windows side of the equation.

... with that in mind, I edited /etc/modules and put the snd-intel8x0 driver in the end.  A reboot later I've still got the ALSA error message, but now there's a whole heap more modules loaded (initially doing "lsmod | grep snd" revealed nothing).

I checked dmesg and there's nothing there that appears to be coming from any of the ALSA/sound-related modules.

In the current state of the machine, this is what a quick peek reveals....

----------------

$ls /dev | grep dsp 

(no response, there's no DSP device)

sean@kilkoo:~ $ lspci | grep audio
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008a (rev a1)
sean@kilkoo:~ $ lsmod | grep snd
snd_intel8x0           35564  0
snd_ac97_codec         67908  1 snd_intel8x0
snd_pcm_oss            53160  0
snd_mixer_oss          19520  1 snd_pcm_oss
snd_pcm                95332  2 snd_intel8x0,snd_pcm_oss
snd_timer              25028  1 snd_pcm
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
gameport                4672  1 snd_intel8x0
snd_mpu401_uart         7872  1 snd_intel8x0
snd_rawmidi            25088  1 snd_mpu401_uart
snd_seq_device          8136  1 snd_rawmidi
snd                    55524  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
sean@kilkoo:~ $ cat /proc/asound/cards
--- no soundcards ---

-------------------------------------------

Anybody got any suggestions?  I'm tearing my hair out here.

---

### Post by richbayliss on 2005-01-13
Hey dude,

If you get any response, im in the same boat. My spec is pretty much the same, but I havent installed yet.

but im fed up with linux not supporting nforce2, so im interested in any fixes available.

---

