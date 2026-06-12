---
title: "Urgent, System Crashes after updating it."
date: 2009-10-03
forum: Hardware
---

### Post by noveus on 2009-10-03
Ive just installed my Ubuntu 9.10 and finished updating it, after rebooting, it crashes and here is a screenshot of it.
P/S : Meanwhile before rebooting it i always just installed my graphic card. nVidia 9600M GT

---

### Post by solar george on 2009-10-03
Thats not entirely crashed, its detected problems with your file system and had dropped into a command line to give you the chance to fix it.
try running:
```
fsck /dev/sda5
```
And answering yes to all the questions (NOTE: this may mean you've lost data but i'm sure you won't have anything imporant on a machine running a beta :)

---

### Post by noveus on 2009-10-03
Im sorry im just being panic. Ill give it a try, Thank You. Please wait for my reply cause im afraid ill need further assistance.

---

### Post by noveus on 2009-10-03
Hey thanks lot, im now replying using ubuntu. Im wondering how you even know that code. -.-

---

### Post by solar george on 2009-10-03
> Hey thanks lot, im now replying using ubuntu. Im wondering how you even know that code. -.-

Glad it worked, the line on your screen in ALLCAPS tells you that fsck (filesystem check) has failed and to run it manually, thus the fsck command, at the start of the line it tells you which drive its failed on (/dev/sda5) thus you can work out that you need to run.
> fsck /dev/sd5
As for the answering yes thats just 'cause it won't try to fix your system without your permission.

---

