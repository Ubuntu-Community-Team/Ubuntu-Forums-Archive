---
title: "CUPS issues with remote printing"
date: 2018-03-16
forum: Hardware
---

### Post by serapis5 on 2018-03-16
I have a Brother 5140 on UBUNTU 17.10.  It works fine whenever I print from the computer it is attached to but I am having two issues with CUPS remote printing that didn't exist under 15.04.

1:  I have an Android phone that I print documents from using Android CUPS printing app.  Under 17.10, if I reboot the machine, I have to manually go into *Printers/Advanced Printer Settings/Server/Connect* and then I can print from my phone.  Is there a way I can get Ubuntu to activate this on startup?

2:  My son runs LUbuntu 17.10 and his computer used to be able to print remotely to mine, but now, while his computer sees and installs the remote printer through the CUPS web interface, all of his print jobs come back with some type of error code or another, usually *Filter Failed* and I have to purge the print job from my server.

Any Suggestions?

---

### Post by pdc on 2018-03-16
perhaps you file it as a bug report with Ubuntu; 

and hope that 18.04, the LTS version due out in a month; is better; 

17.10 was quite a big leap ....... into Gnome etc ......... and various printer and scanner issues emerged; all reported on the forum; and hopefully bug reported

__________ 

each short-term release of Ubuntu allows innovation and exploration it would seem ...... and bugs are seen and fixed; .........  so some install these "experimental" releases; as some would be so bold as to call them; and those installing explore and report; and discover; and assist the developers; 

....... in contrast, the LTS seem to focus on stability ...... so distros such as Mint ........... based on Ubuntu ........ only now offer LTS releases ........... they ignored 16.10 and 17.04 and 17.10 and instead just issue 16.04.1 and .2 etc  ........ the new Mint will be based on 18.04

---

### Post by serapis5 on 2018-03-16
Thank you pdc.  I will file it as a bug report.  I solved the Android CUPS printing problem (somewhat) by adding the command /run/cups/cups.sock through the Startup Applications app.  Phone will now print one job to the printer, but I have to reboot the phone if I need to print multiple docs.  Anyway, I appreciate the input.

Bart

---

