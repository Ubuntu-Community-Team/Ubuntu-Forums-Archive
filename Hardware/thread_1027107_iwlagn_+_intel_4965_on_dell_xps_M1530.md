---
title: "iwlagn + intel 4965 on dell xps M1530"
date: 2008-12-31
forum: Hardware
---

### Post by cataenry on 2008-12-31
Hi all,
i've just installed Intrepid over my new machine, nearly all working perfect, except the wireless.
I have a button/switch to power it on or off, and the device is recognized correctly:

iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4

What happens is that, starting the machine with the button in the 'off' position, if switch it 'on', wireless devices get powered, module correctly working as i see from networkmanager, but it wont do anything.. so i noticed this message:

iwlagn: Radio disabled by HW RF Kill switch

Googled a bit and discovered a trick to make it work:

echo 1 > /sys/class/rfkill/rfkill0/state (as root ofc)



But even this one do not work always..
Any hint? 


(I've already tried to upgrade to backported modules)


ah.. near to forget: happy new year :D


EDIT: I've just noticed that it's not true that the wifi device gets powered, or at least, the led that notify wifi on is not untill i get both working..

---

### Post by cataenry on 2008-12-31
I have also noticed this:
if i start the machine with the switch 'on', then all works fine..

[start machine, switch=on, NM shows access points]
root@experience:~# cat /sys/class/rfkill/rfkill0/state 
1
[switch 'off', NM removes wifi options]
root@experience:~# cat /sys/class/rfkill/rfkill0/state 
2
[switch 'on', NM comes back showing access points]
root@experience:~# cat /sys/class/rfkill/rfkill0/state 
1

Hope this helps for an eventual debug..

---

### Post by tormod on 2009-01-06
See also [https://bugs.launchpad.net/bugs/193970](https://bugs.launchpad.net/bugs/193970)

---

