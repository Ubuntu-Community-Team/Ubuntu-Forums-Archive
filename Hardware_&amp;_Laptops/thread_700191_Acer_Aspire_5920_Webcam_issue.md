---
title: "Acer Aspire 5920 Webcam issue"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by Rotzbouf on 2008-02-18
Hi folks,

I have a small problem with my Suyin webcam on an Acer Aspire 5920 using Ubuntu 7.10.
I have searched the forum for similar posts and only found outdated posts which said "not supported yet".

It seems that the cam is correctly recognized in the system and the driver was correctly installed.

I wanted to use my cam with camorama but on start it tells me "Cannot connect to /dev/video0".
Since on the Aspire 5920 the cam is switched off by default, it looks like camorama has trouble switching it on.

I did another test with aMSN to use the cam and here, the program managed to switch the cam on but I had no output.

Maybe some of you managed to bring the cam to work.

---

### Post by linuxwizard on 2008-02-18
Have you tried using Ekiga ?

At the bottom of this page shows it should work with Ekiga.
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920)

---

### Post by Rotzbouf on 2008-02-19
Thanks for the tipp. I will try this one and give you feedback.

Edit 20/02/08:
Hi,
I have tried with Ekiga and managed to turn on the cam but I can't get an video output. The only thing I see is a green output box.
Even though, my cam is correctly recognized by the system. Maybe I have to wait a bit until the cam is fully supported by all the progs.

---

### Post by spegru on 2008-03-07
I just installed the latest UVC drivers from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
The cam now works fine in Skype although not in Ekiga (which I don't use)

Fine for me now

spegru

---

### Post by davarse on 2008-04-14
if you interest on ekiga, you can open ekiga> edit> preferences, look under devices and click the video devices and change the video plugin to V4L2.... that's should work:popcorn:

---

### Post by davarse on 2008-04-15
hi spegru, i couldn't use the webcam with skype, every time i try to use the webcam the call always drop off, and every time my friend use her webcam the same the call drop off as well, it just went off and i need sign in to skype again and again...
do you have any idea??? how can you make your webcam work on skype???:confused:
i'm using acer aspire 5920G on ubuntu Gusty...

cheeers'

---

