---
title: "Linux support for motherboards"
date: 2018-10-14
forum: Hardware
---

### Post by matthewjake on 2018-10-14
Hi,

I'm in the process of considering buying a new PC setup. And I would like to dual boot windows and ubuntu. I was wondering about linux development in regards to hardware. Does linux develop drivers for new hardware such as motherboards or do I need to rely on the hardware manufacturers to develop and release them?

It would be nice if my choice of motherboard was to depend on the features i desire rather than what is compatible if possible.

I have no particular motherboard in mind, but it will be a relatively new one. One of them has inbuilt wifi and I wonder if ubuntu would support it natively?

is new hardware often supported on linux?

sorry for my naivete 

Thanks,

Matthew Jake

---

### Post by Yellow Pasque on 2018-10-15
Linux is good about supporting the motherboard chipset itself (e.g. AMD B350 or Intel H370) and the audio and LAN drivers, as long as the mobo doesn't have anything too exotic. These drivers are part of the kernel and motherboard manufacturers usually don't provide them or contribute to their development.

> One of them has inbuilt wifi and I wonder if ubuntu would support it natively?
What chipset?

---

### Post by matthewjake on 2018-10-15
> **Temüjin said:**
> Linux is good about supporting the motherboard chipset itself (e.g. AMD B350 or Intel H370) and the audio and LAN drivers, as long as the mobo doesn't have anything too exotic. These drivers are part of the kernel and motherboard manufacturers usually don't provide them or contribute to their development.


What chipset?

One motherboard with wifi onboard is the Gigabyte Z370N WIFI which has a Intel[SUP]®[/SUP] Z370 Express Chipset.

There are like 60 choices for motherboards relevant for me looking at 1151 pin at the computer store. Brands ranging from ASRock, Asus, Colorful, Gigabyte, MSI.

With inbuilt wifi there are 2 that i can see listed which i am interested in. The one listed above and a Gigabyte H370N-Wifi with a Intel[SUP]®[/SUP] H370 Express Chipset

So most boards should be compatible with the latest Ubuntu?

---

### Post by Yellow Pasque on 2018-10-15
> One motherboard with wifi onboard is the Gigabyte Z370N WIFI which has a Intel® Z370 Express Chipset.

I was looking for the wireless chipset specifically. Quick google shows the Gigabyte Z370N board uses Intel 8265, and the H370N uses the Intel 9560. These should work "out of the box" in Ubuntu 18.04 or later: [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)

> So most boards should be compatible with the latest Ubuntu? 
Yes, but you can still encounter bugs even if something is supported/compatible/has an available driver, just like with any OS. Always do your googling homework.

---

### Post by wyliecoyoteuk on 2018-10-15
It might be worth looking on the manufacturer's website in the drivers section, to see if Linux is mentioned.
Some manufacturers actively support Linux.

---

### Post by oldfred on 2018-10-15
This site has users post performance of their system.
You can search for specific parts to see what has been posted.
[http://openbenchmarking.org/s/Gigabyte%20H370N-Wifi](http://openbenchmarking.org/s/Gigabyte%20H370N-Wifi)

---

