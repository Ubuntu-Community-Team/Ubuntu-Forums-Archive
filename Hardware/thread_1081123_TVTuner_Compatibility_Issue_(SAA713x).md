---
title: "TVTuner Compatibility Issue (SAA713x)"
date: 2009-02-26
forum: Hardware
---

### Post by davidbilla on 2009-02-26
I recently bought a tuner card locally, that has a saa7130 philips chip onboard. When I boot up the system with the card in place, Hardy detects the card and loads the saa7134 and saa7134-alsa modules. Some wikis I found over the web say that I have to insert the line
```

options saa7134 card=xx tuner=yy
```

along with some other such lines in '/etc/modprobe.d/options'. Now, the tuner card is Chinese(Earlier I had said it was from India, but no; it's 'made in CHINA'!). They use the SAA7130 Philips chip (for which I found the tuner no. 'yy', to be '56') but there is no 'card no.' for the Supercomp product in v4l. 

What should I do now? Choosing '0' as card no. (for UNKNOWN/GENERIC) doesn't help either. Is there any way to make Ubuntu recognize this card?

Thanks.

---

### Post by davidbilla on 2009-02-27
Hello...?

---

