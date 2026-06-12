---
title: "Ubuntu UEFI doesn't boot with new RAM stick"
date: 2014-11-03
forum: Hardware
---

### Post by fondatommaso2 on 2014-11-03
Hi,
I've just installed Ubuntu 14.10 in UEFI mode on my Samsung R530 JA04, which is a 2009 laptop. Despite being quite old, it has got UEFI v2.00 by Phoenix Technologies.
Ubuntu booted fine, but when I inserted my new 2GB RAM stick into my laptop it stopped booting normally. The laptop has got 2+1 GB of RAM, I've bought a 2GB stick that must take the place of the 1 GB stick in order to have 4 GB of RAM. When I turn on the PC with 2+2 GB of RAM I see grub, after selecting ubuntu it says "No suitable video mode found. Booting in blind mode" 2 times, then the boot process hangs there. Nothing happens. With the previous configuration (2+1GB of RAM), I still see those "blind mode" errors but then Ubuntu starts normally.
Where is the problem?
Thank you

---

### Post by Bucky Ball on 2014-11-03
Can you boot into the BIOS and just check the 4Gb is being recognised, please?

Another thing to try is one by one. Stick in a ONE 2Gb stick and see if you have the problem. If not, take that out and stick in the other one. Make sure the RAM is seated in the slot properly. Sometimes you need to give where you push it in a quick rub with an eraser (not hard, sounds crazy, but has worked for me). They can have factory gunk on there which spoils the connection.

Just to clarify:

You added two 2Gb sticks of RAM;
You booted the machine and installed Ubuntu 14.10 (no Windows?);
Install worked fine, now when you boot first time hangs after the message?

---

### Post by fondatommaso2 on 2014-11-03
> **Bucky Ball said:**
> Can you boot into the BIOS and just check the 4Gb is being recognised, please?

Another thing to try is one by one. Stick in a ONE 2Gb stick and see if you have the problem. If not, take that out and stick in the other one. Make sure the RAM is seated in the slot properly. Sometimes you need to give where you push it in a quick rub with an eraser (not hard, sounds crazy, but has worked for me). They can have factory gunk on there which spoils the connection.

Just to clarify:

You added two 2Gb sticks of RAM;
You booted the machine and installed Ubuntu 14.10 (no Windows?);
Install worked fine, now when you boot first time hangs after the message?
Yes, I installed with 4GB of RAM, didn't boot, then I put in 3 GB of RAM and it booted. I've got no Windows.
The machine boots with the new ram stick only.
What is really strange is that a copy of Ubuntu installed in BIOS mode boots with 4GB of RAM. Really odd. It looks like it refuses to boot in UEFI mode if RAM is >3GB.

---

### Post by sudodus on 2014-11-03
I suggest that you test your memory with memtest (at the grub menu or from the install drive). There may be something wrong, that creates problems only in some special situations. Run memtest for a long time (for example overnight). One single error is too much.

---

### Post by kurt18947 on 2014-11-03
Bucky Ball has given you good advice. Try to boot with just one 2 GB. SODIMM (I presume) installed.  If it boots, shut down, remove that SODIMM and install the other one.  Try to boot again. You're checking to see if you have a bad memory board.  If your machine boots with each stick individually but not both at the same time then I don't really know.  It'd seem like something with the BIOS and I know nothing about UEFI.  You could also run memtest X86 found on most live DVD/USBs for a few hours with each SODIMM installed if you want to test each piece once it boots. I run memtest on each new piece of DRAM I install.  Finding intermittent errors early can save much frustration.

Edit:  I see Sudodus beat me to it.  Great minds think alike and all that :-).

---

### Post by fondatommaso2 on 2014-11-04
I ran the memtest last night and the result was: 7 passes, 0 errors. I'm sure it's not a hardware-related problem, because the two SODIMM modules work fine together when booting a system in BIOS mode. The new 2 GB module works alone, I'll try the old 2 GB module and I'll let you know.

---

### Post by sudodus on 2014-11-04
The two RAM sticks might be OK (both of them), but might not cooperate, if they are built for different internal speed, or there is some glitch in the handshaking. 

But it might also be some problem with the UEFI/BIOS system. If you are lucky, there is an updated version for your motherboard.

---

### Post by Bucky Ball on 2014-11-04
Ah, they are not a matched pair! That could have something to do with it. And as sudodus suggest, may also be an issue in BIOS ...

---

### Post by fondatommaso2 on 2014-11-05
> **Bucky Ball said:**
> Ah, they are not a matched pair! That could have something to do with it. And as sudodus suggest, may also be an issue in BIOS ...
No, one 2GB stick is Samsung, the other is Corsair. The new 2 GB Corsair stick works with the old 1GB stick by Samsung, so
1. There are compatibility problems between the old and the new 2gb sticks _only in UEFI mode_ (but not between the new 2gb and the old 1 GB stick)     OR
2. My laptop's UEFI blocks system from booting when RAM=4GB, but disabling UEFI solves this problem.
Honestly, for me the 2nd option is more likely to be cause of my problem.

---

### Post by sudodus on 2014-11-05
If you are lucky, there is an updated version of the UEFI/BIOS system for your motherboard.

---

