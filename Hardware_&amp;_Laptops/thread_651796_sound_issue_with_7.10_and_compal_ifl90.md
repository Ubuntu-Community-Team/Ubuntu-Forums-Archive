---
title: "sound issue with 7.10 and compal ifl90"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by mab1376 on 2007-12-27
i tried recompiling alsa along with compiling and install the realtek drivers from their site with no luck.

i checked all the volume levels and the  master audio channel and everything is good

its a realtek ALC268 chip..

help please!!

---

### Post by tommcd on 2007-12-28
It seems the realtek alc268 uses snd-hda-intel driver, but I suppose you figured that out by now. Perhaps these will help:
Is it a Toshiba laptop?
[http://ubuntuforums.org/showthread.php?t=551615&highlight=realtek+alc268](http://ubuntuforums.org/showthread.php?t=551615&highlight=realtek+alc268)
or if not, then have you seen this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
EDIT: Oh, and welcome to the ubuntu forums!

---

### Post by mab1376 on 2007-12-28
i bought it from ibuypower
compal makes the barebone unit that they customize.

i'll give those a shot and get back to you, bare in mind ive only been using Linux for 2-3 months now. i barely use windows now unless i want to play a game that is windows dependent.... not to keen on wine yet.

---

### Post by c1rcu17 on 2008-01-02
try looking at this website. it is dedicated to the Compal IFL90/ Sager np2090 and Ubuntu Gusty.

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90)

I'm on a Compal ifl90 right now, and if you follow the directions on compiling the latest Alsa source using module-assistant, it works. The microphones are a different issue though. They work, but not too well.

---

### Post by drawkcab on 2008-01-04
> **c1rcu17 said:**
> try looking at this website. it is dedicated to the Compal IFL90/ Sager np2090 and Ubuntu Gusty.

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90)


I tried this work around (both options) to no avail.  I'm bummed.  Any ideas?


Vid card support isn't so hot either, but at least it's working.

I like the Compal IFL90, but I wish it were a bit more ubuntu friendly.

---

### Post by sKittles on 2008-01-04
i also had the same problem that none of the solutions worked.

i bought my ifl90 from ibuypower as well.  I fixed the sound problem by installing the zip file of the alsa driver manually.

the name of the file is called
alsa-driver-1.0.15rc3 ( make sure its this one )

unzip it in ubuntu and install it.  It will take time ( not as easy as windows ).
i think this is what i did.  Also, somewhere, you have to change the model to toshiba.  I think...i don't remember too well.

---

### Post by mab1376 on 2008-01-06
i downloaded alsa-driver-1.0.15rc3

and ran these commands

tar xjf alsa-driver-1.0.15rc3.tar.bz2;cd alsa-driver-1.0.15rc3.tar.bz2
./configure --with-cards=hda-intel
make
sudo make install

and added options snd-hda-intel model=toshiba to /etc/modprobe.d/alsa-base

no luck...

---

### Post by bstoess on 2008-01-07
Your thread gave me the final missing piece to getting sound on my compal ifl90 w/ 7.10 and I wanted to fill you in on the other missing pieces.

This link was a good start [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
I did "Method E", downloaded the patch, but the rest of the instructions didn't quite get it to work.

[http://users.piuha.net/martti/comp/d630/](http://users.piuha.net/martti/comp/d630/)
from the advice of the above link I ran in the terminal: sudo aptitude install linux-backports-modules

Then I ran: sudo gedit /etc/modprobe.d/alsa-base

and added the line: options snd-hda-intel model=compal

I tried a bunch of other model names and could not get this to work. sKittles suggested using "toshiba" on your thread. I replaced compal with toshiba to the above options line, rebooted, and had sound!!

I hope this helps.

---

### Post by fenixartzz on 2008-01-07
look for backport-generic package and install that
should work i think

---

### Post by mab1376 on 2008-01-08
how do i install the patch?

---

### Post by tdayal on 2008-01-09
Sound is working for me, but with issues. I have the latest alsa (15rc3 I believe). 

When I mess with the options: 

**model=acer:** external speakers work but do not automute when headphones plug in. No separate sliders for speakers and headphones. No inputs work (mics or line-in)

**model=toshiba:** external speakers work but do not automute when headphones plug in. There are separate sliders in alsamixer so I can mute the external speakers while the headphones are on. Line-in does not work and the mics get incredibly soft and crackle-tastic recordings.

Anyone figure out recording yet??

---

### Post by marshaller on 2008-01-13
Hi

I found a swedish guy, that have maked a script to get sound working(here are his blog if you read swedish [http://ubuntu-bossieman.blogspot.com/2007/11/intel-82801h-ich8-family.html](http://ubuntu-bossieman.blogspot.com/2007/11/intel-82801h-ich8-family.html))

[http://www.mediafire.com/?1mht0lc3jzl](http://www.mediafire.com/?1mht0lc3jzl)

Dowload the file, right click, and allow to run as a program. dobel click an start it in terminal.

Its works great on my compal ifl91, but it works with a lot of compal build pc

the fill is called "zepto ljud" because compal is sold as zepto in scandinavia, and ljud is sound in swedish

---

