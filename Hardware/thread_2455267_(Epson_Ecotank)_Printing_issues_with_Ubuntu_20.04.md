---
title: "(Epson Ecotank) Printing issues with Ubuntu 20.04"
date: 2020-12-16
forum: Hardware
---

### Post by csae2608 on 2020-12-16
Hello,

i have installed Ubuntu 20.04 ontop of 18.04 and now i have issues with with my printer Epson Ecotank 20.04


here are several issues:


1. The printer is added automatically onto the printing devices, but it won't print
2. when i delete the printer, it gets automatically added again to the printers, although i don't want that (at the moment).
3. the printer is connected via USB and Ethernet, but USB is not recognized.
       (sometimes it is recognized, sometimes not: then it claims: waiting for the printer to become available, although it is on and not printing at the moment).
4. when i add the printer manually in the advanced options, it would not show under "USB", but only under "Network Printers"
5. i have manually installed the EPSON Printer drivers for ET-4750 from the EPSON Website, but nontheless the printer won't print.

i have not tried to add the printer manually via CUPS, as i want the printer to function also via setting up inside the Ubuntu System Print Settings.


it seems that the automatically adding of the printer is confuesing the system or there is some other issues present?

Maybe there has been some issue with updating from 18.04 to 20.04, but other than printing, everything works just fine.

On Ubuntu 18.04 printing works just fine.

---

### Post by crip720 on 2020-12-16
20.04 does seem to have issues with printing and a few other hardware that just worked in 18.04 for some people.  Not sure if anyone has found good solution yet, but hope so(might just have missed it).  Setting up a dual boot with 18.04 version might be best for now unless better people know of solution.

---

### Post by brian_p on 2020-12-16
> **csae2608 said:**
> Hello,

i have installed Ubuntu 20.04 ontop of 18.04 and now i have issues with with my printer Epson Ecotank 20.04

Ubuntu 20.04 installs ippusbxd to manage a USB connected device. ippusbxd is very much sub-optimal.

> 
here are several issues:


1. The printer is added automatically onto the printing devices, but it won't print

Auto-setup is down to cups-browsed; nothing wrong there. Non-printing is down to ippusbxd.

> 
2. when i delete the printer, it gets automatically added again to the printers, although i don't want that (at the moment).

See the cups-browsed.conf manual.

> 3. the printer is connected via USB and Ethernet, but USB is not recognized.
       (sometimes it is recognized, sometimes not: then it claims: waiting for the printer to become available, although it is on and not printing at the moment). Probably down to ippusbxd.
> 4. when i add the printer manually in the advanced options, it would not show under "USB", but only under "Network Printers" That's correct when IPP-over-USB is involved. Nothing wrong there.

> 5. i have manually installed the EPSON Printer drivers for ET-4750 from the EPSON Website, but nontheless the printer won't print.

That's correct when IPP-over-USB is involved. Nothing wrong there.



> 
On Ubuntu 18.04 printing works just fine.

18.04 does not use IPP-over-USB as a matter of course.  [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting) explains your observations.

---

### Post by Autodave on 2020-12-16
Did you do a clean install of 20.04 or did you upgrade 18.04 to 20.04?

---

### Post by csae2608 on 2020-12-16
i did upgrade to 20.04 via USB stick over 18.04.
now it seems that the Printer is recognized via USB connection, after adding it manually in the "Additinal Printer Settings".
(Epson ET-4750 Series - epson-inkjet-printer-escpr2 1.1.24-1lsb3.2 (Seiko Epson Corporation LSB 3.2))

Please close this thread and mark as solved;

if the problem reappears, i will make myself heard. thank you all for the input;

---

