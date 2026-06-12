---
title: "Problem Trying to Print to Windows XP Shared Printer"
date: 2008-11-01
forum: Hardware
---

### Post by spikedupback529 on 2008-11-01
Hi guys,

I'm having a problem printing to a printer that is being shared via Windows XP. I can browse to the printer via the smb browser, and I can locate it fine. I can find the correct device driver, and it seems as though it will work. However, when I try to print a test page, I get a message saying NT_STATUS_ACCESS DENIED. I checked the settings in Windows XP, and it seems as though it should work. I can print to the printer through all 19 of my Windows XP computers, so it's not a sharing issue. I've set it so that anyone can access the printer as well. I've googled this problem, but there's nothing that really pertains to what I'm experiencing. 

If there's no easy way of getting the printer to work (or if it's not possible), I can also network this printer. If I do connect this to my switch, how would I find the printer in Ubuntu? 


Thanks,
Dale Gallosky

---

### Post by Rinias on 2009-02-18
I, as well, can navigate to the printer and select it but I get the "NT_STATUS_ACCESS_DENIED" error.

I have enabled "Other Network File and Print Services" for Windows' Unix printing and even had a prompt for logging in once! But it never printed anything...

I know that the printer works when directly connected to my Ubuntu (8.10 x86-64) computer, it just won't work when shared.

The firewall (Windows) is open for printing, etc. But nothing prints.

Thanks in advance,

Rinias

---

