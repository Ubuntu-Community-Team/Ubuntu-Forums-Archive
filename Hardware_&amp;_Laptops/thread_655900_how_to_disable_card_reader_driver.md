---
title: "how to disable card reader driver?"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by senkas on 2008-01-01
There is some hardware problem with my card reader device in my laptop. It always detects that a memory card is inserted and tries to read it.
The little LED on card reader always blinks. When I see the system log , it has following continuous messages:

Jan  2 09:57:47 cyberayya kernel: [ 2020.372000] tifm_core: SmartMedia/xD card detected in socket 0:2
Jan  2 09:57:47 cyberayya kernel: [ 2020.372000] tifm0 : demand removing card from socket 0:2
Jan  2 09:57:47 cyberayya kernel: [ 2020.956000] tifm_core: SmartMedia/xD card detected in socket 0:2
Jan  2 09:57:47 cyberayya kernel: [ 2020.956000] tifm0 : demand removing card from socket 0:2

Please let me know how can I disable the memory card reader from the laptop. 
I had done this in my windows OS, using control panel. How can I disable in Ubuntu? 
Please help and Thanx in advace.

---

### Post by Casual Fan on 2008-01-01
I'm trying to *enable* my card reader...would be interested in hearing this solution...it works in Gutsy but not Feisty (I traded a card reader for suspend!)

---

### Post by senkas on 2008-01-02
I checked in HAL Device Manager tool (System->Preferences->Hardware Information).
It lists "PCI secure digital Controller". But I am unable to "edit" the settings, so that I can "disable" the controller. Do u know any way to disable this controller. I guess if the controller is disabled, the device will be indirectly disabled.
Senthil KAS

---

