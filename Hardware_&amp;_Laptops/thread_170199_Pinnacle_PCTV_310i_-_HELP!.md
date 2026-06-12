---
title: "Pinnacle PCTV 310i - HELP!"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by Dryer Lint on 2006-05-04
I'm stuck with this hybrid DVB-T/Analog card and I know already the DVB part is not supported on Linux.

However, the analog part is supposedly supported.

I searched for a while now for documentation on how to set it up but couldn't find anything. I'm not even sure what I have to set up.

I need to change video4linux configuration, right?

Anyway, I'd be really happy if anyone could help me, I bought this card months ago and haven't used it at all yet. :(


Edit: I am running Dapper with all the latest upgrades.

---

### Post by Dryer Lint on 2006-05-08
Please, there must be someone who can give me a hint where I can find information about getting video4linux running.

---

### Post by twotonz on 2006-07-12
Hi Dryer,
I see that this post is a few weeks old, so before I start here, just wanted to know if you have got it working yet?, are you still watching this post?
 I had a pinnacle 100i, and had it working under dapper, yesterday, I swapped it over for a 310i, so am now sitting here with the intention of getting the 310 working.
 You are right, the first step is to pass over the right parameters to the v4l driver.

Love & Peace
anthony

---

### Post by twotonz on 2006-07-24
Hi again,
I see that this thread is not getting a lot of attention. However, it seems to be the only thread dealing with the Pinnacle 310i, so I thought that I should jot down a few things just in case anybody happens to stumble apon this.

 Firstly, people please be carefull if experimenting with the v4l driver! I passed over the wrong settings, and broke the card. Wouldn't even work under windows, apparently this card has a wackly i2c, luckely there is a solution..

Power down the PC, remove the power cord, remove the tv-card, put it into another pci slot, power up again, hopefully the card has reset itself, (or something, anyway).

 The next thing that I have picked up on the net, apparently, it is possible to get the card working, (and some people have allready - under debian, so its looking hopeful). As I understand it, one needs the newest v4l, and the paket from mercurial. It has also been recomended to recompile the kernel.....

> It's a good idea recompile your kernel with this tips:


Device Driver --->
Multimedia Devices --->
<M> Video for Linux
Digital Video Broadcasting Devices --->
[*] DVB for Linux
<M> DVB Core
I2C support ---> <M> I2C support <M> I2C device interface

 Proper support for this card should be available very soon, as one of the Guru's working on v4l has it on his todo list. Soooo, it's either a matter of fiddling, or being lazy, and waiting for someone else to sort it out. I myself shall continue (lazy but impatiant) playing around, if I get a result I shall post again. Good luck....

Love & Peace
anthony

---

### Post by MadeR on 2007-10-21
> **twotonz said:**
> Hi again,
I see that this thread is not getting a lot of attention. However, it seems to be the only thread dealing with the Pinnacle 310i, so I thought that I should jot down a few things just in case anybody happens to stumble apon this.
 
Firstly, people please be carefull if experimenting with the v4l driver! I passed over the wrong settings, and broke the card. Wouldn't even work under windows, apparently this card has a wackly i2c, luckely there is a solution..
 
Power down the PC, remove the power cord, remove the tv-card, put it into another pci slot, power up again, hopefully the card has reset itself, (or something, anyway).
 
The next thing that I have picked up on the net, apparently, it is possible to get the card working, (and some people have allready - under debian, so its looking hopeful). As I understand it, one needs the newest v4l, and the paket from mercurial. It has also been recomended to recompile the kernel.....
 
 
 
Proper support for this card should be available very soon, as one of the Guru's working on v4l has it on his todo list. Soooo, it's either a matter of fiddling, or being lazy, and waiting for someone else to sort it out. I myself shall continue (lazy but impatiant) playing around, if I get a result I shall post again. Good luck....
 
Love & Peace
anthony
 
 
no. just replace the ubuntu firmware with the one from the windows drivers and reboot.
 
kaffeine will work fine then.

---

### Post by alexixor on 2007-11-07
I also have this card in ubuntu 7.10. It works for video in tvtime but I have not been able to enable sound.

lsmod | grep saa shows:

aa7134_dvb            18188  0 
dvb_pll                15492  1 saa7134_dvb
saa7134_alsa           15392  1 
video_buf_dvb           7812  1 saa7134_dvb
tda1004x               17028  2 saa7134_dvb
snd_pcm                80388  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
saa7134               129100  3 saa7134_dvb,saa7134_alsa
video_buf              26244  4 saa7134_dvb,saa7134_alsa,video_buf_dvb,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              35460  2 saa7134,ir_kbd_i2c
videodev               29312  2 saa7134
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev
snd                    54660  13 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device i2c_core               26112  9 tda827x,saa7134_dvb,dvb_pll,tda1004x,tuner,saa7134,ir_kbd_i2c,nvidia,i2c_nforce2

In the sound preferences I see the SAA7134 tab and in there I see only a Video control, which does not work very good :).

Do you have any suddestions?

Thank you

---

### Post by hermelinen on 2007-11-09
I also managed to get the card to work visually, but no sound. I managed to get sound once but then it was way too fast and chopped up. Anyone has any suggestions? Can it be sampling related?

---

### Post by iyiguncevik on 2008-01-27
I couldn't manage to get any sound neither. Any updates on this problem?

---

### Post by MadeR on 2008-01-27
Yes.
This problem is usually caused by the fact that alsa set as default (or 0-indexed) sound card, the one embedded in the tv card.

You have to know the names of the soundsystems in your PC as detected by alsa:
```
asoundconf list
```

then select as default soundcard the one you need:
```
sudo asoundconf set-default-card *YourSoundCard*
```

---

### Post by hermelinen on 2008-01-28
Running:
```
asoundconf list
```

I found out that my sound card was ICH6 so I ran

```
sudo asoundconf set-default-card *ICH6*
```

This worked when I had the cable from the tv card to my sound card. However, when I removed the cable the sound stoppped working.

In mplayer I can get sound by manually selecting the source of the sound as the tv card. However in Mythtv this does not seem to work. Despite the fact that I use /dev/dsp1 in the mythtv configuration. 

This mplayer command gets me sound. See if anyone can figure out why Mythtv fails.

```
 mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=europe-west:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=PAL 
```

When I use tvtime though I get no sound. However that can be fixed by issuing

```
 arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,4 
```

irrespecive of tv software you will get sound since you pipe the sound from the tv card to the native sound card. However this should in principle be what tvtime should do when you give /dev/dsp1 as the sound source right?

/dev/dsp is my native sound card and /dev/dsp1 points to my tv card. Thus

```
  cat /proc/asound/cards 
``` gives

```

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with ALC658D at irq 20
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfddff000 irq 20

```

and ```
 asoundconf list 
``` gives

```

Names of available sound cards:
ICH6
SAA7134

```

Ciao for now.

---

### Post by MadeR on 2008-01-28
what happens if you use klear or kaffeine? (I suppose you are using kubuntu as I do)

---

### Post by iyiguncevik on 2008-01-28
That didn't work. But in the mean time i found something else: I can hear sound if I execute any of followings
```
arecord -D hw:2,0 -r 32000 -c 2 -f S16_LE | aplay -D front
```
```
sox -r 32000 -w -t alsa hw:2,0 -t alsa hw:0,0
```
Bu these are not solutions because I need  to execute this each time I'm watching tv. 
I have three devices in the asoundconf list, ICH5, Camera and SAA7134. What I don't understand is ICH5 (hw:0,0) should be the working card but SAA7134 (hw:2,0) is the one which allows me to listen to tv with arecord. However, I can listen xmms with hw:0,0 only. 

I tried to set both devices as default with asoundconf, but none of them helped me with tv.

---

### Post by hermelinen on 2008-01-29
> **MadeR said:**
> what happens if you use klear or kaffeine? (I suppose you are using kubuntu as I do)

I tried using kaffeine, but that only allows you to watch digital tv, and I can only watch analog. Btw, I use Ubuntu Gutsy. Never really liked KDE. :)

I think I may have found a source for the issue. At least in my case. I've seen reports on other pages saying that sound when using dvb-t with the pinnacle 310i card works fine, but not when using the analog. I've only tried the analog. I suspect I could get it to work with dvb-t. Unfortunately I have to have a card that can do dvb-c in order to watch digital tv. So I have to buy a new card it seems. :mad:

---

