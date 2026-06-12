---
title: "Ricoh Host Controller for MMC/SD cards not Mounting in Ubuntu 16.04"
date: 2016-05-20
forum: Hardware
---

### Post by wanderer3 on 2016-05-20
This seems to be a recurring issue dating a long while back, but I haven't found a solution from previous threads and bug reports

Using the Terminal command

$ lspci | grep MMC

gives the output


43:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)

I don't know where to get the drivers for this or how to install if there are any. Also attempts at manual mount e.g.

$ setpci -s 43:00.0 0xCA=0x57 43:00.0 0xCB=0x02 43:00.0 0xCA=0x00

give output


setpci: Missing width.
Try `setpci --help' for more information.

Can anyone help me with this please.

---

