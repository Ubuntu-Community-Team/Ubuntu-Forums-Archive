---
title: "Finally my hp 6715b laptop has wireless!"
date: 2010-08-25
forum: Hardware
---

### Post by pookiebear on 2010-08-25
Just wanted to point out that my HP 6715b business laptop is finally able to use the built in wireless. 
I am running Xubuntu 10.10 (latest alpa with updates as of today's post) 
And the broadcom wireless is finally working. 

lspci reports as
30:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

The b43 drivers have never worked.
NDISWrapper never worked.
The STA driver finally started working with this last round of updates from update manager today. Not sure what was updating but it is working so thank you ! No tweaks either just go to "hardware drivers" and select the STA ones. 


side note as to why this may be of interest. 
HP usually BIOS locks what mini pci cards you can add to your laptops so I was not able to switch it over to a intel wifi card like you can with some other brands. There are bios "tweaks" using a hex editor and a bunch of steps posted on the internet but I did not want to go through that trouble so I have been using an old usb wireless dongle for awhile.

---

