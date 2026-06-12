---
title: "Connecting ubuntu to LG television"
date: 2015-09-13
forum: Hardware
---

### Post by goosst on 2015-09-13
Hello 

I'm using ubuntu 15.04 gnome on a dell Latitude E6400. 
I have a docking station which has (amongst others) dvi and VGA output to connect to external monitors. 
The setup I'm using is: DVI output of docking station --> DVI / HDMI converter --> HDMI cable to the television.

I've successfully used this without any problems to connect several television screens. 
However with this specific LG television (32LG5000) I can't get images on the screen through dvi (only low resultion VGA works). With windows this works fine so there shouldn't be hardware problems.
I've tried to install the Nvidia binary drivers but that did not make any difference.

Suggestions would be appreciated :)

thanks!

---

### Post by dino99 on 2015-09-14
it will be probably a kernel issue (miss the good module)
use dmidecode to identify the chipset; then searching "kernel+yourfoundref" should give some hints. LKLM is a good place to search too.

---

### Post by efflandt on 2015-09-15
From a quick web search it looks like it may have this for graphics, But I am not familiar with Quadro graphics or which nvidia driver version might be required:
NVIDIA[SUP]®[/SUP] Quadro[SUP]®[/SUP] NVS 160M 256MB DDR2
Intel[SUP]®[/SUP] Graphics Media Accelerator 4500MHD

I am using a 32" LG 1080p HDTV as monitor with DVI to HDMI cable, but the TV is at least several years old. The "Just Scan" mode works better than the 16:9 mode for sizing/centering the image for whatever video signal it is receiving.

---

### Post by goosst on 2015-09-16
> **dino99 said:**
> it will be probably a kernel issue (miss the good module)
use dmidecode to identify the chipset; then searching "kernel+yourfoundref" should give some hints. LKLM is a good place to search too.

Thank you for the reply, I just don't quite know what I should do with this information from dmidecode :icon_frown:

```
I am using a 32" LG 1080p HDTV as monitor with DVI to HDMI cable, but  the TV is at least several years old. The "Just Scan" mode works better  than the 16:9 mode for sizing/centering the image for whatever video  signal it is receiving.
```
Hmm ok, will try to play a bit more with the TV-settings. Not really sure if there is still something left to explore :)

---

