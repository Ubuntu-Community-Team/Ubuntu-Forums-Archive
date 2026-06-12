---
title: "Ethernet device not recognized"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by nejolas on 2006-03-29
I just tried the Ubuntu Live CD and my network card (Sundance Ethernet) was not recognized. Is there a Sundance Ethernet Controller for Ubuntu? 

Regards,

Nicolás.-

---

### Post by jamesr on 2006-03-29
post the output of```
dmesg | grep eth
``` what type of NIC? 
wired or wireless?
PCI card etc?

---

### Post by Danieliozzi on 2006-09-17
for me the Solution was to compile the Encore Drivers for the "ENL832-TX-ICNT" (sundance) after making 2 lines modification in the source.
It seems to be a problem with the kernel 2.6.15-26 and the module that comes with the distro.
To be able to do that u need to

1.Modify sundance_main.c
1.a = line 1400 "pci_dma_sync_single" --> "pci_dma_sync_single_for_cpu"
2.b = line 1653, comment the line
Original = strcpy(info.bus_info, np->pci_dev->slot_name);
Correct = /* strcpy(info.bus_info, np->pci_dev->slot_name); */

3.To compile succesfully u need to intstall the packages from your Ubuntu CD from K/X/ubuntu 6.06.1 i386\pool\main" only if u dont have internet conection other way u can do it online with the package manager tool.

4.copy the sundance.ko module that u make to lib/modules/2.6.15-26-386/kernel/drivers/net "Yes overwrite it".

5.Uninstall the module first ."rmmod sundance"

6.Install the module ."insmod sundance" or maybe "insmod lib/modules/2.6.15-26-386/kernel/drivers/net/sundance.ko"

7.and finnaly bring up the card with "ifconfig eth0 192.168.0.1" or whatever your ethx or ip addres is, or maybe u can use the xwindows system confriguration tool that u have or u like .

I have to say that the main clue for the solution comes from "http://bazar2.conectiva.com.br/pipermail/linux-br/2006-June/040211.html"
but is in brazilian portuguese.

---

### Post by jamesr on 2006-09-18
I though that this thread was dead, no replies to my questions which were in reponse to the original posters problems.

thanks for the information.

---

