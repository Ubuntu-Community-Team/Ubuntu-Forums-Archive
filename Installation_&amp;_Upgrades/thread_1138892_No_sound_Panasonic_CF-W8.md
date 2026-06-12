---
title: "No sound Panasonic CF-W8"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by LordVeovis on 2009-04-26
Just finished an install to my new CF-W8 from Panasonic, but there is no sound.

lspci gives
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Device 8338
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f6a20000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

aplay -l gives
```

class@class-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and lastly codec
```

class@class-laptop:~$ cat /proc/asound/card0/codec#* |grep Codec
Codec: Analog Devices AD1883
Codec: Conexant ID 2c06

```

---

### Post by kambara on 2009-07-02
I encountered the same problem on Panasonic CF-W8.

I added the following line to /etc/modprobe.d/alsa-base.conf and reboot. Then the speaker worked.:p
```
options snd-hda-intel model=thinkpad
```


I don't know why the model name is "thinkpad". I tried other names such as "panasonic", "laptop", and "dell", but they didn't work.

---

### Post by photonik on 2009-11-15
> **kambara said:**
> I encountered the same problem on Panasonic CF-W8.

I added the following line to /etc/modprobe.d/alsa-base.conf and reboot. Then the speaker worked.:p
```
options snd-hda-intel model=thinkpad
```


I don't know why the model name is "thinkpad". I tried other names such as "panasonic", "laptop", and "dell", but they didn't work.

Yes, I had the same problem with panasoni CF-T5.  I searched over the internet and find many people who have the similar/same problem sine long time ago.  And it seemed to be impossible to solve that problem, even I tried every way like: editing the alsa-base.conf, tune the alsamixer ... etc.  Nothing change!

But this morning, suddenly, it's solved.  I just startup Karmic and heard some musics of startup process.  Oh thanks god, thank Xorg or someone in ubuntu comunity.  

It might be solved by updating the bugfixes last time from repository.

Thank you so much, 
I love all of you
Photonix

---

### Post by photonik on 2009-11-17
Today, I've just known a interesting story related to the STAC 92XX soundcard :D (the soundcard in panasonic CF-W8 and CF-T5):

One woman asked me to help her a problem with sound in her Dell - Vostro 1400.  She has just install windows 7.  The problem exactly same: no sound from build-in speaker, but sound can be from headphone line :D.  After a few minutes I found that her laptop using STAC 92xx sound card, and windows7 faced the same problem, it does not support that sound card.  I have to go to dell website to download it for her, and the problem solved.  

Interestingly, Kaola Karmic automatically support that soundcard now.  

Cheer Ubuntu!

---

### Post by listerdl on 2010-04-04
Just want to add to the community that I have the toughbook panasonic CF F8 which is virtually the same as machines described above and the hack worked a treat. Thanks.

---

### Post by tieuvinhlong on 2010-07-05
> **kambara said:**
> I encountered the same problem on Panasonic CF-W8.

I added the following line to /etc/modprobe.d/alsa-base.conf and reboot. Then the speaker worked.:p
```
options snd-hda-intel model=thinkpad
```


I don't know why the model name is "thinkpad". I tried other names such as "panasonic", "laptop", and "dell", but they didn't work.

Good idea!

Now, you have one more sound config for laptop panasonic cf-w8 is: 
```
options snd-hda-intel model=laptop
```

you can find sound model in: [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

---

### Post by euancampbell on 2010-12-08
same problem worked like a charm! Thanks

---

### Post by your_peak on 2011-02-10
Many thanks. :)

It is also a solution for my case.

Ubuntu 10.10, Panasonic CF-S8.

I have been looking for such a solution for many months.

---

### Post by Fir3chi3f on 2011-08-17
As much as I love digging up old posts this actually helped me! I have a Cf-T8 and adding the option snd-hda-intel model=thinkpad helped!

I had actually tried model=thinkpad before, but I was trying to use sudo alsa force-reload instead of rebooting. Cheers!

---

### Post by Constantine013 on 2011-10-11
HELP! Same problem on CF-F8. When Starting Win7 or Vista or XP there's no sound(sound driver installed), but after sleep mode it works. I tried to find the codes you have written here on Windows OS, the system files are not opening. how can I fix it?

---

### Post by listerdl on 2011-10-11
> **Constantine013 said:**
> HELP! Same problem on CF-F8. When Starting Win7 or Vista or XP there's no sound(sound driver installed), but after sleep mode it works. I tried to find the codes you have written here on Windows OS, the system files are not opening. how can I fix it?

I love the CF F8 - best machine. Ever. The F9 has been out for a while, 64 bit i5 processor, way more kick than our 32 bit machines.

Are you running ubuntu as well or are you only using windows? Let me know - i know the CF very well and can help.

---

### Post by CommieIBanker on 2012-02-19
I had this identical audio problem in 11.10 (fully updated through 2/18/12), and used 'laptop' (instead of 'thinkpad' though I suspect that would have worked as well).

Worked like a charm.

> **kambara said:**
> I encountered the same problem on Panasonic CF-W8.

I added the following line to /etc/modprobe.d/alsa-base.conf and reboot. Then the speaker worked.:p
```
options snd-hda-intel model=thinkpad
```


I don't know why the model name is "thinkpad". I tried other names such as "panasonic", "laptop", and "dell", but they didn't work.

---

### Post by charleeontopvegas on 2012-04-16
> **CommieIBanker said:**
> I had this identical audio problem in 11.10 (fully updated through 2/18/12), and used 'laptop' (instead of 'thinkpad' though I suspect that would have worked as well).

Worked like a charm.

Same problem here, but when I type in  /etc/modprobe.d/alsa-base.conf
all I get is command not found, what am I doing wrong?
I type in /etc I get bash: /etc is a directory.

What am I doing wrong.

thanks charlee

---

### Post by HopToIt on 2013-02-03
> **charleeontopvegas said:**
> Same problem here, but when I type in  /etc/modprobe.d/alsa-base.conf
all I get is command not found, what am I doing wrong?
I type in /etc I get bash: /etc is a directory.

What am I doing wrong.

thanks charlee

you need to open **gedit** as the admin in order to save changes to alsa-base.conf
Enter following command in TERMINAL:**  sudo gedit /etc/modprobe.d/alsa-base.conf**

then add the following line and save changes:
**options snd-hda-intel model=thinkpad**
or
**options snd-hda-intel model=laptop**

Another success getting headphone sense jack capability to reactivate on an CF-52 semi-rugged running 12.10 32-bit.  No need to goof around with alsa-mixer, adding the model=thinkpad line now shuts off laptop speakers when inserting headphones.  Will try the model=laptop flavor also to see if that works also.

Try this post for more detail about what's going on with the alsa.conf in this matter:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

