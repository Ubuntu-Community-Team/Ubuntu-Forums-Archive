---
title: "Rollback an ubuntu auto update"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by untitledtv on 2009-07-01
I just did an ubunutu auto update and now my USB wireless doesn't work.

I went and did a GRUB to the next kernel down, still doesn't work.

Help?!  I don't want to do yet another clean install to get the wireless piece working, it's not longer recognizing the USB hardware.

---

### Post by Idefix82 on 2009-07-02
What did you have to do to get it working in the first place? What is the wireless card? What is the output if you type
```
lshw -C network
```
in the terminal?

---

### Post by untitledtv on 2009-07-02
Nevermind -- I did the rollback of the install of lsbase and lsrelease...it totally messed things up and then forcing the old package back from synaptic saved the day!  I think I turned off the updates to prevent this...thank goodness for the rollback feature!

---

