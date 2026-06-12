---
title: "e2fsck: 2 hours and 1.49% done"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by Los Frijoles on 2008-12-14
The other day my friend's computer failed to boot windows with the bluescreen error: "Failed to mount root partition". So, I got in using backtrack, copied his files onto a flash drive, and proceeded to install ubuntu as an alternate os until he could get his windows cd from back home (assuming he didn't decide to keep ubuntu). The first several attempts failed until I deleted the MBR which then allowed me to install ubuntu. Then, the computer operated really slow. Hard drive operations took eons to complete and the system commonly labled programs as crashed. I attempted to restart the computer, but that didn't work so I did a hard shutdown. That caused the system to scan the drive. It would stop scanning around 10-15% with some error about getting a short read on the root sector. So, I decided to use e2fcsk -c to mark bad blocks and hope that there would be enough good blocks to run ubuntu and hold the hard drive over until we could buy a new one.

e2fcsk has now been running for over 2 hours and is not even 1.5% complete. The hard drive is 120Gb and its a dual core AMD processor so I really don't think it should have taken this long. It (the hard drive) also periodically makes strange beeping noises and about every 5 seconds or so it spits out an ata error interspersed with a few buffer i/o errors.

btw, the computer is a crappy Dell Vostro 1000 that he got for $350 on a black friday sale last year.

Do you guys think this hard drive is dead?

---

### Post by sukhhari on 2008-12-15
If Still your have Warranty on HDD, then why? don't you give HDD to Dell Company for repairing.

---

