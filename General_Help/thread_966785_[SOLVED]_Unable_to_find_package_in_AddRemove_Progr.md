---
title: "[SOLVED] Unable to find package in Add/Remove Programs"
date: 2008-11-01
forum: General Help
---

### Post by parameter on 2008-11-01
Hi everyone. I'm having a problem finding a package with Ubuntu 8.10. I'm running my install in a VMware Server VM and I want to add the open-vm-tools package. [I see that the package is available in the multiverse repository]("http://packages.ubuntu.com/intrepid/open-vm-tools"). I have gone to the Software Sources panel and ensured that the multiverse repository is enabled. I ran the Update Manager and had it check and update my list of packages from the server.

Unfortunately, when I run the Add/Remove program from the application menu, set it to show all programs, and then search for "vm" or "open" I do not see the open-vm-tools package listed. I'm an old-school UNIX guy and I know I could do a apt-get install from the shell, but I want to do this "the Ubuntu way" like an average end user.

Why is this package not showing up in the list?

---

### Post by sdennie on 2008-11-01
The Add/Remove Programs applications only shows a subset of available packages.  To get a more comprehensive list, go to System->Administration->Synaptic Package Manager.

---

### Post by parameter on 2008-11-01
Thanks. That worked and I was able to install the package.

Is there any documentation regarding why not all packages show up in Add/Remove Programs? Is there a certain criteria that must be met for a package to appear there?

---

### Post by sdennie on 2008-11-01
I'm not sure what bumps a package to Add/Remove but, with the many thousands of packages in the repos, it makes sense to show a limited number in Add/Remove as it's meant to be a simple way to install "point and click" types of packages.  Cluttering it with the many thousands of packages that are available would considerably diminish its ease of use.

---

