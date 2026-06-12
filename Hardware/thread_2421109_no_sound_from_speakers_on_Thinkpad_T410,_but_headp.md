---
title: "no sound from speakers on Thinkpad T410, but headphones work fine"
date: 2019-06-16
forum: Hardware
---

### Post by thejim on 2019-06-16
I installed Ubuntu 19.04 a couple of weeks ago on my Lenovo ThinkPad T410 and everything seemed fine.  Today I learned of ElectronPlayer and installed it.  I then went to the YouTube section and tried to play a video.  I heard about a second of an ads audio then no audio.  I tried going into system settings and adjusting volume and testing audio, Only occasionally I would get a second of audio then no audio at all. 
I've tried the following:
sudo alsa force-reload
reboot
reinstalling Alsa and Pulse audio and force reload alsa, then I did the test feature in settings and it worked when I clicked the right speaker then wouldn't work again after that.
tried alsamixer and it shows audio levels good.

any ideas how to get audio working through speakers?

thanks!

---

### Post by thejim on 2019-06-16
p.s.  just tried  mv ~/.config/pulse ~/.config/old_pulse and rebooting but still no sound.
also, I rebooted to Windows 7 and audio works fine there.

---

### Post by tea for one on 2019-06-17
Sound is a tricky one to troubleshoot.

However, you mentioned that you had sound after original installation but it gave problems after adding Electronplayer.

I would boot up a **live** session of Ubuntu to see if your sound returns.

---

### Post by thejim on 2019-06-17
Actually I never tested sound until I installed electronplayer. I just upgraded my HDD&#8217;s to a SSID and am in the process of installing everything. When I get Ubuntu installed I&#8217;ll test sound again

---

### Post by thejim on 2019-06-17
I've got Windows 7 reinstalled after upgrading to an ssd and I tested sound and system sounds play fine, but when I play a youtube video or music from pandora, it plays a few seconds and then no audio.  So I'm thinking it's a hardware problem, not an OS problem.  It's a used T410 I bought online so I guess you get what you paid for.  Will install Ubuntu once windows updates are installed and then test there but I suspect the same issue.

---

### Post by thejim on 2019-06-17
just found this out from a youtube video with someone with same issue.  If I press down around the area of the physical volume control buttons, then sound will come back.  What a pain!

---

### Post by tea for one on 2019-06-18
> **thejim said:**
> just found this out from a youtube video with someone with same issue.  If I press down around the area of the physical volume control buttons, then sound will come back.  What a pain!

Agreed, a complete pain.

As I now understand, your sound problem only appeared with your internal speakers when playing a source from the internet?

Out of curiosity, do you have headphone and speaker sound when playing some music from your internal drive?

Thanks for also mentioning that it was a pre-owned machine, because these little bits of detail are often important.

A few years ago, there was a thread about lack of sound and it transpired that the OP did not have any speakers.

Finally, if your sound hardware is a bit inconsistent in the future, you could purchase a cheap and cheerful USB sound card.

---

