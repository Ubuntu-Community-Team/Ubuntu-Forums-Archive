---
title: "Big big problem with intel soundcard and asus a6va"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by Alessio on 2005-12-20
I have tested alsa 1.0.10 and 1.0.9 driver, proprietary driver and a lot of howto. The laptop boots now, but the soundcard isn't recognize.. no card.
What can i do? Should I compile the kernel?
Anyone with asus a6v and my problem?
Thanks in advance
Alessio

---

### Post by er-ku on 2005-12-20
you could at least state what card that is...
If it's Intel's High Definition Audio, you may check [this thread](http://ubuntuforums.org/showthread.php?t=76019), and also try the latest ALSA 1.0.11 RC1 driver.

And please don't post multiple threads with the same question. That sucks, and only make things harder to track down for other people.

---

### Post by Alessio on 2005-12-20
Sorry i'll read the thread...

---

### Post by Alessio on 2005-12-21
Nothing to do, Alsaconf doesn't recognize my sound card!! And the module snd-hda-intel does'nt load..
What can i do? Sholdu I compile my kernel?

---

### Post by arkangel on 2006-03-31
[http://fr.wikibooks.org/wiki/Tout_sur_le_portable_Asus_A6VA](http://fr.wikibooks.org/wiki/Tout_sur_le_portable_Asus_A6VA)

thsi site is in frech  so far was working the problem is that i cannot comile alsa driver  when  typing  make  it say, error  gcc 3.4 not found , but my version of gcc is 4.0.0  default ubunto by typing  apt-get install build-essentials  

any idea ,  if you try and have some success please let me know :)

---

