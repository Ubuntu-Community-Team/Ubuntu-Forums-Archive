---
title: "Partition on install fails"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by primus454 on 2009-02-01
So I got me a brand spankin new ASUS laptop that I am trying to install an Ubuntu partition on. However, neither the GUI installer nor gparted will work. I keep getting errors. With the GUI it says "creation of blah failed" and with gparted I am unable to resize my Vista partition.

---

### Post by caljohnsmith on 2009-02-01
Can you be more specific about what are the exact errors you get? Also, how about opening a terminal and posting:
```
sudo fdisk -lu

```

---

### Post by primus454 on 2009-02-01
I can't at the moment. I have it running the recovery disk(s?). Um. I can't post it because after the first attempted install my wireless card has ceased to work. This is why I hate Vista. I did 2 installs on XP no problem.

---

### Post by primus454 on 2009-02-01
Okay, so I got my internet working, however I cannot even get the installer to load now. I am getting 

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7)
Built-in shell (ash)
Enter 'help' for a list of built in commands
(initramfs)_

---

### Post by primus454 on 2009-02-06
For anyone that may come across this problem, I solved it by going into the BIOS settings and changing the IDE setting from [Enhanced] to [Compatible]

---

