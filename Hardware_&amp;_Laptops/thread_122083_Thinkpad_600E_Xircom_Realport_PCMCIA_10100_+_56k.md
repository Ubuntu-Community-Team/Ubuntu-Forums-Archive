---
title: "Thinkpad 600E Xircom Realport PCMCIA 10/100 + 56k"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by tarotking on 2006-01-26
After much much searching around both the forums and around the internet I decided to give posting a try.

I have the dreaded  TP 600e, Xircom Realport 10/100 Ethernet + 56K modem combination. I have not found a definate answer to how to get an IP adderss.

The pcmcia card worked both under windows98 and Debian sarge where it was detected correctly during install. I decided to move to ubuntu b/c of the quicker releases and experienced the usual sound not working for 600e ( which is fixed ).

So far I have tried,

adding acpi=off to grub and disabling IVP6. 

The driver that is loaded is xircom_cs which is the correct driver. I can view stats for the interface and have tried ifconfig eth0 down/up.

I also tried sudo dhclient, which will not return an ip address to the nic card. 

This issue has been previously posted here

I have [http://ubuntuforums.org/showthread.php?t=82011&highlight=xircom+600e](http://ubuntuforums.org/showthread.php?t=82011&highlight=xircom+600e)

But no new posts have been added for a while. I would like to keep this moving forward. any help is appreciated..

---

### Post by grumpymole on 2006-01-26
I have same setup and it works well.  The only immediate differences I can see to my setup is that I also have > pnpbios=off added to the boot parameters.  That is, in addition to the > acpi=off

Also, check that you have disabled the Fastboot setting in the BIOS.

Regards

Warren

---

