---
title: "Edgy Audigy 2 ZS No Sound"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Exergy on 2006-10-27
Hi, I have a strange problem with my sound, I have an Audigy 2 ZS, it worked fine in Dapper, and even in the Live CD, yet it just refuses to work now ive installed.

Edgy seems to detect both soundcards fine, yet I get no audio from the Audigy, only the Nvidia, the nvidia was coming up as the primary device, so I switched it using the comprehensive audio thread guide on here.

Ive checked both the gui mixer, and alsamixer in console, everything is turned up, nothings muted.

Output of aplay -l is:

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: nForce3 [NVidia nForce3], device 0: Intel ICH [NVidia nForce3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: nForce3 [NVidia nForce3], device 2: Intel ICH - IEC958 [NVidia nForce3 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Anyone able to help? Many thanks.

---

### Post by Dmize on 2006-10-27
try going to system -> preference -> sound, then click the sounds tab and at the bottom, it should allow you to switch sound cards. I had this issue as well, that fixed it. give it a shot! :D

---

### Post by Exergy on 2006-10-29
No joy, ive tried that before, does not want to work.

Ive even disabled my on board sound card now, it seems it just doesnt like the audigy?

---

### Post by cyriq on 2006-10-29
hmm tried making a .asoundrc file in your home folder with settings for alsa?

If i havent made a typo at the settings the following might work (copy this into the .asoundrc) tho its a longshot:

pcm.sound-blaster{
 type hw
 card 0
}

pcm.sb {
 type plug
 slave.pcm "audigy"
}

pcm.audigy {
 type dmix
 ipc_key 1234
 slave {
 pcm "hw:0,0"
 period_time 0
 period_size 1024
 buffer_size 4096
 rate 48000
}
}

ctl.sound-blaster {
type hw
card 0
}

---

### Post by Ubuntist on 2006-10-31
> **Dmize said:**
> try going to system -> preference -> sound, then click the sounds tab and at the bottom, it should allow you to switch sound cards. I had this issue as well, that fixed it. give it a shot! :D

Thanks much -- this did the trick for me.

When I first installed Ubuntu, 5.10, I had no sound and spent weeks tracking down the solution.  Sound worked just fine under Dapper, and I thought the problems was solved.  Then when I put 6.10 on today and lost sound again, I was really ready to scream, because I remember all too well how much trouble I had under 5.10.  Thanks for saving my sanity!

---

### Post by ngowdar on 2006-10-31
Ohhh my god, I can't believe it. The system -> preferences thing actually works. This is my first linux install, and I spent 5 hours tinkering and trying to reinstall emu10k1, with lots of errors, etc etc. I was convinced that the sound was just not going to work. Kinda funny that all I had to do was switch sound cards.

Thanks guys!!!

---

### Post by myname on 2006-11-01
I only have 1 sound card listed there, and for the live CD of Ubuntu Edgy, I had sound, heck, even a full install of uEdgy 64, I had sound, but with uEdgy 32, I have no sound after installing.

This all worked fine in Dapper.  Any ideas where I can go from here to get sound to work, as I would hate to re-download Dapper and install.

--Kevin

---

### Post by Sebasti0n on 2006-11-04
> **myname said:**
> I only have 1 sound card listed there, and for the live CD of Ubuntu Edgy, I had sound, heck, even a full install of uEdgy 64, I had sound, but with uEdgy 32, I have no sound after installing.

This all worked fine in Dapper.  Any ideas where I can go from here to get sound to work, as I would hate to re-download Dapper and install.

I have the same problem. I selected the Audigy as my default sound card. It still doesn't work. I checked all volume levels. It works fine when using the live cd.

Cheers,
Sebastian

---

### Post by ksudbury on 2006-11-04
load "alsamixer" in a console scroll along check to see if your Audigy card is muted press M to unmute it, also check all volumes. 

It seemed to be muted by default on my machine (fresh install of edgy NOT an update). 

Hope this helps.

Cheers 

Keith

---

### Post by i18n on 2006-11-14
The same with Audigy 4 [SB0610] at an AMD 64 System with Xubuntu Edgy Eft. With Dapper it worked fine. I have a second sound card, a VIA AC97 at the main board, but deaktivated it in the BIOS.
Amixer is not mute, 
```
cat /proc/asound/cards
```
says:
```
0 [Audigy2        ]: Audigy2 - Audigy 4 [SB0610]
                      Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0xb000, irq 82
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5
```
and
```
lspci | grep -i audio

```
says:
```
00:0b.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

So the VIA chip is recognized but not used AFAIK.

It would be fine if anybody would have an idea and could help me, for I have to use this computer in a restaurant and it is important to play music. ;) Thanks a lot.

PS.: I'm fresh coming from FreeBSD and a little educated with hte tricky things. But, with Xubuntu, I'm a freshman. So, please be patient with me.

---

### Post by Malithorne on 2006-12-15
> **K31TH said:**
> load "alsamixer" in a console scroll along check to see if your Audigy card is muted press M to unmute it, also check all volumes. 

It seemed to be muted by default on my machine (fresh install of edgy NOT an update). 

Hope this helps.

Cheers 

Keith
Thanks Keith. Mine was an update not a fresh install. This worked for me the second time around after I figured out the interface. (Nearly scared me out of my skin from cranking up sound and speakers trying to figure out the problem!!) I un-muted everything that was muted and Ubuntu never sounded so good before. All along my subwoofer was muted and right channel. I have only been using Ubuntu for about 2 months. I love it though. Bye bye Microsoft.

---

