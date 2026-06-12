---
title: "eth0 interface problem after thundestorm"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by krypto_wizard on 2006-04-09
I live in Florida. Last night during tunderstorm my computer died. But then I replugged everything seemed to work except the ethernet port. 

Ubuntu doesnt detect eth0 and neither does Windows ( I have a dual boot).

Can you please sugest what could be the reason. And if my ethernet card is down or broken what can I do to fix it.

Every help is appreciated.

thanks.

---

### Post by engla on 2006-04-09
Hard for us to say, but it could very well be broken.. be sure to run "lshw" in the terminal and see if you can or can't find your network card there.

Anyway, if only the NIC broke and nothing else, you're quite lucky since that's possibly the cheapest single part to replace. Where I live I can get hold of a new one for &#8364;15 or less.

---

### Post by fatdaddy on 2006-04-09
I have another idea for you to check.

If you have an onboard (built into motherboard) network card go into your computer bios and check to make sure it is still enabled.

In windows you can go to device manager and see if it shows the network card at all under networking.

I have also lost my switch during lightning which drops the network connection but the card is still there although appears to not be working.

---

### Post by krypto_wizard on 2006-04-09
It doesn't detect the NIC using lshw and also using device manger in Systems.

I wil try replacing it. Any more suggestion u can give ??



[QUOTE=engla]Hard for us to say, but it could very well be broken.. be sure to run "lshw" in the terminal and see if you can or can't find your network card there.

Anyway, if only the NIC broke and nothing else, you're quite lucky since that's possibly the cheapest single part to replace. Where I live I can get hold of a new one for €15 or less.[/QUOTE]

---

