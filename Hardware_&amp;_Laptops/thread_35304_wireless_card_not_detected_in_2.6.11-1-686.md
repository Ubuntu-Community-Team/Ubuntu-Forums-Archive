---
title: "wireless card not detected in 2.6.11-1-686?"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by dharm on 2005-05-18
well when i first installed ubuntu hoary, with linux image 2.6.10.5, the wireless worked right out of the box, but, then i used the synaptic package manager to get the 2.6.11-10-686 image.
that went fine.
then i rebooted with the 2.6.11-10-686 image, and i realised... it nolonger detects my wireless card! its not in the networking window... ath0 doesnt exist.

when i switch back to 2.6.10-5-386,  it works fine, but when i goto 2.6.11 its gone...

btw: i am using a toshiba laptop with a builtin Atheros Super-G wireless

---

### Post by dharm on 2005-05-18
i am an idiot...

well it works, i just used ndiswrapper using the driver off the toshiba site (extracted it from the executable zip)

thanks... to me ^^

---

