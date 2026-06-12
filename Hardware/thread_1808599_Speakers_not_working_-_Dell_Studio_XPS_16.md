---
title: "Speakers not working - Dell Studio XPS 16"
date: 2011-07-20
forum: Hardware
---

### Post by Nagl on 2011-07-20
I am having some trouble getting audio to come out of my speakers. Audio works fine if I am listening to it through my headphones. 

I am running Ubuntu 11.04 64bit. Any help would be deeply appreciated and if you need more information just ask. Thank you very much!

P.S. I went through countless posts trying to find a solution before I created this one.

---

### Post by Nagl on 2011-07-21
Any help? Please? :confused:

---

### Post by Kannokki on 2011-07-21
First, the basics. Make sure nothing is muted in the mixer. 
You might want to add &#8220;options snd-hda-intel model=dell-m6 enable_msi=1&#8221; to the end of *"/etc/modprobe.d/alsa-base.conf"*

---

### Post by Nagl on 2011-07-21
lol it isn't muted I already checked that lol, I will try adding that it the bottom of my confg now.

Edit: It still doesn't work.

---

### Post by Kannokki on 2011-07-21
Try installing the following packages: *linux-backports-module* and *linux-backports-module-alsa*. Install them using 

```
sudo apt-get install linux-backports-module linux-backports-module-alsa
```

There is also a hardware switch on the Dell Studio XPS 16, that disables the speakers when headphones are plugged in. This may cause problems if the switch is broken.

I believe this can be fixed by changing the *"options snd-hda-intel model=dell-m6 enable_msi=1"* to *"options snd-hda-intel model=dell-m6 **no-jd**"* (no-jd standing for no jack-detection)

I'm propably not the best tech-support there is, I found all these with a little googling.

I suggest reading [[COLOR="Red"]this[/COLOR]]("http://www.linlap.com/wiki/dell+studio+xps+16") page and searching all speaker-related posts there.

---

