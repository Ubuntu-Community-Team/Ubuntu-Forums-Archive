---
title: "HP Pavillion Does Not Boot"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Ceiling Fan Man on 2009-05-26
I have a friend who wants to get into Linux, so I stopped by his house with an assortment of Ubuntu discs to set up his HP Pavilion a705W. Neither LiveCDs for Intrepid nor Jaunty would start the installation, so I used the Jaunty AlternateCD. This installed just fine. Upon first boot into the OS on his HDD, the progress bar gets to about a fifth of the way and freezes, never moving. Worthy of note: This is the same position the bar would freeze on either of the LiveCDs when trying to start the installation process.

  Judging by the part number, a705W, the computer was purchased from a Wal-Mart location. Wal-Mart get's their very own part number, because the computers are built to Wal-Mart specifications. The Motherboard is a no-name, not the MSIs normally (To my knowledge normally, anyway) found in an HP. I'm not sure if this has anything to do with it. Also, I have his DXDiag information from Windows should anyone need some more system information to help us out here.

  Can Ubuntu be made bootable on his PC? How would I do it?

Thanks in advance.

  Note: I don't have full-time access to the computer, so please bear with me.

---

### Post by Sub101 on 2009-05-26
Do you know what process it hangs on?

Try booting in the recovery mode and check the processes that load.

---

### Post by Ceiling Fan Man on 2009-05-26
> **Sub101 said:**
> Do you know what process it hangs on?

Try booting in the recovery mode and check the processes that load.

I unfortunately don't have access to the computer at the moment. :\ 

I will get this information as soon as possible. Will be an estimated 18 hours from now.

---

### Post by Ceiling Fan Man on 2009-05-27
Okay, I had my friend boot into recovery mode and asked him to write down the line that it hangs on, and also anything that might have said [fail] by it. To the best of my knowledge, this is what he had:
> [ 190.357428]  [<c021c411>] ? ext3 error + 0x51?0x60
init. rcs- sclogin main process (1318) terminated with status 127
/bin/s1:6:/sbin sologin not found
init: rcs main process (644) killed by segu signal

[60.848511] ---- end trace
Also note that due to his handwriting, the two things that say "rcs" may actually say "rc5," neither of us are sure.

---

