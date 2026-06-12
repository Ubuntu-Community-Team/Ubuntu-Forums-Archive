---
title: "failed boot when wireless card is plugged in"
date: 2008-11-09
forum: Hardware
---

### Post by arashpa on 2008-11-09
Hello all,

I have just recently bought a Dell Inspiron 530n with Ubuntu installed. I'm trying to add a linksys wmp55ag which is supposed to be compatible with linux/ubuntu to my box. When I plug in the wireless card the system just doesn't boot. It stops at loading the hardware drivers and hangs there. Any help would be greatly appreciated.

To add further information my wireless card is linksys wmp55ag with atheros chipset which should be madwifi compatible. I'm loading kernel 2.6.24-21-generic .... ro all_generic_ide quiet splash for generic boot and 2.6.24-21-generic... ro all_generic_ide single for recovery mode.

When I boot in single user mode the last line which it hangs at is:
[ 54.446450] ath5k_pci 0000:02:00.0: registered as 'phy0'

Can anyone please give me a hint or direct me to website/docs which can help me solve this problem?

Thanks,
Arash

---

