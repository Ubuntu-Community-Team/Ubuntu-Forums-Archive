---
title: "[SOLVED] How to install printer driver that is not displayed in printer configuration"
date: 2008-09-09
forum: General Help
---

### Post by abcuser on 2008-09-09
Hi,
I have a network printer Lexmark E120N and I would like to install printer driver. But this driver is not listed on printer driver list in Ubuntu "Printer configuration" window. How to install printer driver?
Thanks,
Abcuser

---

### Post by abcuser on 2008-09-09
Hi,
I have found out solution. In article [Insights for a quick and easy Ubuntu printer installation](http://www.eioba.com/a2276/printing_with_ubuntu) there is note to check the "Generic" driver and what tipe of "PCL" is supported. So I checked the [Lexmark printer specification](http://www.lexmark.com/lexmark/product/home/371/0,6970,204816596_653293751_613122419_en,00.html) and found out that printer is supporting Printer Languages "PCL 5e".

In Ubuntu:
1. System | Administration | Printing
2. Select "Other" from "Device" menu.
3. Enter uri address like [http://printer_ip_address/](http://printer_ip_address/) and Forward button
4. "Select printer  from database": Makes: Generic and Forward button
5. From "Models" I selected "PCL 5e" and from "Drives" selected the "recommended" driver.

I tried to print test page and it prited out successfully. So problem solved.

Regards,
Abcuser

---

