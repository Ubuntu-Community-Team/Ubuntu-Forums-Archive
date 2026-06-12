---
title: "DVDs Not Recognized"
date: 2009-10-03
forum: Hardware
---

### Post by Tinieblas on 2009-10-03
I'm new to Ubuntu, just installed 9.04. I've figured out most of my problems using the forums, so thanks to all of you that know what you're doing and help out those of us that don't :-)

I just found another problem that I haven't been able to find an answer for. My laptop (HP Compaq nx6125) has a DVD player / CD burner. It reads and burns CDs just fine, but it does not recognize DVDs. I've tried putting in movies, blank DVDs, etc. and nothing is recognized.

I assume that it must be some driver problem or something because it worked fine when I was running Windows XP. I am still trying to figure out Ubuntu, so maybe it's something simple that I just missed. If so sorry to take up so much time, but thanks for the help!

---

### Post by user333 on 2009-10-03
I can't get DVD's to work either! Ubuntu is great, but sometimes things like this get on my nerves! I hope you get some help! funny thing is that I could use the DVD burner and read DVDs when I was using the live CD(now I can't even get my drive to work!). Try using your live cd and see if it works. It might help you diagnose the problem.

---

### Post by ziret on 2009-10-03
I am having the same problem only with 9.10. I have a Dell Inspiron 1520. The CD/DVD was working fine on the live CD, and also burned .iso images of Ubuntu, but now, when I put a DVD with software in, it not only doesn't read the drive, the drive won't open unless I reboot. I hope someone helps us with this.

---

### Post by SunnyRabbiera on 2009-10-03
Try installing libdvdcss, and libdvdread.
You might even need the udf packages.
I am unsure if you are using the 64bit version though.

---

### Post by ziret on 2009-10-04
Thanks, that did it!!!

---

### Post by Tinieblas on 2009-10-04
Ok, so I'm looking at my synaptic package manager, and I already have libdvdread4 installed... There's no libdvdcss or libdvdread in there... are they something different? I'm using 32 bit, not 64 bit...

---

### Post by soni1770 on 2009-10-05
yea, i'm having the same problem, only my dvd playback used to work, and just decided to stop, i even tried installing 9.04 from scratch again with no joy? whats going on?

when i lsdvd i get 

libdvdread: Encrypted DVD support unavailable.

---

### Post by bresdog on 2009-10-05
This might help-
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by soni1770 on 2009-10-05
yup, that's solved the problem.:guitar:
sweet as a beat,

now, where did i put my pet monster duck

---

