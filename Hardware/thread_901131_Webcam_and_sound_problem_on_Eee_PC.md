---
title: "Webcam and sound problem on Eee PC"
date: 2008-08-26
forum: Hardware
---

### Post by botokely on 2008-08-26
I'm new user of Linux and I've xubuntu 8.04 installed on my ASUS Eee PC 4G. It seems to work well but I've just remarked that I can't hear any sound from my laptop especially after loading (but sometimes some games sound work). I don't know where the problem comes from or how to check it?
And I've remarked too that it don't detect my integrated webcam. Should I download a driver or ...?
Has anyone got the same problem :confused: ?

Thanks for help

---

### Post by Crafty Kisses on 2008-08-26
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by SteelWo1f on 2008-08-26
My sister just bought an Eee and I know her webcam didn't work with Ubuntu either.She eventually gave up and went with Windows :(. I don't blame her though.

---

### Post by Kane_of_NOD on 2008-08-26
Hei,

I have Eee pc 901  with Ubuntu and eee Linux kernel

it works  PERFECTLY..

i just had a little problem.. wi-fi   webcam and bluetooth..

how to resolve it:

going into the BIOS setup.. there is an option out there that you can make like this:

webcam  enable
wireless  enable
bluetooth  enable

I had these 3 disabled  so I could not access the devices..

---

### Post by botokely on 2008-08-28
> **Codename said:**
> Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

Thanks it works when I tried with Ekiga.

---

