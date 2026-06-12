---
title: "[SOLVED] printer won't print"
date: 2008-05-27
forum: Hardware
---

### Post by Stolea on 2008-05-27
My Canon i965 printer was recognized and installed by Hardy. Unfortunately it can't / won't print and gives the following error:

CUPS server error:
There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

On closer inspection it has only Letter size instead of A4.

I downloaded and installed the Canon i965 driver from openprinting.org. Same result. It would appear that the printer driver selection database doesn't know of the newly installed driver? Is there something that i need to do to point the printer to the new driver?

---

### Post by HotShotDJ on 2008-05-27
> **Stolea said:**
> I downloaded and installed the Canon i965 driver from openprinting.org. Same result. It would appear that the printer driver selection database doesn't know of the newly installed driver? Is there something that i need to do to point the printer to the new driver?Did you either manually restart the cups server:```
sudo /etc/init.d/cupsys restart
```or reboot (unnecessary if you just restart the effected system, but it makes former Windows users very happy for some reason)

---

### Post by Stolea on 2008-05-27
Nope, that won't do it. Is there some place that I can see what version driver is used?
Also the i965 is not listed under the Canon printers. Only i865.

---

### Post by Stolea on 2008-05-27
I tried and installed the BJ8200 driver and it seems to work (so far)
Thanks

---

