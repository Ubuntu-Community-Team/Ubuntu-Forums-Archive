---
title: "solution for no sound on suspend/resume for toshiba"
date: 2008-10-02
forum: Hardware
---

### Post by kazzmir on 2008-10-02
I just wanted to report on a solution I found for making sound work on resume after suspend on my Toshiba Satellite A215-S474 satellite.

The solution is to add the following line to /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=toshiba

```

If that does not work, forcibally reloading the alsa modules always fixes it, although sometimes I had to do it twice in a row.
```

$ sudo /sbin/alsa force-reload

```

Other methods of force reloading alsa did not work for me, things like killing all programs that currently use alsa, modprobe -r snd_hda_intel && modprobe snd_hda_intel. I also thought /etc/init.d/alsa-utils force-reload would help but it did not.

---

### Post by geomac on 2008-10-02
Hello i have a similar problem in my s1900-303. The thing is, i have no sound. Can you help!? Thanks.

---

### Post by kazzmir on 2008-10-02
Did you try the force reload modules solution?
```

sudo /sbin/alsa force-reload

```

Otherwise you probably have to find the right module to reload in /etc/modules.d/alsa-base. Do you have snd_hda_intel loaded? You can find out with
```

$ lsmod | grep snd

```
And search for snd_hda_intel. This page, [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), says to add the 'option snd-hda-intel model=XXX' line to alsa-base and to find your model look at linux/Documentation/sound/alsa/ALSA-Configuration.txt. I looked through that file but I don't know which model to pick, I just tried 'toshiba' because my laptop is a toshiba :p.

Is s1900-303 also made by toshiba? Have you tried my solution?

---

### Post by nemesis_haven on 2008-10-07
Thank you!

I'm running 8.10 beta on a Toshiba Protege m700 and my sound was totally non-existent from the get-go. A bunch of moderately to very-complicated fixes did jack. Your fix has got everything running smoothly, even automatically turning off the speakers when I plug in headphones (as it darn well should).

---

### Post by bear24rw on 2009-03-15
> **kazzmir said:**
> 
The solution is to add the following line to /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=toshiba

```


Thanks I was having trouble getting sounds to work on my 700m but that worked perfectly.

---

### Post by enigmatichus on 2010-11-18
Hello, it's a lot of time I have the no audio after suspend-to-ram problem, I have a almost-4-years-old toshiba satellite P100-120 (intel core 2 duo T5500, nvidia geforce 6800 go, intel hda sound) and I used a few releases. Now even with maverick merkaat (32 bit) the issue persists. I tried almost EVERYTHING such as adding "options snd-hda-intel model=toshiba" or "model=3stack", restarting both pulseaudio (which I HATE) and alsa with the proper scripts, but no ways, after resuming the system I have no sound at all. The strange thing is that I have a sound blaster audigy 2 zs for notebook (pcmcia) and that this sound card works even after resuming (of course I have to use earphones or external monitors to listen). Has anyone a possible solution? Thank you very much!

---

