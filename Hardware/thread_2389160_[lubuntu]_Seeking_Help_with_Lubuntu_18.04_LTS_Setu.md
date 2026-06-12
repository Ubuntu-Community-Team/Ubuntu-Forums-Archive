---
title: "[lubuntu] Seeking Help with Lubuntu 18.04 LTS Setup for Newest RPi3B+"
date: 2018-04-12
forum: Hardware
---

### Post by tloatdae on 2018-04-12
Greetings, good folks!

I have managed to get my hands on the newest iteration of the Raspberry Pi 3, Model B+, and would so very much LOVE to get Lubuntu 18.04 LTS to run on it, but am having beastly luck in my attempts.

Does anyone have some pointers for getting started, or happen to have something put together already that can simply be expanded onto a card?

Thanks in advance!

---

### Post by pqwoerituytrueiwoq on 2018-04-13
I do not see any images for armhf
[https://ubuntu-mate.org/raspberry-pi/](https://ubuntu-mate.org/raspberry-pi/)
i guess you could install mate 16.04 upgrade and install lubuntu-desktop and remove the mate desktop

---

### Post by tloatdae on 2018-04-16
Thanks for the reply and wonderful suggestion!

What I keep running into, is the new RPi3B+ seems to be having issues with power and/or initial configuration on setup, with the rainbow screen sporting the little lightning bolt.
It's sad that there's a new iteration of the Pi, but it almost seems broken and not very usable.
Even the RPi3B has fallen off the functionality, when you install Lubuntu on it. After a single update, it flakes right out on me completely.

Hence, the desire to run the Bionic Beaver 18.04 LTS (if I can get it to work, of course).

---

### Post by tsimonq2 on 2018-04-19
You're probably looking for this: [https://ubuntu-pi-flavour-maker.org/](https://ubuntu-pi-flavour-maker.org/)

Martin will release 18.04 images by the time 18.04.1 comes out.

---

### Post by tloatdae on 2018-04-23
Thanks for the suggestion, tsmonq2!

Sadly, the Lubuntu image they offer right now won't work on the RPi3vB+ (yet).
If someone in that community updates it for the newest Pi, then it might just work. Unfortunately, there still seems to be a lag in the support for the newest board.

I really miss having the available images for OSs that will just Work when downloaded. If I was more 'Nix savvy, I'd try and compile one, myself. I'm not that savvy.

Anyone else have enough experience, and want to try earning the worshipful admiration of the Raspberry Pi community willing to get this up and running? There will be a Lot of happy people there, if you manage to pull it off!

Me included! ;)

---

### Post by notinkeys on 2018-05-04
Don't feel alone, tloatdae. Even though I am an IT and tech professional, I am not even remotely able to compile for my RPi. I've had a modest amount of frustration that the image on the flavor maker page is an old one which seems to have a few minor issues on my RPI 3. Count me among those waiting for it to be updated!

Out of curiosity, what makes it fail on the 3B+?

---

### Post by pqwoerituytrueiwoq on 2018-05-04
the 3b+ requires a newer kernel for the new hardware it has, in theory if you update the kernel to (my rasbian 3b+ has 4.9.80) it should boot (though unsupported)

---

