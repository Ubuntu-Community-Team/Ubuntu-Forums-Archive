---
title: "Do i need to install a chipset driver?"
date: 2008-12-29
forum: Hardware
---

### Post by gm__ on 2008-12-29
Hi!

First of all id like to congratulate the people from Ubuntu for the fantastic job they have done on this distro. Honestly HP and Microsoft should be ashamed of themselves. I think i dont need to explain why...

I just installed 8.10 (intrepid) on a HP dv7 1050ef laptop.
Almost everything works out of the box. I had to follow somebody's instructions in a thread here in order to audio and now its working also. 

The nvidia driver was proposed by ubuntu itself.

My question is: do i need to install the windows chipset driver by Wine or Ndiswrapper, or Ubuntu has an universal driver for every motherboard?

I dont really understand, thanks.

---

### Post by balaknair on 2008-12-29
No you don't really need to install chipset drivers for Linux. There is no 'universal driver' but most hardware is detected by Ubuntu automatically and open source drivers are installed. If closed source proprietary drivers are available for some hardware which can improve performance, you will be given the option to enable them(like the nVidia drivers).

Some hardware however might not work as well in Linux, because the manufacturers do not release Linux drivers, and many do not even release product specs to allow the open source community to write workable drivers(like in the case of some Creative audio cards and some WiFi cards).
In such cases it might be necessary to use ndiswrapper or some other workaround.

---

### Post by gm__ on 2008-12-29
Thank you Balaknair, that was very informative, now i get it better. :)

---

