---
title: "Gateway M675 Broadcom Wireless Card Help Needed"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by Remi Rokosa on 2007-01-24
I have a Gateway M675 Notebook, and the built-in Broadom Wireless Card does not work!

It shows up under Networking, but when activated fails to powerup the card. (The blue light doesn't turn on, but it says it's "Activated.")

I've tried using ndiswrapper, and as soon as I get to the step involving modprob I encounter errors.

Any ideas, I really need to get my wireless working.

---

### Post by virtual_void on 2007-01-24
Did you copy the firmware into /lib/firmware//2.6.17-10-generic ?
I have broadcom WiFi in this computer (PowerPC MacMini) that work fine. I've attached the firmware I'm using, the firmware is specific for the WiFi chip so it does not matter that I'm running on a different CPU.

However, Broadcom have several WiFi chips so this might not be the correct firmware for you device. But it might be worth a try :)

---

### Post by Remi Rokosa on 2007-01-27
How do I pull all this jazz off? Is there a guide I can follow? Thanks.

---

