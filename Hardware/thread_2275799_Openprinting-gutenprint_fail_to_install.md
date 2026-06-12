---
title: "Openprinting-gutenprint fail to install"
date: 2015-04-28
forum: Hardware
---

### Post by svannay on 2015-04-28
I changed my printer last week for a HP Officejet Pro 8610. On my Ubuntu 14.04.2 and on Mint 17.2, I tried to "add a printer" in the system-config-printer but things went wrong while installing openprinting-gutenprint driver. The installation process stalled, leaving a few packages half-installed (lib6-dev:amd64, lsb...) 

I was not able neither to remove the packages, nor to finish the install.  I've tried lots of advices I've found on various forums, but nothing happens.

Now, at last I've got a solution I put here for the record :
[LIST=1]
[*][FONT=courier new]sudo dpkg -i /var/cache/apt/archives/libc6-dev_2.19-0ubuntu6.6_amd64.deb [/FONT]to finish to install libc6 manually
[*]install the openprinting-gutenprint package from synaptic
[*]"add a printer" again from system-config-printer
[/LIST]
That's all

---

### Post by Pbear8118 on 2016-03-29
Thank you for posting these instructions. As a newer Linux user, I was going nuts installing my new Brother printer (too new to have drivers avail from Brother for Linux) and the Gutenprint was my only hope, but Add New Printer hung on install of the gutenprint package. 

I didn't need to uninstall anything, but downloaded the newest version of gutenprint from Sourceforge and then used Synaptic Package Manager to install the drivers then did the Add Printer using the system recommended drivers which was DCP-1200 for my HL-L2380DW (laser) - it prints great wireless. Very grateful to these forums.

---

