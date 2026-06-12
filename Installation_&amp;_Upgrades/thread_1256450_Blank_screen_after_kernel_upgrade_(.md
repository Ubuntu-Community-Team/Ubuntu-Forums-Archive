---
title: "Blank screen after kernel upgrade :("
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by Drgnslr on 2009-09-02
HI! I have 9.04 running and it has been running ok for a while. Computer is 
Acer 7520 and ATI HD 2400 graphics card. After last kernel update to version 2.6.28-15 my screen goes blank after startup. During startup the ubuntu logo and loading bar are ok, but after that screen just goes blank... :( 

I guess the problem is with my craphics card and it's driver. How do I start to fix it ?? :confused::confused:

---

### Post by presence1960 on 2009-09-02
> **Drgnslr said:**
> HI! I have 9.04 running and it has been running ok for a while. Computer is 
Acer 7520 and ATI HD 2400 graphics card. After last kernel update to version 2.6.28-15 my screen goes blank after startup. During startup the ubuntu logo and loading bar are ok, but after that screen just goes blank... :( 

I guess the problem is with my craphics card and it's driver. How do I start to fix it ?? :confused::confused:

That happened to me on the same kernel upgrade with a nvidia 8600GT. I booted into recovery mode. Let it do it's thing. When the menu comes up scroll down to xfix. When that is complete resume normal boot. It fixed it for me.

If that doesn't work you can boot into recovery mode and choose command prompt with networking. You can install envyng by running these commands > sudo apt-get install envyng-core & > sudo apt-get install envyng-qt After they install run > envyng -t and follow the prompts to install the ATI driver.

---

### Post by Drgnslr on 2009-09-03
XFIX didn't work. It seems allso that my comp is unable to connect to internet while in recovery mode. (it cannot resolve adresses to fetch the pakages). Really irritating... how do I connect to internet in recovery mode???

---

### Post by Drgnslr on 2009-09-04
Problem solved! Thank you Precence1960!!! I just had to go and get online another way. I usually use Wi-fi but it didn't work on recovery mode. So envyng did the trick! Thanks dude!! :D

---

### Post by presence1960 on 2009-09-04
> **Drgnslr said:**
> Problem solved! Thank you Precence1960!!! I just had to go and get online another way. I usually use Wi-fi but it didn't work on recovery mode. So envyng did the trick! Thanks dude!! :D

Glad you got it working. Enjoy Ubuntu!

---

