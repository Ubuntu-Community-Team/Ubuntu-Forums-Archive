---
title: "Sound plays through speakers all the time, even after headphones are plugged in"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by smartboyathome on 2008-03-02
I have an emachines d5239 (don't know the sound card, sorry :(), and the sound always plays through the speakers, even with headphones plugged in. I think this may be a driver problem, since it works fine in Vista. All help is appreciated, thanks. :)

---

### Post by jeffus_il on 2008-03-02
Have you opened a mixer like alsamixergui and played with the different output volume sliders?

---

### Post by smartboyathome on 2008-03-02
> **jeffus_il said:**
> Have you opened a mixer like alsamixergui and played with the different output volume sliders?

Just did, and it had no effect. I think my headphones are detected as the same speaker as the monitor's.

---

### Post by jeffus_il on 2008-03-02
Does the monitor have a headphone output?

---

### Post by smartboyathome on 2008-03-02
> **jeffus_il said:**
> Does the monitor have a headphone output?

No, my desktop does. My monitor plugs in to the back of my computer, while my headphones plug into the front.

---

### Post by jeffus_il on 2008-03-02
OK, a speaker socket would have automatically switched them off, bad luck!

---

### Post by Omnios on 2008-03-02
Not shure on this set up as in if they are hard plugged together.
 
 I found a trick a long time ago where I used the sound config and has two sound controlls on the pannel one was set for the main sound and the other was set to the plug in spearerets.
 
 My use was a bit different as one slider was for the computer volume and the other for a tc-tuner card.

---

### Post by smartboyathome on 2008-03-02
Ok, I got my soundcard from the GNOME ALSA tool, it is a Realtek ALC662 rev1.

I don't get two "panels", I only get separate sliders, and all are turned off except for the PCM and Front.

---

### Post by smartboyathome on 2008-03-02
I just researched my soundcard, seems like I am out of luck until hardy because I need newer alsa drivers. :(

---

### Post by Omnios on 2008-03-02
K the thing about the panel sliders. I added two seperate sound panel controls andused the propertiesto set them so they set the volume for different uses. One for the main sound and the other set up to controll the microphone. My vid card has a speaker plug that goes from the tv-card to the mic.

---

### Post by jeffus_il on 2008-03-02
> **smartboyathome said:**
> I just researched my soundcard, seems like I am out of luck until hardy because I need newer alsa drivers. :(

You could install the driver easily if you find it as a .deb (debian) package, and you could also build it from source (not so bad as it sounds)

---

### Post by smartboyathome on 2008-03-02
> **jeffus_il said:**
> You could install the driver easily if you find it as a .deb (debian) package, and you could also build it from source (not so bad as it sounds)

I'd rather wait for hardy, I can manage without headphones on here for a month anyway. Thanks for the help though. :D

---

### Post by jeffus_il on 2008-03-02
Sounds sensible, you could also unplug the speakers when you use headphones...

---

