---
title: "dv2000 sound"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by nihalz on 2007-07-09
can anyone explain me why the sound on my dv2310 laptop works right out of the box with ubuntu 6.10 but not with 7.04?
is there any easy way to make the sound work on 7.04?
i have a conexant video card
thanks a lot!

---

### Post by camini on 2007-07-10
This will not really help, but at least I share your pain :)

When my dv2000 (dv2386ea) starts up, I get the Ubnuntu 'tribal' log on sounds, and then, when started, no sound in any application..
Maybe it's merely a question of choosing the correct output device in the preferences - I will try that.

---

### Post by matheuu on 2007-07-10
Hey Guys,
You should sign onto Launchpad and let the dev guys(and girls) know about this so they can make Ubuntu better.... It might be a simple fix.

---

### Post by camini on 2007-07-10
I'd be glad to.. what is the launchpad?

---

### Post by nihalz on 2007-07-11
well i dont hear the log on sounds at all
all i hear is myself making the logon sound and pretend that its not me thats making the sound but ubuntu!
and yea what is launchpad?

---

### Post by aschmack on 2007-07-11
I have a dv2125nr laptop(same sound card) and I don't get any sound either.

---

### Post by zakirs on 2007-07-12
same problem here  dv3239 :( could some body help

---

### Post by oootheoneooo on 2007-07-24
Have you guys checked the volume controller of your Ubuntu System? Could it be that your speaker/headphone is muted for some of you. Try checking the volume controller to see if this might be causing the problem. Also, try installing the multimedia codecs to listen to mp3's by downloading Automatix.

[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")


Another thing you might want to try is installing the latest stable version of alsa drivers (alsa vers. 1.0.14)... it worked for me! Special thanks to lexarrow.
 
[http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000]("http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000")

---

### Post by audentis on 2007-09-05
After messing around compiling various alsa drivers and editing config files on my dv2000, I think the actual issue for me was that my "PCM-2" track was muted (it didn't show up in the volume control by default, only "PCM" did).  To check to see if that's the case, open up the volume control, then Edit -> Preferences, checkmark all the boxes, and *then* go back and make sure nothing is muted.

---

