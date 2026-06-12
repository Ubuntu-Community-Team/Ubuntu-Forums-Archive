---
title: "Initialization of Ethernet when booting - doesn't work at certain times"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by veraction on 2005-04-14
Hi,

I'm new to Ubuntu & it seems very nice, but there is one problem that is driving me crazy.

Some info about my comp (what I think is needed to know):

Motherboard: Asus A7N8X - Deluxe
Dual boot - Windows XP / Ubuntu 5.04 using GRUB bootloader

When I turn my computer on after its been off for an extended period of time (~8 hours overnight), and boot into Ubuntu, it never can initialize my network connection/ethernet -- so I have no Internet. I can restart many times, then boot back into Ubuntu and still no Internet. Though, If I boot into Windows once, the Internet will work - then I restart and go into Ubuntu and then the Internet works. **How can I make it so Ubuntu successfully initializes my ethernet/Internet connection on boot without having to boot into Windows first?**

I hope that was clear enough, I'll try to add any infomation which is needed..

Thanks

---

### Post by alastair on 2005-04-14
On a non-working Ubuntu boot, look through your boot log :

/var/log/syslog

and check for network/ethernet related messages. This might point to a cause.

---

### Post by spd106 on 2005-04-14
hi veraction,

Could be a problem with getting an ip address from your dhcp server, assuming you have one.

scanning through $dmesg might point to the problem or $ifconfig eth0

---

### Post by veraction on 2005-04-14
I'll also add that I can reboot Ubuntu and the internet will still work

Trying to fix this looks very difficult :(

---

### Post by veraction on 2005-04-17
so, nobody has any ideas? Looked at that log, and it didn't seem to help..

/sigh - back to windows  :(

---

