---
title: "Ubuntu Desktop 9.04 Try without installing error."
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by baha24 on 2009-06-30
Computer: Compaq Presario CQ60-210US Notebook PC
Processor:  2.0 GHz AMD Athlon X2 QL-62 Duel-Core Processor
Hi! I am trying to try out Ubuntu on my Compaq Presario. I downloaded the .iso file and did the md5 checksum, which was correct. Once I restarted the my computer and booted the live cd I was shown the Boot menu where I selected Try without changing your computer. After selecting it I was shown a loading screen, when completed it turned into a black screen with my mouse. Any ideas how I can get this working?

---

### Post by merlinus on 2009-06-30
Did you burn the .iso at 4x or slower speed?  If so, you might try pressing F4 at the opening menu and selecting safe video mode.

---

### Post by baha24 on 2009-06-30
yes I burned it at 4x and when I do graphics safe mode it still stalls after loading.

---

### Post by merlinus on 2009-06-30
Try the boot options when the opening menu appears, and add 

noapic nolapic

to the end of the boot line.

---

### Post by baha24 on 2009-06-30
that didn't work it gave me a error

---

### Post by merlinus on 2009-06-30
What kind and model of video card do you have?

---

### Post by baha24 on 2009-06-30
I have a NVIDIA GeForce 8200M G

---

### Post by merlinus on 2009-06-30
This should not be a problem.  Did you check the cd for errors at the opening menu?

---

### Post by baha24 on 2009-06-30
Yes but when it finishes It restarts.

---

### Post by merlinus on 2009-06-30
You might try reburning it or on another computer, as the cd or drive may be defective.

---

### Post by baha24 on 2009-06-30
so reburn it on another computer? or reburn it on this one?

---

### Post by merlinus on 2009-06-30
Try it first on another computer, and if it works then you know it may be your cd drive.

If it still does not work, then you know it is almost certainly the cd.

---

### Post by baha24 on 2009-06-30
when doing a disk integrity check is it supposed to restart at the end?

---

### Post by merlinus on 2009-06-30
I do not recall, but it should at least give you a message that no errors were found.  Again, the easiest test is to try it on a different machine.

---

