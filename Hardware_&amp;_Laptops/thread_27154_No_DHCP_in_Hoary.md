---
title: "No DHCP in Hoary"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Soko on 2005-04-15
This is frustrating.

I have a Dell D800 laptop with an ipw2100. Hoary detected it fine, so I enabled it, selected the essid, typed in my WEP key correctly and ... nothing. No DHCP, no data moving.

iwconfig shows that I am indeed associated with my AP properly, but I can't get an address in any way, nor does a static IP work. I'm at a loss - the same setting worked on FC3 and XP as well.

Anyone know where I fell down here? ](*,) 

Soko

---

### Post by jensyt on 2005-04-15
[QUOTE=Soko]This is frustrating.

I have a Dell D800 laptop with an ipw2100. Hoary detected it fine, so I enabled it, selected the essid, typed in my WEP key correctly and ... nothing. No DHCP, no data moving.

iwconfig shows that I am indeed associated with my AP properly, but I can't get an address in any way, nor does a static IP work. I'm at a loss - the same setting worked on FC3 and XP as well.

Anyone know where I fell down here? ](*,) 

Soko[/QUOTE]
Is DHCP configured at all on your host? As in, do you have:
```
iface eth0 inet dhcp
```
in you "/etc/network/devices" file? (Substitute eth0 with whatever you're using...)

---

