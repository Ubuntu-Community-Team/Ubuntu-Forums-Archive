---
title: "Unison SSH-sync and file permissions"
date: 2008-08-15
forum: General Help
---

### Post by T0mmy on 2008-08-15
I have set up my desktop computer as SSH-client and my laptop as SSH-server.
I sync with Unison.

If a file doesn't exist on the laptop, it is added during sync.
The problem is that the file gets a "Lock"-emblem.
When checking the file permissions, it says that the owner is "1000", which isn't my username.

The other way around, the permissions seems correct.

Both computers are running Ubuntu 8.04.1, and I use the same username and password on both computers.

Any ideas why the created files on the laptop are owned by "1000"?
Any ideas how to fix it?

---

### Post by toni_uk on 2008-08-18
Hi Tommy,
the problem is that the owner of the files on the one computer does not exist on the other. There are two simple solutions to this:

a) using your filemanager (Nautilus if you use Ubuntu) as root. To do that you type 

sudo Nautilus 

into the Terminal - that will open Nautilus in root. Go to the folder containing the locked files and right click on the folder:

Permissions - now you can change the owners, the groups and the access rights of the folder to you liking. Make sure you add to apply to all subfolders. 

b) using sudo chown in the Terminal.

go to the folder containing the folder with the files.

Type: sudo chown -R [your user name] [folder name]

that will change the folders owner and all files contained to you.

Hope this helps

---

