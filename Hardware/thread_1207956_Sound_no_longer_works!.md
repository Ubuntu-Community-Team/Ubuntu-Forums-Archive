---
title: "Sound no longer works!"
date: 2009-07-08
forum: Hardware
---

### Post by Iteria on 2009-07-08
I'm currently running Xubuntu 9.04. Up until recently the sound on my desktop worked. I checked the jack that the speaker was using with some headphones to make sure that the speaker didn't just die and I couldn't hear anything. I don't know what happened. 

I don't really know what caused it or when it happened exactly. I know it happened within the last 24 hours and the only things I installed in that time was conky favors, gparted and unetbootin. I also reinstalled wine, which was acting weird after an update. I don't really think that those are the problem, though. I figureif they were other things besides the sound would be broken too.

I did have a bad shutdown today. Xubuntu was taking so long to shutdown that I had to force the computer to turn off. That seems more likely, but I don't know what caused that either, so... yeah...

If anyone could help me. It'd be much appreciated.

---

### Post by shatterblast on 2009-07-09
I think a recent compatibility issue has occurred with Creative sound cards.  If this applies to you, it might be good to install the following from the Karmic test version to see if it helps:

[http://packages.ubuntu.com/karmic/alsa-base](http://packages.ubuntu.com/karmic/alsa-base)
[http://packages.ubuntu.com/karmic/alsa-firmware-loaders](http://packages.ubuntu.com/karmic/alsa-firmware-loaders)
[http://packages.ubuntu.com/karmic/alsa-source](http://packages.ubuntu.com/karmic/alsa-source)

Also if you're able to confirm your sound card as a Creative type, then there is apparently a setting in "/etc/modprobe.d/alsa-base.save" that may need double-checking.  A line in that file may possibly have a continuous run-on setting such as:

options snd-hda-intel model=XXXXXXoptions snd-hda-intel model=XXXXXXoptions snd-hda-intel model=XXXXXX
(The X's represent the model of your card's hardware driver.)

It should instead read something like:

options snd-hda-intel model=XXXXXX

Please make sure of your sound card maker before attempting any steps.

---

### Post by kerry_s on 2009-07-09
try removing pulseadio.

---

### Post by Iteria on 2009-07-09
Pulseaudio wasn't installed when I went to uninstall it. Also, I don't think my soundcard is from creative this is what I got from lshw:

```

 description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0


```

Any other suggestions?

---

### Post by shatterblast on 2009-07-09
I recommend installing the following links anyway:

[http://packages.ubuntu.com/karmic/alsa-base](http://packages.ubuntu.com/karmic/alsa-base)
[http://packages.ubuntu.com/karmic/alsa-firmware-loaders](http://packages.ubuntu.com/karmic/alsa-firmware-loaders)
[http://packages.ubuntu.com/karmic/alsa-source](http://packages.ubuntu.com/karmic/alsa-source)

That should replace the non-GUI sound part of your operating system.  As a temporary solution, you could also try switching everything from ALSA to OSS in the Sound window under Preferences.  I would recommend the "sudo apt-get install --reinstall" way, but it doesn't appear to function with those three.

---

### Post by Iteria on 2009-07-10
Tried using OSS. That failed. I tried reinstalling the alsa packages via synaptic. Also failed.

Any other takers?

---

### Post by kerry_s on 2009-07-10
i would try uninstalling all the sound parts, delete all the sound settings in your home folder, reboot to make sure there all unloaded, then do a fresh install of alsa-base alsa-utils & reboot.

---

### Post by Iteria on 2009-07-10
Success! 

I didn't know how to remove everything specifically, so I reinstalled. I keep my home folder on a different partition than everything else, so after the reinstall everything booted up the exact same--with the exception of gnome-do and conky, which I'll have to reinstall, but at least they will auto-configure themselves this time. 

After all the updates, I played a music file and my speakers are working just fine.

---

### Post by Iteria on 2009-07-10
I take that back... After I rebooted (And, I guess, the updates kicked in), My sound died again.

Is there a way for me to know updated I installed and roll them back one a time, so I can see what's causing this?

---

### Post by kerry_s on 2009-07-11
are you sure it's not like muted?
try running **alsamixer** in terminal, crank all the bars up, make sure there's no "MM" if so press "m" to unmute them.

check /etc/group make sure your user name is in the sound group.

---

### Post by Iteria on 2009-07-11
:oops: It was muted... Weird because I used mixer (which I assume is different from alsamixer) to check if it was muted before and everything was fine. Oh well, I'll just have to alsamixer to my linux knowledge.

Thanks!

As a side note: why is ANYTHING muting the sound without telling?

---

### Post by kerry_s on 2009-07-11
yeah, weird. does it stay after a reboot or mute again.

if so you can add> **amixer set Master 75% unmute**
to ~/.profile to get it unmuted & set it to 75% for comfort at every start.

---

### Post by Iteria on 2009-07-11
I rebooted and the sound stayed just the same. I guess it was a fluke? Still, I wonder what caused it.

---

### Post by shatterblast on 2009-07-11
If you feel secure repeating the process, you could "Lock Version" on your ALSA items in Synaptic.  However, I don't encourage it.

---

