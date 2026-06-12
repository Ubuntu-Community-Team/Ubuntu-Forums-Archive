---
title: "t60 fan restart"
date: 2010-06-11
forum: Hardware
---

### Post by shiri_prgmr on 2010-06-11
Hi,
I have a T60 running Ubuntu 8.10. The fan started giving occasional problems a few months back. It just starts rotating faster and faster. The only solution then was to switch it off. I gave the laptop for servicing and fan replacement. After the fan was replaced, everything worked fine for a while, but now the problem has returned to resume the haunting. When the fan starts picking up speed, I tried to manually switch it off (for testing purposes only). Manual switch off by following info in this page:

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed")

The fan does get switched off, but after couple seconds, it switches back on automatically. Something else is overriding the manual OFF command. Can anyone tell me what this could be?

Thanks in advance,
sph

---

### Post by shiri_prgmr on 2010-06-11
T60 = IBM T60 laptop.

Switch off command = 
[FONT="Courier New"]# echo level 0 > /proc/acpi/ibm/fan (fan off)[/FONT]

---

