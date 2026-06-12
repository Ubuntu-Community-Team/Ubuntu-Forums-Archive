---
title: "grey install/uninstall windows in wine"
date: 2008-11-29
forum: General Help
---

### Post by Chris_Doc on 2008-11-29
At first, Wine was working fine for me but recently when I try to install/unintsall all I have is a small grey window. For example, I could install Football Manager 09 fine with it earlier, but now when I click setup it loads up the install shield wizard as normal as if everything is fine and instead of the window that should come up asking to agree to terms etc. its just a grey window.

any help on how to fix is appreciated!

---

### Post by Chris_Doc on 2008-11-30
I can give other details if it will help?

---

### Post by 3rdalbum on 2008-11-30
Possible cause: the programs you have installed have overwritten some WINE libraries with their own Windows ones. Rename the .wine folder inside your home directory, and try running the installer again. If you still get the problem, then my hypothesis is not correct. If it solves the problem, then you might need to erase your .wine directory and reinstall your Windows programs, or just switch between the first and second .wine folders.

---

### Post by Chris_Doc on 2008-11-30
Thanks alot. I'm new to Ubuntu however, and I'm unsure exactly how to rename the .wine folder. If I type in the .wine directory the folder opens, however when I go to my home directory the wine folder does not appear for me to rename.

edit: I found out what to do and it worked! Thanks again.

---

