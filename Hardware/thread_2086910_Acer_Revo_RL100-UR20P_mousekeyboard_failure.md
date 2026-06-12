---
title: "Acer Revo RL100-UR20P mouse/keyboard failure"
date: 2012-11-22
forum: Hardware
---

### Post by evanb on 2012-11-22
This box has a wireless combination keyboard and mouse, where one switches between the two functions on a single track pad. When I install (or run from a live CD) a 64-bit version of the O/S, the track pad's mouse functionalty works until I switch to the keyboard. Then, one keypress and the computer no longer responds to either keyboard or mouse input. I've tried Lubuntu 12.04 and 12.10, but I believe the problem is not specific to Lubuntu. 32-bit *buntu works fine.

Stranger yet, both keyboard and mouse track pad functions work fine in the installer. It's only after the O/S starts that problem manifests.

What I'm looking for is help in determining what mouse and keyboard drivers *buntu is using, and how I might influence that choice. I could just install the 32-bit O/S and be done with it, but I'd like to see if I can get the 64-bit version to work.

-evan

---

### Post by sahabcse on 2012-11-22
Paste the o/p of 

dmesg 
dmesg | grep mouse

---

### Post by evanb on 2012-11-23
This forum's rather fussy attachment tool won't accept the files w/o extensions, and won't accept the dmesg capture as a text file, so I've attached them in a compressed archive.

-evan

---

### Post by evanb on 2012-11-23
After I uploaded the previous attachment I realized I had booted the computer w/ a second keyboard plugged in, to ensure I would have a working one. Between that attachment and this one I installed updates and unplugged the second keyboard.

-evan

---

