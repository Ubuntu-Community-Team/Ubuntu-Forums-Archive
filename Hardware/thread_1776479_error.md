---
title: "error"
date: 2011-06-06
forum: Hardware
---

### Post by anoopcumar on 2011-06-06
sudo apt-get update

if I give the command the following error is coming

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)

---

### Post by Yellow Pasque on 2011-06-06
You have another package manager running somewhere, and if you don't, you have a stale lock file. Close any other program that does package management (Synaptic, Software Center Update Manager) and see if you get the same message.

---

### Post by hatalar205 on 2011-06-08
@Temüjin + if you still get the same message, simply reboot.

---

