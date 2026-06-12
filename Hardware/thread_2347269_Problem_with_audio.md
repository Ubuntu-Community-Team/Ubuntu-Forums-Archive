---
title: "Problem with audio"
date: 2016-12-23
forum: Hardware
---

### Post by spiritdemojo on 2016-12-23
Hello i am working on a E-system 2513 laptop and i cant get the audio working what ever i tried  install alsa drivers or realtek still it doesnt work  i know that my laptop to using a  realtek hd audio it using the same motherboard with that laptop [http://www.uktsupport.co.uk/advent/laptop/5712.htm ]("http://www.uktsupport.co.uk/advent/laptop/5712.htm")Thats my motherboard [http://www.ebay.co.uk/itm/Advent-5712-Laptop-Motherboard-P-N-37GU41000-10-Tested-/252600966362](http://www.ebay.co.uk/itm/Advent-5712-Laptop-Motherboard-P-N-37GU41000-10-Tested-/252600966362). But what ever i tried i couldnt make my audio work plz help  and here is my alsa info [http://www.alsa-project.org/db/?f=aeb22025db98b3a45e5f039ee5dfa3872d91a327](http://www.alsa-project.org/db/?f=aeb22025db98b3a45e5f039ee5dfa3872d91a327) .

---

### Post by Yellow Pasque on 2016-12-24
```
Driver version:     <----- THIS SHOULD NOT BE BLANK
Library version:    1.1.0
Utilities version:  1.1.0
```

The kernel sound modules are broken, probably as a result of something you did to fix your issue. Try reinstalling your kernel image package:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```
Reboot and run Alsa info again. Hopefully, driver version should be the same as kernel version.

---

### Post by spiritdemojo on 2016-12-24
OK i run the code you send me but still it doesnt seem to work here is the alsa info [http://www.alsa-project.org/db/?f=5211d86a34a40ce8b7173b79564844d16f59948a](http://www.alsa-project.org/db/?f=5211d86a34a40ce8b7173b79564844d16f59948a)

---

### Post by spiritdemojo on 2016-12-27
After long search i found out that my sound car its not physically  recognize by my hardware but i dont understand why on windows vista it was working fine since i format to ubuntu  even if i installed back windows 7  i coudnt make the sound work again any ideas ?[h=3][/h]

---

