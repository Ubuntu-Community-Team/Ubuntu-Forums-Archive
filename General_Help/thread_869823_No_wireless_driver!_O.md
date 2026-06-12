---
title: "No wireless driver! :O"
date: 2008-07-25
forum: General Help
---

### Post by paddymac125 on 2008-07-25
When I use Vista it has no trouble connecting to the internet wirelessly, but when I run Ubuntu it can't find the driver!
I've tried all of the troubleshooting advice, but now I think I might have to build the driver!:(
Please help me!

---

### Post by coffeecat on 2008-07-25
> **paddymac125 said:**
>  but now I think I might have to build the driver!:(

Maybe. Maybe not.

To know what to do next, you need to know the chipset of the wireless nic. Once you've done that, either search the forums (there will be quadrillions of threads for each of the chipsets) and/or post back to this thread and someone may be able to help you.

You should be able to determine the chipset somewhere in Vista (but I don't know where - I've never used Vista, neither will I). Or in Ubuntu, open a terminal and if your wireless nic is a PCI card in a desktop, or you are using a laptop, run:

```
sudo lspci
```and look for the line with 802.11 and/or wireless in it. If you are using a USB wireless dongle, run:

```
sudo lsusb
```instead and find the wireless/802.11 line.

Word of advice - when starting help threads, always post some information about your hardware. These forums are friendly, but the probable reason your post was left unanswered for so long is that it was short on relevant detail.

**Edit**: another piece of advice. :wink: Click on the report button for your post and ask the forum mods to move this thread to the 'Networking and Wireless' subforum. You might get more replies there.

---

