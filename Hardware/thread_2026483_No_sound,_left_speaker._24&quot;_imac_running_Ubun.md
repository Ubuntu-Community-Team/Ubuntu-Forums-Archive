---
title: "No sound, left speaker. 24&quot; imac running Ubuntu 12.04"
date: 2012-07-15
forum: Hardware
---

### Post by dbrace on 2012-07-15
I have a 24 in iMac running Ubuntu 12.04 exclusively. I have sound from the right speaker, but none from the left. Any idea of how to fix this? It makes watching movies sound kinda crappy. Ah btw, I am running 64bit.

---

### Post by robtygart on 2012-07-15
> **dbrace said:**
> I have a 24 in iMac running Ubuntu 12.04 exclusively. I have sound from the right speaker, but none from the left. Any idea of how to fix this? It makes watching movies sound kinda crappy. Ah btw, I am running 64bit.

Go to your sound settings and check your balance.

---

### Post by dbrace on 2012-07-15
Hm, ok, not sure when I moved the balance to the right. Sound quality is still comparably worse than when I was running OS X. Any ideas?

---

### Post by robtygart on 2012-07-15
That happened when you had OSX on it too?

If so I would guess bad spkeaker or lose connection.

Try pluging in earphones and see how it sounds.

---

### Post by dbrace on 2012-07-15
No, the sound was fine on OS X. It sounds like I am in a tin can now.

---

### Post by jmfal on 2012-07-15
Welcome to Ubuntu

Open alsamixer in a terminal
```
  alsamixer     
```

Press F5(all) turn down PCM if there is a control for it and increase volume controls for all speakers,
You will have to play around till it sounds right.
When you have it setup how you want it 
Press "esc" and at command prompt enter
```
  sudo alsactl store   
```
To set mixer
If you close mixer you will lose settings and have to start over.

---

