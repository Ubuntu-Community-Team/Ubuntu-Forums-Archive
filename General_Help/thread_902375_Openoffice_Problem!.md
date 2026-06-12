---
title: "Openoffice Problem!"
date: 2008-08-27
forum: General Help
---

### Post by iampriteshdesai on 2008-08-27
I dual boot between Ubuntu and XP.
When I start a document in XP using Office M$ 2007 and save it in .doc format and I try open that document in OOo and make changes it says it cannot and gives an option ti discard the change. I don't know what to do!
I tried Kubuntu and OOo worked in that case. I used Hardy Heron.
I can edit documents created by OOo in Office 2007.

---

### Post by Orlsend on 2008-08-27
If their are Updates for Open office get them, if that does not not work remove and install it again.

If that does not still solve it then post again here

---

### Post by iampriteshdesai on 2008-08-28
Nope didn't work!

---

### Post by Orlsend on 2008-08-28
have you tried abiword?

Btw can Open Office in the terminal and do what you wnat to do and we you get to the error copy what ever is in the terminal and post it here.

---

### Post by Cheesehead on 2008-08-28
Are you trying to save the OO .doc file to:
A) Your Ubuntu partition (/home)?
B) Your Windows Partition (C: drive)?
C) A usb-drive or other common shared storage?

Are you *sure* that's where you're trying to save it to? It's surprising how often people save to completely unexpected places.

If A), then congratulations, you have probably uncovered a bug of some sort. Please report it at Launchpad.net and OpenOffice.org.

If B), Do you *as a user* have permission to write to that drive? Quite possibly you don't, and that's GOOD. You can read from the Windows partition, but you should not write to it. You risk damaging your Windows install.

If C), Do you *as a user* have permission to write to that drive? If not, then simply let us know, and we'll post the instructions to grant yourself user permission.

---

### Post by iampriteshdesai on 2008-08-28
I started the document in XP using Office 2007 next when I log into Ubuntu installed using Wubi, open the document in OOo make edits to it and try to save it I get an error saying I cannot save it and I get an option to discard the changes. I have opened the document in Ubuntu from all above 3 places. External hard drive, Ubuntu partition, etc.
Ooo worked in Kubuntu.

---

### Post by Ms_Angel_D on 2008-08-28
I believe it could be an issue with Open Office as from what I understand the version currently running on Hardy is not compatible with Office 2007, However I believe the Ibex version will be compatible.

---

