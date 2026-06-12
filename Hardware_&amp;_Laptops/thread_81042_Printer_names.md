---
title: "Printer names"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by steve_mcgarrett on 2005-10-23
how can I change the name of a Printer in Ubuntu?

---

### Post by hajk on 2005-10-23
I guess you don't want to delete and reinstall with a different name in the System/Administration/Printing menu... but if all else fails...

---

### Post by steve_mcgarrett on 2005-10-23
I can do that but I cannot set a name there too.

---

### Post by Joe_lurker on 2005-10-24
You can manually edit the file '/etc/sups/printers.conf'.  The lines '<DefaultPrinter ???>' or '<Printer ???>' define the names of the printers.  Change them to what ever you want but you shouldn't use names with spaces in them.  After you have made the changes and saved the file run the command 'sudo /etc/init.d/cupsys restart'.

-Joe

---

### Post by steve_mcgarrett on 2005-10-24
This seems to be a bad hack as I can no longer change media size and such after I do this.

---

### Post by Joe_lurker on 2005-10-24
Sorry, I forgot one step - remember think twice type once!

After modifying the file '/etc/cups/printers.conf' change the file '/etc/cups/ppd/<old-printer-name>.ppd' to '/etc/cups/ppd/<new-printer-name>.ppd'.

That should do it.

-Joe

---

### Post by Orlandus on 2005-12-05
A more foolproof workaround is to install KDE, and then use the KDE printing manager to change the printer name.

---

