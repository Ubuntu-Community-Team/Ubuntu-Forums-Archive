---
title: "install ubuntu to a specific drive"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by delian87 on 2009-05-06
Hi I am new to ubuntu and sick of MS windows. So:
Windows was installed to drive C:
I have drive D: where i keep all my stuff. i splitted that to D: and G: (G: is 20 GB). I want to install ubunto to G: so I can keep windows and have dual boot, and later get rid of windows,when i am completely used to ubuntu.
When installing ubuntu i use manual partitoning option. It shows me all three drives i have C: D: G: (sda1 sda5 sda6). So i select sda6 which is G:, click forward and a mesage shows " No root file system is defined. Please correct this from the partitoning menu"
So what should i do now?
tnx

---

### Post by fminmexico on 2009-05-06
> **delian87 said:**
> Hi I am new to ubuntu and sick of MS windows. So:
Windows was installed to drive C:
I have drive D: where i keep all my stuff. i splitted that to D: and G: (G: is 20 GB). I want to install ubunto to G: so I can keep windows and have dual boot, and later get rid of windows,when i am completely used to ubuntu.
When installing ubuntu i use manual partitoning option. It shows me all three drives i have C: D: G: (sda1 sda5 sda6). So i select sda6 which is G:, click forward and a mesage shows " No root file system is defined. Please correct this from the partitoning menu"
So what should i do now?
tnx

Go back to the partition manager choose sda6 click format this and choose ext2 then choose / for boot.
           fminmexico.

---

### Post by delian87 on 2009-05-06
ext2 or 3?

---

### Post by cholericfun on 2009-05-06
go for ext3

---

### Post by Bartender on 2009-05-06
or ext4

---

