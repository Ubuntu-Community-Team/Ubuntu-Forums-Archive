---
title: "Dell Inspiron E1505 - Audio Record, Memory Stick problem"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by cyberkoa on 2006-08-01
I have just bought a Dell E1505 with the following spec

1. Intel Core Duo T2050
2. Intel built-in Video
3. Intel built-in Audio(82801G (ICH7 Family) High Definition Audio Ctrler)
4. Ricoh Memory Card Reader (R5C592 Memory Stick Bus Host Adapter)
5. Sony DVD+RW
6. USB ports (4x)
7. S-video output
8. 1394 port (firewire)
9. PCMCIA slot
10. Intel Wireless 3945
11. Synaptic TouchPad
12. BCM4401-B0 100Base-TX
13. Modem 
= = =

[U]Result of the Ubuntu running on this machine
[/U]
1. Core Duo feature - require to update kernel package linux-686-smp. Done
2. Video work fine, but only have 1 resolution option 1024x768
3. Audio output works fine but audio record have problem. When I try to  use the sound recorder to do a test record , pressed the record button have no effect , press again freeze the program.
4. Ricoh Card Reader does not read Memory Stick but SD card work out of box. Other cards not tested.
5. DVD+RW detected. Reading tested , works fine. Writing not yet tested.
6. USB port tested with Kingston USB Drive, works out of box.
7. S-video not tested
8. 1394 not tested.
9. PCMCIA not tested and most probably not intend to test.
10. Intel Wireless 3945, WIFI works fine but Ubuntu will confuse when it is turned off. Activate and reactivate needed sometimes, bluetooth function not tested (have bluetooth function ?).
11. Synaptic TouchPad works out of box including the scroll function which in the pre-installed Windows Home Edition does not work.
12. Network card work out of box except sometimes confuse with wireless
13. Modem seems like does not work but I do not really need that.

= =

My help request (Any help is welcomed)
1. Audio recording/input problem. 

I have tested Ubuntu on 2 PCs, 2 Laptop 50% of them , 2 of them audio recording does not work in Breezy but work in Dapper. 1 Laptop tested only in Dapper works fine. And the last one is this Dell E1505 , does not work.
In my opinion , this is an important must-feature in this era because the VoIP /Voice chat requires such feature be working properly.


2. Memory Stick support
I heard that Ricoh Card Reader driver are in 2.6.17 kernel but I have not tested with compiling kernel

My main concern is the audio recording/input because I need it to establish voice chat.

---

