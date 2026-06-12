---
title: "[New INFO] No sound after resume from suspend."
date: 2008-05-08
forum: Hardware
---

### Post by worc on 2008-05-08
Hi people.

I know there are many threads in the forum talking about this. But I guess what I found today might be a little different.

Laptop: Toshiba Satellite P105 S9337
Sound Card: HDA INTEL (Conixant 20549)

Problem: 
No sound after resume from a suspend. All info shows the sound card is working properly except I can hear nothing (I've tried all solutions I can find, check alsamixer, edit /etc/modprobe.d/alsa-base, edit /etc/default/acpi-support...). It is interesting that I can get sound back if I in step give it another hibernate( NOT suspend). 
By saying everything shows the sound card is working properly, I mean I get no error when trying to play some sound, aplay/mplayer/audacious, the funny  part is that I can even see the waveform of the music that audacious is playing.

This is an old problem for me since the first time I use Ubuntu (6.10). It remains in 6.10 all the way along to the current 8.04.
I believed it was an alsa issue. 

Somehow, my earphone doesn't work in 8.04 (that's not true in 7.04 and 7.10), so I tried to downloaded and installed latest free OSS. Boom, earphone works perfect with OSS. Then, I tried a suspend. After resume, I lost my sound again. 
What? OSS performs the same as ALSA on the part? 
I tried to play some music in the shell with OSS's ossplay, it says something like "/dev/dsp: Input/output error". What? Does that mean the problem is actually not caused by the driver but the suspend action itself? Then I tried a couple of times to reproduce it and get the same result.

Here is my conclusion (but BASED ON GUESS, cause I'm just a user instead of a pro):
I tried years to fix the problem of losing sound after resume from suspend but all failed. There are so many solutions on the internet but none of them works for me. But, if the problem is not on the driver side, that all make sense to me.
What if something happend during suspend/resume and cause the sound card 'dead' but the system doesn't realize it?
I spend hours to check files in /etc/acpi but found nothing really suspicious.

That's really beyond my scope. If anyone is interested, please, you got someone to save.:)

---

### Post by skydog2004 on 2008-08-13
I have been using OSS on my laptop (Sony VGN-NR160E) for some time now and have been dealing with the sound problems when hibernating. My first crude "fix" was to stop all my sound applications then "sudo soundoff" before hibernating and then a "sudo soundon" after restoring. 

The problem with OSS is that it will not unload/stop unless all the processes that are using OSS devices are stopped/killed first. When you hibernate OSS does not go away properly, so the restore process brings OSS back in a "stupid" state and really isn't doing anything. If I tried to stop OSS with soundoff at this point it would give lots of errors trying to cleanup the mixer stuff. 

I have since come up with a second method, still crude but more convenient (sort of). It is a script that gets put in the /usr/lib/pm-utils/sleep.d directory that detects running processes that are using OSS, kills them and then stops OSS when going into hibernate. On restoring it starts OSS back up again. It would be better if it could restore all of the audio applications after restoring, but at least sound works after hibernating. 
I have not tried this with suspend yet...

As with all script files be careful...

---

### Post by Rianthas on 2008-09-16
Thanks for that script.

---

