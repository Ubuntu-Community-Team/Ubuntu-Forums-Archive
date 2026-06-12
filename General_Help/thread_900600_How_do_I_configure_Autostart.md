---
title: "How do I configure Autostart"
date: 2008-08-25
forum: General Help
---

### Post by gusst250 on 2008-08-25
I just got myself a firewall and I want it to start everytime I start my computer. I have tried to add the firestarter.desktop to Sessions -> Startup programs but nothing happens when i reboot.

Where is the file that specifies the autostarting programs and how do I edit it properly?

//Gustav

---

### Post by coffeecat on 2008-08-25
> **gusst250 said:**
> I just got myself a firewall

No - you already have a firewall. You've just installed a GUI configuration utility for iptables rules. You only need to start that when you need to change the rules. Have a read of [this thread]("http://ubuntuforums.org/showthread.php?t=899004").

---

### Post by mssever on 2008-08-25
> **gusst250 said:**
> I just got myself a firewall and I want it to start everytime I start my computer. I have tried to add the firestarter.desktop to Sessions -> Startup programs but nothing happens when i reboot.

Where is the file that specifies the autostarting programs and how do I edit it properly?

//Gustav
I assume that firestarter runs as root. So you need to put an appropriate command in /etc/rc.local.

Disclaimer: I don't use firestarter and know very little about it.

---

