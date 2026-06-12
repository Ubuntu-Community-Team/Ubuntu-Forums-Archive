---
title: "ubuntu 10.04.2 sound problem"
date: 2011-06-03
forum: Hardware
---

### Post by bunizz on 2011-06-03
Hello,

I have just installed ubuntu 10.04.2 LTS on HP G62-b16ST laptop. It plays audios but I cannot head the sound via the laptop's speaker. If I plug in a headphone, I can hear the sound.

I could heard while the version of ubuntu was 10.10.

Is this a kernel related problem? If I compile the newest version of the kernel, would it solve the problem? or cause new ones?

What do you suggest me ?

Thanks.

---

### Post by manfromthezoo on 2011-06-03
Hhhmm - there's things you can check before talking about kernel re-compilation, so it's worth starting with some basics first.

Open Sound Preferences (right click on the audio icon in the Gnome toolbar at the top). Check that everything is configured properly in there. Since you're able to hear audio from the headphone socket, it seems unlikely that the wrong audio device is selected, however.

It might worth launching alsamixer from a terminal, and checking that any appropriate channels are un-muted and the volumes cranked. I'm busy at the moment, so can get into any specifics but hopefully that'll send you down the right troubleshooting path (or someone else can jump in with some suggestions, too).

---

### Post by manfromthezoo on 2011-06-03
Also, I'm sure that ALSA versions changed between 10.04 and 10.10. This affected me when helping a friend troubleshoot a problem with no sound over HDMI.

It may be relevant to you if, for instance, you're using an audio chipset that isn't placing nicely with the older version of ALSA (I want to say it's version 1.21 in 10.04 but cannot check at the moment). I overcame his sound problems by installing 1.23.

There's a guide here:

[COLOR="Blue"][http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")[/COLOR]

I'm not sure if this is relevant to your problem, so please research some more first / listen to others input - it would also be good if you could list what audio hardware you have.

Good luck!

---

### Post by lidex on 2011-06-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

