---
title: "Sound automatically muting whenever I stream a video from YouTube or other websites"
date: 2009-11-13
forum: Hardware
---

### Post by zhongguohua88 on 2009-11-13
Ubuntu has been doing this for a few weeks now. I always have to press the mute button every time I open a flash button because it automatically mutes my computer. Is there any way to fix this? I have an HP EliteBook 8530w and I run the 32 bits Ubuntu 9.10

---

### Post by zip_000 on 2009-11-13
I've been using 9.10 for a couple of weeks, and I keep getting random muting as well.

Also, frustratingly, none of the standard mute options seemed to actually unmute it - I had to install alsa mixer in order to unmute it.

At first I thought my kid was doing it since there is a mute button on the keyboard, but after watching closely for a few days I know it isn't that - it just happens fairly randomly from what I can tell.

---

### Post by zhongguohua88 on 2009-11-14
I also thought it was random but then noticed that it always happen when a flash video (e.g. YouTube) is starting. The mute button works for me luckily but it gets annoying to press it every times I watch a video because I spend a lot of time on YouTube.

---

### Post by zhongguohua88 on 2009-11-30
It stopped muting whenever I watch YouTube videos but now it automatically mutes whenever I try to hear an mp3...

---

### Post by josteinaj on 2009-12-22
I've got the same problem: random muting with no apparent cause. But when it happens, it usually coincides with a sound playing.

I tried youtube, mp3 and avi now without anything happening. If I can help with some debug-output the next time it happes, I'll be happy to help.

9.04 was fine, 9.10 brought problems.

---

### Post by josteinaj on 2009-12-22
It just muted itself. I believe these are the relevant log-entries. I unmuted the sound before checking the logs.

**messages**
```

Dec 23 00:31:53 josteinlappis pulseaudio[10579]: pid.c: Stale PID file, overwriting.
Dec 23 00:34:04 josteinlappis pulseaudio[10579]: ratelimit.c: 109 events suppressed

```

**syslog**
```

Dec 23 00:33:02 josteinlappis pulseaudio[10579]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Dec 23 00:33:02 josteinlappis pulseaudio[10579]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Dec 23 00:33:02 josteinlappis pulseaudio[10579]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Dec 23 00:34:04 josteinlappis pulseaudio[10579]: ratelimit.c: 109 events suppressed

```

**user.log**
```

Dec 23 00:31:53 josteinlappis pulseaudio[10579]: pid.c: Stale PID file, overwriting.
Dec 23 00:33:02 josteinlappis pulseaudio[10579]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Dec 23 00:33:02 josteinlappis pulseaudio[10579]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Dec 23 00:33:02 josteinlappis pulseaudio[10579]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Dec 23 00:34:04 josteinlappis pulseaudio[10579]: ratelimit.c: 109 events suppressed

```

The number of events suppressed by ratelimit.c varies from 1 to at least 170.

During bootup, **dmesg** mentions ratelimit as well:
```

[   18.734458] __ratelimit: 9 callbacks suppressed

```

So it seems to be a problem with snd_hda_intel. Do you guys use that driver? Or at least know if it's a intel sound card?

---

### Post by josteinaj on 2009-12-22
I have a button on my laptop which lets me mute and unmute. It has a red/green light which shows that it reacts to my clicks. The problem as previously described is that this hardware-mute gets randomly muted.

I haven't noticed before, but this button doesn't seem to affect the mute-button in Ubuntu itself. I can mute Ubuntu 9.10 and my laptop hardware independently. Even more evidence that this is a driver issue...

---

### Post by nmcgrew on 2010-01-25
Mine does this as well.  Upon start up.  I know to check my sound controls now to confirm that it isn't muted daily... what a pain in the ****.  I should be able to rely on my settings that they stuck but they don't always.  It is random and somedays it isn't muted whereas others it is.  These are the kinds of bugs that make our Ubuntu not efficient or professional.  They really need to be addressed and fixed permanently without all this terminal coding or software additions.  Something like this should just be a given that it works.  Period.

---

### Post by sfennell on 2010-03-17
> **josteinaj said:**
> 
So it seems to be a problem with snd_hda_intel. Do you guys use that driver? Or at least know if it's a intel sound card?

Mine mutes about 10-20 seconds into an mp3 song and I do have an intel onboard sound card in my dell laptop.  Ubuntu 9.10.

---

