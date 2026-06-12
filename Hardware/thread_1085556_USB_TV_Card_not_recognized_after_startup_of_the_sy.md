---
title: "USB TV Card not recognized after startup of the system, reconnect necessary"
date: 2009-03-03
forum: Hardware
---

### Post by ProgX on 2009-03-03
Hi people,
please help me with the following problem:
I've got a notebook Averatec 3200 and I'm trying to use it as a &#8222;HTPC&#8220;. 
The problem is the USB TV Card Winfast Dongle (the version with just DVB-T).
If all of my USB devices (sound card 5.1, tv card, wireless keyboard and mouse) are connected while booting (to be more specific &#8211; the devices are connected before turning the notebook on), only the wireless adapter and the soundcard are detected properly. I looked to the logs, it says &#8222;USB 1-3: device descriptor read/64, error -110.&#8220; Sometimes it says that once, sometimes more times, sometimes the number 64 changes to 0, 8 etc. Or instead of USB 1-3 there is 4-1 in the log. The only thing that helps is disconnecting the card and connecting again. Then it correctly loads the firmware, the blue LED on the card lights up and everything works (recording and watching TV).

But this solution is not very practical, I plan in the future to make some DVD-like case, completely dismantle the notebook and all of the stuff put into this case, if it shall be a &#8222;HTPC&#8220;, it shouln't look like a notebook covered by USB devices and cables I plan also to solve the cooling another way, to make it less noisy. But this is another chapter.
The important thing is that reconnecting is not the perfect solution. I've figured out another one, purely hardware solution, to build a device communicating via FT232, which would via 3 FETs connect the TV card after the system boots up. But I believe there must be another, better way to solve this problem

I've had another problems, sometimes while recording the card mysteriously &#8222;disconnected&#8220;, in the logs I've found something like USB disconected and right after this &#8222;I2C mt2060 write failed&#8220;. But it seems to be solved via USB suspend disabling. After this step I've succesfully recorded a lot of TV shows, series etc. without any problem. So I hope it stays this way

I'm using Ubuntu 8.04, but I've had same problem (reconnect necessary) even with Ubuntu 7.10.

Thank you for the responses!

Regards,
ProgX

---

### Post by ProgX on 2009-03-03
Hi people,
please help me with the following problem:
I've got a notebook Averatec 3200 and I'm trying to use it as a „HTPC“. 
The problem is the USB TV Card Winfast Dongle (the version with just DVB-T).
If all of my USB devices(sound card, wireless adapter for keyboard and mouse, tv card) are connected while booting (to be more specific – the devices are connected before turning the notebook on), only the wireless adapter and the soundcard are detected properly. I looked to the logs, it says „USB 1-3: device descriptor read/64, error -110.“ Sometimes it says that once, sometimes more times, sometimes the number 64 changes to 0, 8 etc. Or instead of USB 1-3 there is 4-1 in the log. The only thing that helps is disconnecting the card and connecting again. Then it correctly loads the firmware, the blue LED on the card lights up and everything works (recording and watching TV).

But this solution is not very practical, I plan in the future to make some DVD-like case, completely dismantle the notebook and all of the stuff put into this case, if it shall be a „HTPC“, it shouln't look like a notebook covered by USB devices and cables I plan also to solve the cooling another way, to make it less noisy. But this is another chapter.
The important thing is that reconnecting is not the perfect solution. I've figured out another one, purely hardware solution, to build a device communicating via FT232, which would via 3 FETs connect the TV card after the system boots up. But I believe there must be another, better way to solve this problem :-)

I've had another problems, sometimes while recording the card mysteriously „disconnected“, in the logs I've found something like USB disconected and right after this „I2C mt2060 write failed“. But it seems to be solved via USB suspend disabling. After this step I've succesfully recorded a lot of TV shows, series etc. without any problem. So I hope it stays this way :-)

I'm using Ubuntu 8.04, but I've had same problem (reconnect necessary) even with Ubuntu 7.10.

Thank you very much for your responses!

Regards,
ProgX

---

### Post by ProgX on 2009-03-04
Nobody knows?

---

