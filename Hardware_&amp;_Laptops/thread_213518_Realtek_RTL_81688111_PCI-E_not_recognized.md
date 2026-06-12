---
title: "Realtek RTL 8168/8111 PCI-E not recognized"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by colonna on 2006-07-11
During installation, Ubuntu 6.06 server-version complains of not having found any network card.

When the installation ends from the CD,the /etc/X11 directory has not been installed.

I can access to the computer through a command line interface..

On the Realtek web site I found the necessary files to implement in the kernel. But a lot of commands are missing to compile the kernel :
*no make
*no install 

The computer is an Asus W2JC with:
* Realtek RTL 8168/8111 PCI-E Gigabit
* Screen 17" WSVGA+
* Video card ATI Mobility Radeon X1600 3D

My questions are:
1. what I have to do to install the Realtek driver ?
2. is the X11 problem connect with the network access ?

Thanks for answering.

---

### Post by insanedc on 2006-07-11
During the BETA cycle, I had to download the driver from Realtek, plus download the necessary files for compilation from Ubuntu. I thought that the released version included the Realtek drivers (at least the desktop version does).

---

### Post by didobuntu on 2007-02-16
Now it is recognized

---

