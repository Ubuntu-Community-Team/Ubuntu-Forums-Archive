---
title: "[SOLVED] Ubuntu 8.10 LiveCD/Installation orange boot progress bar freezes"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by tpaljor on 2009-01-01
Hi,

I recently had a problem getting Ubuntu 8.10 Live CD/Alternate installation to work. Right after selecting the language and attempting to either boot into the live desktop or install, the orange Ubuntu progress bar freezes at about 20 percent. If you press and hold down any key, the progress bar continues to load and eventually will boot. However, after installation, you will need to hold down a key during boot every time. 

I had a fair bit of trouble trying to find the solution, so I decided to post the one I eventually found that worked for me. This might make it easier for other's.

In Grub, use the kernel parameter (F6) 'hpet=disable'.

This is taken from [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fedora-10-x8664-system-hangs-on-boot-unless-i-press-or-hold-down-any-key-688411/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fedora-10-x8664-system-hangs-on-boot-unless-i-press-or-hold-down-any-key-688411/)

All the best!

---

