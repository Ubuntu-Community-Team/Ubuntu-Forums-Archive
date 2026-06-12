---
title: "vmware installation problem"
date: 2008-09-11
forum: General Help
---

### Post by Brady152 on 2008-09-11
hi, 

Ive been working on installing vmware on my pc, Ive tried a few different tutorials and I found one that works, but I am getting hung up on a step.

this is the tutorial:
[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

Im on the step where Im supposed to enter the following into the terminal:

tar xvfz VMware-server-*.tar.gz
cd vmware-server-distrib
sudo ./vmware-install.pl

It was working, then I entered sudo ./vmware-install.pl

and I got this:

:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to find the binary installation directory (answer BINDIR)
       in the installer database file "/etc/vmware/locations".

Failure


Execution aborted.



Im pretty sure this is because I skrewed up on a previous attempt.
What do I do now?

thanks

---

### Post by fsmithred on 2008-09-12
You could try running /usr/bin/vmware-uninstall.pl, or you could delete or rename /etc/vmware, then install again.

---

