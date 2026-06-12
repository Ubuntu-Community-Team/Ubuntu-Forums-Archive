---
title: "Karmic - WinFast TV2000 XP Expert - No Sound"
date: 2010-02-18
forum: Hardware
---

### Post by sherbert on 2010-02-18
I've only dabbled in linux for a little while. Got everything working great, decided I'd give this tv tuner card a shot.

Well I'm completely stumped here. Got a picture, and all channels in TVTime, but no sound. I've searched and searched and searched and found some old guides and tried pretty much everything and have had no luck. All alsa channels are at full blast (Except PCM, which is at about 75%).

---

### Post by sherbert on 2010-02-18
Well I may be giving up all hope on this card. I do have another one I can try but I haven't got the slightest clue what kind it it is. The only physical clues on the card itself are "SV7130PCIA" and "ywx 0720". 

when i do lspci it appears as:

```
00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```

---

### Post by sherbert on 2010-02-18
UPDATE: I am an idiot.

While searching around for stuff about that SV7130 card I glanced over at the WinFast card laying on my bed and noticed something: A mobo-style 4-pin plug. So I went and found a 4-pin cable from the depths of my basement, plugged it in to my CD1 on my motherboard and voila, SOUND.

---

