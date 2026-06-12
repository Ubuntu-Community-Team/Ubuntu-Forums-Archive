---
title: "no bios access on free dell laptop"
date: 2008-08-06
forum: Hardware
---

### Post by ivandewolf on 2008-08-06
I got a FREE laptop (woohoo) from a canadian phone company. 
It's a dell inspiron 1525 and it came with vista (waaa!). i tried the vista- it's worse than I feared.
I want to put ubuntu on it, so I tried to make the CDrom the first boot option, but there's some weird BIOS on there. 
only 2 options: boot vista or do a memory test.
Any suggestions? anybody else seen this?

any cure? or did I get a free doorstop?

---

### Post by Megatog615 on 2008-08-06
You might be trying to load the BIOS at the wrong time and loading one of Windows' troubleshooting menus instead.

Some Dell machines have bios' that don't display any "Press the 'X' key to enter BIOS" message.

When the first screen appears(should be a big "DELL" logo), try all the F keys in quick succession, then try the Delete and Escape keys. One of them will get you to the BIOS.

---

### Post by ivandewolf on 2008-08-06
well, wadda ya know! it worked!! 
pecked fervently at that F like a chicken in a skinner box, and got the actual BIOS instead of the DELL bootloader- got the ubuntu disk to try (and fail) to boot! on to the next issue....

---

### Post by jualin on 2008-08-06
What do you mean it failed to boot?

---

### Post by ivandewolf on 2008-08-06
well, the disk starts to boot. It has that splash screen and I choose "install or boot ubuntu", it tries, and then it dies.

---

### Post by howlingmadhowie on 2008-08-06
maybe you should start a new topic about this and mark this one as solved.

---

### Post by Megatog615 on 2008-08-06
It dies with... what? Error message?

---

### Post by ivandewolf on 2008-08-06
something like 
/bin/sh: cannot access tty

it then gives me a command prompt with a fairly minimal set of commands.
I can try ahrdy heron or centOS tomorrow.

---

### Post by jualin on 2008-08-07
Check the Cd for defects, maybe the CD has some errors.

---

