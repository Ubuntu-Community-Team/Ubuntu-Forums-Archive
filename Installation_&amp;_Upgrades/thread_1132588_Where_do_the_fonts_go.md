---
title: "Where do the fonts go?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-22
Where do the fonts go after installation?...or where do I manually place them for the applications to find?

Something tell me it should be in the /usr/lib folder.

---

### Post by balaknair on 2009-04-22
By default, fonts are installed in /usr/share/fonts
This requires superuser(admin) privileges and the fonts are available systemwide(to all users and applications). Fonts installed using the package manager usually get installed here. If you have more than one user account, you might want to place the font files here.

You can also install fonts to /home/user_name/.fonts
This does not require superuser privileges, but the fonts are loaded only for that user's sessions(the .fonts folder may not exist by default, you can create it manually). If you have just one user account for the system, you can install the fonts here.

Note:
*The "." in front of the file/folder name means it is hidden. Pressing ctrl+h when browsing a folder toggles 'view hidden files/folders'*

---

### Post by dE_logics on 2009-04-22
Ok...thanks a lot!

---

