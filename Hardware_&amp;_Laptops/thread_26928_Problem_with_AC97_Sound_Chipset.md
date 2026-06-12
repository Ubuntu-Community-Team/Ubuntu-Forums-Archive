---
title: "Problem with AC97 Sound Chipset"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by bibao76 on 2005-04-14
I've installed KUbuntu on my new Targa Traveller 826 and it works fine. The problem is the sound system, it works in a really strange way.  My card is **ATI IXP rev 1 with ALC658 at 0xfbdfc800, irq 5**. Alsa recognize my card but sound works only by hearphones jack instead of notebook speaker. Can anybody help me?

---

### Post by StephenTidey on 2005-05-27
Greetings,

Have you found an answer to this problem as it's one of the remaining one's I'm suffering from with my Targa :-)

---

### Post by Data on 2005-07-16
So, has anybody sound running on a Targa Traveller 826?

I would be interested, how to achieve that! I cannot make it work...

Data

---

### Post by Data on 2005-09-02
Indeed it needs a patch to the kernel resp. the alsa modules.

I have attached a patch, which worked fine for me with the 2.6.13 kernel. It will be in the new alsa drivers.

Data

---

### Post by GsmCyber on 2005-11-29
how can i use that patch?! i've the same problem :(

---

### Post by Data on 2005-11-30
The patch is incorporated in linux-2.6.14. A patch for linux-2.6.13 is attached.

Data

---

