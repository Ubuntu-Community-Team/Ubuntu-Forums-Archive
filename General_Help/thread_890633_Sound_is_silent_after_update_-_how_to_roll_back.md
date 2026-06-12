---
title: "Sound is silent after update - how to roll back?"
date: 2008-08-15
forum: General Help
---

### Post by Redsandro on 2008-08-15
**-edit-**

I am sure a lot of people (including me) would still like to know how to roll back an update. But this exact problem was *'bypassed'* by formatting, reïnstalling and not updating.

**-original post-**

Today I updated **Xubuntu 8.04** on my **P3 800MHz** for the first time in at least a month. I use it as media center. It has a *"C-Media Electronics Inc CM8738 (rev 10)"* (I think it's Sweex or something cheap) sound card which has always worked without a problem.

But after the update, there is no sound anymore! The driver is still loaded. The soundmix icon is there, all sliders are at maximum value. Alsamixer in a terminal runs fine, also everything at 100%. Mediaplayers (and mplayer in a terminal) don't whine, everything plays but I hear nothing! Not on my TV, not on my rear speakers..

How do I find out what causes this? How do I roll back the updates?

---

### Post by iaculallad on 2008-08-15
Just install the linux-generic file:

```
sudo aptitude install linux-generic
```

---

### Post by Redsandro on 2008-08-15
I'm on it, will let you know!

-edit-

I guess that one would be too easy. ;) It's still silent.

---

### Post by Redsandro on 2008-08-15
Dammit, I'm expecting a bunch of people soon, and we was supposed to play some games on the emulator. I should have never done an update. How can I roll this back? I am not really finding similar topics with solutions.

Here's a bunch of info that might be helpful?
[SIZE="1"]```
$ **aplay -l**
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: CMI8738 [C-Media CMI8738], apparaat 0: CMI8738-MC6 [C-Media PCI DAC/ADC                          ]
  Sub-apparaten: 0/1
  Sub-apparaat #0: subdevice #0
kaart 0: CMI8738 [C-Media CMI8738], apparaat 1: CMI8738-MC6 [C-Media PCI 2nd DAC                          ]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: CMI8738 [C-Media CMI8738], apparaat 2: CMI8738-MC6 [C-Media PCI IEC958]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
sander@mc-rups:~$ aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: CMI8738 [C-Media CMI8738], apparaat 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Sub-apparaten: 0/1
  Sub-apparaat #0: subdevice #0
kaart 0: CMI8738 [C-Media CMI8738], apparaat 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: CMI8738 [C-Media CMI8738], apparaat 2: CMI8738-MC6 [C-Media PCI IEC958]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0


$ **lspci**
(...)
02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


$ **lsmod|grep snd**
snd_rtctimer            4640  0
snd_cmipci             38528  2
gameport               16008  1 snd_cmipci
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_rtctimer,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  18 snd_rtctimer,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```[/SIZE]

I don't even know what update was problematic. There were maybe 50 updates or so.

---

### Post by Redsandro on 2008-08-15
&@# Live cd of Ubuntu 8.04 runs audio fine.. can someone tell me how to install drivers from that CD instead?

---

### Post by Redsandro on 2008-08-16
Guessed not.

Well I reinstalled Xubuntu and lost an entire day trying to get stuff sort of the way it was.

I will **never** do any updates on that machine again. If it ain't broke, don't fix it. :-x

---

### Post by stoneage on 2008-08-16
Did you try paconfig:-

[http://216.239.59.104/search?q=cache:Vz0f8BFUyhYJ:ubuntuforums.org/showthread.php%3Ft%3D759147+paconfig+ubuntu&hl=en&ct=clnk&cd=3&gl=uk&client=firefox](http://216.239.59.104/search?q=cache:Vz0f8BFUyhYJ:ubuntuforums.org/showthread.php%3Ft%3D759147+paconfig+ubuntu&hl=en&ct=clnk&cd=3&gl=uk&client=firefox)

---

### Post by Redsandro on 2008-08-18
No, I already reinstalled everyting, and I deliberately don't use Pule Audio because Alsa Sound System worked perfectly for like.. ever.

But thanks for thinking with me!

---

