---
title: "command 'ls' not displaying colour"
date: 2008-09-08
forum: General Help
---

### Post by Dthdealer on 2008-09-08
The 'ls' command normally displays coloured file names for me. Yesterday it stopped.
I tried the 'ls' and 'dir' commands with the colour parameter to no avail, resulting with monotonous text on my screen.
This problem does not exist while a super-user, causing me to believe that it is account-related.
For once Linux has acted like windows. Mysteriously changing settings.

---

### Post by quibbler on 2008-09-08
> **Dthdealer said:**
> The 'ls' command normally displays coloured file names for me. Yesterday it stopped.
I tried the 'ls' and 'dir' commands with the colour parameter to no avail, resulting with monotonous text on my screen.
This problem does not exist while a super-user, causing me to believe that it is account-related.
For once Linux has acted like windows. Mysteriously changing settings.
Look for a hidden file in your home directory called ".bashrc".
If there isn't one, look for ".bashrc~" and rename it to .bashrc.
If neither of these files are there, then copy as root /root/.bashrc
to /home/(your_home)/.bashrc.
Why your .bashrc went south, I have no idea.

Regards quibbler

---

### Post by Dthdealer on 2008-09-08
It was my fault - I had recently overwritten my .bashrc file. I'll copy one over from another userfile.

---

### Post by cszikszoy on 2008-09-08
Don't forget to mark your thread as solved.

Thread Tools > Mark as Solved

---

