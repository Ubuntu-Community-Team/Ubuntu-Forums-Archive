---
title: "Question about parallel port in ubuntu"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by wtherapy on 2008-01-13
Hello,

I am using Ubuntu 7.0.4, x86  and I am developing applications for Atmel microcontrollers using avrdude and for transfering the binary to the microcontroller I am using the parallel ( printer ) port. I've read all those stuff with Parport0 and everything works fine, except that, after my program is sucessfully transferred to the microcontroller, PIN 5 of the parallel port ( which is connected to the RESET pin of the microcontroller ) is kept low ( 0 logic ), thereby keeping the microcontroller in a continuous hardware reset. If I unplug the parallel cable from the microcontroller, everything start to work fine. 
I would desperatelly need to know HOW can I set the parralel pin 5 to 1 logic ( 5V ) using a command or something, so I won't need to unplug the parallel cable from the microcontroller everytime I run it.
Any help / suggestion highly appreciated.

Thanks a lot.

---

