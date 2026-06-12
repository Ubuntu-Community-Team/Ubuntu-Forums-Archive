---
title: "Dell 500m Ethernet/WLAN not working..."
date: 2004-10-14
forum: Hardware &amp; Laptops
---

### Post by lockenkeyster on 2004-10-14
Hi -

bear with me, very newbie:

I haven't been able to get Ubuntu to use my ethernet adapter or my Intel WLAN 2100. Both show up in the hardware section of the system settings, which tells me that they have been detected, but when I try to set up the network (by setting the eth0 to "active") it goes right back to "inactive".

Please help!

---

### Post by arctic on 2004-10-15
hi. :)

maybe we can fix this problem. have you typed in a console as root "ifup eth0" if not, do it. then we need the output of "ifconfig" and the contents of your /etc/sysconfig/networkscripts/ifcfg-eth0 file.

---

### Post by Damon on 2004-10-15
Hey Lock,
My ubuntu install went flawlessly, and my onboard eth card (eth0) worked fine. Then I tried to install my linksys wlan pcmcia card, and neither would come up. Same symptom as you. I had to manually edit the /etc/network/interfaces file and remove all the garbage my wlan card put in there.

Hope that helps..

---

### Post by lockenkeyster on 2004-10-16
Just a followup to my problem:

So neither card was working, and also sound was broken...
I made these changes:

1) in synaptic package manager I removed the pcmcia-cs package
2) in /etc/boot/grub/menu.lst I edited the boot line for ubuntu (like I've seen in the forum for broken sound ("pci=noacpi") and rebooted....

3) broke out the champagne, as all three problems were corrected by these changes!

Thanks much for the help!

---

