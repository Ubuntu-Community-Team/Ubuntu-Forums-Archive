---
title: "Printer Recognized but Not Working (HP Deskjet 1050)"
date: 2011-01-18
forum: Hardware
---

### Post by ebasa on 2011-01-18
Ao did you install the drivers or just download the file?

---

### Post by onam1 on 2011-01-18
> **ebasa said:**
> Ao did you install the drivers or just download the file?

Whats the command to install it? I have the hplip toolbox but I may not have installed the drivers. I click the "hplip-3.10.9.run" and receive the message "Cannot open desktop bitmap file" but I think it is trying to open with wine.

---

### Post by onam1 on 2011-01-18
sudo apt-get install hplip
[sudo] password for oem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
The following packages were automatically installed and are no longer required:
  krita-data kdelibs4c2a kdelibs-data liblualib50 koffice-data ruby1.8 ruby
  libavahi-qt3-1 liblua50 libruby1.8 koffice-libs
Use 'apt-get autoremove' to remove them.




So I already installed it, I guess.

---

### Post by onam1 on 2011-01-18
Alright, so I opened the .run file and get this...

"7 missing REQUIRED dependencies.
missing: gcc (gcc - GNU Project C and C++ Compiler)
This installer cannot install 'gcc' for your distro/OS and/or version."





If I just upgrade my OS, (running Mint 8, its the same as Ubuntu and you guys seem to get things done quick, so just answer this as if I was on Ubuntu) will I be able to get these or what do I need to do?

---

