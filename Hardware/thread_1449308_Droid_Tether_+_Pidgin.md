---
title: "Droid Tether + Pidgin"
date: 2010-04-07
forum: Hardware
---

### Post by pteri498 on 2010-04-07
I have tethering on my Droid working just fine through AziLink (in fact, that's how I'm writing this post). However, I think I'm lacking port forwarding or something, because I can't get Pidgin to connect to anything.

For example, MSN, which appears to work on port 1863, does not connect.

I tried this:
```
adb forward tcp:1863 tcp:1863
```

But I still get nothing from it.

Does anyone know what I'm doing wrong?

---

### Post by pteri498 on 2010-04-07
Ahh, got it!

I have my openvpn connection forwarding through 41927 (I guess; I'm just following the one tutorial that works with this that uses AziLink).

So I ran 1863 through 41927:

```
adb forward tcp:1863 tcp:41927
```

And now my MSN is connected!

Mind you, this was a shot in the dark (I could just as well have done it the opposite way), but this worked for me.

---

### Post by wigglez85 on 2010-10-09
I'm having trouble getting pidgin to run.

I tried forwarding it by changing adb forward
sudo adb forward tcp:1863 tcp:41927

but then it would refuse connection and not connect at all.

---

