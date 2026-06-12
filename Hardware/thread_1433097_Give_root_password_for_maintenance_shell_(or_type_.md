---
title: "Give root password for maintenance shell (or type Control-D to continue):"
date: 2010-03-18
forum: Hardware
---

### Post by rojsl55amg on 2010-03-18
the error :  rootpassword required or press ctrl-d

proplem   :cannot take my root password for some reason 


solution  : by the way this for user with grub2 and grub as well


1 go to additional recovery mode
2 then press e to edit the highlighted recovery mode you chosen from the boot-up list
3 then press e to edit kernel line by adding ro init=/bin/bash
4 type fsck -l to list the options for more control
5 type fsck dev/sda2 (where my dear linux is )
6 then press yes till you finish ,bingo!!!!:P

---

### Post by neo unplugged on 2010-08-11
Hello,
I am having the same issue and I am trying to get into advanced recovery mode. How do I get into advanced recovery mode. When I boot I have a normal kernel and kernel with recovery mode.
Thanks.

---

