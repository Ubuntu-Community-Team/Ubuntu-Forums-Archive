---
title: "where is the best place to put script"
date: 2008-09-14
forum: General Help
---

### Post by amin_inb on 2008-09-14
Hi

I want to put some script in a place so system run them just AFTER user log-in to his/her account

P.S: If I add them to /etc/profile it just do my purpose
is it the correct place ?

what if I want to have some script files (not just add some code to existing file ?)

P.S2: please don't suggest visual ways, I am on CLI

---

### Post by bingoUV on 2008-09-14
Is it for a particular user, or all users of the system? For a particular user, ~/.bashrc is best.

For all users, there are more choices. /etc/profile as well as /etc/bash.bashrc get run for each user the last time I checked. Just try these files and see whether it works for your usage. I remember some startup scripts do not run when logging through ssh, rather than logging in locally.

---

### Post by caljohnsmith on 2008-09-14
You could put the scripts in the ~/.config/autostart directory.

---

