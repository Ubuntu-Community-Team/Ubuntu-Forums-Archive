---
title: "CUPS: Can print test page in web interface but nothing else"
date: 2008-08-12
forum: General Help
---

### Post by rawlins02 on 2008-08-12
I'm having trouble getting printing set up. Running Gutsy. Began process using the CUPS web interface on localhost:631/ to define two printers which are on network here at work.   I can print a test page to each printer from the interface but can't seem to figure out how to print from applications. Nothing but 'Postscript/default' shows in most application printer dialog boxes. How do I get each printer set up in CUPS to show in the applications?  Also, in the System -> Administration -> Printing -> printer configuration tool everything is gray and inaccessible. I believe I set server for that in /etc/cupd/client.conf and suspect I've got the wrong setting. It is my understanding that using that tool is optional (?)

---

### Post by rawlins02 on 2008-08-12
Update: Got System -> Administration -> Printing menu GUI to respond. Was as simple as correcting line in /etc/cupsd/client.conf with localhost, like so:

# Servername
ServerName localhost


I can now see the printers I installed with CUPS interface at left in the GUI and have printed a test page as well. Printers now show up in applications and all works fine.

---

