---
title: "No sound on Toshiba R500"
date: 2009-07-19
forum: Hardware
---

### Post by Itkovian on 2009-07-19
Hi, I'm new to linux and have just installed Ubuntu 9.04. Everything seems to be working, except that I have no sound.
Can anyone help me?

---

### Post by sarfarazkazi on 2009-07-19
Check the volume levels by clicking the Volume Control applet.

---

### Post by Itkovian on 2009-07-19
Yes, I've done that.
They are all at full, and none are muted.

---

### Post by tamerucar on 2009-07-19
Hi,

I had a similar no-sound problem on my Toshiba laptop and I managed to fix it. Check it out here:

[http://ubuntuforums.org/showthread.php?t=1208041](http://ubuntuforums.org/showthread.php?t=1208041)

Please notify me if it works for you or not.

---

### Post by Itkovian on 2009-07-19
Thanks for the advice, but unfortunately that doesn't seem to have helped.

---

### Post by Itkovian on 2009-07-20
Anyone got any other ideas?

---

### Post by Itkovian on 2009-07-20
Just to add:
```
lspci | grep -i audio
```
returns
```
0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```
and 
```
cat /proc/asound/card0/codec#* | grep Codec
```
returns
```
Codec: Realtek ALC262
```

---

### Post by Itkovian on 2009-07-26
Anyone?

---

