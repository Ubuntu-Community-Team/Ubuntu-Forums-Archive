---
title: "Laptop Shuts down inconsistently when running 16.04"
date: 2016-04-24
forum: Hardware
---

### Post by kenneth-fechter on 2016-04-24
I am running a W530 with the following specs 

[LIST]
[*]Intel Core i7-3720QM
[*]Nvidia Quadro K2000M (Optimus Disabled)
[*] 16GB of ram
[*]1920x1080 FHD display
[*]128GB SSD + 500GB Hard Drive + 750 GB Hard Drive (Ubuntu installed to SSD)
[/LIST]

Sometimes, when shutting down Ubuntu, the Power LED goes out, but the rest of the machine stays running. The Display still shows the Ubuntu shutdown screen with the animation stopped, and I can still elicit responses from the keyboard hot keys. This is on a clean install of Ubuntu Desktop 16.04 64 bit with all the updates. (I had it perform updates during the install, and  ran an apt-get update && apt-get dist-upgrade) after first boot. 

On a side note, occasionally the machine will also fail to sleep, instead the power light will pulse like it is sleeping and the display shuts off, but the fans crank up to full and the machine cannot be woken out of sleep.

---

### Post by kenneth-fechter on 2016-05-02
It seems that upgrading from the 4.4.x kernel of 16.04 to 4.5.2 fixes the issue. I will report back if anything changes or the issue comes back.

---

