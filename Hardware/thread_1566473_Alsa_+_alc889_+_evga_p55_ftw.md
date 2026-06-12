---
title: "Alsa + alc889 + evga p55 ftw"
date: 2010-09-02
forum: Hardware
---

### Post by btown1987 on 2010-09-02
Ok so as you can see in the title I have an EVGA P55 FTW edition mobo with an onboard audio ALC889. Now my problem is that I get basic speaker sound over the "front" port in alsa. However my headphone jack in the front does not work at all, and my mic in the front passes its sound stright to the speakers. I suspect this is because alsa doesn't have a good model option for my card.

Currently I use...
options snd-hda-intel model=auto

but i have tried many from the list and none of them quite work correctly. Does anyone know what the correct model for EVGA P55 FTW should be or have an alternate hypothesis?

---

### Post by lidex on 2010-09-03
Need more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

Have you tried:
6stack-dig or 6stack-dig-demo or intel-alc889a

---

### Post by btown1987 on 2010-09-03
ok here is the link to the alsa info report...

[http://www.alsa-project.org/db/?f=40f3a7bc47bf4771aed9ec179850685cb88838a6](http://www.alsa-project.org/db/?f=40f3a7bc47bf4771aed9ec179850685cb88838a6)

Ty for the help Lidex

---

### Post by lidex on 2010-09-03
What happened to pulse audio?

---

### Post by btown1987 on 2010-09-03
sudo apt-get remove happend to it.

---

### Post by lidex on 2010-09-03
What exactly did you do to your sound system? Don't leave anything out.

---

