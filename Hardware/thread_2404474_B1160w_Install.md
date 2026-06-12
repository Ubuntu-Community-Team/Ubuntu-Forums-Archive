---
title: "B1160w Install"
date: 2018-10-24
forum: Hardware
---

### Post by rick0612 on 2018-10-24
Hello all


The Dell unified driver install for my B1160w printer worked perfectly in a vmware client (KDE Neon based on 16.04). The gui opened and I could install the printer no problem. I setup a new client on the same system with KDE Neon based on 18.04 but the gui doesn't open and I get the following error in /var/log/syslog:


kernel: [41568.054839] traps: guiinstall[12095] trap divide error ip:7ff8f3840b39 sp:7fffd6479598 error:0 in libQtGui.so.4[7ff8f33bb000+918000]


Any ideas on how to fix this?


Thanks

---

### Post by mik13ST on 2018-11-09
I have a very similar problem, but caused by entirely different software. I was trying to run SP Flash Tool ([https://spflashtool.com/download/](https://spflashtool.com/download/)) and a GUI was supposed to appear, but instead got "Floating point exception". I am also using KDE Neon based on 18.04. It worked fine on Ubuntu 18.10.
"dmesg" shows a very similar message:

[ 9079.835908] traps: flash_tool[19983] trap divide error ip:7fd94863a568 sp:7ffffe0ec1d0 error:0 in libQtGui.so.4[7fd94811d000+b39000]

It must be something Neon related.

---

