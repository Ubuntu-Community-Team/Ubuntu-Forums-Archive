---
title: "No Sound Card"
date: 2008-10-31
forum: General Help
---

### Post by sup3roque on 2008-10-31
Hi all

I install ubuntu 8.04 in a Fujitsu Simens Scenic P300

And no Sound Card are found,I don't know what to do :(


# aplay -l

> aplay: device_list:205: no soundcard found...

# lspci -v

> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Fujitsu Siemens Computers Unknown device 1058
	Flags: medium devsel, IRQ 20
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=64]
	Memory at d0080c00 (32-bit, non-prefetchable) [size=512]
	Memory at d0080800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

I don't know what to do pelase help

Tks

---

### Post by sup3roque on 2008-10-31
more info > esacf@esacf-14:~$ lsmod | grep snd
snd_intel8x0           33948  0 
snd_ac97_codec         99876  1 snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            40736  0 
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                75400  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3972  0 
snd_seq_oss            34048  0 
snd_seq_midi            8480  0 
snd_rawmidi            24608  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51152  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23556  2 snd_pcm,snd_seq
snd_seq_device          8588  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54692  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
esacf@esacf-14:~$ 


---

### Post by sup3roque on 2008-11-03
a litle help please

---

