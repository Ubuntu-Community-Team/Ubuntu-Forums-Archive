---
title: "Fuji Xerox DocuPrint C525A Driver (CUPS)"
date: 2021-11-14
forum: Hardware
---

### Post by frizby66 on 2021-11-14
Hope someone can help. Trying to get a Dell 1320C printer running on CUPS and see that I need to install the Fuji Xerox DocuPrint C525A Linux drivers, however Fuji have now put this end of life and removed all trace of their drivers online! Spoke with tech support and they said that I should either use the original disc to get the driver or consider buying a new Printer (talk about saving the planet!). Does anyone have a set of drivers or point me in the right direction (have search the forum and all the links to the drivers point to Fuji site, which is a dead-end)?

---

### Post by brian_p on 2021-11-14
```
 wget http://fastcat.org/debrepo/pool/main/f/fuji-xerox-docuprint-c525-a-ap/fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb
```

The package dates from 2005. The driver is probably 32-bit. Good luck :).

---

### Post by frizby66 on 2021-11-14
Thanks Brian...

Found a driver I could manually install but when I follow the instructions, still have issues..but looks like file path issues and cant get my head round why!

This the path setting in the PDD file, but when I do a test print, I get a weird path error!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289466&stc=1[/IMG]

*cupsFilter: "application/vnd.cups-postscript 0 /usr/lib/cups/filter/FXM_PF"
*cupsModelNumber: 0
*FXMainFilter: "/usr/lib/cups/filter/FXM_MF"
*FXFilterDir: "/usr/lib/cups/filter"
*FXFilterChain: "FXM_PS2PM, FXM_PM2FXR, FXM_SBP, FXM_PR, FXM_CC, FXM_ALC, FXM_HBPL"
*FXDlutFilePath: "/usr/share/cups/FujiXerox/dlut/FX_DocuPrint_C525_A_AP.dlut"

---

### Post by brian_p on 2021-11-14
*/usr/lib/cups/filter/FXM_PF* exists in the package. I am unable to offer any further help. Sorry.

---

