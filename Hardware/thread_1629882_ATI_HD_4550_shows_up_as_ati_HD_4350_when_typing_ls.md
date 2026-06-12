---
title: "ATI HD 4550 shows up as ati HD 4350 when typing lspc | VGA in terminal"
date: 2010-11-24
forum: Hardware
---

### Post by npm1 on 2010-11-24
ATI HD 4550 shows up as ati HD 4350 when typing lspc | VGA in terminal

how comes.....i've installed the latest drivers from amd drivers website....

would this degrade my GPU performance....

---

### Post by coffeecat on 2010-11-24
Your card must be identifying itself as a HD4350 for that to show up in lspci. Are you sure it is a HD4550? Whatever, according to [this link]("http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Radeon_R700_.28HD_4xxx.29_series") the 4350 and 4550 are basically the same chipset with a few minor differences - the 4550 being a little more capable.

My HD4350 shows up as 4350 in lspci, if I remember correctly. I'm in Windows 7 atm so I can't check but interestingly Windows' Device Manager is telling me it's an 'ATI Radeon HD 4300/4500 Series'.

Out of interest, why did you install the proprietary driver? Are you a gamer? You'll get perfectly good compiz with the open-source driver with that card in the latest two versions of Ubuntu.

---

### Post by npm1 on 2010-11-24
yes i am warsow for example

---

