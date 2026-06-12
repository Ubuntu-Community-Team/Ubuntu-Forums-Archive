---
title: "CUPS Web Interface"
date: 2013-03-22
forum: Hardware
---

### Post by roly33 on 2013-03-22
I'm trying to add a my Printer using the CUPS Web Interface and I get a username & password box.  I've tried using my login but that doesn't work, and wondered if there was a pre-set Admin login.  I'm using 13.04 by the way?

Roland

---

### Post by ajgreeny on 2013-03-22
How are you opening the web interface?  A browser using address [http://localhost:631](http://localhost:631) should get there with no problem and only your own password needed when you try to add the printer, assuming you have not added a root password on your system.  If you're using a root account I do not know how to help; sorry.

---

### Post by roly33 on 2013-03-22
> **ajgreeny said:**
> How are you opening the web interface?  A browser using address [http://localhost:631](http://localhost:631) should get there with no problem and only your own password needed when you try to add the printer, assuming you have not added a root password on your system.  If you're using a root account I do not know how to help; sorry.

I'm trying to Add my Printer the way you said, with no Root Password, and everytime I input my username & password the login box just keeps popping up.

I ended up using the Printer option in Settings to add my Printer.

Roland

---

### Post by tgalati4 on 2013-03-22
Try using "root" for user and then your regular password.  It could be a regression in the CUPS authentication.  On 12.10 it works with either "root" or your username and a valid username password.

---

### Post by jafrelin on 2013-04-17
I cannot log in to the CUPS web interface with either root as user name or my user name and my password.

Can I can in onthe command line?

---

