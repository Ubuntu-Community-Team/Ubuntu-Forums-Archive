---
title: "Install almost done then... BOOM!"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by Barfoot on 2006-01-31
For some odd reason about 84% the way through configuring packages (after the partition/copy/reboot phase) I get a vague error saying a package failed to install and my Ubuntu install is incomplete. I hit "OK" (the only option) and I get a scrambled screen with ascii characters all over it. I can hit enter a few more times and get to a login screen, but the install is broken and unusable.

- I tried the Live CD, it boots fine.
- I tried replacing the HD in the machine, thinking maybe my HD was faulty, didn't help.
- I tried unpluging all non-critical devices. No dice.
- I ran that CD test in the install menu, no problems found.

System:
ABit IT7 Mobo
P4 2.53 GHz
1024 MB RAM
Two (2) 120 GB ATA100 HDs
Geforce TI 4200
SB Audigy
CDRW/DVD Combo drive

What other things can I try to get the install to go all the way through? Any help or tips would be greatly appreciated. Thanks.

---

### Post by Ocxic on 2006-01-31
have you tried using a different cd, or burning at a lower speed. you could also 
try doing a server installation, and then when you get to you login prompt type
```
sudo apt-get install gnome-desktop-enviroment
```

---

