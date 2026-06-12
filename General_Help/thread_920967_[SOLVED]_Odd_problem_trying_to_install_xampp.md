---
title: "[SOLVED] Odd problem trying to install xampp"
date: 2008-09-15
forum: General Help
---

### Post by tstack77 on 2008-09-15
I have the latest xampp version in my home folder (tar.gz format). 

Terminal output:

xxxxx@xxxxx ~ $ sudo tar xvfz xampp-linux-1.6.7.tar.gz -C /opt
tar: xampp-linux-1.6.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Do I have an error in syntax somewhere?

EDIT: Figured it out, had to make an /opt folder first.

sudo mkdir /opt

---

### Post by tstack77 on 2008-09-15
solution above

---

