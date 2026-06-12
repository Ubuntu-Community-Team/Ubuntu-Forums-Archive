---
title: "9 Questions about SLI &#65288;waiting in patience and  polite &#65289;"
date: 2017-04-16
forum: Hardware
---

### Post by 243750496 on 2017-04-16
Q1:If i connect the two card with SLI bridge then use blender or playing games though with SLI off will it be the double performance through disconnect the SLI bridge?
Q2:if i don't get the SLI bridge connect will the only one card working or both working?(Playing game and rendering ) and what about the performance?
Q3:if i don't connect the SLI bridge and connect two monitor and playing games the one witch working on games is the monitor witch show the game right?
Q4:if i connect the SLI bridge but with settings SLI off so only main card will get the screen displayed?(Though i connect the two monitor to both card with one monitor one card connect )

Q5:why the am4 motherboard sli function is not supported by official?
Q6:will community drivers with opensource will support the sli on the motherboard ?
Q7:will nvidia official will support the sli on am4 motherboard in the future?
Q8:So do you mean that until all the motherboard of am4 come out?
Q9:will community release the driver with SLI enabled or from NVIDIA official or Linux official?
Thx in advance and 




waiting for reply!:)

btw: i am using Ubuntu on msi am4 motherboard TITANIUM +Ryzen 1800X + Titian X Pascal 


[https://www.amazon.com/MSI-X370-XPOWER-GAMING-TITANIUM/dp/B06WLNZ1JH/ref=sr_1_fkmr0_2?ie=UTF8&qid=1490860505&sr=8-2-fkmr0&keywords=msi+titan+x370+am4](https://www.amazon.com/MSI-X370-XPOWER-GAMING-TITANIUM/dp/B06WLNZ1JH/ref=sr_1_fkmr0_2?ie=UTF8&qid=1490860505&sr=8-2-fkmr0&keywords=msi+titan+x370+am4)

---

### Post by QIII on 2017-04-16
Hello!

"Laundry list" questions are confusing for both you and those who try to help.  They become jumbled quickly.

Please ask one question per thread.

---

### Post by Yellow Pasque on 2017-04-16
SLI is only supported by the nvidia binary driver and only a few apps/games actually have the necessary profiles to take advantage of it under Linux. It may help with Blender, but probably not worth it if you're a gamer.

The bridge allows the cards to communicate directly without using the bandwidth of the PCI Express. It's not necessary on some GPU's. I don't know if it's necessary for Titan-Xp cards, but if you spent the large sum of money for two Titan-Xp's in SLI, it doesn't make any sense not to spend a few more $ for a bridge.

> Q5:why the am4 motherboard sli function is not supported by official?
Q7:will nvidia official will support the sli on am4 motherboard in the future?
Q8:So do you mean that until all the motherboard of am4 come out?

The X370 chipset officially supports SLI. Lower-end AM4 chipsets (X200, B350) don't support it. If you've read differently, link to the source of information.

> Q6:will community drivers with opensource will support the sli on the motherboard ?
Q9:will community release the driver with SLI enabled
The open-source nouveau driver does not support SLI at this time. I haven't seen any nouveau developer state that work on it is planned or that it is a priority. nouveau has more basic/important functionality to focus on, especially on newer Geforce models (like reclocking, power/fan management, vulkan support, etc.)

---

### Post by 243750496 on 2017-04-16
> **Temüjin said:**
> SLI is only supported by the nvidia binary driver and only a few apps/games actually have the necessary profiles to take advantage of it under Linux. It may help with Blender, but probably not worth it if you're a gamer.

The bridge allows the cards to communicate directly without using the bandwidth of the PCI Express. It's not necessary on some GPU's. I don't know if it's necessary for Titan-Xp cards, but if you spent the large sum of money for two Titan-Xp's in SLI, it doesn't make any sense not to spend a few more $ for a bridge.



The X370 chipset officially supports SLI. Lower-end AM4 chipsets (X200, B350) don't support it. If you've read differently, link to the source of information.


The open-source nouveau driver does not support SLI at this time. I haven't seen any nouveau developer state that work on it is planned or that it is a priority. nouveau has more basic/important functionality to focus on, especially on newer Geforce models (like reclocking, power/fan management, vulkan support, etc.)


The Other question i want  to ask is whether the  bridge is a must in setting up blender rendering

I mean it's a must to connect two cards then go blender  rendering or it's Ok to connect and  it's  also Ok to connect  both cards without the  bridge which have same results in  blender  rendering

---

