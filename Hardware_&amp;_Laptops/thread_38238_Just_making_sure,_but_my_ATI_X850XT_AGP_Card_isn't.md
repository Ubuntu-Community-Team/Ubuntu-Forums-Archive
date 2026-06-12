---
title: "Just making sure, but my ATI X850XT AGP Card isn't supported right?"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by Serus on 2005-05-30
I've been trying for a few days now at getting my ATI X850XT AGP 256MB card to work to no avail. I've followed every tutorial with no success.

I found a post saying that if your card isn't listed in this document ( [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-supported.txt](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-supported.txt) ) then it's not supported. I just wanted to confirm that nobody else with an AGP X850XT has gotten it to work. Thanks for the help!

---

### Post by fackamato on 2005-05-30
It's supported by the ATi driver. You're not saying anything about any errors you've encountered during the time you tried to make it work, so that's all I can say.

---

### Post by Serus on 2005-05-30
The problem I ran into, was when I got to the point of every tutorial to replace the "ati" with "fglrx" in the xorg.conf file, the system halted on boot saying there was an error in the xorg.conf file at the same line as the "fglrx".

I found a post talking about puting in the "ChipID 0x5548" and when I did that, I could boot fine. However, since 5548 was a different card, it didn't work. I put in the number for my card and the system halted again. The main error was the "No screens  found" error and the "(EE) No Devices detected" error.

Once I found the post saying that it wasn't supported I stopped. Guess I'll ahve to try to get it working again.

---

