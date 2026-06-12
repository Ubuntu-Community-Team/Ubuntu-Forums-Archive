---
title: "No Sound, Acer Aspire 6920, 9.04"
date: 2009-04-24
forum: Hardware
---

### Post by Changturkey on 2009-04-24
I had sound working during the LiveCD, but as soon as I installed 9.04, sound did not work. Why?

---

### Post by executorvs on 2009-04-26
ok I've got two approaches which worked on mine and a friends aspire 6930s.

first is to make sure your sound is on. this may sound dumb but for some reason on a few computer the default volume is at zero.

 just left-click the speaker icon in the upper right of you screen then click where it ays volume control. make sure you see master, front, and headphone. if not click preferences and make sure they are checked. preferences will bring up a different list for each item selected in the drop down.

the other one is to edit your alsa file.
go to: 
/etc/modprobe.d/alsa-base 
then add the line:
options snd-hda-intel model=auto 

where it says auto you may get better results by changing it to read "acer" or "ACER" or one of a few other variants mentioned in the alsa documentation which I can't recall.

I'm not sure how similar the 69020s and 6930s are but try loking at the info on [http://www.linlap.com/wiki/acer+aspire+6930#comment_40b3742fdf6e4bbeccaf810b349e90e9](http://www.linlap.com/wiki/acer+aspire+6930#comment_40b3742fdf6e4bbeccaf810b349e90e9)

hope this helps.

---

