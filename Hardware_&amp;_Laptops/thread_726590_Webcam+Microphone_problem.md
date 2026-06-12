---
title: "Webcam+Microphone problem"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by Rinaldo on 2008-03-16
I have a Dell inspiron 1720, There is a microphone and webcam embedded in the moniter. Any Idea on how to get them to function?

Webcam manager does not work.

---

### Post by linuxwizard on 2008-03-16
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

According to this > [https://wiki.ubuntu.com/LaptopTestingTeam/Dell/DellInspiron1720](https://wiki.ubuntu.com/LaptopTestingTeam/Dell/DellInspiron1720) > it should work with Ekiga. Also look in section for Integrated mic notes on making it work.

---

### Post by Rinaldo on 2008-03-17
I toggled the setting and was able to get the webcam to function under V4L2. The webcam does not function however when I try streaming to a flash based website (Stickam). 

I clicked on the link you provided for the microphone and it said it would work  "with linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb from Dell and "digital" as input in alsamixer"

I googled these terms but was unable to to find a turorial for implementing them. 

Thank you for your help

---

### Post by linuxwizard on 2008-03-17
Good to hear you got your webcam working.
linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb [COLOR="Red"]from Dell[/COLOR]. Have looked on Dell's website?

---

