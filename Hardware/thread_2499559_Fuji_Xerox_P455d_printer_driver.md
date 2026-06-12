---
title: "Fuji Xerox P455d printer driver"
date: 2024-07-31
forum: Hardware
---

### Post by rudolfl on 2024-07-31
Hi all
Printer driver in Ubuntu does not allow for duplex printing. Double side printing option is set to OFF and can not be changed. I was unable to find an updated driver. Fuji Xerox site only lists Windows and Mac drivers.

I am on kUbuntu 22.04LTS. 

Yes, printer supports double sided printing. I can print double sided from Windows and Mac

Thanks
Rudolf

---

### Post by euol on 2024-08-05
Check your printer settings in System Settings > Printers are correctly configured for duplex printing. If the option is missing, try installing a generic driver like Generic PostScript Printer or using a PPD file for your model. You can access the CUPS web interface at [http://localhost:631](http://localhost:631) to modify duplex options.

---

### Post by rudolfl on 2024-08-09
Thank you!!!

There is no PPD file for this printer (at least I did not find one) and there is no option to to turn duplex on, but I did try your suggestion.
Tried few generic drivers and one of them worked. Now I can print double-side

Rudolf

---

