---
title: "Some sound lag problems"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by Ricapar on 2005-07-13
When I open some games, I will often get this message:
```
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
```
The sound will still work, but it will be behind what is going on by about 2-3 seconds.

In alsamixergui, it said this for my sound card:[indent]Card: VIA 82C686A/B rev50
Chip: Cirrus Logic CS4299 rev 4
[/indent]Any one have any ideas what is causing this and/or how to fix it?

---

### Post by BigCdaAnswer3 on 2005-07-13
[QUOTE=Ricapar]When I open some games, I will often get this message:
```
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
```
The sound will still work, but it will be behind what is going on by about 2-3 seconds.

In alsamixergui, it said this for my sound card:[indent]Card: VIA 82C686A/B rev50
Chip: Cirrus Logic CS4299 rev 4
[/indent]Any one have any ideas what is causing this and/or how to fix it?[/QUOTE]

trying doing a:

pkill esd

see if that helps

---

### Post by Ricapar on 2005-07-13
Nope =(

I've tried "killall esd", "pkill esd", no luck. When I do "killall esd", it says: "esd: no process killed".

---

### Post by varunus on 2005-07-13
Can you post your ~/.asoundrc or your /etc/asound.conf (whichever one you have)?  Delay problems can usually be fixed by tweaking these files.

---

### Post by Ricapar on 2005-07-14
/etc/asound.conf:
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

---

### Post by varunus on 2005-07-14
Reduce period_size to 1024 and buffer_size to 4096.  Then type "sudo /etc/init.d/alsa restart" in a console.  This will reduce the delay, but may make scratchy sound.  If your sound is scratchy, slowly raise each value and restart alsa again until you find the right balance.  I'm using an onboard intel 8x0 card (not exactly the best sound card) and those values produce perfect sound with no delays.

Good luck.

---

### Post by Ricapar on 2005-07-14
I did that, sound didn't become scratchy, but the delay and that little message was still there.

---

### Post by varunus on 2005-07-14
Hmm...do you only have lag in games?  Which games are those?  Do they happen to use OSS?  If so, there's something you could try adding to your asound.conf...

Add this to the end:
```

pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

```
and then restart ALSA.

Does that work?

---

### Post by Ricapar on 2005-07-15
Going to give that a try. The games I've gotten those thigns with was Quake2, ZSNES(any rom), and a few others I can't remember off the top of my head =(

update: Nope, same message, same lag ](*,)

---

### Post by varunus on 2005-07-15
Hm...I did a little searching, and read on the ZSNES forums that it uses SDL for audio output.  (I'm not sure about quake.)  Do you have the ALSA version of SDL installed?  Check synaptic...If you don't it might be trying to play through ESD, which can have lag.

---

### Post by Ricapar on 2005-07-18
[QUOTE=varunus]Hm...I did a little searching, and read on the ZSNES forums that it uses SDL for audio output.  (I'm not sure about quake.)  Do you have the ALSA version of SDL installed?  Check synaptic...If you don't it might be trying to play through ESD, which can have lag.[/QUOTE]
 I searched through Synaptic. Searched for ALSA, and didn't find any packages that related to SDL. Searched for SDL, and didn't find any packages that related to ALSA.

---

### Post by varunus on 2005-07-19
Really?  I have libsdl1.2debian-alsa listed in synaptic.  Do you have universe enabled in your repositories?

---

### Post by Ricapar on 2005-07-24
Strange. That one didn't show up when I searched for alsa and sdl, but it's there. Anyways, I installed it, it said that it would remove "libsdl1.2debian-all". I let it, and went to try quake2. It worked. Went to try ZSNES, and there was no sound at all. It would give me "Sound init failed" right after the error mentioned on the first post of this topic. I went back to try Quake2, and I got the same thing with a slightly wording, but still no sound. I tried again, this time it worked, but with the lag back. Went back to ZSNES, no sound.

I reinstalled libsdl1.2debian-all, sound in ZSNES and Quake2 was back, but with the same lag.

This is driving me crazy >_<

---

### Post by Ricapar on 2005-08-01
I also noticed that it only happens somtimes. For example, with ZSNES: I'll open it and get that error, I close it, open it again, get the error. if I repeat enough times, it will open **without** the error.

Any ideas?

---

### Post by Nihilist on 2005-08-02
im on xandros 2.0 currently.

but are you using a binary for zsnes? you can get it from zophar.net and other places, and ive never ran into trouble with it that way.

---

