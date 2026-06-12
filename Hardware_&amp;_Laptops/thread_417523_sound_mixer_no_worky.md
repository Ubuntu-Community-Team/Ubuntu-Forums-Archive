---
title: "sound mixer no worky"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by aztektum on 2007-04-21
the volume controls in the mixer don't adjust my volume and if i run

```
speaker-test -c6 -twav

```

i only get sound out of the front 2 speakers "Front Left" "Front Right" says the nice lady and nothin when it passes through the remaining channels. (I have 5.1 speakers, the card does do 7.1)

i read other posts, all had problems with surround sound but not the mixer issue. i tried some diff .asoundrc settings which just killed any sound. so i am back to a blank rc file and no solution 

i have a creative sound blaster live 24-bit card. i do have onboard but that's disabled in BIOS

---

### Post by Merdyn on 2007-05-02
What about this:  
> 
speaker-test -Dplug:surround51 -c6 -twav   

or this 

> speaker-test -Dsurround51 -c6 -twav

I can hear the test voice in all speakers it this test, but when I try to play some 'stereo tunes' in totem, xmms, mplayer or whatever - only front speakers plus subwoofer are working. :confused:

---

