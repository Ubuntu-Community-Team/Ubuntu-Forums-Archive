---
title: "Detecting/configuring Wired Ethernet"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by JaimeMM on 2005-04-21
Hi all, 

I have just installed Ubuntu on my new laptop (Toshiba Tecra A3) and everything seems to work fine but wired lan. 

I need to configure de wired lan, and I don´t know how to do it. 

The Lan Card is a "Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller" I think it uses an Intel chipset and it runned fine with Mandrake.

Must I install some package ??  load some kernel module ?? How do I do that??? 

How can I see the devices detected by the system ? How do I configure them ?? 

I´ve benn using "Device Manager" but it only allows me to see the devices, but not to configure them. 

Thanks a lot, and best regards.

---

### Post by dataw0lf on 2005-04-21
I need: 
your 'ifconfig' output.
and your '/etc/network/interfaces' file.

---

### Post by heimo on 2005-04-21
In the System menu you should find Networking (in some submenu). There you should see network interface card and can enter configuration. If you don't see any card there, please post the output of lsmod and lspci (run on terminal). Those will tell us about modules which are already loaded and pci devices.
 
You could also try running *ifconfig*, if network interface is up, you'll find at least two devices (lo and eth0). All the interface settings are in /etc/network/interfaces (I'm not 100% of that path, may be "networking"). You should also have DNS server ip addresses configured in /etc/resolv.conf - those will appear automaticly, if you are using DHCP settings (which I recommend, if that's possible).

---

### Post by ferriol on 2005-04-29
[QUOTE=JaimeMM]Hi all, 

I have just installed Ubuntu on my new laptop (Toshiba Tecra A3) and everything seems to work fine but wired lan. 

I need to configure de wired lan, and I don´t know how to do it. 

The Lan Card is a "Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller" I think it uses an Intel chipset and it runned fine with Mandrake.

Must I install some package ??  load some kernel module ?? How do I do that??? 

How can I see the devices detected by the system ? How do I configure them ?? 

I´ve benn using "Device Manager" but it only allows me to see the devices, but not to configure them. 

Thanks a lot, and best regards.[/QUOTE]
 I have this problem too. Is this chip suported by kernel ?

---

### Post by larsivi on 2005-05-06
I have a Toshiba Tecra A3 too, and have the same problem.

I can see no loaded eth-modules with lsmod. lspci says 

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10).

This is really annoying as the Wired-support-table in the wiki says it should work out of the box.

---

### Post by larsivi on 2005-05-06
[QUOTE=larsivi]I have a Toshiba Tecra A3 too, and have the same problem.

I can see no loaded eth-modules with lsmod. lspci says 

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10).

This is really annoying as the Wired-support-table in the wiki says it should work out of the box.[/QUOTE]

lspci -n says

0000:02:00.0 0200: 11ab:4351 (rev 10)

---

### Post by larsivi on 2005-05-06
[QUOTE=larsivi]

I can see no loaded eth-modules with lsmod.[/QUOTE]

I was lying, there. I have sk98lin installed. It doesn't help, though.

---

### Post by darrenism on 2005-07-26
Same problem here.  Anyone found a solution yet?

---

### Post by mscman on 2005-12-08
I had this same problem on my toshiba laptop (m45-s331).  The thing that fixed it for me was disabling ACPI for PCI devices on boot.  When grub boot loader comes up, press 'e' and you'll get a list of the commands grub is being sent.  Highlight the 2nd choice and add to the end of the line:

```
pci=noacpi
```

This fixed the problem of both my wireless and wired network cards not coming up.  If it works, you should add the line permanently to your 
/boot/grub/menu.lst file.  Just ask if you need help...

---

