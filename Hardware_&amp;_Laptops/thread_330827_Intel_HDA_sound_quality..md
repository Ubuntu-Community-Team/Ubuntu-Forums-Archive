---
title: "Intel HDA sound quality."
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by antek on 2007-01-03
Hi. I have a really strange problem.

I have intel hda sound chipset on my ASUS A3H-5012 laptop. Until today i didn't have any sound, but finally I managed to fix it. Well, maybe "fix" is not a good word for this, but here's what is happening.

Normally, the sound is working OK.
When I plug in the headphones to headphones jack, there is completely no sound.
When I plug in the headphones to mic-in jack, there is sound both on internal speakers and in one headphone (mono sound).
When I plug in the headphones to line-in jack, there is sound both on internal speakers and both headphones, the volume is OK, but the sound quality isn't good (it lacks bass).
So, the result is, i have 3 jacks, two of them that shouldn't work are working, and one that should work is not working.

On Windows everything is OK.

I can mute internal speakers, so there's only sound on headphones, but the quality is rather disturbing. I mean, it's not so bad, but comparing to Windows there should be more bass tones. I've tried some things like plugging in only halfway, I've tried few versions of ALSA: 1.0.14rc1 (the one I have now), unpatched 1.0.11 (afair the default on Ubuntu 6.10, or was it .10?), patched 1.0.9c from realtek's website. None of them could provide the sound through normal headphones jack. I've built a custom 2.6.19.1 kernel without ALSA.

Some sites are suggesting that after plugging in the headphones to headphone jack it's just a matter of unmuting the headphone jack channel, but the thing is, i don't have it in alsamixer. I tried to mute/unmute everything in probably most of the permutations (](*,)), no success.

Also, I heared about the model=XXX option when modprobing the snd-hda-intel driver, but it seems that it ignores what i write as an argument. I've tried to use a 'test' model, an nonexistant model (like 'dupa') and I don't see any complaints from driver on dmesg.

Here is the device (from lspci):
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

I am trying to fix this problem since a week or so, and i'm getting a little frustrated atm.

So what is so special about this chipset anyway? I can see a lot of threads on a lot of forums about Intel HDA's problems on Linux. 

Thanks for any help and sorry for my english. ;)

---

### Post by Lord Illidan on 2007-01-03
I got it working by appending this line to /etc/modprobe.d/alsa-base

options snd-hda-intel position_fix=1 model=3stack

---

### Post by antek on 2007-01-03
Man... it works. :)

Tho not with 3stack, but it gave me another slider in alsamixer (headphones), so I had a proof that model specified by 'options' declaration in modprobe.d dir works. Using the trial and error method I found 'z71v' model. The microphone is also working. 

Thanks a lot! :)

---

### Post by Lord Illidan on 2007-01-03
> **antek said:**
> Man... it works. :)

Tho not with 3stack, but it gave me another slider in alsamixer (headphones), so I had a proof that model specified by 'options' declaration in modprobe.d dir works. Using the trial and error method I found 'z71v' model. The microphone is also working. 

Thanks a lot! :)

You're welcome, and it depends on the model, as usual.

---

