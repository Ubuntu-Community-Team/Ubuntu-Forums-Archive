---
title: "Skype microphone issues on Gateway L2030u netbook"
date: 2010-01-01
forum: Hardware
---

### Post by Iyunkateus on 2010-01-01
For some reason, I'm not getting any output from echo123, the Skype microphone test. I've tested my microphone with Checkbox and it seems to be working fine. I've also googled around, but people with Ubuntu on the L2030u all say that everything works great, and everything does, except for this case. How could I fix this?

---

### Post by Iyunkateus on 2010-01-01
oh meh, bump

---

### Post by kluffinator on 2010-01-02
I've got a Gateway netbook as well, different model however.

Here's how I got Skype working.

1. Make sure Skype is off.
2. Open a terminal. 
3. Type in alsamixer 
4. Hit F4 so that View should be set to Capture.
5. Highlight Mic
6. Hit the z key so that the left bar volume is lowered completely but the right side volume is 100%.
7. Start Skype. Try the echo test.

Good luck!

---

### Post by rodspi on 2010-01-16
kluffinator

It worked like a charm on my Gateway LT3103U.  Had to crankup the mic setting to 65% for a descent level.

---

