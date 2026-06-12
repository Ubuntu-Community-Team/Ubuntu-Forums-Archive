---
title: "Wireless Problems with Ferrari 4002"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by Califer on 2005-11-12
I am unable to get the wireless card to work with Ubuntu, there has been some cases where it started after a reset but I dont have a clue on why.

I used ndiswrapper to use the 64 bit wireless drivers off of the acer site. iwconfig has wlan0 show up but "iwlist wlan0 scan" shows no wireless signals. I know for a fact that my router reaches down here since I can connect with windows and my Pocket PC.

Also, when I try to switch settings with the iwconfig command. Nothing happens, if I try to change the ESSID, it just remains as off/any.

Im pretty sure the card in this notebook is a broadcom one.

Any help will be appreciated.

---

### Post by Califer on 2005-11-12
it also appears that if I restart windows with wireless enabled, it works in Ubuntu.

---

### Post by Califer on 2005-11-13
another update

When I restart without first booting to windows and enabling the wireless, the bootup tells me that loadndisdriver was ignored. When it says that in boot, iwlist wlan0 scan does not pick up anything.

This notebook has a hardware wireless button that I think has something to do with this problem, since when wireless DOES work, and I push this button, it stops the connection. Even after I cant connect by pushing this button, iwlist wlan0 scan still works. If I push this button again, nothing happens.

Please, can someone help me get this working right?

---

### Post by Califer on 2005-11-15
anyone?

---

### Post by stknightmare on 2005-11-16
[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)
Try this.

I dont know if this really works.
[http://www.roessner-net.com/wlan_button/](http://www.roessner-net.com/wlan_button/)

I have an acer 5024 but i believe the problem is the same.

---

### Post by Califer on 2005-11-16
the acer_acpi does not work on the Ferrari 4000 series.

---

