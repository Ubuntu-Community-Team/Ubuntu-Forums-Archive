---
title: "Microphone and Headphones don't work EeePC 1215T"
date: 2011-03-27
forum: Hardware
---

### Post by unboogyman on 2011-03-27
Hi, I'm having problems with my audio devices in Ubuntu 10.10 64 bit.

My built in microphone doesn't work, and also, headphones don't work in my headphone jack.

Please note, I mean my built in microphone, I haven't tested the microphone jack nor have one to test it.

I'm more concerned with my headphones not working.

I'm new to linux and would appreciate any help.  Thanks :)

---

### Post by lidex on 2011-04-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by unboogyman on 2011-04-04
Here is the link: [http://www.alsa-project.org/db/?f=cd62bdcfbaa75cd91ab98b645bde5c867b876a59](http://www.alsa-project.org/db/?f=cd62bdcfbaa75cd91ab98b645bde5c867b876a59)

---

### Post by lidex on 2011-04-05
You have installed alsa-modules from the audio dev ppa?
Remove them and remove the ppa from your sources. Now follow the link in my sig to manually upgrade alsa.

---

