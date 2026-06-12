---
title: "TR2 wireless problem"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by Crowhurst on 2005-12-11
Wifi card (built in) used to work, then became intermittent then stopped altogether. Works in windows (dual boot).

Card can find the network with scan. Wifi network is fine, i am on it now.

Card will not associate. I can't even force it to associate.

Sony TR2
Intel Pro/wireless Lan 2100 3B Mini PCI (rev04)

ifconfig shows the wireless cards' MAC address

lshw -C network shows the card enabled but unnassociated

iwconfig shows the card unassociated

any ideas? This is driving me nuts. I dont remember making any changes, I could for a bit use Network Settings to Deactivate/Activate the card and that would make it work for a while - or reboot - but that won't work anymore.

---

### Post by Crowhurst on 2005-12-11
I did an "ifdown -a" and then an "ifup -a" and it found the system and worked.

Could it be something preventing the dhcp acquisition?

I had tried "ifconfig eth1 down" and "ifconfig eth1 up" but that did not fix it. The "man ifup" says that it use "ifconfig" and "route" to do its work.

Any ideas what is going on?

---

### Post by scubajeff on 2005-12-11
try installing the wifi-radar. It works like a charm. I even create a new ACPI event handler to bring it up when I switch on the wireless hardware button.

---

