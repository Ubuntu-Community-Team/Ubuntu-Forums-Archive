---
title: "Out of options for fixing sound - one last try"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by Corlian on 2005-08-19
One more try to fix my sound before I have to go back to XP until Breezy:

I have a Sound Blaster Live! 24-bit under Kubuntu, which works fine under XP.  At first the sound system wouldn't start.

I've followed all three of these guides, in this order:

[http://ubuntuforums.org/showthread.php?t=19307&highlight=live+24+bit](http://ubuntuforums.org/showthread.php?t=19307&highlight=live+24+bit)
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)
[http://ubuntuforums.org/showthread.php?t=21211&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=21211&page=1&pp=10) (substituting emu10k1 with ca0106)

Now the sound system starts, files and CDs play within their programs, and system sounds seem to exist (never had Linux before so I can't tell where to expect bells and dings), but no sound comes out of the speakers.

I checked alsamixer and the bars are all around halfway up.  The volume bars are up in KMix.

Is there anything else I can do?  Is there anything I missed?  Is there anything I shouldn't have done?

Here is my current lsmod|grep snd:

> snd_ca0106             26532  1
snd_ac97_codec         67320  1 snd_ca0106
snd_pcm_oss            55712  0
snd_pcm                91016  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24580  1 snd_pcm
snd_page_alloc         10116  2 snd_ca0106,snd_pcm
snd_mixer_oss          18048  1 snd_pcm_oss
snd                    59780  8 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  1 snd

If anyone can...please help!

---

### Post by EnderTheThird on 2005-08-19
Run alsamixer again, and make sure that nothing is muted or turned off.  Press "m" while highlighting a setting to mute/unmute/turn it on/turn it off.  Make sure you check EVERY setting.  My sound wasn't working for a while, and I think I overlooked the correct setting 4 or 5 times (that or it wasn't there until I installed some of the packages that the other HOWTO's told me to).  Also make sure that you try rebooting after that, and if you test the sound with a media player, that it's set to output via ALSA (not OSS or something else).  Good luck.  If that doesn't work, then hopefully someone who knows more than me (there are plenty here) can help you out.

---

### Post by Corlian on 2005-08-20
Well, it didn't work, and I the one step I thought I may have messed up I went back and did again.

The only suspicious thing is that there's one bar (SPDIF Out) in the alsamixer that just reads "00" and won't go up, but will switch to "MM" if I press M.  Also, all the other bars are high in volume, but none of them will mute if I press M.

Does that make sense to anyone?

---

### Post by woedend on 2005-08-20
[QUOTE=Corlian]Well, it didn't work, and I the one step I thought I may have messed up I went back and did again.

The only suspicious thing is that there's one bar (SPDIF Out) in the alsamixer that just reads "00" and won't go up, but will switch to "MM" if I press M.  Also, all the other bars are high in volume, but none of them will mute if I press M.

Does that make sense to anyone?[/QUOTE]
 if you have the digital/analog option, make sure that one is muted.

---

### Post by Corlian on 2005-08-22
For posterity's sake, this is how my situation resolved:

I don't know what I did wrong the first time or right the second time, but I reformatted and reinstalled, and *only* followed the instructions from the first link I listed above.  Then I raised the volume on one of the mixer bars and everything was great.

This second time, the mixer bars were all at 0, but my first time through when I followed the instructions from all three of the threads I listed above, the mixer bars were preset at a certain level (yet no sound came out).

Another oddity (or perhaps not...I'm still oblivious) is that *only* OSS works, ALSA gives me the skipping and popping.  OSS seems to work perfectly.

Now everything soundwise seems to work, as long as whatever CD player I'm using gets the audio digitally (why doesn't analog work?).  My only complaints are that audio doesn't sound as "full" as in Windows, and the volume control on XMMS doesn't do anything.  Any suggestions about either of those?

---

