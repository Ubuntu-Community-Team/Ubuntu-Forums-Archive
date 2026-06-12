---
title: "HP Pavillion tx1205us - Startup issues"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by winless on 2007-09-09
I recently purchased an HP Pavillion tx1205us.  I've installed Ubuntu 7.0.4 (dual boot w/ XP pro)  The system boots into Grub just fine but when I choose to boot into Ubuntu it will get to the load screen w/ the Ubuntu logo and then after that, the screen fades to white and then goes black.  Trying to boot into recovery mode won't work either.  It stops after the following messages:

"CPU#0 had -216 usecs TSC skew, fixed it up."
"CPU#1 had 216 usecs TSC skew, fixed it up."

This system has an AMD Turion 64x2.  I haven't tried the AMD 64 version yet.  I used the Ubuntu 7.0.4 alternate i386 version but will be trying the AMD version next.  My video chip is an NVidia GPU, the Geforce Go 6150.

Any and all help would be greatly appreciated.

Thanks

OK, Just tried the AMD 64 version and got the exact same results as listed above.

---

### Post by ddrichardson on 2007-09-10
I don't know if this will help but I needed to specify the noapic option at boot to get Ubuntu to run on my tx1250ea.

---

### Post by winless on 2007-09-10
Hmmm.... I think I ran across something like that in one of the forums...  I think the  solution was to append "noapic vga=0x317" to a line in the start up sequence.  that didn't seem to work for me  either though I may give it another shot.  Thanks for the reply!

---

### Post by ddrichardson on 2007-09-11
I haven't read through this yet but [here]("http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z") is someones experience with the TX1000 series.

---

