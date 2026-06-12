---
title: "Nforce drivers do not compile / SN85G4 / Nforce 3"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by ember on 2005-01-24
Hi again,

I'm trying to set up the Nforce drivers for my new shuttle barebone (SN85G4, Athon 64, running 32bit-Hoary-Array3). Yet I have not been able to compile them using the installer. I've attached the corresponding output from the installer. Maybe someone has an idea what I can do?

---

### Post by kunjan1029 on 2005-01-27
I am having the same problems.
 
 I do get sound whn the login screen is there but then i cant compile the nvsound module either same error as u.
 ----------------
 I am having some issues with my sound on nforce3-amd64 hoary system
 udev didnt create any /dev/dsp files there but i have
 /dev/snd/pcm*,controlC0 etc there
 
 what do i do to create /dev/dsp ????
 
 Thanks,
 K.

---

### Post by Arktis on 2005-02-05
I found a fix for this error.  [http://www.ubuntuforums.org/showthread.php?t=14266](http://www.ubuntuforums.org/showthread.php?t=14266)

---

