---
title: "Keyboard trouble : function button doesn't woek"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by Angel777 on 2006-07-28
Hi all,


I am running Dapper on a Toshiba A100-165.

I have trouble with the "Function" button of my keyboard. Normally, when I would press Function + F6 it should decrease the luminosity of my screen, but nothing happens.

In fact, it seems that the "Function" button is not recognized (I have the configuration of a Generic Keyboard in xorg.conf). I used xev command but no keycodes is attributed to the "Function" buton. I also tries to see the output of tail -f /var/log/messages
 but there is nothing relevant to a keyboard trouble...

Therefore, as a previous user said, the battery only last 1h40... and the ACPI for battery doesn't want to use the different profiles (all profiles do the same).

Would anyone have an idea how to get that screen luminosity work (no I won't use xbrightness) and everything related to the combination of Funtion+something.


Thanks in advance

---

