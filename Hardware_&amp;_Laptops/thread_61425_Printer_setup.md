---
title: "Printer setup"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by Zaare on 2005-08-31
I want to use a printer connected to a server on my network. The server runs on Windows 2000. When I try to add a new printer I choose *Network Printer* as the printer type and then *Windows Printer (SMB)*. But I don't know how to fill in the following fields: Host, Printer, Username and Password.
I just typed the network name of the server, the name of the printer as seen in the printers window in the server, and the username and password requierd to log on to the server computer. When I try to print a test page it says the job has been sent, but nothing happens. Then when I check the printer properties, it says the following message in the status field:
> Printing: Connection failed with error NT_STATUS_BAD_NETWORK_NAME

And if I type *smb://NAME_OF_SERVER*, the following message is displayed in the status field:
> Printing: Connection failed with error NT_STATUS_UNSUCCESSFUL

Any ideas on what I'm doing wrong?

---

### Post by tonym on 2005-09-01
The hostname can be found by right clicking on My Computer,  selecting Properties and looking at the Computer Name tab.

The printer share name can be found by looking in Settings->Printers.  Right Click on the relevant printer,  select Properties and look at the Sharing tab.

Try no username and password.  If that doesn't work try username guest.

---

### Post by Zaare on 2005-09-01
Thank you for the help, tonym.
Well, I was using the right name for the server, but not the printer.
I tried without username and password, I got:
> Printing: Connection failed with error NT_STATUS_LOGON_FAILURE

Then I tried username guest, and no password, I get the same result:
> Printing: Connection failed with error NT_STATUS_LOGON_FAILURE

---

### Post by Zaare on 2005-09-03
Ok, I finally got it working.
First I tried to give printer access to everyone on the server, but that didn't help. Finally I created a user account with access to the printer. Then, when I used that username+password, everything worked perfectly.

---

