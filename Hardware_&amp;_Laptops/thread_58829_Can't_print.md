---
title: "Can't print"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by robins_web on 2005-08-21
Here's the deal: I have a Canon S300 printer which is connected via USB. In KDE, I installed it using the Printing Manager. On the screen taht shows the USB port options, I grabbed the first empty one (/dev/usb/lp0). WHen I try to print, nothing happens.

My job shows up in KJobViewer. What am I doing wrong? And is there an easier way to install a printer, other than by trial and error?

---

### Post by Totzo on 2005-08-21
not sure but this might help:

check that you are a member of the "lp" group and  try putting "lp" and "usbcore"  in your /etc/modules file then reboot with your printer switched on. If that doesn't work throw it out the window and grab a paper n pen! :-)

---

### Post by markthecarp on 2005-08-22
Moanin'  Have you checked the linuxprinting.org site? They list this printer as partially supported. There are some user comments you may find helpjul at...

[http://linuxprinting.org/show_printer.cgi?recnum=Canon-S300](http://linuxprinting.org/show_printer.cgi?recnum=Canon-S300)

-mark

---

### Post by robins_web on 2005-08-22
[QUOTE=markthecarp]Moanin'  Have you checked the linuxprinting.org site? They list this printer as partially supported. There are some user comments you may find helpjul at...

[http://linuxprinting.org/show_printer.cgi?recnum=Canon-S300](http://linuxprinting.org/show_printer.cgi?recnum=Canon-S300)

-mark[/QUOTE]
 Thanks for both suggestions. The first one didn't work, so I'm off to linuxprinting.org (the first thing I'll do there is bookmark the site!)

R

---

### Post by robins_web on 2005-08-26
[QUOTE=robins_web]Thanks for both suggestions. The first one didn't work, so I'm off to linuxprinting.org (the first thing I'll do there is bookmark the site!)

R[/QUOTE]
 Still can't print, but I'm getting closer. The printer printed part of a test page, then quit with this ermsg:

A print error occurred. Error message received from system:

cupsdoprint -P 'tmpprinter_Q3xamX8p' -J 'KDE Print Test' -H 'localhost:631' -U 'robin' -o ' multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3' '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:

client-error-not-possible

---

### Post by s_p_a_r_k_y on 2005-08-26
canon = bad with linux, hp = good with linux. any chance you can trade a buddy?

---

### Post by robins_web on 2005-09-05
[QUOTE=s_p_a_r_k_y]canon = bad with linux, hp = good with linux. any chance you can trade a buddy?[/QUOTE]
 << canon = bad with linux, hp = good with linux. >>

You're right about that. I just broke down and bought an HP PSC 1310 All-In-One at Sam's Club for less than $65. Brought it home & 10 minutes later was printing like a champ.

---

### Post by s_p_a_r_k_y on 2005-09-05
sorry it came down to that but sometimes the hours * hourly rate you spend troubleshooting & debugging is greater than buying a printer for 65. Glad its working though : ) I have the same model from HP

---

