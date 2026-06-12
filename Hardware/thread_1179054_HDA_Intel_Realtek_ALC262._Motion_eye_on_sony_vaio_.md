---
title: "HDA Intel Realtek ALC262. Motion eye on sony vaio cure"
date: 2009-06-05
forum: Hardware
---

### Post by davavanstone on 2009-06-05
Hello people, just though i'd finally get myself on this forum.  I've been using Ubuntu Intrepid since its release and am loving it. There are just a couple of things i couldn't get my head around, one was my motion eye built in cam on a sony VAIO and the other was my sound card (built in microphone).


I have cured my webcam situation here (i'm a newbie so this will hopefully help other newbies)

lsusb result 

Bus 003 Device 005: ID **05ca:1839** Ricoh Co., Ltd
The websites mentioned here have support for lots of Ricoh cams, just take note of your kernel version for the correct download. In the readme of the Palmix archive [http://www.palmix.org/download/r5u870_k2.6.27.tar.bz2](http://www.palmix.org/download/r5u870_k2.6.27.tar.bz2) (kernel version 2.6.27) ignore the sony laptop type just follow the cam type: **05ca:1839** from lsusb My laptop wasn't listed but the cam type was.

First of all i followed this link on Palmix, after all the messing around....................it didn't work for me  :lol:  but other forums have showed great results, hopefully it will work for you.
[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

After some more scouring around i found this one
[http://wiki.mediati.org/b/2008/01/r5u870/](http://wiki.mediati.org/b/2008/01/r5u870/)
The info in the bold at the bottom or the site did it for me, the only problem i had was that the chmod command would have to be re-entered at every start just enter the 
sudo chmod 777 /dev/video0 at the end of /etc/rc.local. This will hopefully cure it.

Right now for some help from you guys if possible, no worries if you cant.
My laptop is a Sony VAIO vgn-bx61xn if anyone is familiar with this laptop (range) they have a built in mic [http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-BX&m=3095](http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-BX&m=3095) though no matter what i do i cannot get alsa to find the internal mic.  I have no trouble with the mic jack, and if i have to i will use an aftermarket mic but it would be great to get this one working.

I have played about with alsamixer and alsamixer -V capture -c 0 

also edited alsa-base 
```
sudo gedit /etc/modprobe.d/alsa-base
```
and added 
```
options snd-hda-intel model=vaio
```

The pulse audio capture is linked to front:0 which is my jack.

```
lsmod | grep snd
``` 
Gave me this result if this is any help to anyone.

```
snd_hda_intel         381488  5 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
```

amixer result
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]
```

Like i said i am generally new to linux so my result might show something obvious to someone that knows what they're doing  :D 

Anyways i hope someone can help

Dave

---

### Post by davavanstone on 2009-06-06
Bump
Anyone know anything about this? I know my mic i working because when i boot into xp all is fine.

---

### Post by magic-neophyte on 2009-10-16
For me (Intrepid 9.04) on Sony Vaio NS-11Z, recording and playback were fine when I added the following line: 

# Enable microphone and other features
options snd-hda-intel model=toshiba-s06

to the bottom of

/etc/modprobe.d/alsa-base.conf 

And then reboot the computer and recheck all the settings in Volume Preferences. Set Options > Input Source to: Int Dmic

Apparently the internal chipsets are most similar to Toshiba's s06 model.

Anyways, hope this solves your problem, 

magic neophyte

---

### Post by darkdragn on 2009-10-30
> **magic-neophyte said:**
> For me (Intrepid 9.04) on Sony Vaio NS-11Z, recording and playback were fine when I added the following line: 

# Enable microphone and other features
options snd-hda-intel model=toshiba-s06

to the bottom of

/etc/modprobe.d/alsa-base.conf 

And then reboot the computer and recheck all the settings in Volume Preferences. Set Options > Input Source to: Int Dmic

Apparently the internal chipsets are most similar to Toshiba's s06 model.

Anyways, hope this solves your problem, 

magic neophyte

Just wanted to say thank you. I havn't attempted it yet, but this is the only little light of hope for the mic in my vgn-cr240e. I'm going to attempt it tonight, and if it does work I will scour every forum i can find and post your resolution. Do you mind if I mention you? (To give you credit for the resolution of course, ^_^)

---

