---
title: "Transferring files with Xvnc4viewer"
date: 2008-10-09
forum: General Help
---

### Post by PoopyTheJ on 2008-10-09
Trying to use xvnc4viewer to remote admin a Windows XP box. With TightVNc on windows there's a handy icon to click to transfer files, how does one go about transferring files using xvnc4viewer in gnome? I don;t have a menu bar or anything like that, I'm sure I'm missing something I googled xvnc4viewer file transfer and man but the man pages are all other languages and nothing shows up for file transfer...

---

### Post by Mister.Vash on 2008-10-10
When you have xvnc4viewer running, press the F8 key - this will bring up the menu.  I didn't see an option to transfer in my menu, but I'm not connecting to a windows machine, so I don't if that is relevant or not.

If your menu doesn't show it, you could try:
sudo apt-get install xtightvncviewer
which install xtightvncviewer, which may do the trick.  The menu access is the same, the F8 key.

---

### Post by PoopyTheJ on 2008-10-11
Will give it a shot, in the meantime I'm using an FTP server to send over files, slow but it works.

---

