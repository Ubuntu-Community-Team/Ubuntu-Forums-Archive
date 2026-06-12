---
title: "ATI FirePro V3700 and 12.10"
date: 2013-04-09
forum: Hardware
---

### Post by weliwarmer on 2013-04-09
I'm trying to install the proprietary AMD/ATI Catayst on my z600 that contains a ATI FirePro V3700.

According to [this]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx") page 12.10 only supports ATI drivers above 9.3.

AMD [recommend]("http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.3%3b2.4.5%3b2.4.7&product=2.4.7.3.3.1&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20") driver version 8.801 for the V3700.

Can anyone confirm
[LIST=1]
[*]that the FirePro V3700 only works with 8.801?
[*]or can the newest 9.012 driver (13.1 catalyst) be used?
[*]or Ubuntu 12.10 will work happily with ATI driver version 8.801?
[/LIST]
Thanks, Tim

---

### Post by Yellow Pasque on 2013-04-09
> **weliwarmer said:**
> can the newest 9.012 driver (13.1 catalyst) be used?
No, it doesn't support your card.

> or Ubuntu 12.10 will work happily with ATI driver version 8.801?
No, 8.801 doesn't support the Xserver (1.13) found in Ubuntu 12.10

The open-source radeon driver should work fine on Ubuntu 12.10. If you really need to use Catalyst, you're better off using Ubuntu 12.04.

---

