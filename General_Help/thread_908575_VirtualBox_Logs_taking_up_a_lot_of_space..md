---
title: "VirtualBox Logs taking up a lot of space."
date: 2008-09-02
forum: General Help
---

### Post by Newuser1111 on 2008-09-02
How can I stop having VirtualBox creating those files?

3 of those files took up 3GB. And just opening a VirtualBox Machine causes a 9MB one.

---

### Post by Zalbor on 2008-09-02
Which version of VB do you have? I have the onw I downloaded from the website (non-open source edition) and the following advice is for it, although it's probably the sabe for the OSE.

This is a known bug with the current version. The way to fix it is to set the VBOX_LOG_DEST environment variable to "nofile". To do that, open the ~/.profile file (a file called ".profile" in your home folder; you'll need to show hidden files to open it) and add this line at the end:
```
export VBOX_LOG_DEST=nofile
```
Then log out and back in.

---

### Post by Newuser1111 on 2008-09-02
There isn't a .profile folder.

And it's Version 1.6.4, Not OSE.

EDIT:
Sorry, I thought you said Folder. Yes, there was a FILE with that name.

EDIT:
Thanks! That worked.

---

