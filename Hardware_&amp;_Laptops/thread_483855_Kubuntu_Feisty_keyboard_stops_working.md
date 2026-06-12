---
title: "Kubuntu Feisty: keyboard stops working"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by bean1975 on 2007-06-25
After some time -- hours, 1-2 days -- the keyboard just stops working everything else, including mouse still operates. If I log out it works again so does not really look like a hardware error. Tried with PS2 and USB keyboards both, no change. Have not happened with past Kubuntus, only since I upped to Feisty. Very frustrating to begin with. Tried KDE 3.5.7, same. /var/log/messages , /var/log/syslog empty. Intel 945GM chipset, Asus N4L motherboard, Nvidia 7600GS video card with 'nvidia' driver. I run Skype, but it happened with 1.3 and 1.4beta too. I can't find any particular happening which would cause this -- not an incoming call or chat or something. It just locks up :(

Is there a special shortcut in KDE which would cause the keyboard to look like I am hung? Like Ctrl+S in console. Or, is there a way to force a 'keyboard reset' with the mouse?

---

### Post by rooford on 2008-02-28
I have exactly the same issue:
2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

I've found if you hold down the keys for a couple of seconds, the character eventually appears. So you can quit terminal sessions. Logging in and out fixes this issue.

---

