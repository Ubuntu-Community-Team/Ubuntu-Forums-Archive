---
title: "Access Denied"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by P4r4b014 on 2009-02-16
When I try to install Ubuntu it gets about 1/4 the way loaded and then stops after twenty minutes or so I finally get a bunch of text all ending in ...access denied or something similar

i'm sorry for not being more specific but help is appreciated.

---

### Post by P4r4b014 on 2009-02-16
if it helps any it's p4 machine with 2gb ram and a really old graphics card, i'm upgrading from 7.10 which I had no problems installing way back when.

---

### Post by uberg on 2009-02-16
Can you provide a little more information.  Is this is a fresh install on the whole hard drive?  If not what does your partition table look like?  Info of this nature could help to isolate the problem.

---

### Post by P4r4b014 on 2009-02-16
yes, i'll reboot and jot down a what i see

---

### Post by P4r4b014 on 2009-02-16
I've tried installing with regular settings and in safe graphic settings

both ways it hangs up and i get this (after about ten minutes of a stuck loading bar):

segmentation fault
/etc.........: permission denied
(a bunch of different files i assume)
and at the end 
init: unable to execute '/bin/sh' rc-default
init: rc-default main process (7181) terminated with status 255

---

### Post by P4r4b014 on 2009-02-16
this is really pissing me off.

---

### Post by uberg on 2009-02-16
I am really sorry.  I know EXACTLY the frustration you are feeling.  i don't know what to advice you at this point.  Only make a few suggestions.  Did you test the CD for errors?  Check md5sum and all that?

---

### Post by P4r4b014 on 2009-02-17
I've tested the CD for errors and it found none.  What is md5 sum?

---

### Post by P4r4b014 on 2009-02-17
for some reason 8.04 kind of works

---

### Post by uberg on 2009-02-17
MD5 checksums are a way to check that the files you downloaded arrived correctly (no corruption).  If you had the CD check itself for errors this is what it does.  Checks all the MD5 checksums on all contained packages to make sure they aren't corrupted.  

If you have 8.04 running have you tried to do a system upgrade right from 8.04 rather than using the CD to install?

---

