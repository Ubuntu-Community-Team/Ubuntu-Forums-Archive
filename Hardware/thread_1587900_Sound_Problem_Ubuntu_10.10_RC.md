---
title: "Sound Problem Ubuntu 10.10 RC"
date: 2010-10-04
forum: Hardware
---

### Post by riddix on 2010-10-04
Hello,

i've a problem getting my 5.1 sound machine correctly running, but first some general Info:

Motherboard => Abit IX38-QuadGT
cat /proc/asound/card0/codec#* | grep Codec => Realtek ALC888

In Sound-Preferences, if i choose any "Analog Surround 5.1 Output" profile only my front speakers work, if i choose any "Analog Surround 7.1 Output" profile my front speakers and the woofer works, but no center and no rear speakers.

How can i add a custom profile to this list which make all my speakers work?

thx, greets rid

---

### Post by riddix on 2010-11-18
..., long time ago, new setup and still in trouble :-)

running the official 10.10 now. i solved the previous problem: goto sound preferences > hardware, choose the profile which fits best to your soundcard. In my case "Analog Surround 5.1 Output + Analog Stereo Input".

start a terminal > alsamixer and increase the "Surround" and "Center" volumes.

quite easy if you know what to do,... now if i test the speakers in sound preferences, every single one sings. But if i listen to godsmack theres is no bass, youtube no bass, VLC no bass,...  :_(

Can someone give me a hint?

thx rid

---

### Post by riddix on 2010-11-24
come on guys,... still no bass and i can't find any solution.
why does the test button in sound preferences make my woofer kick like it shoud, but nothing else??

---

### Post by riddix on 2010-11-27
installing the package "paconfig" solved the bass problem!

---

