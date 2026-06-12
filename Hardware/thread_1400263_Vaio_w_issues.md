---
title: "Vaio w issues"
date: 2010-02-06
forum: Hardware
---

### Post by gabrielcik on 2010-02-06
Hello,

Im using ubuntu 9.10 desktop 32bit on my Vaio W and everything seem to be fine except the front mic.

Any idea how to make it works?


Thank you in advance:)

---

### Post by gabrielcik on 2010-02-07
Hello,

I was able to make the internal mic of the Vaio W working in Ubuntu.

I had to add this line in alsa-base.conf

options snd-hda-intel model=auto

restart

then lunch alsamixer and select under <input so> int mic.

Now you can try to lunch Sound preferences and blow inside the mic
or more simply lunch Sound recorder:)


Thank you!

---

