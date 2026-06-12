---
title: "Headphones not being detected."
date: 2010-10-20
forum: Hardware
---

### Post by LakatosI on 2010-10-20
Hi guys. I recently bought an ASUS K52JK notebook/laptop with Windows 7 preinstalled on it. Now although I am a devoted Linux fan, since I basically "bought" Windows 7 I thought I might as well  give it a try. I quickly grew tired of it because it always froze up whenever I useg gvim or emacs when programming, so I decided to delete everything and install a fresh copy of Linux. After many unsuccessful attempts to install openSUSE (it kept freezing during installation when configuring the boot-loader), I decided to give the new 10.10 a try. I kept avoiding it because I knew that on laptops suspend and hibernate don't always work. Fortunately I found a solution this time, so I'm quite happy with it.

My only problem is that although the internal speakers work without any problem, Ubuntu doesn't seem to acknowledge the existence of  my plugged-in headphones, so it keeps using the internal speaker. The microphone doesn't seem to be recognised either. It's as if they were never plugged-in. 

I checked other posts, but didn't find anything that would work. 
If it helps with anything, my sound card is a Conexant CX20585.

Everything worked fine in Windows 7, and I don't think the hardware got busted in such a short time.

Any help appreciated.
Cheers.

---

### Post by LakatosI on 2010-10-20
bump -- So many threads that I got pushed down.

---

### Post by Nullifi3d on 2010-10-20
Confirmed.

Asus U50F in 2.6.32 and 2.6.35

---

### Post by LakatosI on 2010-11-06
Bump - Any suggestions?

---

### Post by I'mGeorge on 2010-11-06
Do you want your personal headphones to be detected by your OS ? Well alsa does has an option for headphones ... you know

---

### Post by LakatosI on 2010-11-06
I don't understand...
I dais in the first post that my headphones are just simply not being detected. There is no such option in alsa.

---

### Post by I'mGeorge on 2010-11-07
try gnome-alsamixer. I'm using it right now and I know it has an option for headphones either.

---

### Post by LakatosI on 2010-11-07
I'll say it again: My headphones are not detected. There's no such option in my alsamixer because it doesn't detected it.

---

### Post by Rahul Jain on 2011-02-19
hey.. were u able to find any solution to that problem? I am having the same problem here.. please reply.

---

### Post by gradinaruvasile on 2011-02-19
> **LakatosI said:**
> I'll say it again: My headphones are not detected. There's no such option in my alsamixer because it doesn't detected it.

What does PulseAudio say?
Right-click on the sound icon from the tray, select preferences, go to the input/output tabs and see what options you have there.

---

