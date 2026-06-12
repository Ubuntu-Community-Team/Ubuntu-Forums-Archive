---
title: "howto: semi suspend-to-ram support that may work on your laptop"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by epb613 on 2005-05-24
This isn't really suspend to ram but it's a fairly powered down state (my battery lasts for 10hrs in this state) that may work well for you if suspend-to-ram (ie: echo 3 > /proc/acpi/state) doesn't work.

First if you're not using kubuntu then: 'sudo apt-get install klaptopdaemon'
^^ will install klaptop and some kde libraries neccessary for running kde programs in gnome.

Next disable your power button from shutting down your pc. Easiest way to do this is:
'sudo mv /etc/acpi/powerbtn.sh /ect/acpi/powerbtn.sh-backup'

Now, to sleep the laptop, type:
'sudo klaptop_acpi_helper --standby'

To resume, press your power button.

Whether or not this works for you, post your laptops and results if you have time. I tested this on a Compal CL56 (aka Zepto Znote 4200 and Chembook 2056 and other names).

Thanks for reading and I hope this helps.

---

