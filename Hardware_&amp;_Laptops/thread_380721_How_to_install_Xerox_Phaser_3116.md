---
title: "How to install: Xerox Phaser 3116"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by glisteringwaters on 2007-03-10
Hi, I am having difficulty installing my Xerox Phaser 3116 (USB).

When I tried to add my printer via System->Administration->Printing, I can only find options for parallel port printers.

I was still unable to install my printer even after finding very good instructions given at:
[https://help.ubuntu.com/community/XeroxPrinters]("https://help.ubuntu.com/community/XeroxPrinters").

Here's what I tried to do:
I was able to copy my Xerox printer disc contents to tmp/printer and run, sudo ./setup.sh, Expert, defaults and "Begin Install".

However when I tried to press "Start", I got a windo popup stating: 

*CUPS_BackEnd: get-printers failed: client-error-not-found*

Looking back at my terminal window, I found many lines of warnings like:

[I]Warning: kbuildsycoca is unable to register with DCOP.
.
X Error: BadDevice, invalid or uninitialized input device 168
.
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
.
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
.
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
uninstall: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted (core dumped)
setupdb-bin.ATupKH: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted (core dumped)
.
CUPS_BackEnd: get-printers failed: client-error-not-found

Warning: LPP_Init() failed! Waiting 2 seconds...
CUPS_BackEnd: get-printers failed: client-error-not-found

Warning: LPP_Init() failed! Waiting 2 seconds...
CUPS_BackEnd: get-printers failed: client-error-not-found

Warning: LPP_Init() failed! Waiting 2 seconds...
[/I]


Could someone help me or point me to the right direction please?

-Thank you very much for at least reading my cry for help...

---

### Post by arnab.bhaumik on 2007-07-15
hi all,

    after lot of trying to install phaser 3116 on my ubuntu 7.04 i am able to install the printer and get it worked.

    in ubuntu 7.04 go to system => administration => printing. then right click on the new printer icon and then add printer.....................


   well i will not go in the details of the installation process. the main trick is that the driver needed for the printer is Samsung- ML-1520. its working perfectly via usb.


   this is very important for the people of india because now it is the low priced laser printer in the country.......................


arnab/vu2bpw

---

