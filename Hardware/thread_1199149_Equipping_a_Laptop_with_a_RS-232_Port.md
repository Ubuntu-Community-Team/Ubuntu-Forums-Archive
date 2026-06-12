---
title: "Equipping a Laptop with a RS-232 Port"
date: 2009-06-28
forum: Hardware
---

### Post by ZombiePinguin on 2009-06-28
Hello,
I want to upgrade my ubuntu 8.10 laptop with serial port connectivity. I have a certain device (electrical measurement equipment) which communicates with its PC program through a RS-232 port, unfortunately, the program is win32 (thus wine).
At first I tried it with USB/Serial adapters (PL-2302/3 chipset), but they fail to work with wine (ttyUSB*->/dosdevices/com* links do not work very well in wine).
Then I tried it with a express card from a store and realized that the manufacturer simply built this card upon the same PL-2303 chipset and the card acted like a USB/serial adapter. Of course it didn't work either. 

My question is, are there any express cards or maybe even USB/serial adapters, which act like a native COM port instead of a virtual one (ttyS*, not ttyUSB*).
Or am I missing something and the ttyS*->/dosdevices/com* links work just as bad as the ttyUSB*->/dosdevices/com* ones in wine?

Cheers

P.S.: this serial connectivity mess is the only thing preventing me from completely abandoning BillSoft, any help appreciated!

---

### Post by ZombiePinguin on 2009-07-02
Uhm, I think the people here misunderstand the title, how can I edit the thread title?

---

