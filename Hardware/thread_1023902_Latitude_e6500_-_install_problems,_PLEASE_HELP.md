---
title: "Latitude e6500 - install problems, PLEASE HELP"
date: 2008-12-28
forum: Hardware
---

### Post by DJpattiecake on 2008-12-28
OK so here goes.

I got a new latitude e6500 2.4 c2d, 4gb ddr2

The second I get it I pop in my linux mint (based on ubuntu) cd and try to live boot/install.

First off, just to live boot i have to try repeatedly because it either says Kernel Panic: attempt to kill init, and sits there, or it comes to a prompt of (initramfs) _ and does nothing.  FINALLY i manage to randomly get into live boot, and i start installing, and i get the following messages

The following file did not match its source copy on the CD/DVD
(filename) abort/retry/skip?

it does this over and over and i can hit retry repeatedly and it seems like it goes thru because it moves on to other files. However, after doing this for about 10 minutes it freezes up.

Googling the init kill and file not matching issues says the problems are usually bad memory modules.

I ran the dell diagnostics with extended memory tests, and ALL PASSED, wtf.
I ran PC-Check from Geek Squad MRI, and memory stride 1 and Memory Topology tests fail on BOTH dimms.

I tried 2 dimms from a different working computer, and got the same init kill and file copying errors.

Dell says theres nothing wrong unless dell diags says there is, and they dont support 3rd party testing, which is ******** because I work at best buy and we do warranty work on dells.

I tried to install with 32 bit linux mint 6 felicia, as well as 32 & 64 bit ubuntu 8.10. I did not try wubi with either, but I assume results would be similar.

And when i try to install windows XP or vista i succeed only sometimes, because it randomly blue screens during install.

I think there is something wrong with my dimm slots or memory controller. Please anyone offer their 2 cents and previous experience with dell. How can I make them accept this thing for a warranty repair if they worship their dell diagnostics so much? (which dont work apparantly)

---

### Post by DJpattiecake on 2008-12-28
has anyone else had experience with these errors before?

my ram tests ok on ramtest for 8 hours but still fails ram tests on PC check. i made dell accept the fact that its prolly my motherboard and got approved for a new mobo under my warranty

---

