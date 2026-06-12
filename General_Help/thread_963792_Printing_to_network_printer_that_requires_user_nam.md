---
title: "Printing to network printer that requires user name and password"
date: 2008-10-30
forum: General Help
---

### Post by vanadium on 2008-10-30
We have a new photo copy machine / network printer (Ricoh Kyocera KM-350). It is configured to print when supplying a username and pasword created on the machine.

Installing the manufacturer supplied PPD file is a breeze. However, nowhere in the user interface of CUPS (System - Administration - Printing) is there an option to provide user name and pasword for the printer. When attempting to print a test page from within the Printer configuration dialog, a dialog appears "Submitted Test page submitted as job 286" but nothing happens. An administrator of the network printer can see that the job was send but not accepted.

Is printing to a password protected network printer not supported in Linux?

---

### Post by vanadium on 2008-10-31
Does linux support having paswords on a network printer? If not, how is access control normally done using linux systems?

---

### Post by vanadium on 2008-10-31
Do I need to install MS Windows for this?

---

### Post by xueg0i on 2008-11-03
Open /etc/cups/printers.conf as root and change the URL of your printer to something like this: ```
http://username:password@domain.net/folder/.printer
```
Only add username: password, don't change the rest. Then restart cups:```
sudo /etc/init.d/cups restart
```
Hope it helps!

---

