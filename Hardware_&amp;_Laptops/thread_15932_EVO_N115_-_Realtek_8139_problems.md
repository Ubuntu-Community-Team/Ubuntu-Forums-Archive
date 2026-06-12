---
title: "EVO N115 - Realtek 8139 problems"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by iDleR on 2005-02-18
Hi! I have an Evo N115 and I use Ubuntu Warty in this Laptop. I have a serious problem: my eth card do not recognize some cables. For example: I have an adsl connection, the provider gave me an eth modem with own cable. When i launch pppoeconf Ubuntu recognize eth0 but is not able to find the modem, so i decided to change the cable and use a cross cable, and it works!! But te strange thing is it works only with the 2.6.1-3 kernel, not with 2.6.1-4 :/. One day i went to a friend's college to install matlab on his computer, there was an adsl room so i tried to connect my laptop but after I configured the manual network, computer did not access to the network and it can't ping [www.google.it](www.google.it) and internal network ip too and in this case it did not work both 2.6.1-3 and -4 kernel.
I've launched lspci and eth card is recognized, lsmod and 8139 modules are uploaded, I don't know which is the problem. Windows works fine in the same situation.

Pls help me.

---

### Post by iDleR on 2005-02-18
pls help me :(

---

### Post by iDleR on 2005-02-20
[QUOTE=iDleR]pls help me :([/QUOTE]
 Am I the only one who has this problem? O_o

---

### Post by zenwhen on 2005-02-20
I have the same ethernet controller on my motherboard and don't have any of the issues you are experiencing. I am stumped. I've never seen anything like that.

---

### Post by iDleR on 2005-02-20
[QUOTE=zenwhen]I have the same ethernet controller on my motherboard and don't have any of the issues you are experiencing. I am stumped. I've never seen anything like that.[/QUOTE]
 My friend tried the warty relase today and he has the same problem, but his laptop is an ACER

---

### Post by somuchfortheafter on 2005-02-20
per chance are you using the same disks?

---

### Post by iDleR on 2005-02-25
[QUOTE=somuchfortheafter]per chance are you using the same disks?[/QUOTE]
 uhm...the same image .iso, not the same disk...he used a dvd, i used a cd...

---

### Post by TeleTommy on 2005-09-09
did you solve your problem with your 8139 nic in the meantime? i have a similar problem.

---

