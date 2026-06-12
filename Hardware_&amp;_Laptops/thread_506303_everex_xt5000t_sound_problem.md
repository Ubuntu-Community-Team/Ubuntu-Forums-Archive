---
title: "everex xt5000t sound problem"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by zergling on 2007-07-21
Hi, I am having problem with my everex xt5000t with  Ubuntu feisty 7.04.
The problem is that I am not able to hear any sound though the laptop's speakers but if I connect my headphone to the audio card output (the green connector) the sound works...
What should I do?
The sound chipset is Realtek  ALC885
Sorry my English :(

---

### Post by Ruthsarian on 2007-08-03
I've got the same laptop and was having the same problem. Here's what worked for me.

Check out this page: [HDA Intel Sound HowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto") I followed the instructions on that page to get the latest version of ALSA (1.0.14) installed on my machine. This step is not necessary as the instructions listed below work with the current ALSA package available through Ubuntu repositories.

I then opened up the /etc/modprobe.d/alsa-base file (as directed to on that page) and added the following line to the bottom of the file:

```
options snd-hda-intel model=3stack-dig
```

Once that was done I rebooted. I now had sound coming out of both the speakers and the headphone jack. However there were some oddities in how the ALSA mixer identifies the various components. 

First make sure you're using the ALSA mixer and not the OSS mixer. Do this, if you're using the volume control application in Gnome, by opening up the FILE menu and select CHANGE DEVICE -> HDA NVidia (Alsa mixer).

Next you need to make all the channels visible in the mixer. Do this by selecting PREFERENCES under the EDIT menu and checking off every track listed.

Now set the FRONT, CENTER, and LFE channels to 100% volume. These three channels control the speakers for the laptop. Your headphone jack is controlled by the SURROUND channel, put this to 100% as well.

You should now control your audio output level through ONLY THE PCM channel. Leave the others that I described above at 100%.

Note that the dial to control the volume next to the headphone jack won't work.

Hope that helps.

---

### Post by duphenix on 2007-08-05
Thanks for this post, now everything works on my laptop.

---

### Post by Techman010 on 2007-08-08
Ruthsarian: Thanks a lot.  It worked perfectly...

but I had one more question.  When I lower the volume in the gnome panel at the top of the screen it seems to only lower one speaker.  Anyway to change this?

---

### Post by zergling on 2007-10-14
Thank you a lot my friend :)
Finally I can use my laptop's speakers :guitar:
Ciao !

---

### Post by LetterRip on 2007-12-29
> **Techman010 said:**
> Ruthsarian: Thanks a lot.  It worked perfectly...

but I had one more question.  When I lower the volume in the gnome panel at the top of the screen it seems to only lower one speaker.  Anyway to change this?

Right click on the volume icon, go to preferences, and change it to PCM.

LetterRip

---

### Post by nytel on 2008-03-06
Thanks! It worked but it's not using the full potential power. It sounds like an old FM radio. Any clues?

---

### Post by Techman010 on 2008-03-06
nytel: Have you tried opening up the volume panel and moving all of them up?> Now set the FRONT, CENTER, and LFE channels to 100% volume. These three channels control the speakers for the laptop. Your headphone jack is controlled by the SURROUND channel, put this to 100% as well. 

Ubuntu sets it as three different speakers.  If all of them are at or near the same level, it should sound fine.

LetterRip: Sorry for the very late response, that worked fine though... thanks!

---

### Post by crakowski on 2008-05-16
> **nytel said:**
> Thanks! It worked but it's not using the full potential power. It sounds like an old FM radio. Any clues?

I just had the same problem.  Wouldn't have noticed it if I didn't already know the speakers sounded good in my last OS.

Appears that Center and LFE came up muted by default even though the sliders are at 100% (you'll see a red X over the speaker underneath the slider.)  Make sure you click on the red X to un-mute them.

Ecstasy of Gold is a fun mp3 to test this with, btw.  :)

---

