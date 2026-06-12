---
title: "NO sound.  Intel, Realtek, ubuntu 10.4"
date: 2011-07-04
forum: Hardware
---

### Post by Peashooters on 2011-07-04
I am as new to Linux as I am to this problem.  I have no sound.  Now I have been all over these forums and I haven't been able to find a solution.

Now the funny thing is, my brother has the very same laptops and we both used the very same disk to install Ubuntu 10.4.  Everything is the same!  Yet he has sound and I do not.

The one thing I did differently was install Linux and windows side-by-side.  I am not quite ready to drop Windows.  I would have had it not been for this one problem.

I believe reinstalling Ubuntu might help.  I feel I should remove Ubuntu first but I don't want to format my entire hard drive.  I doubt this will work because I just tried running it live from the CD.  If anyone wants to try and help I am all ears. 

I found nothing muted.  Under Sound Preferences output is set to Internal audio analog Stereo.  That is my only option.  That's all I can think of that might be helpful.

     snd_hda_codec_realtek   203408  1 
snd_intel8x0           25652  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_hda_intel          22005  1 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  5 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  16 snd_hda_codec_realtek,snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_intel8x0,snd_hda_intel,snd_pcm

---

### Post by Peashooters on 2011-07-10
In my frustrations it seems I didn't leave very many possibilities open for anyone willing to to reply with words of hope and encouragement.  Even still the people of this forum were here to help.  

I discovered this post by saurabhshah.

[URL="http://ubuntuforums.org/showthread.php?t=1796021&highlight=sound+intel+laptop"]http://ubuntuforums.org/showthread.php?t=1796021&highlight=sound+intel+laptop
[/URL]
Here Mustegman posted this link.

[http://ubuntuforums.org/showthread.php?t=1744966](http://ubuntuforums.org/showthread.php?t=1744966)

And here psilogon posted the link that ended my search.

[http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html](http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html)

It told me to open a terminal.  I typed in what it said.  It opened a text file.  At the very end of the file I added that line.  Now no one noticed that I don't have the exact same codec.  Mine is around 863 I think.  This solution was for an 887.  But I tried it anyways and it worked fine.  I heard static through my speakers even when they were muted but I typed alsamixer into my terminal and muted the microphone and that fixed it.  Now my sound works perfectly.  I should also say I heard static with my ear phones but that was because the CD volume in the alsamixer was turned all the way up.  So it works great.  These forums were of great help.  I just had to find it myself.

---

