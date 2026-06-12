---
title: "Headphones not working on Toshiba A135-S4727 laptop (8.10)"
date: 2008-11-09
forum: Hardware
---

### Post by linkmaster03 on 2008-11-09
Sound works fine on my laptop, Toshiba A135-S4727, through the speakers, but the headphones don't work. None of the necessary audio channels are muted. My audio card is snd-hda-intel (Intel HDA, ALC861VD).

---

### Post by linkmaster03 on 2008-11-14
Anyone? :(

---

### Post by Ecologger on 2008-11-14
My guess is you will have to alter your alsa-base file. Something like [http://forum.soft32.com/linux2/Bug-407252-Pkg-alsa-devel-Bug-407252-alsa-base-Intel-High-De-ftopict68119.html]("http://forum.soft32.com/linux2/Bug-407252-Pkg-alsa-devel-Bug-407252-alsa-base-Intel-High-De-ftopict68119.html") but you would have to find your model. Also try looking at [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by farebalk on 2008-11-14
First forgiveness for my misspelling but it's just that I'm learning English and also helped me with the translator of google, but I hope help you a little on your problem.

I think that you should try to connect your headphones in another computer with Ubuntu to see if they work, and you should also mention if are usb

---

### Post by Ecologger on 2008-11-14
Also [http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845") gives the models for editing the alsa-base file.

---

### Post by linkmaster03 on 2008-11-17
I tried the position_fix=1 and that didn't work. Also I've tried a lot of models. No dice.

---

### Post by linkmaster03 on 2008-12-08
Still not working...

---

### Post by libertykull on 2009-05-30
I am using ubuntu(9.04). I had the same problem before, headphone jack was not working. Then I found this solution from one of the forum sites: 

Headphone not working in Toshiba 

Add this line to the end of "/etc/modprobe.d/alsa-base"

Code:
options snd-hda-intel model=lenovo

Then run this command:

Code:
sudo alsa force-reload

Now you can even mute the laptop speakers from alsa mixer while listening from headphone if you want.

I hope it works for you too...

---

