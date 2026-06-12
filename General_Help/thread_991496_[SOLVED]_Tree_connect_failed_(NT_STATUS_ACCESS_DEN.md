---
title: "[SOLVED] Tree connect failed (NT_STATUS_ACCESS_DENIED)"
date: 2008-11-23
forum: General Help
---

### Post by iitywygms on 2008-11-23
I upgraded my laptop and main computer to Intrepid.  Now when I try to print from my laptop, I get the error message in printer properties.  Tree connect failed (NT_STATUS_ACCESS_DENIED) 
I can print from the main computer fine. I have the printer hooked up to the main computer obviously.
The printer shows up on my laptop just fine.  All other samba stuff works fine.

I had no problems on gutsy or feisty or hardy, but now I can't get the laptop to print.
The printer is a hp-deskjet3740.
Any suggestions?  I think it is a permission issue but I am not sure.

---

### Post by iitywygms on 2008-11-23
Fixed by deleting the printer and reinstalling. WHY? :roll:

---

### Post by migolopolus on 2009-10-29
It's not just reinstall if when creating printer sharing you put the key, this key you have to put it, not marking key checking, but enter user name and password. It worked for me.

---

