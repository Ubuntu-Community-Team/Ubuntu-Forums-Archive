---
title: "Access privileges lost after adding users."
date: 2008-06-17
forum: Hardware
---

### Post by X-Seti on 2008-06-17
I seem to be having some issues, firstly not being able to access the ntfs partition because I no longer have the right privileges.

How this happen.. 

From my login name 'K', I went into the Administration menu selecting User and Groups, from this panel I added 3 new users.


Thinking all was fine I closed the window, and had to reboot after an update.

The sudo command will no longer work apart from being in root, and nor can I in User and Groups click on unlock?, 


I get the 'Could not authenticate' an unexpected error has occurred, error message. 

how can I fix this? 


If I log off this session and log back in, Why will it not let me log in as root, if I could, all this could be fixed..


Is there a way to fix the user group using the shell?

---

### Post by phidia on 2008-06-17
I believe in Ubuntu by default only the 1st an orginal user has admin privledge.

To create a root user which differs from using sudo read the [thread here]("http://ubuntuforums.org/showthread.php?t=831502&highlight=root+account") including the warnings.

---

