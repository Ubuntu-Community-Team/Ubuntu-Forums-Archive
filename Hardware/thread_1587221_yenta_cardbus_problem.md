---
title: "yenta cardbus problem"
date: 2010-10-03
forum: Hardware
---

### Post by eaglecros on 2010-10-03
Hi!

In my old laptop I had a PCMCIA Creative SoundBlaster Audigy2 ZS notebook card in order to get my external speakers working.When I bought a new laptop, I found out that my old PCMCIA card did not fit in any hole any more... damn! :confused: So, I decided to buy a PCMCIA to ExpressCard adapter. Specifically, I bought  DuelAdapter, but I don't seem to be able to get it working. It does work properly in the Vista installation my laptop has since I bought it, so a hardware problem is out of question. I have been doing quite a lot of googling, but I am not sure what the issue may be. Here a couple of things which I think could be related.

```

$ lspci
...
04:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
05:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller

```

(no sound card!)

Note that the adapter has a switch, which is intended to be in "position A" for MacOS, and in "position B" for Windows XP (although my Vista system recognised it perfectly in position A). Under linux, lspci reports the above devices with the switch in A position, and in B the devices do not show up.

When googling, I read that the "pci=assign-busses" kernel option could be the solution, but that didn't help either. Here more lspci info:

```

$ lspci -v | grep subordinate
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Bus: primary=00, secondary=04, subordinate=09, sec-latency=0
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
        Bus: primary=00, secondary=00, subordinate=00, sec-latency=0

```

In addition, yenta seems not to be very happy with the setup:

```

$ dmesg | grep yenta
[   21.098659] yenta_cardbus 0000:05:00.0: No cardbus resource!

```

And I have been unable to find anybody reporting such error in google... only pages where this error is listed along with the kernel code!

I also tried installing the sound card modules by hand via /etc/modules and rebooting, but that doesn't help either, although the modules get loaded correctly:

```

$ lsmod | grep yenta
yenta_socket           22901  0 
rsrc_nonstatic          9830  1 yenta_socket
pcmcia_core            38176  2 yenta_socket,rsrc_nonstatic

$ lsmod | grep emu10k
snd_emu10k1_synth       6036  0 
snd_emux_synth         37367  1 snd_emu10k1_synth
snd_emu10k1           148561  1 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
snd_pcm                87882  5 snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            23420  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6924  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71187  20 snd_emux_synth,snd_seq_virmidi,snd_hda_codec_idt,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_hwdep,snd_timer,snd_seq_device
snd_page_alloc          8500  3 snd_emu10k1,snd_hda_intel,snd_pcm

```

I would have thought that, simply, the adapter is not supported, but then I also came accross
 [[COLOR="Blue"]the following site[/COLOR]]("http://fr.audiofanzine.com/carte-son-pcmcia/e-mu/1616M/forums/t.280979,emu-1616m-adaptateur-pcmcia-expresscard-linux.html"). Although in french, the author reports that he got a similar sound card working a PCMCIA-ExpressCard adapter wich reports the same chip in lspci (the Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge).

I am running Lucid with a 2.6.32-25-generic kernel, on a x86_64 machine (an HP dv3000 series laptop).

Any ideas or hints towards where to get any help? ANY help at all is appreciated, since I have run out of resources towards solving this problem!! And if you need any further info, please do ask me!

Thanks!!

---

### Post by eaglecros on 2010-10-07
I hope this is a legit bump... does really nobody have any clue about how to attempt to solve this issue?

Thanks again!

---

### Post by eaglecros on 2010-10-22
Still not solved... any ideas anyone?

Thanks! :guitar:

---

