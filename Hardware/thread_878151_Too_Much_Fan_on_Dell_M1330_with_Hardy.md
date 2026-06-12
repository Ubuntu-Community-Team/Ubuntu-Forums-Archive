---
title: "Too Much Fan on Dell M1330 with Hardy"
date: 2008-08-02
forum: Hardware
---

### Post by bimargulies on 2008-08-02
I'm running Hardy on a Dell XPS M1330.

The fan is on. The machine is idle according to 'top', but the fan is on full blast.

I do use compiz, but no effects are happening right now.

How do I diagnose this?

---

### Post by rainwalker on 2008-08-02
I'm running Hardy on an Inspiron 8600 (not exactly the newest computer) with Compiz and the fan is almost alwasy humming for me. I don't remember if it did the same back before I used Compiz, but from my experience (and what I've heard in general) is that Ubuntu always seems to run a little hot on laptops.

---

### Post by bimargulies on 2008-08-03
1) It doesn't do this always. Rebooting sometimes makes it go away.

2) It's really not tolerable, so while I appreciate your commiseration, I'll leave this open in the hopes of more advice.

---

### Post by rainwalker on 2008-08-03
Ah, well if it doesn't happen a lot then I guess there is a problem

I'll let you know if I figure anything out :)

---

### Post by Valehru on 2008-08-13
What BIOS Version do you have and what graphics card do you have?

8800GTS cards have been found to be faulty, dell issued a new BIOS as a stop gap measure but the fan always seems to be on as a result on it's lowest setting. It will effect you if you are on BIOS version A15.  I find my graphics is always around 60 degrees plus with the fan constantly on and I'm on lowest graphics settings.

---

### Post by pognonec on 2009-09-28
I found a (weird) solution: in system/administration/harware drivers:
Shift from NVIDIA version 180 to NVIDIA version 173.
Et voilà!
Quiet again :-)

---

