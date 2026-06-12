---
title: "Another Headphone Issue"
date: 2008-08-16
forum: General Help
---

### Post by lilleprechaun on 2008-08-16
Hello all!

Let me start off by stating that I am COMPLETELY NEW to Ubuntu. I really love it - the OS and the Philosophy behind it. And while I have worked out most of the kinks in the past few days, there is one that I cannot fix despite hours of searching online... My Headphone issue.

Unlike most of the other posts found throughout the internet, when I plug headphones into my port, my speakers DO turn off. But there is no sound through my headphones.

Things I have tried:

 - Different sets of headphones
 - Alsamixer (see note below)
 - Sound Prefernces: Headphone as line out - I tied it with this box both ticked and un-ticked.

About the Alsamixer: When I go into there, I can turn my headphones on (via the M key), but I cannot raise the volume. Is this normal? In any case, I can't hear anything at all when  plug my headphones in, except for that initial "pop" I always hear when plugging them into something - SO I assume that the port is on... but that the output isn't high enough???

ALSO: I am using a Dell Studio 1535.

Thanks all for your help!!!

---

### Post by Jack the R on 2008-08-16
Read through this [thread](http://ubuntuforums.org/showthread.php?t=820959)

Pay particular attention to setting your alsa base file, as I had everything else installed correctly but the headphones didn't work until I had the correct model setting in alsa base.

Sorry I can't tell you what your model is, I'd try auto or Dell.

My headphones work now but I still don't get a volume control in alsa mixer.  The gui volume works though.  Go figure.

---

### Post by lilleprechaun on 2008-08-16
Well, I fooled around a bit in Alsa - go figure, you had to turn the "Surround Sound" option on and turn t up all the way to get the headphones on. Weird, but whatever - my headphones work now :^)

---

### Post by mbeach on 2008-09-16
hi, same here, fresh install of hardy 8.04.1 - all I had to do was double click the sound icon by the clock, then Edit -> Preferences, select "Surround", then use the surround volume for the headphone jack. Incidentally, this works only for the first headphone jack (the one closest to the front of the machine).

edit:
the master switch seems to control the headphone jack between the mic and first headphone jack.

---

### Post by marioquark on 2008-10-11
hi, same pc model but i use ubuntu intrepid. operations you told don't work with my OS... any suggestion?

---

### Post by netpro25 on 2008-11-30
This has been resolved in the latest snapshot of the ALSA drivers, you can find details here: [http://ubuntuforums.org/showpost.php?p=6159988&postcount=4](http://ubuntuforums.org/showpost.php?p=6159988&postcount=4).

Marcel

---

