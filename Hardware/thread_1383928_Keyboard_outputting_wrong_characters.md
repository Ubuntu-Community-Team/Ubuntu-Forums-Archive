---
title: "Keyboard outputting wrong characters"
date: 2010-01-17
forum: Hardware
---

### Post by okayneil on 2010-01-17
Hey guys, 

from one minute to the next ubuntu 9.10 is spitting out the incorrect character for the key. 

I have tried resetting the keyboard in the preference settings with no luck

Any ideas?

p.s the @ key has moved elsewhere and the # key.

---

### Post by byStanderone on 2010-01-17
...hard to tell, but perhaps you can isolate the problem by first using another keyboard that's functioning properly.

---

### Post by adam814 on 2010-01-18
Sounds like you might have more than one keyboard layout installed and you may have one of the keys to switch layouts set to something you're accidentally pressing.

Of course if you don't have multiple layouts installed I guess that can be ruled out.

---

### Post by okayneil on 2010-01-18
> **adam814 said:**
> Sounds like you might have more than one keyboard layout installed and you may have one of the keys to switch layouts set to something you're accidentally pressing.

Of course if you don't have multiple layouts installed I guess that can be ruled out.

I think i have accidently pressed something, and there are two layouts installed on the laptop. USA and UK(Default) I tried deleting the USA and resetting it to uk but no joy...

any ideas on how it can be fixed?

---

### Post by okayneil on 2010-01-19
Bump

---

### Post by adam814 on 2010-01-19
It's kind of a shot in the dark, but give this a try:
```
sudo dpkg-reconfigure xkb-data
```

---

