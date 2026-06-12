---
title: "Graphic Driver for ubuntu 9.04 Jaunty"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by mike66939 on 2009-07-14
ok... i have ubuntu 9.04 installed on a latop with 1.60 ghz processor AMD athlon 64 (i kno its crap) and 2 gigs of ram. when i click system>administrator>hardware drivers, the only bum driver is my STA wireless driver, which is not the problem because i log on to the net just fine. the problem is when i borwse the web or load youtube videos or any sort of video the screen tends to get glitchy. its rather annoying. lines would jump up on the screen very fast etc... i was wondering if its the graphic driver because i hadnt installed any. i dont know how on ubuntu.

i checked my graphic card name and chipset with 

lspci -nn | grep VGA

the results were

01 :05.0 VGA compatible controller [0300] : ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]

also.. my compiz fusion effect does not work... can anyone tell me what i need to do in order to make things right. should i use linux mint instead? please help. thanks in advance. ;)

---

### Post by Mark Phelps on 2009-07-15
Your radeon chip is not supported anymore through AMD/ATI, so you can't use proprietary drivers -- which is why you weren't offered any.  Ubuntu 9.04 only works with open source drivers for your chip.  AMD/ATI have already stated that they are NOT going to be producing any new drivers for your chip -- and a lot of others that they dropped support for as well.

The problem is complicated in that the older drivers that work with your chip don't work with the Xorg version in Ubuntu 9.04.  So, they won't work with any other Linux distro that uses that version or newer, either.

---

### Post by csabo2 on 2009-07-15
> **Mark Phelps said:**
> Your radeon chip is not supported anymore through AMD/ATI, so you can't use proprietary drivers -- which is why you weren't offered any.  Ubuntu 9.04 only works with open source drivers for your chip.  AMD/ATI have already stated that they are NOT going to be producing any new drivers for your chip -- and a lot of others that they dropped support for as well.

The problem is complicated in that the older drivers that work with your chip don't work with the Xorg version in Ubuntu 9.04.  So, they won't work with any other Linux distro that uses that version or newer, either.

Gotta love ATI.

---

### Post by mike66939 on 2009-07-15
well... i guess i will just have to put up with the glitches because there is no way in hell im gonna go back to windows. its either stick with ubuntu or buy a mac... ubuntu it is. thanks for the useful info. i really appreciate the help... thanks  ):P

---

