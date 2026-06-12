---
title: "Which Of These Services Can I Safely Turn Off?"
date: 2008-10-03
forum: General Help
---

### Post by taurusx5 on 2008-10-03
Hi, guys! Here's a list of services I want to disable. I use my computer for wireless and dialup, faxing, printing, word processing, mp3, radio listening over the net, DVDs through VLC, Virtualbox, and pop/smtp mail. Which ones can I safely disable, considering what I use my computer for, and can you tell me why for each? This is important for me to bootup ubuntu faster... Thanks!

[B]- apparmor
- dhcdbd
- hal
- killprocs
- libpam-foreground
- makedev
- module-init-tools
- mountoverflowtmp
- policykit
- powernowd
- powernord.early
- procps
- rc.local
- sendsigs
- single
- sysklogd
- udev
- udev-finish
- ufw
- umountfs
- umountroot
- urandom
- wpa--ifupdown
- x11-common
[/B]
.

---

### Post by Joeb454 on 2008-10-03
Moved to General Help

---

### Post by oldos2er on 2008-10-03
You seem to be missing a whole bunch of services. Have you seen this: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) ? Most of the info there is still relevant.

---

### Post by hyper_ch on 2008-10-03
research what each of those is doing and then decide whether you need any of them.

---

### Post by lukjad on 2008-10-03
It's hard to say. It's more of a personal choice than a simple list. I have a 10 year old PC. I can safely turn off my bluetooth services. The rest I don't touch. If I were you, I would carefully research each and every one of those things on your list and then make a list of those you don't want. Print the list and then disable them one by one. After you disable one, power down your system and then boot it up again. Test that everything works well and proceed to the next. That way you will know what the problem is if something stops working. 

DO NOT just shut a bunch of them dowm at once. That can create a great deal of confusion if something goes wrong.

---

