---
title: "Wheres the GUI-Gnome??"
date: 2008-08-23
forum: General Help
---

### Post by gwapscoffee on 2008-08-23
Hi All,

I've installed Ubuntu 8.04 Server in my VMware 6 Workstation.After finalizing the installation, a prompt appear stating that I should reboot my PC(virtual machine). After rebooting, I'm stuck on a terminal prompting my username and password. I do know my account but after entering my username and password, I don't get to see the graphical user interface. How do I switch to it. Thanks in advance.

---

### Post by dje on 2008-08-23
ubuntu server does not install a gui as it is unnecessary on a server, to install it login then run this:
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

dje

---

### Post by gwapscoffee on 2008-08-24
Thanks for the prompt reply.Cheers!!

---

