---
title: "Is sata hotswappable?"
date: 2008-11-29
forum: Hardware
---

### Post by |{urse on 2008-11-29
I've read a lot of conflicting answers to this question. I've been a pc/server tech for quite a few years now and have been afraid to just "go ahead and try it" well now im sitting here with a mobo/cpu/ram/psu on my table and a couple abys drives set up as a jbod running gutsy. While digging through boxes a few minutes ago i found a matching 60gb i'd like to try it with.

Can i? | Should i?

:confused:

---

### Post by Skripka on 2008-11-29
> **|{urse said:**
> I've read a lot of conflicting answers to this question. I've been a pc/server tech for quite a few years now and have been afraid to just "go ahead and try it" well now im sitting here with a mobo/cpu/ram/psu on my table and a couple abys drives set up as a jbod running gutsy. While digging through boxes a few minutes ago i found a matching 60gb i'd like to try it with.

Can i? | Should i?

:confused:

Can you?  Yes.



Should you?  Well that depends-do you want a SATA HDD paperweight to go on your desk?

---

### Post by |{urse on 2008-11-29
Thanks for your positively witty answer. Are you saying it will fry the drive if i plug it in? Because i just plugged it in and it didn'y fry it. I just removed the newly swapped drive and fired it up on a bench machine and it is reading/seeking fine. 

 While the drive suffered no damage it was still not seen by the os. Is there some (cpu economical) way to keep the hal looking for new drives on this fake array?

---

### Post by Skripka on 2008-11-29
> **|{urse said:**
> Thanks for your positively witty answer. Are you saying it will fry the drive if i plug it in? Because i just plugged it in and it didn'y fry it. I just removed the newly swapped drive and fired it up on a bench machine and it is reading/seeking fine. 

 While the drive suffered no damage it was still not seen by the os. Is there some (cpu economical) way to keep the hal looking for new drives on this fake array?

I don't think BIOS are written to look for anything other than USB/Firewire ports on the fly.  Best bet is to reboot and let the BIOS see the drive.



I'm always beyond cautious....if you plugged in the SATA data cable first then the power cable, odds are it wouldn't harm the drive as it is not powered, though it is never advisable to plug anything into a motherboard that is hot; and it is never worth the risk of borking hardware.

---

### Post by |{urse on 2008-11-29
yeah plugging it in in that order seemed correct. Okay i just tried it with a sata2 compliant mobo and drive (another bench) and *poof!* it works (the other was sata1). If anyone can splain this to me I'll chisel your name in my forehead (sorry no photo evidence will be sent).

Okay i just tried the sata1 on winxp and it worked.. B000!

---

