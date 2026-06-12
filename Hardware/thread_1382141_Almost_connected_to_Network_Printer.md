---
title: "Almost connected to Network Printer"
date: 2010-01-15
forum: Hardware
---

### Post by Nordite on 2010-01-15
I am fairly new to Ubuntu and have just installed the latest release of Jaunty on my HP laptop. I am having trouble connecting to my HP5700 USB printer connected to a Windows Vista laptop. I followed the help document and found how to connect using the Printer installer and selecting (Windows Samba) it sees my [Workgroup]/[Vista laptop]/ [but cannot find USB HP5700 Printer port]. For the port I am inputting "USB001" which is what my Vista laptop shows in printer properties. Can anyone help me get the rest of the way there?
Nordite

---

### Post by Morbius1 on 2010-01-15
Ubuntu shouldn't be looking for any port on the machine that has the printer.

When you get to the "Windows Printer via Samba" part and you see the workgroup / machine name it should also show the "Printer Name" not the printer port. If it doesn't see the "Printer Name" then my guess is that you didn't enable "Sharing" of the printer on the Vista machine.

I don't have a Vista machine handy so I found you a Howto about sharing the printer on Vista: [http://www.home-network-help.com/vista-printer-sharing.html](http://www.home-network-help.com/vista-printer-sharing.html)

Once you have sharing enabled on the Vista machine go back to ubuntu and see if it can find the Printer Name.

[COLOR=Blue]EDIT: I just looked at the Printer Utility in Ubuntu and realized where the initial confusion about ports comes from.[/COLOR] Under the SMB Printer it has the following example:>  smb://[workgroup/]server[port]/printerThe port it's refering to is a networking port not a hardware port. It only has meaning for a linux attached printer .

What it's looking for is something in the form of :

smb://WORKGROUP/SERVER/PRINTER_NAME  or
smb://SERVER/PRINTER_NAME

But again that Printer Name can only be referenced if the printer has "shared" enabled on the Vista box.

---

