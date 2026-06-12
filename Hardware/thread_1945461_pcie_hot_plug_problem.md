---
title: "pcie hot plug problem"
date: 2012-03-23
forum: Hardware
---

### Post by faeng on 2012-03-23
hello all
i am trying to make my laptop recognize  firewire pcmcia expresscard. i am having trouble with it. when i plug the card, nothing was happening.  if i plug the card before booting process, system recognizing it and using the card without any problem. but when i unplug the card, system still showing the firewire card but not working. dmesg doesnt return any result when i plug and unplug the firewire card. 

i have modified the my /etc/modules files and added pciehp.pciehp_force=1 or 0 and pciehp.pciehp_poll_mode=1 but these didnt worked. 

i also tried to echo 1 > /sys/bus/pcie/rescan .
this works if i plug the card after boot process. but again when i unplug the card, system doesnt understand that.

do you have any suggestion about that? what can i do to use my card  as a real hot-plug card?

---

