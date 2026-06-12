---
title: "No sound with VIA8237 sound device"
date: 2008-05-11
forum: Hardware
---

### Post by chiten on 2008-05-11
Hi! i have installed ubuntu 8.04 and have no sound. It recongnizes the soundcard, but i can't get any sound. Never had this problem with older Ubuntu versions. Dont know what to do, what can i do? thanks!

.....and sorry, my english it is not good :(

---

### Post by Pettman on 2008-05-11
Have you tried to open a terminal, run alsamixer and made sure nither Master nor PCM is at the bottom or muted?

---

### Post by chiten on 2008-05-11
yes i did that, but everything seems to be fine....thanks for your reply :)
[IMG]http://i30.tinypic.com/b5pe7m.png[/IMG]

---

### Post by Pettman on 2008-05-13
> **chiten said:**
> yes i did that, but everything seems to be fine....thanks for your reply :)
[IMG]http://i30.tinypic.com/b5pe7m.png[/IMG]

I've spotted a possible cause of the error; It's PCM that looks like it has been muted, use the arrow-keys to select PCM and press m onec and it should work (the MM under the bar means muted).

---

### Post by chiten on 2008-05-13
:( sorry...didnt see that ](*,)...really thanks!! \\:D/

---

