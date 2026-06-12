---
title: "2 nvidia gfx cards - only one can use non nouveau driver?"
date: 2013-03-03
forum: Hardware
---

### Post by neekos on 2013-03-03
greetings!

i am configuring a new ubuntu studio x64 12.10 instalation to replace a linux mint 14 fresh installation on my music making pc. i am having similar issues with ubuntu studio as i did with mint 14.

i have 2 gfx cards installed - one is an nvidia GT 430 (2 outputs) and one is an older nvidia 6200 (1 output). 
i gave up attempting to install functional nvidia drivers in linux mint. i went through every option i could find online and all had issues.

on the ubuntu studio install, i have successfully got dual screen to function (temporarily) but the driver was not functioning cleanly - there were glitches. 
i changed the driver via the 'software sources' -> 'additional drivers' list. 
in that list, both cards are listed and i have a choice of :
[LIST]
[*]nouveau or 1 nvidia proprietry driver for the GT 430 card
[*]nouveau or 4 different proprietry xorg drivers for the 6200.
[/LIST]

so far, every combination of settings has resulted in that after i set the 2nd card (regardless of which card i change first) to an xorg proprietry nvidia driver, the process appears to succed.. but when i reopen the software sources listing, the list has reverted to use the nouveau driver (without any notification popup message).

does anyone have any tips here? 
thanks

---

### Post by neekos on 2013-03-05
i have now read more thoroughly about the nvidia glitches and non-nvidia glitches with 12.10.. so installed 12.04 - i still have hardware issues, though less now.

---

