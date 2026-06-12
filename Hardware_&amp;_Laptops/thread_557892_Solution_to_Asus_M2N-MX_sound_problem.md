---
title: "Solution to Asus M2N-MX sound problem"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by ekehat on 2007-09-23
I had the same sound problems described here [http://ubuntuforums.org/archive/index.php/t-374297.html](http://ubuntuforums.org/archive/index.php/t-374297.html)
(left channel gives an annoying tweet)
Since there's no solution posted on the forums, here's how I solved it:

```
sudo gedit /etc/modprobe.d/alsa-base
```

add the following line:
```
options snd-hda-intel model=3stack
```

re-install alsa:
```
sudo apt-get install --reinstall alsa-util
```

restart PC.

---

### Post by hvymtlsteve on 2007-09-23
I have the same motherboard and same problem! 
I will try this immediately... thanks for posting!

EDIT-- had to do
```
sudo apt-get install --reinstall alsa-utils
```

just needed "s" at the end of "utils"

---

### Post by hvymtlsteve on 2007-09-23
Didn't take but a minute, and worked like a charm! 
No more annoying high pitched sound in the left channel, and now I can finally LISTEN to stuff on my desktop box!

I made a post about this very topic a couple weeks ago but never got a reply. 

Thanks again for posting that! Such a simple fix and I wouldn't have thought to try it...


EDIT-- by the way, a little off topic but what resolution do you get with the onboard video on this mobo? 
I thought I should be able to get 1280x1024 but I can't seem to get anything better than 1024x768... it was this res when I was on the vesa driver (that's what Feisty did on install) and it didn't change when I installed the nvidia driver.

---

