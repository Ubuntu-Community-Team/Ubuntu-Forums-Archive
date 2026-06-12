---
title: "Help: Network Printer Setup - HP Officejet 7210"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by strange_days on 2006-03-20
Hi,
 Hoping you can help me to set up my printer. It is a network attached HP Officejet 7210 All-In-One printer. As I'm pretty new to Linux I would appreciate it if someone can assist by giving me some step by step instructions in getting this done. 

Many Thanks.......

---

### Post by strange_days on 2006-03-21
Okay - i checked out the fact that i have hplip installed, which i do:

un  hplip          <none>         (no description available)
ii  hplip-base     0.9.5-2ubuntu2 HP Linux Printing and Imaging System - base
ii  hplip-data     0.9.5-2ubuntu2 HP Linux Printing and Imaging - data files
ii  hplip-ppds     0.9.5-2ubuntu2 HP Linux Printing and Imaging - PPD files

I then try to enter the following command:

sudo hp-setup -m 'ip address of printer' (without the quotes)

and get the following response:

bash: hp-setup: command not found

Can anyone assist and tell me what i'm doing wrong. I'm following instructions at the following location:

[http://hpinkjet.sourceforge.net/install.php#help](http://hpinkjet.sourceforge.net/install.php#help)

Thanks.....

---

### Post by dieselpower on 2006-03-22
I am having the exact same problem. I am trying to set up a HP laserjet 3p with PCL5 on an ubuntu headless server and it kinda seems impossible right now ](*,)

---

### Post by strange_days on 2006-03-23
:-D Success:

After confirming that you have hplip installed: do the following (hopefully should work for you).

Click on System --> Administration --> Printing, and double click on the New Printer icon. Choose Network printer and HP JetDirect; then enter the printer address (just the address - eg. 198.123.6.2), the 9100 port is already standard; then in the next screen choose HP and select your HP system, and accept the suggested driver - hpijs. That's it, a HP Printer icon appears next to the New Printer icon; right-clicking on it and selecting Properties should enable you to set page size etc. Then printing a Test Page should work.

My thanks to hajk for his response to another query in the hardware help-->networking section of this forum. 

strange_days

---

