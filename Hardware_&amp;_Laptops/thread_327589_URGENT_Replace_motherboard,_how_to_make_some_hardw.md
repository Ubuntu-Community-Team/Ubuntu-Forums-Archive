---
title: "URGENT: Replace motherboard, how to make some hardware work?"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by roberthr on 2006-12-29
Please, please help.

I just replace motherboard and CPU now I can't make some hardware to work. For VGA I did dpkg-reconfigure -phigh xserver-org. 

What do I have to do for network card?

Sound seems to be working, USB too. 

Doesn't ubuntu have anything to start hardware detection in such cases?

---

### Post by coffeecat on 2006-12-29
If the appropriate drivers are compiled into the kernel, then the hardware will just work. You don't have to do anything. Let me give you an example.

A year or so ago I installed a particular Linux distro using a machine with an AMD64 CPU and a motherboard with a VIA chipset. The distro wasn't Ubuntu but I'm sure the result would have been the same. And it was a 32-bit version. Then I took the HD out of the AMD64 machine and fixed it into another machine which had an Intel Celeron CPU and motherboard with Intel chipset. It booted up with no problems at all. All the hardware was detected because it was fairly mainstream and the drivers were in the kernel.

I'm surprised that your network card (I presume you mean the ethernet card) is not being detected because Linux kernel support for ethernet cards is good. So, suggest you do two things. Go into the networking GUI app (under System > Administration in Gnome) and check that the ethernet card is detected there and is activated. If not, open a terminal and type:

```
sudo lspci
```Look for the line with the word 'ethernet' in it, post that and someone should be able to help.

---

### Post by roberthr on 2006-12-29
I found that little thing. I just had to replace MAC address in /etc/iftab

---

### Post by coffeecat on 2006-12-29
Thanks for mentioning that, roberthr. I'd not come across /etc/iftab before - it seems to be an Ubuntu peculiarity. It's not in Fedora, Gentoo or Zenwalk, to name but three.

I recently cloned my desktop Gentoo installation by making a tar.gz archive and copied it to my laptop - I'm posting from there now. I had quite a bit of tweaking to do, but the ethernet card 'just worked', even though the MAC addresses are different. I'll bear the existence of /etc/iftab in mind if I ever need to clone Ubuntu from one machine to another.

---

### Post by dahas on 2007-03-14
Hi
I did a full replace a old pc with a new 1 just moving the hdd and cd-rom from older on new 1.
The problem was with network card who on syslog say:
 **eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 12**
when look at** ifconfig -a** was set as **eth2**
The only way to make it to be set as eth0 was to remove the 2 line from /etc/iftab from old 2 nework card.
Thanks for info about /etc/iftab

---

