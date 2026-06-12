---
title: "Internal Mic in Acer 8942G not working"
date: 2010-09-05
forum: Hardware
---

### Post by badex on 2010-09-05
Hi there. I recently installed Ubuntu 10.04, alongside Windows 7, on my laptop. I really love it and everything seems to be working except for a couple of sound issues. The internal  mic is not working and the audio jack is not detected when I plug in headphones- the speakers don't turn off when I plug in my headset. The sound card is Realtek 670.  I was wondering if anyone has any ideas on how to fix this? Do I have to download a special driver or something? I have a basic grasp of the terminal if you need me to issue any commands there. Thanks in advance.

---

### Post by badex on 2010-09-06
I finally got this working.....well sort of. I had to upgrade Alsa to 1.0.23. I found the instructions [here]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/"). I took a while, but I followed the instructions step-by-step. Then I went into Sound Preferences, selected Input and changed Connector to Microphone 2. 

It still doesn't recognize when I plug in my headphones??

Any help would be appreciated!

---

