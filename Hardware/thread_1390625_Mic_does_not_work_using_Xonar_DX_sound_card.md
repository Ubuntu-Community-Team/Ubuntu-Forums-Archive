---
title: "Mic does not work using Xonar DX sound card"
date: 2010-01-25
forum: Hardware
---

### Post by Jephir on 2010-01-25
I'm trying to get my microphone to work on Ubuntu 9.10 using an [Asus Xonar DX]("http://www.asus.com/product.aspx?P_ID=R3E8hhLCEgwyAOt9&templete=2") sound card. Sound output works fine on the sound card.

The mic is at maximum volume and is not muted in Sound Preferences, and I have mic boost on in alsamixer. I have tried switching between the different connectors: Analog Microphone, Analog Input, and Analog Line-In, however none of them show a level on the Input level meter. I have also tried switching between the front panel and rear panel mic jacks.

The mic works fine on the same sound card under Windows Vista and 7.

I noticed on that back of the sound card that the input light isn't on. On Windows the mic jack emits a red light, but on Ubuntu it doesn't.

---

### Post by Jephir on 2010-02-02
Fixed the problem, in alsamixer, Mic has to be set to CAPTUR and set to maxiumum level, it is at zero by default.

---

