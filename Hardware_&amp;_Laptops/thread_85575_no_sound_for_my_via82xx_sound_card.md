---
title: "no sound for my via82xx sound card"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by wattsup on 2005-11-03
I have no sound at all at this point.
I've download the alsa-driver-1.0.8.tar.bz2 for my 2.6.10-5-386 kernal.
When I run ./configure --with-cards=via82xx --with-sequencer=yes i get:
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard via82xx

even though the instrucitons are for this card at [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235&module=via82xx)

any ideas?

---

### Post by heimo on 2005-11-03
Do you have snd_via82xx loaded? 
```
lsmod | grep snd
```

If not, what happens if you run?
```
modprobe snd_via82xx
```

How about?
```
lspci | grep -i audio
```

I'm using Breezy, but my via based sound was working "out-of-the-box" for Hoary too. Information from commands above should be very helpful to diagnose why yours is not.

---

### Post by wattsup on 2005-11-03
```
 lsmod | grep snd
snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd_pcm_oss            47652  0
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mixer_oss          16768  2 snd_pcm_oss
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  2 snd

```

and the other one:

```
lspci | grep -i audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

```

is breezy running well?

---

### Post by wattsup on 2005-11-03
any ideas what could be wrong. do you think upgrading to breezy would be a possible solution?

---

### Post by acehigh on 2005-11-04
I had no sound at all, but my modules were correctly loaded like yours (Hoary).
For me it was a simple problem of mixer, not of driver.
I had (with alsamixer or gnome volume control selecting alsa device) to activate
the mixer channels VIA DXS, VIA DXS2, VIA DXS3...
this worked for playback.
For recording: I had to deselect "Audio IEC958 capture monitor".
Hope it's helpful for you.

P.S. I have the same hardware like you:
```
lspci | grep -i audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

---

### Post by wattsup on 2005-11-06
Acehigh, I'm sure this could help me. I opened alsamixergui and I see the VIA DXS, VIA DXS2, VIA DXS3... I can adjust the volume, but I can't mute them, so I don't know if they're active. Is there some command I have to run?

Also, I don't have "Audio IEC958 capture monitor". I have IEC958, IEC958 Output, IEC958 Playback AC97...

---

### Post by heimo on 2005-11-06
In alsamixer, m should mute a channel. You could also try different settings in multimedia systems selector. If you're using alsa, change to esd and vice versa - also try killing esd (run: killall esd). What ever it is, it's most probably not driver / kernel module issue.

---

### Post by wattsup on 2005-11-08
heimo.. I've tried so many things. I was told to mute all IEC channels, but I can't mute IEC958 Playback AC97-SPSA. My school host a NCLUG (northern colorado linux users group) one tuesday a month, I hope to find the solution there. I'll let you know. In the mean time, I'm going to try breezy

---

### Post by pezz on 2005-11-09
After de upgrade from Hoary to Breezy I had the same problem with my soundcard (via8235).

In Breezy only esound-common was installed. I installed **esound** with synaptic en my problem was solved.

Hope it helps.

---

