---
title: "Brother QL-700 USB Label Printer"
date: 2018-03-12
forum: Hardware
---

### Post by bananafishbones on 2018-03-12
I've installed the driver from the Brother website for my QL-700 USB printer but when I add the printer within the Device > Printer settings applet, a notification pops up telling me that Ubuntu needs the driver for this device then abruptly tells me that no driver could be found. The printer is not printing at all. See my details below: Any idea?

> Bus 002 Device 004: ID 0bda:0328 Realtek Semiconductor Corp. 
Bus 002 Device 006: ID 154b:00d2 PNY 
Bus 002 Device 003: ID 05e3:0612 Genesys Logic, Inc. 
Bus 002 Device 002: ID 0bc2:ab31 Seagate RSS LLC Backup Plus Desktop Drive (5TB)
Bus 002 Device 005: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 058f:9410 Alcor Micro Corp. Keyboard
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 005: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 010: ID 04f9:2042 Brother Industries, Ltd 
Bus 001 Device 002: ID 067b:2571 Prolific Technology, Inc. 
Bus 001 Device 006: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


--LOGS--
Failed to start Automatic USB/Bluetooth printer setup (devices-pci0000:00-0000:00:14.0-usb1-1x2d3)
unable to access /sys/devices/pci0000:00/0000:00:14.0/usb1/1x2d3

--INSTALLED--
ql700lpr/now 1.1.4-0 i386 [installed,local]

---

### Post by pdc on 2018-03-13
I had understood you needed both the lpr driver; and the cupswrapper driver [http://support.brother.com/g/s/id/linux/en/download_esp.html#QL-700](http://support.brother.com/g/s/id/linux/en/download_esp.html#QL-700)

if you copy ```
dpkg -l ql700*
``` it will clarify just what is installed ...........

---

### Post by bananafishbones on 2018-03-14
Thanks for your help PDC. I installed the wrapper but still no cigar. 

I may remove it all and start over. The main brother website made no mention of a wrapper in regards to its linux drivers. 

Cheers,

---

### Post by pdc on 2018-03-14
when I go over Brother's instructions again [http://support.brother.com/g/s/id/linux/en/instruction_esp3.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_esp3.html?c=us_ot&lang=en&redirect=on)

I see they say > *** If CUPS is working on your system, we recommend to use CUPS.      .... so I guess that just means Cupswrapper ....... I had understood they wanted both .......

....... indeed the page on cupswrapper seems to me to say ....... lpr first and then cupswrapper ......... [http://support.brother.com/g/s/id/linux/en/instruction_esp1.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_esp1.html?c=us_ot&lang=en&redirect=on)

and this page [http://support.brother.com/g/s/id/linux/en/instruction_esp6.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_esp6.html?c=us_ot&lang=en&redirect=on) covers the removal of the lpr .......

which version of Ubuntu are you running?    

______________

brother offer an FAQ page [http://support.brother.com/g/s/id/linux/en/faq_esp.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_esp.html?c=us_ot&lang=en&redirect=on) .......... maybe something there ......

---

### Post by kurt18947 on 2018-03-17
> **pdc said:**
> when I go over Brother's instructions again [http://support.brother.com/g/s/id/linux/en/instruction_esp3.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_esp3.html?c=us_ot&lang=en&redirect=on)

I see they say      .... so I guess that just means Cupswrapper ....... I had understood they wanted both .......

....... indeed the page on cupswrapper seems to me to say ....... lpr first and then cupswrapper ......... [http://support.brother.com/g/s/id/linux/en/instruction_esp1.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_esp1.html?c=us_ot&lang=en&redirect=on)

and this page [http://support.brother.com/g/s/id/linux/en/instruction_esp6.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_esp6.html?c=us_ot&lang=en&redirect=on) covers the removal of the lpr .......

which version of Ubuntu are you running?    

______________

brother offer an FAQ page [http://support.brother.com/g/s/id/linux/en/faq_esp.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_esp.html?c=us_ot&lang=en&redirect=on) .......... maybe something there ......

When I use the Brother installer for desktop printers, it does install both lpr and cupswrapper so I'm inclined to think both are required.

---

