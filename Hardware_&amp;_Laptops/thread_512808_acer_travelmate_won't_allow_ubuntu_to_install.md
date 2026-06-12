---
title: "acer travelmate won't allow ubuntu to install"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by MajorOwned on 2007-07-29
hi, i was wondering if someone could help. i have an 'ACER TRAVELMATE 529 TXV'  i bought off a friend and ubuntu won;t install on it,

it goes to a screen that says...

/bin/sh: can't access tty; job control turned off
(initramfs)_

it's got an 850mhz pentium 3 and 384mb of ram

same thing happens with ubuntu and xubuntu although Solaris did install

i can't get into the bios either cos my numpty friend forgot the password

:confused:

---

### Post by mrlogik on 2007-09-07
hey i get the exact same message on my acer travelmate 529atxv, i have access to my bios and nothing seems to make a difference? I did have 192 meg of ram and presumed this was the problem so bought a couple more sticks for a 512meg setup but nope same err message anyone have any ideas? This laptop does seem to run a strange intel boot manager system i notice? any other acer travelmates have issues with ubuntu? thanks.

---

### Post by mrlogik on 2007-09-08
Oops read the sticky on install options, press f6 and add no acpi option and it installs fine.

---

### Post by MajorOwned on 2007-09-08
hi, when do i press f6? i cant get into the bios

---

### Post by merlinus on 2007-09-08
At the opening menu, where you have a list of choices.

-merlin

---

### Post by MajorOwned on 2007-09-11
ah solved!

for future reference on an caer travelmate 527 from the main menu press f6, then type 

boot: live acpi=off

to the end of the long string of letters and numbers, and the whole thing should work

---

