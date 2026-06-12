---
title: "Sound card problem"
date: 2015-09-22
forum: Hardware
---

### Post by agnes4 on 2015-09-22
I've got and old emachines PC with Ubuntu 12.04 installed on it. I've tried the new Lubuntu 14.04 and loved it - everything works fine apart from the fact that there's complete lack of sound. The same was true for Ubuntu 14.04.


My PC's specs:
Emachines 5250
160 GB 
originally 512MB
Intel pentium 4
sound card Realtek Intel ALC 880


I've tried all the suggestions I could find on the web, nothing works. First I just had a Dummy Output, then manged to get it fixed to Analog stereo output. My sound card is sometimes seen by the system, sometimes not. 


I've tried re-installing pulseaudio and alsa several times - nothing. 
I've tried to do modprobe commands but all I get in return is: Permission denied.


What am doing wrong? Any suggestions?...........[http://www.besanttechnologies.com/training-courses/php-training/php-training-institute-in-chennai](http://www.besanttechnologies.com/training-courses/php-training/php-training-institute-in-chennai)

---

### Post by howefield on 2015-09-22
Post moved to own thread and also to the "*Hardware*" forum for better support.

---

### Post by Yellow Pasque on 2015-09-22
> My sound card is sometimes seen by the system, sometimes not. 

Get the information when it does work, and when it doesn't, and compare them: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by tgalati4 on 2015-09-23
Welcome to the forums.  A P4 system is quite old.  It's possible that your sound chip is broken.  It happens.  I've seen several eMachines with failing motherboards.  Inspect the motherboard for leaking or bulging  capacitors.  Clean the motherboard with compressed air.  Realtek soundchips are well-supported, so I don't think it is a driver problem. They are part of the Intel HDA (high definition audio) chipset which is pretty standard.  The reason you can't find much on the web for this problem is that it works for most people--so there are not any posts about "magic switches" needed to get the soundchip to work.

Find the chip on the motherboard and put your finger on it.  Is it really hot?  Press down on it hard and listen for sound.  It could be an intermittent connection.  Try the microphone input.  Can you record sound with *audacity*?

eMachines were low-cost machines and were not built to the somewhat higher quality level of Dell, HP, Compaq, etc.

Here's a similar thread:  [http://www.linuxquestions.org/questions/linux-newbie-8/no-sound-dummy-output-in-ubuntu-lubuntu-14-04-a-4175523450/](http://www.linuxquestions.org/questions/linux-newbie-8/no-sound-dummy-output-in-ubuntu-lubuntu-14-04-a-4175523450/)

Open a terminal and post the output of:

```
aplay -l
```

Post the output of:

```
lsmod | grep snd
```

It should look similar to:

> 
tgalati4@Mint17 ~ $ lsmod | grep snd
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd


---

