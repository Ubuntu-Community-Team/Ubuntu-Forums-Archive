---
title: "[SOLVED] utorrent problem in wine"
date: 2008-08-19
forum: General Help
---

### Post by uroskriznar on 2008-08-19
When I double click on a torrent file that I saved on my desktop, utorrent runs automaticaly but sais:

Unable to load '/home/uros6/Desktop/blabla.torrent'
Path not found!

Then I have to press the button "add torrent" in utorrent and chose the location of the torrent manualy. This is quite an inconvenience.

Does anyone have a solution???

---

### Post by mb_webguy on 2008-08-19
My first suggestion would be to use Deluge instead of uTorrent under Wine, since Deluge is very similar to uTorrent but native to Linux.

However, if your intent on using uTorrent...  Check your Wine configuration, and make sure you have a drive (usually Z) mapped to the Linux filesystem.  If not, then Wine programs don't have any access to your home directory (which is what seems to be happening).

---

### Post by uroskriznar on 2008-08-19
I installed Deluge and it seems to work very well. Thanks.

But I still wasn't able to solve the problem with utorrent.
Applications -> Wine -> Cofigure Wine
I clicked on Drives, and there are many letters of drives including Z.
Could you give me more detailed instructions?

---

