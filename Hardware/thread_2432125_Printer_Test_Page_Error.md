---
title: "Printer Test Page Error"
date: 2019-11-27
forum: Hardware
---

### Post by surreal-zebra on 2019-11-27
When adding a printer, I'm running into problems printing a test page.  It successfully found the printer, a Canon D480, and used the Generic Text-Only Printer driver.  But when trying to print the test page I got the below message:  Failed to perform request: Unsupported format "application/vnd.cups-pdf-banner".  Running an up-to-date Kubuntu 18.04.  How can I get this problem resolved?

---

### Post by brian_p on 2019-11-27
My first thought is that a text-only driver is not suitable for use with this printer. I believe you need to find and install Canon's linux-UFRII-drv-v500-uken-04.tar.gz package.

---

### Post by surreal-zebra on 2019-11-27
That worked! Thanks for your help. :)

---

