---
title: "Will these soundcards work under ubuntu/gutsy?"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by TwiStEr55 on 2007-12-09
Hi folks,

I wanna completly change to ubuntu but I have an X-fi which im going to sell and I need a new soundcard for a fresh install of ubunut. Right now Id like on of these but I cant really find out if these will work flawlessly under gutsy ... I have a 5.1 system and want it to work obviously :)

Terratec Aureon 7.1 Dolby Digital 
Club 3D Theatron Dolby Digital 7.1

both have the C-Media CMI8768+ chipset .... on the alsa page ist doesnt say unsupported, yet I wanna be sure before I buy ... thx for the advice

---

### Post by TwiStEr55 on 2007-12-09
no one has these cards?

---

### Post by KyRo1989 on 2007-12-22
I bought the theatron and although I don't have it yet, I am quite sure that it is supported - CMI8770 (CMI8768+) is listed [here]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media") for ALSA, but ALSA does not support DTS because  they don't want to open their source for Linux. But as far as I know from [this]("http://ubuntuforums.org/showthread.php?t=236826") thread, the new OSS 4.0 drivers (download [here]("http://www.4front-tech.com/oss.html")) completely support the chipset - this may be possible because it is a commercial driver (free to use), but I don't know it exactly.

Though all other things should be supported at least with the OSS driver.

Greets

---

