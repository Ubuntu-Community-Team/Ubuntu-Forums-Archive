---
title: "Memory Not Recognized"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by misterfixit on 2009-03-22
OK, I've searched here with all kinds of key words, but nothing comes up for me when I look for "Memory Not Recognized" or variants there of.

I just stuck in a couple of DDR2 2GB sticks in addition to the already installed 2x 1GB DDR2 sticks.  Cold boot and BiOS says I now have 6 GB.  When fully booted, Ubuntu says I still have the original 2GB.

Seems that I recall there used to be problems along this line of not recognizing added memory.

Anyone want to help me out here?

P.S.  Wonder if I am using the wrong keywords to search for an answer to this question??

---

### Post by misterfixit on 2009-03-25
Bump, anyone.  No, not THAT kind of bump!  Bump as in does anyone have a clue?

---

### Post by WakkiTabakki on 2009-03-25
It could be of two reasons (that I can think of anyway):
- Faulty memory modules, try running memtest on it (included on the Live-CD) 
- If you're running a 32-bit operating system, the limitation in address space (due to the 32-bit architecture) limits usable memory to roughly 3Gb. I have 4Gb in my laptop, but Ubuntu only recognizes 3 of them (waiting for Jaunty to migrate to 64bit...)

/N

---

### Post by misterfixit on 2009-03-25
> **WakkiTabakki said:**
> It could be of two reasons (that I can think of anyway):
- Faulty memory modules, try running memtest on it (included on the Live-CD) 
- If you're running a 32-bit operating system, the limitation in address space (due to the 32-bit architecture) limits usable memory to roughly 3Gb. I have 4Gb in my laptop, but Ubuntu only recognizes 3 of them (waiting for Jaunty to migrate to 64bit...)

/N

Thank you for the very quick response.  After reading your reply I did a search for  "memory limitation" and got the same answer.  Seems I wasn't using the correct search terms to find my answer.

I appreciate your assistance!.

Regards,
Dave

---

