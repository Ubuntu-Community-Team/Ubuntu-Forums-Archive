---
title: "USB problem - TV Card Winfast Dongle, reconnect necessary"
date: 2009-03-01
forum: Hardware
---

### Post by ProgX on 2009-03-01
Hi everybody,
please help me with the following problem:
I've got a notebook Averatec 3200 and I'm trying to use it as a „HTPC“. Its performance should be enough for this purpose (it's Athlon 1600+XP, 512 MB RAM, but I'd like to expand it to 1 GB if necessary).
I bought the USB 5.1 Soundblaster, no problem to configure it, it works without any problems. Next I have connected the wireless keyboard and mouse from HP (even if it's recognized as Logitech, due to the used wireless adapter), also without problems.
The problem is the USB TV Card Winfast Dongle (the version with just DVB-T).
If all of the USB devices are connected while booting (to be more specific – the devices are connected before turning the notebook on), only the wireless adapter and the soundcard are detected properly. I looked to the logs, it says „USB 1-3: device descriptor read/64, error -110.“ Sometimes it says that once, sometimes more times, sometimes the number 64 changes to 0, 8 etc. Or instead of USB 1-3 there is 4-1 in the log. The only thing that helps is disconnecting the card and connecting again. Then it correctly loads the firmware, the blue LED on the card lights up and everything works (recording and watching TV).

But this solution is not very practical, I plan in the future to make some DVD-like case, completely dismantle the notebook and all of the stuff put into this case, if it shall be a „HTPC“, it shouln't look like a notebook covered by USB devices and cables :-) I plan also to solve the cooling another way, to make it less noisy. But this is another chapter.
The important thing is that reconnecting is not the perfect solution. I've figured out another one, purely hardware solution, to build a device communicating via FT232, which would via 3 FETs connect the TV card after the system boots up. But I believe there must be another, better way to solve this problem :-)

I've had another problems, sometimes while recording the card mysteriously „disconnected“, in the logs I've found something like USB disconected and right after this „I2C mt2060 write failed“. But it seems to be solved via USB suspend disabling. After this step I've succesfully recorded a lot of TV shows, series etc. without any problem. So I hope it stays this way :-)
  
I'm using Ubuntu 8.04, but I've had same problem (reconnect necessary) even with Ubuntu 7.10.

Thank you for the responses!

Regards,
	ProgX

---

