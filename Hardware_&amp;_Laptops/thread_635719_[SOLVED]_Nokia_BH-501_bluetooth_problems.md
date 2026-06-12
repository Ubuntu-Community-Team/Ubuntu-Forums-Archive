---
title: "[SOLVED] Nokia BH-501 bluetooth problems"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by ksadil on 2007-12-09
Hello,

I am trying to use the bluetooth applet and my Nokia 6120 connects via bluetooth just fine, but my BH-501 bluetooth headset will not connect. I have read quite a few "guides" and it gets complicated as they are written at different points in time, hence certain parts are obsolete. Can someone please help. I think I have everything related to bluetooth installed including bluez-utils 3.19, but I still get :

Couldn't display "obex://[00:0d:3c:a6:85:91]".

and my ~/.asoundrc contains:

pcm.bluetooth {
type bluetooth
device 00:0D:3C:A6:85:91
}

Any ideas?

PS Gutsy i386 desktop on a Asus f3sv laptop and I can send files between my phone and the laptop

Cheers
Kim

---

### Post by ksadil on 2007-12-09
it was not exactly elegant, but the kde bt tools worked for my device. Solved !

---

### Post by steveneddy on 2007-12-09
Would you mind marking this as **SOLVED** please?

---

