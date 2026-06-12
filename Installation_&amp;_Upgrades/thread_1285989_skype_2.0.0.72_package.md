---
title: "skype 2.0.0.72 package"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by dirtypirate on 2009-10-08
could anyone hook me up with the package for skype 2.0.0.72? this new beta is the pits.

Thanks much guys

---

### Post by howefield on 2009-10-08
Did you have 2.0.0.72 installed on your machine ?

If so, the .deb file may still be in your apt cache.

Can find the portable edition for that version but nothing else.

---

### Post by kgarbutt on 2009-10-08
> Skype isn't in the repositories so you have to add this to your sources.list file: 

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

> You can add it manually from the terminal by opening the sources.list file:

sudo gedit /etc/apt/sources.list

> Install Skype from the terminal with this:

sudo aptitude install skype

> And finally if you want, hash out ## the Skype repo when finished.

---

### Post by dirtypirate on 2009-10-08
i am on a fresh install i didn't back it up, also if i get the package it will set me up with current 2.1 beta which only has pulseaudio and also sucks? cause i can just download that from skype.. hehe. i am looking for the previous version

---

### Post by dirtypirate on 2009-10-09
bump to the top.. can anyone help me out?

---

### Post by kiridude on 2009-10-17
I find it surprising you prefer the previous version of skype to the new one. For me the new version fixed alot of problems I was having with the previous version, plus it has many new functions. 

I have everything set to pulseaudio and have perfect audio in skype.

What problems exactly are you having with the new version?

---

### Post by CraigSBlackie on 2009-10-20
[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)
[http://download.skype.com/linux/skype_static-2.0.0.72.tar.bz2](http://download.skype.com/linux/skype_static-2.0.0.72.tar.bz2)

---

### Post by gabega on 2010-01-19
Does anyone run a portable skype?
I tried to launch it with runz but I got an error message.
I have ubuntu 9.04.

Thanks.

---

### Post by areteichi on 2010-03-08
[http://mirror.ucf.edu.cu/medibuntu/pool/non-free/s/skype/](http://mirror.ucf.edu.cu/medibuntu/pool/non-free/s/skype/)

---

### Post by gradinaruvasile on 2010-03-08
> **dirtypirate said:**
> i am on a fresh install i didn't back it up, also if i get the package it will set me up with current 2.1 beta which only has pulseaudio and also sucks? cause i can just download that from skype.. hehe. i am looking for the previous version

I use Skype beta 2 with both alsa and pulseaudio (On Ubuntu and Debian boxes) and works perfectly with both. It uses PulseAudio only if its available. Works with ALSA just as well.

Maybe you have sound problems because pulseaudio isnt working right.
Skype works if the Ubuntu's sound system works. Test it with sound recorder.

---

### Post by olalaaa on 2010-03-09
I have an older version, but maybe it is of help to you, too. Please check my signature or this post, too [http://ubuntuforums.org/showthread.php?t=1025240&highlight=skype+linux](http://ubuntuforums.org/showthread.php?t=1025240&highlight=skype+linux)

I can help you if you have 8.04.

---

