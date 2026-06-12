---
title: "ATI Graphics Card problems, worse than integrated graphics!"
date: 2008-10-20
forum: Hardware
---

### Post by Keithamus on 2008-10-20
I've just upgraded my mythtv box, which used to have integrated graphics - it ran fine, no real problems, except games were slow. So I thought ATI would be a good move...

I couldn't be more wrong, the performance is SO poor! Moving window produces loads of artifacts, HD playback is no less intensive on my CPU, games are still as choppy, and the worst bit is that MythTV LiveTV is completely unusable as there is no picture...

I've tried using the drivers downloaded from the AMD website, tried using the drivers from the restricted drivers manager, tried using envyng, and also tried using radeonhd drivers, all of them are abysmal!

Am I doing it wrong? I am a pretty die hard nvidia user so this is new territory for me, is there any advice at all? Surely an ATI HD 3450 256mb can perform better than the 8mb intel integrated chip??

---

### Post by thepizzaman on 2008-10-20
hey i have almost the same card (512mb)
go to the restricted hardware drivers (or somethin like that) in the admin page open it and click on your card to enable and install the drivers hope this works :)

---

### Post by Keithamus on 2008-10-21
I've tried the restricted drivers manager - they offer dismal performance. To be specific, anything that requires OpenGL (Ie anything on mythtv) just plain doesn't work.

I'm seriously considering returning the card, because so far its had no positive impact on my performance!

---

### Post by thepizzaman on 2008-10-21
well what you need to do then is get the python opengl drivers in the synaptic package manger theres about 3 of them and u should get the ati catylist control center i think thats in the add remove programs..... maybe this will work :)

---

### Post by Bablefish on 2008-10-21
Ubuntu has literally the worse time with ATI drivers. Enough so I call them the drivers from HELL!!! The truth is you have no better than a 50% they will even work for you. As for the other 50% that is the chance you take that the video drivers will crash and maybe you have to reload your OS. This comes from experiance, for when I tried to install them my Video drivers crashed.

---

### Post by thepizzaman on 2008-10-21
yes that is true but i played with mine and got them to work great - a little screen flicker in tremulous i love my HD3450 :)

---

### Post by thepizzaman on 2008-10-21
[http://ubuntuforums.org/showthread.php?p=5831610#post5831610]("http://ubuntuforums.org/showthread.php?p=5831610#post5831610")
also try this :)

---

### Post by Keithamus on 2008-10-21
Could you please be more specific about the packages needed?

I can't seem to get the catalyst control center, tried installing fglrx-amdcccle and found out it is a dummy package. Can't find out what command to do to run it, and its not in my menu...

There are about 20 packages when I search for "python opengl", but I've already got "python opengl" installed, so what do i do now?

---

### Post by thepizzaman on 2008-10-21
ok hmmm if you have the python opengl.... are there any programs that you havn't tried? some of them might give you a missing driver
and the ati catlyst control were you tryin to get it from the pakage manager or from the add\remove programs?

---

### Post by Keithamus on 2008-10-21
I looked around online for a bit, and went into IRC to get some more help, and I have found the following things:

[LIST]
[*]ATI drivers do not support MythTVs opengl, as such Mythtv needs to be changed to use QT and Xv
[*]Updating to the latest drivers from the AMD website is best
[*]Randomly, using mythtv fullscreen doesnt work, you need to suffix "--geometry WxH" where W is your screen width and H is your screen height -1px, in my case, "--geometry 1280x1023"
[*]ATi might not be a worthwhile investment right now, but in time when the driver(s) mature might be
[/LIST]

So right now I'm kind of back to square 1, no better, no worse than the intel drivers. I guess time will tell for the good stuff.

---

### Post by Chainz on 2008-11-04
When using proprietary drivers (for my HD 3450 AGP) I get terrible lags!

See: [https://bugs.launchpad.net/ubuntu/+bug/292317](https://bugs.launchpad.net/ubuntu/+bug/292317)

How did you people made this card to work?

---

### Post by 73ckn797 on 2008-11-04
> **thepizzaman said:**
> [http://ubuntuforums.org/showthread.php?p=5831610#post5831610](http://ubuntuforums.org/showthread.php?p=5831610#post5831610)
also try this :)

The thread you reference, which I posted, does not work for me in Intrepid. Go figure? I am working on it now.

---

