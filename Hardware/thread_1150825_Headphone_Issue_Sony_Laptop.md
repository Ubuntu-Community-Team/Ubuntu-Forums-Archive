---
title: "Headphone Issue Sony Laptop"
date: 2009-05-06
forum: Hardware
---

### Post by lex0429 on 2009-05-06
I have seen there are many others with this problem and have gone through all the fixes on this forum and many others but i cant get mine working...

With that said any help will be greatly appreciated, i have pulled my hair out over this for weeks and until i get it fixed i still have to boot into windows if i want to watch a movie or something on the train :(


I have a Sony Vaio VGN-TT190 notebook running 8.10, everything works great but when i plug in headphones the sound still comes out the notebook speakers. i have tried editing the /etc/modprobe.d/alsa-base file adding in the following lines and rebooting but still nothing changes...

options snd-hda-intel model=sony
options snd-hda-intel model=vaio
options snd-hda-intel model=auto

If anyone can help me with this i will greatly appreciate it. I also tried the upgrade to 9.04 thinking that might help but didnt and i went back to 8.10

---

### Post by b6of12 on 2009-05-06
try and compile the latest version of alsa 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) here is a guide or just google
compiling alsa on ubuntu this helped me

---

### Post by lex0429 on 2009-05-06
i went there already which lead me to [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) which lead me to [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

i used that script, it did its thing, rebooted and still same issue

---

