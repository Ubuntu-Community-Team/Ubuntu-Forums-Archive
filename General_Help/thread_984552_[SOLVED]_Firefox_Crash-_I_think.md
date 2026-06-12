---
title: "[SOLVED] Firefox Crash- I think?"
date: 2008-11-16
forum: General Help
---

### Post by ddixonr on 2008-11-16
I'm having difficulty remembering exactly when it happened, so I don't know what may have been the initial cause. Here's what Firefox is doing:

1. Starting a new session does not direct to the homepage; it opens a blank page with nothing in the address bar. Clicking on home directs to the default firefox google homepage no matter how many times I try to change it in preferences.

2. The address bar will not automatically change websites typed in after hitting enter. Ex: typing "google.com" and hitting enter does not change to "http://www.google.com"

3. No forward or back buttons. They are grayed out, and just in case, keyboard shortcuts don't work either.

4. I have uninstalled firefox completely using synaptic, but I thought my bookmarks would be safe somehow. I, apparently, was very wrong on that assumption.

Please, I have no desire to learn konqueror, or any other browser. Please help.

**update:** here is the output when launching firefox from the terminal:

(firefox:11416): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

**update:**

I just tried launching firefox as root (sudo) and unbelievably, it works! Bookmarks are all there too. Why is this?

---

### Post by cyracks on 2008-11-16
I assume something is wrong with your firefox profile. Try to delete/move your profile and start the firefox again.
Don't know the exact location of firefox profile, but it should be something like /home/yourusername/.firefox/profiles

---

### Post by PocketDog on 2008-11-16
Try running it from the terminal with this  ```
firefox -p
``` This will force it to open the profile manager when it starts: you can select the one which works from there

---

### Post by ddixonr on 2008-11-16
Problem solved after logging into nautilus as root (gksudo nautilus) and changing the owner from root. Don't know how it got that way. I backed up the "default" profile folder first, then make the changes. All is good. Extra thanks for making me think harder. I love how linux gives "real" error messages in the terminal to help solve these issues. Winblows error messages are only useful to those who wrote them.

---

