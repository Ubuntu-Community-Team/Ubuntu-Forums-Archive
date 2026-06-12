---
title: "HP Printer Driver upgrade question"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by klhoard on 2007-11-01
I upgraded my hplip to the latests version 2.7.10 using the automated script installer from HP.  However, when I check the version of hplip from the terminal using:

dpkg -l hplip

I get:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  hplip          2.7.7.dfsg.1-0 HP Linux Printing and Imaging System (HPLIP)

I have used Synaptic to uninstall the version 2.7.7 driver with the "Completely Remove" option and have rebooted the system twice.  The HP Device Manager shows that version 2.7.10 is installed (Help, About).

Which one is right, the command line or the gui Device Manager?  I've been having problems printing in Ubu and am hoping that getting an updated driver may help.  Thanks!!

---

### Post by GlennW on 2007-11-08
I have exactly the same output. 

Now what?

---

