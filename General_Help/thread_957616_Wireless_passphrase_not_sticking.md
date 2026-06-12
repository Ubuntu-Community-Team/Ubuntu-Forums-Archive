---
title: "Wireless passphrase not sticking"
date: 2008-10-24
forum: General Help
---

### Post by rmcellig on 2008-10-24
Every time I restart my computer, the Wireless Network Key required window comes up prompting me to enter my Passphrase. How can I stop this from happening so that when I start up my computer, Ubuntu 8.04 will know that a passphrase has already been entered.

---

### Post by louieb on 2008-10-24
Its a bug in network-manager. I had to check the roaming mode box to get mine to remember the pass phrase. Others have switched to WICD. 
Just search the wireless and networing section for other fixes.
Heres where I found my fix [**System will not remember WPA2 settings**]("http://ubuntuforums.org/showthread.php?t=787098")

---

### Post by bodhi.zazen on 2008-10-24
I had similar problems and I struggled with network manager for over two weeks.

Switching to wicd fixed my issues and it is easy to install.

I would DL the network manager .deb first in case wicd does not work. (wicd will replace network manager).

---

### Post by rmcellig on 2008-10-24
What is WCID and where do I get it?

---

### Post by bodhi.zazen on 2008-10-24
Sorry, LOL

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

