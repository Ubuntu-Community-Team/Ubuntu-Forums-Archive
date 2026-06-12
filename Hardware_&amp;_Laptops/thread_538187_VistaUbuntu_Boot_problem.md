---
title: "Vista/Ubuntu Boot problem"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by 98GreenGT on 2007-08-29
I recently installed ubuntu following one of the guides ive seen on the net that would allow me to dual boot...well it does..but when i click longhorn on the grub menu it takes me directly to the vista bootloader asking me to choose between my recovery driver or vista.  My question is how do i get the vista bootloader to stop asking me what to load and just load vista once i choose it on the grub menu...its more of an annoyance than anything.

Thanks for the help,
Aaron

---

### Post by ThrobbingBrain66 on 2007-08-29
It's been a long time since I used Windows, but open a run prompt (Windows key + r) in Vista and type msconfig.  I think under the Boot tab there's an option for either turning the bootloader off or making one partion the default.  Then you can reduce the Timeout settings if needed as well.

---

### Post by 98GreenGT on 2007-08-29
I see no option as to turn it off...and thats what bothers me too..windows vista is already set as the default os

---

### Post by RageOfOrder on 2007-08-30
You basically just have to go to msconfig, and then go to the boot.ini tab, and remove any other boot lines besides Vista. Otherwise it's gonna ask you every time.

Stupid NTLoader

---

### Post by 98GreenGT on 2007-08-30
that fixed it..just wondering though..when it starts up now its giving me a message about it doing selective startup rather than normal startup..is it ok to leave it like this?  Everything seems fine

---

### Post by merlinus on 2007-08-30
My motto:

If it ain't broke, don't fix it!

There are plenty of other problems and challenges to deal with.

:lolflag:

-merlin

---

### Post by dmitriyp13 on 2007-08-30
> **98GreenGT said:**
> that fixed it..just wondering though..when it starts up now its giving me a message about it doing selective startup rather than normal startup..is it ok to leave it like this?  Everything seems fine

I've used msconfig a lot in the past and whenever you change anything (and I mean anything) there, this warning pops up.  It is perfectly ok to ignore it, its just there as a reminder.

---

