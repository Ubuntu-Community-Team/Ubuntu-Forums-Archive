---
title: "Sound problems on two machines"
date: 2019-02-26
forum: Hardware
---

### Post by jians5 on 2019-02-26
Hey all,

***SOLVED: had to install pavucontrol and set it there***

So I'm trying to make the switch away from Windows. I've installed Ubuntu on two of my machines - my main gaming machine with a Gigabyte Sniper g1 z87 motherboard, and the other is an old Baytrail tablet. Both machines are having crippling sound problems.

First, my gaming PC:

The board has an onboard Soundblaster Recon 3Di. Sound is working - but I can't figure out of how enable the Line-In or microphone so I can always hear them. I think there's a setting in Unity but I'm using Cinnamon and it's not there. (Should I abandon Cinnamon? A lot seems to be missing. I'm gonna try KDE) The goal is to run the tablet's output through the PC's line in and out the speakers because the tablet's single speaker's low frequency response is in the thousands of hertz. There's no line-in in alsamixer but everything else seems to be there - master, pcm, front, surround, centre, LFE, S/PDIF, etc. it's all there apart from the inputs. The inputs are all there in sound settings and they're receiving signal (the input level bar moves).

On to the tablet:

It's a Hipstreet W10. It seems to use the same sound driver as the Asus Transformer T100 - bytcr-5460 which according to google has had issues for a long time until somewhat recently - at least that's what Ubuntu recognizes. The problem is many-fold, which tells me it's the wrong driver. First - the headphone detection is backwards - if I plug in some headphones - headphones is disabled and sound comes out the internal speaker. If I unplug them, headphones reappears in the sound settings audio output defaults to the non-existent headphones. The only way I've been able to get audio out of the tablet other than the built-in speaker is to use bluetooth, which would be fine except after going back to Windows on the desktop to hear what's coming out of the tablet over bluetooth - the channels are reversed! I can live with that if I have to, but I really shouldn't have to use bluetooth to get audio from one machine to another.

So, am I doomed to continue with Windows or is there something I can do? I'd be willing to buy a new sound card for the PC if that's what it takes - but I obviously can't do that for the tablet. I've tried messing around in alsamixer, which has seemingly hundreds of devices (If I had to guess I'd say around 50), but nothing I change in there has any affect. I can turn headphones on and off - but they won't unmute and the volume level doesn't appear.

---

### Post by jians5 on 2019-02-26
[FONT=arial]So - I've managed to get sound in to my line-in with [/FONT][FONT=courier new]

[/FONT][FONT=courier new]pactl load-module module-loopback

[FONT=arial]So the desktop seems to be working properly. Now if I could just get audio out of the tablet's line out.[/FONT]
[/FONT]

---

### Post by webaake on 2019-02-26
On your Cinnamon machine is Pulseaudio installed? I guess it is and in that case you try pavucontrol form the terminal.  It's the sound setting for pulseaudio, volume and mixer.

---

### Post by CatKiller on 2019-02-26
> **jians5 said:**
> First - the headphone detection is backwards - if I plug in some headphones - headphones is disabled and sound comes out the internal speaker. If I unplug them, headphones reappears in the sound settings audio output defaults to the non-existent headphones.

That mechanism is called "presence detection." There is a way to configure how ALSA interprets the signal pins, but it's not something I've ever done. Hopefully that's enough to get you started.

---

### Post by jians5 on 2019-02-26
Sorry excuse my neophytism. 

pulseaudio was installed but pavucontrol wasn't. I was able to set the line out there and it seems to work. Thanks!!

---

### Post by cooklook on 2019-04-15
Seems to have a solution on this [blog]("https://www.allicdata.com/blog.html")?

---

