---
title: "Acer 8920: no sound AT ALL"
date: 2008-07-20
forum: Hardware
---

### Post by mendoh on 2008-07-20
:confused:

After two whole days spent in trying to have my new Acer Aspire 8920 sound card working with Ubuntu 8.04 Hardy Heron, I've given up.

I apparently tried EVERYTHING so far (tweaking alsa drivers, modifying alsa base file with options snd-hda-intel model=acer, installing hardy-backports, etc.): NO WAY, audio card JUST DOES NOT WORK.

The audio device installed is an Intel 82801H (IC8 Family) rev 03.

As long as I could verify, this is quite a serious issue concerning the very latest release of UBUNTU, as when I use VISTA, the whole audio setup works flawlessly.

Is there any UBUNTU Guru out there able to assist?
In my opinion a detailed step-by-step procedure regarding installation of the latest alsa driver along with kernel modifications should do the trick...any suggestions?:confused:

Mendoh

---

### Post by jonathanjoe10 on 2008-07-20
I have an Acer 5920 with a Reltek ALC888 and this worked for me

In the Terminal type "alsamixer". Once there use M to turn on the speakers that are off. And increase the levels as needed. It is easier to do when a song is playing in a player so you know when it's working

---

### Post by mendoh on 2008-07-21
Hi Jonathan, 

thanks for your reply!

As a matter of fact, I already tried with alsamixer and...it does not work.
The only channels I see muted (double M in alsamixer) are microphone and line in ones and I really do not believe they have anything to do with the problem. Regarding the other audio channels I am unfortunately unable to hear any sounds, no matter I unmute them and set their volume to a decent level.

According to the information I have, your laptop should have an identical sound card to mine: would you please confirm that?

If your sound card is the same, you have Ubuntu 8.04 installed and you can hear sounds correctly, would you please post me all your current (audio) settings from Alsa mixer/GNOME Alsa mixer, alsa base file, alsa driver and Ubuntu kernel release? I believe this way we could try to "close the circle" and find our what the hell is going on here...

Thanks!

---

### Post by glethro on 2008-07-22
hey i have the same laptop (8920) and have the same problem.. no sound.

i was thinking it might have something to do with the built in dolby home theater.. tht seems to be one of the things tht sets it apart from other laptops (sound wise).. could this have nything to do with the issue?

no1 ive asked seems to be able to fix this ..

---

### Post by mendoh on 2008-07-22
Glethro the main trouble is with the Intel HDaudio sound card: it is so messy with the sound drivers!
So far I only found out how to have 2 speakers working in stereo mode at half the volume I would get when running VISTA: indeed very frustrating, if you consider this is the FOURTH day I am trying to have this ******* sound card working correctly with Ubuntu.

I will keep you posted...

---

### Post by jansaell on 2008-07-29
I have had the same problem and there is 2 ways of solving this. I have them listed on my blog at [http://jan.saell.org/blog/archives/30]("http://jan.saell.org/blog/archives/30").
In short:
Way 1 - remove ALSA and install OSS4 - this works and gives sounds but i had problems with mics on that but playback was ok.

Way 2
[LIST=1]
[*]Upgrade to ALSA 1.0.17 - not totally sure that that's fully required
[*]Set model to acer-aspire in /etc/modprobe.d/alsa-base
[*]Download and compile hda-verb from [here]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2")
[*]Copy the compiled program to /usr/local/bin
[*]Run the command (prefably from /etc/rc.local so it will happend every bootup): /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
And you have to run that as root
[/LIST]
That should give you sound working.

---

### Post by bamboo85 on 2008-07-29
use external sound card

---

### Post by mendoh on 2008-07-31
> **jansaell said:**
> I have had the same problem and there is 2 ways of solving this. I have them listed on my blog at [http://jan.saell.org/blog/archives/30]("http://jan.saell.org/blog/archives/30").
In short:
Way 1 - remove ALSA and install OSS4 - this works and gives sounds but i had problems with mics on that but playback was ok.

Way 2
[LIST=1]
[*]Upgrade to ALSA 1.0.17 - not totally sure that that's fully required
[*]Set model to acer-aspire in /etc/modprobe.d/alsa-base
[*]Download and compile hda-verb from [here]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2")
[*]Copy the compiled program to /usr/local/bin
[*]Run the command (prefably from /etc/rc.local so it will happend every bootup): /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
And you have to run that as root
[/LIST]
That should give you sound working.

:popcorn: Jansaell, what can I say?

First of all a HUGE and HEARTFELT THANK YOU!!
Thank you, thank you, thank you and once again thank you!

By following the directions in your blog, I finally managed to get this ******* sound card working correctly with ALL the 5 speakers!:popcorn:

Considering that I have spent almost one entire week so far in trying to find a way out of this mess, you really made my day.
I own a security business and if there is something that I can do for you in return, please feel free to message me or email me private.

Keep up the good work!:)

Mendoh

---

### Post by mendoh on 2008-07-31
Anybody experiencing the same trouble on 8920 and 6920 Acer laptops, simply follow these clear indications and you will be out of an awful mess in a matter of minutes::guitar:

[http://jan.saell.org/blog/archives/30](http://jan.saell.org/blog/archives/30)

---

