---
title: "how to switch off the wireless card indicator on acer travelmate 2300 laptop"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by ssck on 2005-06-15
how do i switch off the wireless card light indicator once it has been activated by ubuntu ?

---

### Post by xristos on 2005-06-15
I have an Acer Aspire 1520 and I have done the following :
In windows there is a programm installed by Acer when you first purchased the laptop that lets you control the buttons for wirelless , bluetooth , internet browser etc. ( I don't remember the name right now , It's in the start-programms menu ).
So find this programm and select for the wirelless device to be **off** when the computer boots . Keep in mind that you won't be able to use the wirelless card in Linux because the button that turns it on ( the one with the light ) doesn't work in Linux.

PS : I am talking about the internal card of the laptop not a PCMCIA one .

---

### Post by ssck on 2005-06-15
[QUOTE=xristos]I have an Acer Aspire 1520 and I have done the following :
In windows there is a programm installed by Acer when you first purchased the laptop that lets you control the buttons for wirelless , bluetooth , internet browser etc. ( I don't remember the name right now , It's in the start-programms menu ).
So find this programm and select for the wirelless device to be **off** when the computer boots . Keep in mind that you won't be able to use the wirelless card in Linux because the button that turns it on ( the one with the light ) doesn't work in Linux.

PS : I am talking about the internal card of the laptop not a PCMCIA one .[/QUOTE]


i am using ubuntu exclusively, not dual boot .... so i was wondering whether it is possible to switch the wireless card on and off using the manual switch.i realize that once the card has been switched on by ubuntu, even if i deactivate the wireless lan card later using ifdown command.the light on the wireless card is still on.

---

### Post by luca_linux on 2005-06-15
```
echo "0" /proc/acpi/search_for_something_like_wlan
```
Search for something file like "wlan" (or something like that)...also in the subdirs...

---

### Post by CassioBunana on 2005-10-10
HI! I've the same problem like u, but I'm using a Fujitsu-Siemens Laptop...how have u managed to solve it?

---

