---
title: "SeaMonkey closes when terminal closes"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by rhcodey on 2009-04-21
I hope this is an easy one. I installed SeaMonkey 1.15 via the Package Manager, but then read that there were security issues with that version. I uninstalled, downloaded the SeaMonkey 1.16 tarball, and installed. 

Now there is no launcher for the application in any menus and the only way to launch Seamonkey is via the terminal...and every time I close the terminal, Seamonkey closes as well.

I've tried uninstalling SeaMonkey via the command line, but when I went to terminal and typed "SeaMonkey", it still opened.

I downloaded and installed the tar.gz from my home folder, and installed the seamonkey installer bin from my home folder.

In the file system, SeaMonkey is installed in the local folder. I get the feeling that somehow this is an issue that SeaMonkey isn't listed as a shared application.

Anyway, my main goal at this point is to get SeaMonkey off my computer. I don't want to just delete the SeaMonkey folders from my /usr/local and home folder, thinking there has got to be more to it than that to uninstall, since command line failed to uninstall.

Any assistance you could provide and clarification of my issue would be appreciated, and I hope I have been clear and provided enough information.

I am using Ubuntu 8.10.

---

### Post by jsowoc on 2009-04-21
To answer your first concern, if you type "seamonkey" and it launches from somewhere, you can type "which seamonkey" to find out from where.

For your second concern, if you start any program, say emacs, from the command line, and then close that terminal window, your program will also close because its parent got killed. To avoid this behaviour, you can type "seamonkey &", which sends seamonkey to the background, and it now runs independent of the terminal.

For your third concern, you can add custom launchers to whatever program you install. Simply right-click on the applications menu, and choose customize. You can now add/remove/change any shortcuts, including one to /usr/local/bin/seamonkey (or wherever it installed -> check with 'which seamonkey').

I don't know where the 1.16 tarball extracted the files, but many installers have an install manifest that lists off all the files that were installed. The uninstaller should have read this file and removed all the corresponding files.

---

### Post by rhcodey on 2009-04-21
Thank you for your reply. I'll do all and let you know what I find.

---

