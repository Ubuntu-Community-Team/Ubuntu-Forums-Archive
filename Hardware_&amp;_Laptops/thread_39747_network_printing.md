---
title: "network printing"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by minimidgy on 2005-06-06
How can I set up a network so that I can print to another computer? I have ubuntu, and I want to send it to my brother's computer, which has windows XP, and a Lexmark X73 all-in-one printer. How do I set this up?

---

### Post by bleakcabal on 2005-06-06
I have a similar situation. I installed Samba with Synaptic. Went in the System->Administration->Printing. Try adding a new printer but then it asks me info I can't awnser so im stuck there.

---

### Post by brickbat on 2005-06-06
I managed to get this working but it was a while ago.  I will do my best.

You have to share the printer on the windows machine.

In XP go to Printers and Faxes, Right click on the printer and select sharing.  Turn on sharing and give the printer a reasonable name. Click OK

Then, when you set up the printer in Linux, 

Connection settings should be

Network Printer / Windows Printer (SMB)
Host should be the IP address of the xp machine
The printer should be the name of the printer from the step above.
For username and password I used the windows admin username and password.

You also need to set the printer driver on the other tab in this dialog.

Perhaps this is not technically exactly the way it is supposed to be done but it worked for me.

btw,  Im not 100% sure but I dont think you need to install samba to use an xp printer on another xp machine.  I think samba is a server that lets a windows pc use resources on the linux machine.  I think you only need samba-common and libsmb but I might be wrong.

ciao
bb

---

