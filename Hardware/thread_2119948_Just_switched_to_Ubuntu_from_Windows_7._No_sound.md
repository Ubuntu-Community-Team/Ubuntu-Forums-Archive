---
title: "Just switched to Ubuntu from Windows 7. No sound?"
date: 2013-02-25
forum: Hardware
---

### Post by rafiaziz1943 on 2013-02-25
Hi. I am absolute beginner to Ubuntu/Linux. So please try to help out thanks.

I have no sound. 

Here is all the info about my sound system: -

[http://www.alsa-project.org/db/?f=d160b03094060b5b12cdb84f6d948413fc25c33a](http://www.alsa-project.org/db/?f=d160b03094060b5b12cdb84f6d948413fc25c33a)

!!Soundcards recognised by ALSA !!-----------------------------

 0         [Intel          ]: HDA-Intel - HDA Intel                       HDA
               Intel at 0xb7cfc000 irq 87  

1          [NVidia         ]: HDA-Intel - HDA NVidia                       
             HDA NVidia at 0xbbdfc000 irq 34 

2          [NVidia_1       ]:             HDA-Intel - 
              HDA NVidia                       HDA NVidia at 0xbf4fc000 irq 37

---

### Post by TheFu on 2013-02-25
There is an "Ubuntu Sound Troubleshooter" that will lead you through the steps. [https://wiki.ubuntu.com/DebuggingSoundProblems#Preliminary_checks](https://wiki.ubuntu.com/DebuggingSoundProblems#Preliminary_checks)

[LIST=1]
[*]Did you load the proprietary nvidia GPU drivers?
[*]Have you turned up the volume inside **alsamixer**?
[*]Plus the obvious - are the speakers plugged into the correct ports, powered and volume at reasonable level?
[/LIST]
 Sorry, but I had to ask.

---

### Post by rafiaziz1943 on 2013-02-25
Hi,

Its a laptop so speakers are built in. This is what alsamixer looks like: -

[http://oi49.tinypic.com/250pjxt.jpg](http://oi49.tinypic.com/250pjxt.jpg)

---

### Post by rafiaziz1943 on 2013-02-25
I have literally just installed Ubuntu last night. So i probably have not put the right nvidia drivers. I will go through the guide you have provided. And come back with the result.

Thank you for your help so far :)

---

### Post by TheFu on 2013-02-25
Thanks for the image.  Looks like 3 of the possible speakers are set to ZERO volume.  Also, you may need to switch the audio card inside alsamixer to access the built-in speaker controls.

---

### Post by rafiaziz1943 on 2013-02-25
Is there a way to uninstall the other audio cards and just have one. I been reading everywhere that there can b a clash between multiple cards. Maybe if i just hav one installed and the others shut off it may work?

---

### Post by SimonDPRZ on 2013-02-25
have you done sudo apt-get update and upgrade to get latest drivers etc

---

