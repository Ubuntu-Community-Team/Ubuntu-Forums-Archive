---
title: "trying to install rme multiface II"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by salatmensch on 2007-09-22
greetings,

i am trying to install rme's multiface II on ubuntu studio feisty fawn.

the standart install of ubuntu configures only the onboard soundcard of my laptop (samsung x-20 -> intel ich6). the rme soundcard is listed in ubuntu's device manager.

i tried to manually compile the hdsploader provided by the alsa-tools. however it said it could not find a compatible version of libasound.

any ideas?

best,
salatmensch

---

### Post by salatmensch on 2007-09-22
strangely,
i can't find the typical configuration files on my system. no ".asoundrc" and no "asound.conf".

hm...

---

### Post by salatmensch on 2007-09-22
when i go to

/proc/asound/

the cards and devices file is empty. the folder card0 seems to include files to connect to a standart ac97 codec, card1 contains only 2 empty files.


by the way, i am using a multiface II connected via the pcmia interface provided by rme.

---

### Post by salatmensch on 2007-09-22
ok,
i got it to run now. i just typed in hdsploader and ubuntu found a already compiled version of the loader.

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

