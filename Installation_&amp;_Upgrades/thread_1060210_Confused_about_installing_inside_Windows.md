---
title: "Confused about installing inside Windows"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by GTengineer on 2009-02-04
Hey everyone,

I was under the impression that by choosing the option "Install Inside Windows", you are really installing Ubuntu as a Virtual OS and not a native OS. Is that not correct?

I would like to run Ubuntu natively but I only have a single partition in my HDD of my work computer and I would rather not wipe out Windows unless I absolutely must. I have always partitioned my HDD manually before when installing Ubuntu so I am wary of letting Ubuntu mess around with my Windows partition.

Can anyone clarify this?
Thanks!

---

### Post by RedSingularity on 2009-02-04
If you install inside windows you can easily remove it anytime you want.  It still installs grub to the MBR but once you use windows Add/Remove to take it out the Grub MBR comes with it.  Sounds to me like thats the better way to go in your case.  Makes life nicer if you need to take it off at any time.

---

### Post by GTengineer on 2009-02-04
Shadow, thanks for the reply. However I still would like to know if it is run as a virtual OS or natively. I plan to run number crunching on Ubuntu and I was under the impression that a virtual OS would degrade performance.

---

### Post by RedSingularity on 2009-02-04
No its considered native as far as i know.  You will have to boot into it.  You cant access it from within windows like a Virtual OS.  It slightly degrades performance but its really only noticeable if your gaming.  And looking at your PC specs......i dont think you should worry. :)

---

### Post by GTengineer on 2009-02-04
> **Shadow121 said:**
> No its considered native as far as i know.  You will have to boot into it.  You cant access it from within windows like a Virtual OS.  It slightly degrades performance but its really only noticeable if your gaming.  And looking at your PC specs......i dont think you should worry. :)

ok cool, I guess that will do then. It is actually not going into the machine in my sig but into a decently powered dual core Penryn 2.53GHz. Many thanks!

---

### Post by avtolle on 2009-02-04
Just a quick note: the only slight difference that I found with a Wubi install was HDD access being a bit slower (not really noticeable to me most of the time). Otherwise, the system is running natively and quite "sprightly", if I may say so. Good luck, and remember the Wubi sub-forum for further questions about Wubi (not Ubuntu, once installed).

---

### Post by GTengineer on 2009-02-04
> **avtolle said:**
> Just a quick note: the only slight difference that I found with a Wubi install was HDD access being a bit slower (not really noticeable to me most of the time). Otherwise, the system is running natively and quite "sprightly", if I may say so. Good luck, and remember the Wubi sub-forum for further questions about Wubi (not Ubuntu, once installed).

excellent, thanks! I can deal with a small hit on HDD performance.

---

