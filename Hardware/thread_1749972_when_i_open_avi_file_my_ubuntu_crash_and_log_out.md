---
title: "when i open avi file my ubuntu crash and log out"
date: 2011-05-05
forum: Hardware
---

### Post by magdi on 2011-05-05
when i open avi file the message appear 
{{{
Your video output acceleration driver does not support the required resolution: 720x304 pixels. The maximum supported resolution is 768x304.
Video output acceleration will be disabled. However, rendering videos with overly large resolution may cause severe performance degration.
}}} 

i searched for it , and find solution 
by changeing AccelMethod option to uxa in xorg.conf file
ut i can't do it in 11.04 ,
because i can't find the xorg.conf file to edit it .   

my vedio driver is sis 617 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE 
VGA Display Adapter (rev 10)


please help 
thanks,
magdi

---

