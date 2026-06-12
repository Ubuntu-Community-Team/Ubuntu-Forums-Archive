---
title: "audio port not functioning"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by odysseus.lost on 2007-07-17
Strangest of problems.... sounds works fine... however, when i plug in my headphones to the headphones audio port there is no sound coming out (from the headphones of course). System is an asus a6000 with feisty 7.04. Headphones are good and port is also good as it is working under win xp. Any clues? Cheers

---

### Post by odysseus.lost on 2007-07-17
OK, here is the solution
Only the SPDIF OUT must be configured for listen music on headphones. For do this U need to insert this line at the bottom of file /etc/modprobe.d/alsa-base, and then make a restart

options snd-hda-intel model=z71v position_fix=1

Thanks to the following post:
[http://ubuntuforums.org/showthread.php?t=168793&highlight=alc880+spdif](http://ubuntuforums.org/showthread.php?t=168793&highlight=alc880+spdif)

If the above fails then maybe the following post might be of help:
[http://ubuntuforums.org/archive/index.php/t-76307.html](http://ubuntuforums.org/archive/index.php/t-76307.html)

---

### Post by chillfaktor on 2007-07-19
Hi there,

i just installed ubuntu (thus clueless) and ive got a couple of questions:

1. what are the chances that this fix works for me? ive got a completeley different laptop
2. how do i change the permission of alsa-base so i can edit and save it? 

Thanks

edit: oh, now the whole file is gone!

---

