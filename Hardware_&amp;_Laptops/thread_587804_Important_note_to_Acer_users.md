---
title: "Important note to Acer users"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by Rimfrost on 2007-10-23
If you, like me, are on a Acer notebook (I have an Acer Aspire 5020) you might be experiencing the same problems I did with the WIFI-card. 
The card was detected succesfully and the proprietary drivers installed, but I could not find a connection. 

On some ACER notebooks you have to install the acer-acpi kernel module in order for the network card to work: 
[https://blueprints.launchpad.net/acerlaptop-wifi/+spec/acerlaptop-wifi](https://blueprints.launchpad.net/acerlaptop-wifi/+spec/acerlaptop-wifi)

Just go to this pages, add the repositories mentioned there to your module source's and do 

[PHP]sudo apt-get install acer-acpi[/PHP]

and the green light on your WIFI-card should (hopefully) light up.

---

### Post by tommcd on 2007-10-23
Good find!
Is the acer-acpi module just for the wifi, or does it enable other things, like bluetooth? How well is it working for you? Is your integrated wifi an atheros chip?
I have an Acer Aspire 3680-2633 and have never been able to get the integrated atheros wifi to work. So I bought a Belkin 9010 card that uses the rt61 driver from serialmonkey and works well. I think I might just stick with that for now, since I have it set up nicely in ubuntu, slackware, and zenwalk, but I will keep it in mind, thanks!
It seems to be available for other distros also:
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)
EDIT: Do you know which Acer laptops this module is for? The wiki says just 3020 and 5020 series:
[https://wiki.ubuntu.com/acerlaptop-wifi](https://wiki.ubuntu.com/acerlaptop-wifi)

---

### Post by AJB2K3 on 2007-10-23
Ive been using the network selector/wifi radar to connect on my 3690 wmli ( or what ever)

---

