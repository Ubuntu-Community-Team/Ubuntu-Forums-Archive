---
title: "Odd lpr banner problem"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by Paul Moir on 2008-01-03
Suddenly and seemingly without provocation, programmes that use lpr like firefox started printing with the CLASSIFIED banner on my HP Deskjet 5650.  When printing via the CUPS-PDF virtual printer, this problem didn't happen.  Also, I don't think it's a core CUPS problem as these banners did not appear when printing from gedit, etc, and also Start and End Banners are set to <none> in the cups configuration.

I managed to suppress the banners with "sudo lpoptions -o job-sheets=off".  Incidentally, before doing this lpoptions didn't report job-sheets as being set.  The command creates the file /etc/cups/lpoptions so this change is permanent, but this seems to be a work-around.

Is this a common problem?  Where else would I look to find this setting?  Is /etccups/lpoptions normally existent and did mine just disappear for some reason?

Thanks for your time!

---

