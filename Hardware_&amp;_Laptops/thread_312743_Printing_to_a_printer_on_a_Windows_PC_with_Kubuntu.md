---
title: "Printing to a printer on a Windows PC with Kubuntu and Samba"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by NeoChaosX on 2006-12-04
Okay, recently got a new printer on short notice because my old Epson broke down. The specific model was an HP Deskjet D4160. Now, since the printer is shared among my family, it's connected to the main PC, a decidated Windows XP Pro machine. My laptop uses Kubuntu Edgy, and is connected with the main PC on a wireless network.

Now here is my problem; I can connect to and browser the Windows machine, and I can see the printer as shared on the network, but it will *not* print. I'll run through the KDE printer wizard and add the printer, select the Deskjet D4100 driver, but when I print a test page, the printer does nothing. Checking the Windows machine, it shows that the printer receives a document from the Windows machine, but only 64kb of the document is received by the printer before it stalls. I don't have any firewalls running on the Kubuntu machine, and this happens even without a firewall running on the Windows machine. This never happened with my old Epson Stylus C86; it printed with no problems.

So now, what am I supposed to do? Does anyone know how to print to this printer over Samba?

---

### Post by NeoChaosX on 2006-12-07
So nobody can help me here?

---

### Post by joelito on 2006-12-07
What I did was installing Ubuntu on my file/print server and used the gnome-cups-manager to configure it and enable the Lan printer.

After that I installed Samba and modified the settings to allow any user to connect to it.

On the Windows Clients I used the Adobe Postscript Drivers to install the network printer.

Yeah I know that you'll probably have to figure out many of the details but in general terms that should work

And just in case the printer is a Deskjet 3740 with an old eMachines PC as server.

---

### Post by NeoChaosX on 2006-12-08
Well, I can't install Ubuntu to the computer the printer's connected to (as it's a Windows desktop, not a server). Since it's sending the file to the Windows machine, I assume it's soemthing wrong with the Linux printer driver. I'm using the HP Deskjet D4100 driver - is this the right driver, or should I wait for one for my specific printer model?

---

### Post by NeoChaosX on 2006-12-11
Nevermind, it turns out it's a configuration problem on the Windows end. I had to disable bi-directional printing on the D4160, and now print jobs are being processed properly.

---

### Post by sanedog on 2008-03-20
Is bidirectional printing a windows thing or a linux thing?  Thanks

---

