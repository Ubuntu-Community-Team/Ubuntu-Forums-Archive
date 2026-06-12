---
title: "Cannot record using microphone input jack at all??"
date: 2011-10-08
forum: Hardware
---

### Post by davidlondonuk on 2011-10-08
Hi all,

Just installed xubuntu 11.04 and really like it.

Sound worked out of the box with pc speakers connected to a packard bell pc -so I can listen to music, watch youtube etc. My problem is, no matter how I configure xfce4-mixer I cannot record using the mic input jack.

This pc has a sis si7012 on-board card which uses a realtek alc655 chip, card provides for surround sound and 4 speakers etc if you want it. 

I have tried test recording (mic and guitar) using audacity and qtractor-I have tried mic, line-in, iec958 and aux capture and nothing works. Tried mic1, mic2 and all obvious variations. Tried audacity using jack server but still all recording failed. 

The only time I see any sort of response is with line-in but the output is just silence and audacity doesn't show anything being recorded.

Xubuntu system configured itself to use  snd_intel8x0 and snd_ac97_codec (drivers) for sound.

If anyone has any ideas it would be appreciated.


**Solved: Well sort** of-the expensive sony mic with a mono mini jack won't work but a really cheap mic with a stereo mini jack does? Why is that? Anyway the standard mixer setup was ok all along -but I don't understand this mic thing.

---

