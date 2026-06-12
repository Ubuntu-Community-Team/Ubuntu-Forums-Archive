---
title: "Old prob: Headphone jack sense is not working"
date: 2009-11-06
forum: Hardware
---

### Post by Berniebln on 2009-11-06
Hello there,

I have a ASUS laptop (X72T aka X72TL with motherboard M70TL) and the following audio hardware built-in:

```
~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: SB [HDA ATI SB], Gerät 0: ALC663 Analog [ALC663 Analog]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: SB [HDA ATI SB], Gerät 1: ALC663 Digital [ALC663 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: HDMI [HDA ATI HDMI], Gerät 3: ATI HDMI [ATI HDMI]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

```I've updated from 9.4 to Karmic Koala, and I'm still experiencing the same problem I had before: The headphone jack sense is not working, that means if I listen to music on the internal speakers (no head phone plugged in), and I plug in a headphone, the music can be heard on both speakers (but with lower volume on the headphone).

The expected behaviour would be that the internal speakers are getting disabled when I plug in the headphone, and get enabled again if I plug it out.

Moreover, if I boot the pc with headphones already plugged in, the internal speakers are disabled (and stay disabled).

This question was asked quite often in the forums, and every time, people are told to check the "headphone jack sense" switch in the mixer, but in 9.4 and in 9.10, there was/is no such switch on my system.

Under Windows, it works as expected.

Would be cool if someone knows a solution :D

Bernhard

---

### Post by Berniebln on 2009-11-07
Hi again, it's getting even better :)

I realised that sometimes, the jack sense seems to work (right now, it works perfectly), but just a few days it didn't ... :shock:

Was something updated recently??

If not, I'll keep posting my experiences in this thread...

Bernhard

---

### Post by Berniebln on 2009-11-08
Hm, it is **not** working if I boot the computer **without the plug inserted**. Then I can plug it in and out as much as I want, the internal speakers are not switched off...

](*,)

Bernhard

---

### Post by wileur on 2009-11-10
Hi,

The simplest solution is to unmute headphone detection in alsamixer. I posted how to do that as well as how to script it here a couple of days ago: [http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect](http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect)

---

### Post by Berniebln on 2009-11-10
Hi,

> **wileur said:**
> The simplest solution is to unmute headphone detection in alsamixer. I posted how to do that as well as how to script it here a couple of days ago: [http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect](http://ubuntuforums.org/showthread.php?t=1319424&highlight=laptop+headphone+karmic+detect)

Thanks for your answer! Unfortunately, there is no such item, channel or switch called "Headphone Jack sense" in the mixer, hence when typing

[FONT=Courier New]~$ amixer -c 0 sset 'Headphone Jack Sense' unmute
[FONT=Arial]
I get the error message[/FONT]

**[COLOR=DarkRed]amixer: Unable to find simple control 'Headphone Jack Sense',0[/COLOR]**
[/FONT]
As in the past, under 9.04, there was never any switch or channel with a name similar to "Headphone Jack Sense", and I've tried switching on or off the other switches, it never helped.

Here's a little filtered dump of amixer:

[FONT=Courier New]~$ amixer | grep 'control'
[B]Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Default PCM',0
Simple mixer control 'Capture',0
Simple mixer control 'Beep',0
Simple mixer control 'Digital',0
Simple mixer control 'F-Mic',0[/B]
[/FONT]
I really have no idea what to do...

Bernhard

---

### Post by jas007 on 2009-11-15
I have the same problem using 9.04 with a dell optiplex 760

> ~$ amixer -c 0 sset 'Headphone Jack Sense' unmute

I get the error message

amixer: Unable to find simple control 'Headphone Jack Sense',0

Found a temp keyboard shortcut that will mute unmute the inbuilt speaker of my computer.

```
amixer sset Mono toggle
```

I adapted it from 

[http://www.commandlinefu.com/commands/using/amixer]("http://www.commandlinefu.com/commands/using/amixer")

---

### Post by Berniebln on 2009-11-16
Hi!

Doesn't work for me, unfortunately:
[INDENT][FONT=Courier New][COLOR=Black]$ amixer sset Mono toggle[/COLOR][/FONT]
[FONT=Courier New][COLOR=Black]amixer: Unable to find simple control 'Mono',0[/COLOR][/FONT]
[/INDENT]:(

Bernhard

---

### Post by jas007 on 2009-11-17
> Hi!

Doesn't work for me, unfortunately:

    $ amixer sset Mono toggle
    amixer: Unable to find simple control 'Mono',0



Bernhard 

You probably haven't got a Mono control. You can use amixer to find what your main speakers are and the card number, using:
```
amixer scontrols
```
which gives:
```
Simple mixer control 'Master',0
Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Front Mic',0
Simple mixer control 'Front Mic Boost',0
Simple mixer control 'Line',0
Simple mixer control 'Line Boost',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Default PCM',0
Simple mixer control 'IEC958 Playback Source',0
Simple mixer control 'Mono',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'Beep',0
Simple mixer control 'Digital',0
Simple mixer control 'Input Source',0
Simple mixer control 'Input Source',1

```

If changing the name dosen't help than also try adding your sound card number with the corrected name of the control.
```
amixer -c 0 sset Mono toggle
```
presuming that your card number is 0 and you have Mono.


On a side I still have exactly the same problem as you originally described. try 

```
 amixer scontents 
```
to see if Headphone Jack Sense is even an option. If it isn't than try this

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

if you have done that, than I can't suggest anything else. 

Please let me know if you figure it out how to fix the headphone jack sense issue.

Jason

---

### Post by Berniebln on 2009-11-18
Hey Jason,

thanks for your reply.

Just in case, I've just updated my ALSA to 1.0.21, but it didn't help either.

These are the controls I have on my system:

```

~$ amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Default PCM',0
Simple mixer control 'Beep',0
Simple mixer control 'Capture',0
Simple mixer control 'Digital',0
Simple mixer control 'F-Mic',0
```As you can see, there is no Mono, Jack sense etc. I've tried your command with some of the controls listed here, but it wouldn't work either.

I've used the alsa-info-script to post my system config on the internet: [http://www.alsa-project.org/db/?f=223945095585df0d31705b25c6d38525db8d939a](http://www.alsa-project.org/db/?f=223945095585df0d31705b25c6d38525db8d939a)

I checked your link to the HdaIntelSoundHowto, but I don't really understand what they are writing; my sound card module is snd_hda_intel, my codec is Realtek ALC663, but in the ALSA-Configuration.txt, there is no reference to the codec, nor to the models he is giving as examples in the text. I'm wondering if the manual is outdated, or if I simply get something wrong.

The strange thing is that sometimes, it would just work perfectly, but after a restart, it again does not work as expected.

Bernhard

---

### Post by jas007 on 2009-11-18
Hallo Bernard,
I am anything but an expert, so i can only help you a little, I never did manage to get my internal sound card's Headphone Jack sense working, using this method for my computer, but I did read somewhere that it works.

Before doing the next few steps try
```
 amixer scontents 
```

to see what options you have in relation to your sound card. If Headphone Jack Sense is listed there, than you just need to change that setting, if not than try below.

I found your card in the ALSA-Configuration.txt file, under
```

	ALC662/663
	  3stack-dig	3-stack (2-channel) with SPDIF
	  3stack-6ch	 3-stack (6-channel)
	  3stack-6ch-dig 3-stack (6-channel) with SPDIF
	  6stack-dig	 6-stack with SPDIF
	  lenovo-101e	 Lenovo laptop
	  eeepc-p701	ASUS Eeepc P701
	  eeepc-ep20	ASUS Eeepc EP20
	  ecs		ECS/Foxconn mobo
	  m51va		ASUS M51VA
	  g71v		ASUS G71V
	  h13		ASUS H13
	  g50v		ASUS G50V
	  asus-mode1	ASUS
	  asus-mode2	ASUS
	  asus-mode3	ASUS
	  asus-mode4	ASUS
	  asus-mode5	ASUS
	  asus-mode6	ASUS
	  auto		auto-config reading BIOS (default)

```

so I'm not sure which model your computer is but once you figure that part out you can add it to the alsa conf file, heres the how to again

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")


Unfortunately this is about all the help i can give you, but please let me know if this worked, or if you figured it out another way.

Jason

---

### Post by jackopo on 2009-11-23
I had also the same problem and the same conditions as Bernhard (an asus laptop and the same problem in the previous ubuntu releases).

After reading this thread I tried some tweaks,and I finally found the one that worked for me:

In alsa-base.conf I added at the end this line of code:

```
options snd-hda-intel model=auto
```

NB auto was the magic word
now it works and I can hear my music disturbing nobody ;)

Jacopo

---

### Post by Berniebln on 2009-11-23
Hi guys,

thanks for your hints.

I was trying the different model types for my sound card, but it wouldn't help, and with auto it also doesn't bring me a Jack Sense or Mono switch, and when plugging in the phones, it still doesn't switch off the internal speakers :(

I've posted a bug report on the alsa bug tracker, maybe they will find a way...

Thanks for your help anyways!!

Bernhard

---

