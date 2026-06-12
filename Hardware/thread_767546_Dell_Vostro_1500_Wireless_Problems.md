---
title: "Dell Vostro 1500 Wireless Problems"
date: 2008-04-25
forum: Hardware
---

### Post by sMC 2k7 on 2008-04-25
Hi Ubuntu world,

I am having problems. Basically i bought a new dell vostro 1500. It comes with windows vista which of course i want rid of as soon as possible. I have installed 7.10 and installation went smooth doing a complete install and full ubuntu partition. But my wireless dnt work, and i cannot get the wireless light to come on, meaning the wireless isn't on??? can someone please help me on this, as i have no internet :(

Thank You sMC

---

### Post by andied on 2008-04-25
I have a Dell Vostro 1500 with the Dell 1390/Broadcom wireless.

 I did a search for Broadcom (name and description) in Synaptic Manager and B43-cutter came up, which I installed. I then went to System>Administration > Hardware drivers and enabled the Broadcom B43 driver and it downloaded the firmware and my wireless works great.

---

### Post by sMC 2k7 on 2008-04-26
Hi,

Thanks for that, I i have tried this and many other things like using ndiswrapper and installing windows drivers but all to no avail. Im still stuck without wireless :( Can anyone else help me?

Cheers
sMC

---

### Post by juventuscadillac on 2008-04-26
I have the same card, and had no luck making it work. I hope someone makes a guide for Hardy.

---

### Post by Keymone on 2008-04-30
i got wireless working after running apt-get install b43-fwcutter

---

