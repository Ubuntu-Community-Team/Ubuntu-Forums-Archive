---
title: "sound gone within gnome"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by lee_connell on 2005-08-10
sound is not working within gnome.  alsa recognizes the card and i can run speaker-test and it works.

I can't load the volume control cause it says no device.

what can i do to troubleshoot the issue?

NOTE: i hear the ubuntu sound right when the GDM login loads up and if i log out and get to the GDM login.  anytime after that i got no sound and volume control doesn't load in the panel etc...

my sound modules are all loaded:

snd_intel8x0           32352  0
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm

---

### Post by lee_connell on 2005-08-12
Can someone please give me some kind of direction on this, i really rely on sound for music and i can't use it, i have no clue what to do as alsa seems to be working fine, just not working in gnome.

I don't want to reinstall my os for this!

---

### Post by olivierp on 2005-08-12
[QUOTE=lee_connell]Can someone please give me some kind of direction on this, i really rely on sound for music and i can't use it, i have no clue what to do as alsa seems to be working fine, just not working in gnome.

I don't want to reinstall my os for this![/QUOTE]

Check your "Default Audio Sink" in gstreamer-properties & have you disabled Gnome's system event sounds (Enable sound daemon on startup) ?
I have had problems when esd (the sound daemon) is not loaded, in conjunction with having the default audio sink set to "autodetect".

---

### Post by lee_connell on 2005-08-12
Yes sound events are all on.  Even when i go to play mp3 file with rhythmbox it says no device available.

i've tried the gstreamer-properties and none of the options work, they all say failed to construct test pipeline.

I can't load volume-controls either... what do you think?  Can i reinstall some things to get it back?

---

### Post by lee_connell on 2005-08-12
Figured out the most of it.  A couple days ago something wierd happened.  Some reason I was removed from sudoers.  I had to login as root and put myself back in and everything worked again.  However this is what caused the sound not to work anymore.  

i dont have permissions to /dev/dsp, /dev/hdc anymore.  No burning cd's and no playing music.  So whatever happened with my sudoers caused other permission issues.  

I gave myself permissions to those devices and sound plays now and cd's burn, however I still can't load the volume-control applet or application.  says no elements found.  

NOTE: logging into X as ROOT does load the applet.

Anyone help me on getting this to work again?

Thanks!!

---

### Post by lee_connell on 2005-08-12
just had to add myself to audio and cdrom groups and everything is now fine :)

---

### Post by jaysee on 2005-08-13
[QUOTE=lee_connell]just had to add myself to audio and cdrom groups and everything is now fine :)[/QUOTE]
 Is that just through fstab? I'm having the same/similar problem and if you could help me fix it that would be great.

---

