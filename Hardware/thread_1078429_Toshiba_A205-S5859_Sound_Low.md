---
title: "Toshiba A205-S5859 Sound Low"
date: 2009-02-23
forum: Hardware
---

### Post by mikeypizano on 2009-02-23
Sorry if this is in wrong section, I tried to post in the Media forum but it said I didn't have permission...


On Vista, I would normally have my volume at under 15% but usually around 7%, but on Ubuntu it seems to need to be over 50% to even really hear anything.

---

### Post by mikeypizano on 2009-02-25
Anyone???

---

### Post by chriskin on 2009-02-25
master volume is at 50% as you say, are the others in volume control high as well?
(pcm, or speaker or some other related for example (headphone etc etc)

---

### Post by stchman on 2009-02-25
> **mikeypizano said:**
> Sorry if this is in wrong section, I tried to post in the Media forum but it said I didn't have permission...


On Vista, I would normally have my volume at under 15% but usually around 7%, but on Ubuntu it seems to need to be over 50% to even really hear anything.

I have the exact same laptop and the sound level is fine.  Are you running Hardy or Intrepid?

Double click the little speaker up in the right hand corner.  Bring up the sliders and see if that cures the problem.

---

### Post by mikeypizano on 2009-02-25
I have PCM and Headphones maxed out and use Master to control it, I am saying on Vista, I will have it at like 10% but it needs to be like 50% plus on Ubuntu to be just as loud.

EDIT: Forgot, using Intrepid.

---

### Post by chriskin on 2009-02-25
maybe you should try recompiling alsa
i did and i can say that everything is a little louder now

i don't know though, i'll let someone using your laptop answer to be more accurate

---

### Post by mikeypizano on 2009-02-25
> **chriskin said:**
> maybe you should try recompiling alsa
i did and i can say that everything is a little louder now

i don't know though, i'll let someone using your laptop answer to be more accurate

How do I do that?

---

### Post by chriskin on 2009-02-26
here [http://www.box.net/shared/454ic17as0](http://www.box.net/shared/454ic17as0) is a script that does all the work for you

credit goes to [CJay554]("http://ubuntuforums.org/member.php?u=269230") and his thread [http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920](http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920) 

(the script works on any kind of laptop of course)


it will download the newest alsa from the site and get it ready for you, so it MIGHT help you, it helped me at least

---

### Post by bendib on 2009-02-26
Do you see that little speaker on the top right panel? right click it and select open volume control. Then Drag either one of the pcm bars to wherever, and keep in mind, a little bit from the top can take away a lot of sound. I'm doing this on my ubuntu-based distro, still in alpha. It's called Shift Linux. Look for it on my site in about a month, as a installation package for ubuntu, and around 2010 expect a downloadable iso.
It supports both deb and rpm, every desktop environment you can think of, Tons of awesome free software, and a theme that will have you saying OOh! Ahh! The login screen is a nebula! The default wallpaper is a beautiful waterfall! The gnome splash screen is beneath the ocean! And all these images are branded with the slogan, Shift linux. Shift Life. I have yet to design a usplash.

---

### Post by mikeypizano on 2009-02-26
> **bendib said:**
> Do you see that little speaker on the top right panel? right click it and select open volume control. Then Drag either one of the pcm bars to wherever, and keep in mind, a little bit from the top can take away a lot of sound. I'm doing this on my ubuntu-based distro, still in alpha. It's called Shift Linux. Look for it on my site in about a month, as a installation package for ubuntu, and around 2010 expect a downloadable iso.
It supports both deb and rpm, every desktop environment you can think of, Tons of awesome free software, and a theme that will have you saying OOh! Ahh! The login screen is a nebula! The default wallpaper is a beautiful waterfall! The gnome splash screen is beneath the ocean! And all these images are branded with the slogan, Shift linux. Shift Life. I have yet to design a usplash.


They are maxed out yes, and I look forward to Shift.

Will recompile Alsa with that script later today, thanks.

---

### Post by mikeypizano on 2009-02-26
> **mikeypizano said:**
> They are maxed out yes, and I look forward to Shift.

Will recompile Alsa with that script later today, thanks.

Tried to run it, but it won't run. What am I doing wrong?

---

### Post by chriskin on 2009-02-28
if you are talking about the script, are you using the script's name in the commands given in the thread i said?

it has a different name, but i thought you would see it , sorry :$

---

### Post by mikeypizano on 2009-03-01
I downloaded it and clicked on it.

---

### Post by chriskin on 2009-03-02
these are definitely not the instructions on the thread i redirected you to :)
use the instructions from there, two commands at most, and use the name of this script instead of the one he does

---

### Post by mikeypizano on 2009-03-02
> **chriskin said:**
> these are definitely not the instructions on the thread i redirected you to :)
use the instructions from there, two commands at most, and use the name of this script instead of the one he does

Oops, I didn't see the thread! :mad:

---

### Post by mikeypizano on 2009-03-02
> **mikeypizano said:**
> Oops, I didn't see the thread! :mad:

Hmm, don't think it really made a difference. Oh well. Any other ideas?

---

