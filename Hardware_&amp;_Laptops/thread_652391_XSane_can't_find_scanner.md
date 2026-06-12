---
title: "XSane can't find scanner"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Island_Jon on 2007-12-28
With Gutsy, I have a HP PSC2210xi which is supported. It's installed as HP2200 series

When trying to start XSane it looks for devies and after a while finally says 
Failed to open device 'hpaio:/usb/PSC_2200_Series?serial=MY2ASD41190G'
error during device I/O

this device is listed in the admin/printer as the device URI

gscan2pdf  scans looking for printer and also returns a similar error 
scanadf returns nothing

terminal command returns:
scanimage -L
 `hpaio:/usb/PSC_2200_Series?serial=MY2ASD41190G'

Installed HPLIP, no help, uninstalled it.

Printing under word processors is OK.

Any help/suggestions would be appreciated very much.

Jon

---

