---
title: "Sound Problems"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by Night on 2007-05-03
Hey I'm having some sound problems. I just updated to fiesty and my sound stopped working. I followed the various guides around here and eventually I got it to work. Turns out the problem was with my groups there was a ',' where there should have been a ':'. After my next reset my sound stopped working I don't know exactly what error messages or log files you need copies of so I'll include  what I think will be helpful in hopes that you guys can work your magic.

```
alsamixer: function snd_ctl_open failed for default: No such device
```

```
lspci | grep 'Audio'
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

```
asoundconf list
Names of available sound cards:
Intel

```

```
lsmod | grep 'snd'
snd_hda_intel          22552  0 
snd_hda_codec         213504  1 snd_hda_intel
snd_pcm_oss            44800  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            35328  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54256  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56452  9 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

```
This is the one that worries me, if I understand lsmod at all (which I really don't) then should my sound driver, which should be snd_hda_intel according the the alsa guide, be used at least once not 0 times?

Hope someone can help, I really don't want to have to back up to reinstall.

---

### Post by gradedcheese on 2007-05-03
it is used once:

```

snd_hda_codec         213504  1 snd_hda_intel

```

Hey, this is an odd question but does the PC in question have a built-in modem?  have you disabled it?  If so, re-enable it in the BIOS and sound might be fixed.

---

### Post by aot2002 on 2007-05-05
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)

---

### Post by armornutz on 2007-05-05
Don't know if this will help you, but I have had sound problems with mine as well. I installed updates and my sound went away. I too searched all the forums and tried various different things that I got from the forums, In the end it was so simple. Go to Apps-Add/Remove-Sound&Video. Make sure that Alsamixergui and Alsamixer are checked. When I checked them and installed, my sound immediately worked.

---

