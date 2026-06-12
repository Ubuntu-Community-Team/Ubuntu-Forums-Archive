---
title: "Finding my Soundcard's Name"
date: 2009-06-23
forum: Hardware
---

### Post by cell_son on 2009-06-23
I'm trying to install an HD internal speakers driver, but part of the installation process is to run "modprobe snd-xxxx, with xxxx being the name of the soundcard."  However, I can't figure out what the name of my soundcard is... could anyone help me out?

---

### Post by syrex314 on 2009-06-23
Have you tried lspci on the command line?

---

### Post by 73ckn797 on 2009-06-23
> **syrex314 said:**
> Have you tried lspci on the command line?

Go to Applications/Accessories/Terminal.
enter:
```
lspci
``` Look for audio device line. The brand will be listed there.

You can highlight the info, copy (ctrl-shift-c) and paste into a reply if you have any questions.

---

### Post by cell_son on 2009-06-23
I did that and it says I have an Intel Corporation 82801I (ICH9 Family) HD Audio Controller, and when I plugged that into "modprobe snd-xxxx," the command line told me that Intel wasn't a command.

---

### Post by 73ckn797 on 2009-06-23
> **cell_son said:**
> I did that and it says I have an Intel Corporation 82801I (ICH9 Family) HD Audio Controller, and when I plugged that into "modprobe snd-xxxx," the command line told me that Intel wasn't a command.


I have not had to perform what you are trying to do but maybe try, instead of the name, use the number "82801I".

Have you looked here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by syrex314 on 2009-06-23
modprobe snd-hda-intel

---

