---
title: "[SOLVED] Did 8.10 Mess Up My 8.04 swap access??!"
date: 2008-11-01
forum: General Help
---

### Post by wilberfan on 2008-11-01
I did a clean install of Intrepid on a separate partition yesterday, and ever since, Hardy has been freezing up on me if I open too many apps!

I just noticed that if I boot into Hardy my gkrellm display shows no Swap usage!  If I click on that panel in gkrellm, it says:  "0M - 0M Free"

WTF!

Intrepid detected all of my other distros (XP, Sidux) and wrote a new GRUB to the MBR.  Does the grub affect swap assignments or something?

Booting into Intrepid shows Swap availability in gkrellm...

What could be going on here?

:confused:

[edit]  Booting into Sidux just now shows the same gkrellm swap display:  "0M-0M Free"

---

### Post by wilberfan on 2008-11-01
Okay.  Duh.

Intrepid reformatted the Swap file when it installed.  Which means it has a new UUID.

The fstab files for Hardy and Sidux had the OLD UUID.

Double Duh.

#-o

(I don't know a lot about how 'nix uses swap files--but I'm surprised it would boot without being able to mount one!)

---

