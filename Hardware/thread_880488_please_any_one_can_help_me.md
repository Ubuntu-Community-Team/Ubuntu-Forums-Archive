---
title: "please any one can help me"
date: 2008-08-05
forum: Hardware
---

### Post by amr6060 on 2008-08-05
i'm useing ubuntu 7.10 and i have 1 pci slot give 2 out of 9pine  and  i want to add 1 pci slot anather but i cant
and i want to see all the com port been

i sent with  the lunix for the card and i do the firest  stup

but the scondary  i cant  understand it   <2>-Add /usr/sbin/install_ss_80x86 at the end of the /etc/rc.d/rc.local.     i cant understand it
    



1-install and uninstall CH352 PCI to two serial ports
(1)-install
<1>-copy install_ss_80x86.o to /usr/sbin
<2>-Add /usr/sbin/install_ss_80x86 at the end of the /etc/rc.d/rc.local.
<3>-reboot
The ttyS2 and ttyS3 are ready for application.
(2)-uninstall
(1)-Remove /usr/sbin/install_ss_80x86 at the end of the /etc/rc.d/rc.local.
(2)-Remove /usr/sbin/install_ss_80x86.o

---

### Post by wyliecoyoteuk on 2008-08-05
I am not sure if I understand you correctly, but I think that for what you are trying to do, you need to edit the file /etc/rc.d/rc.local with a text editor.

sudo nano /etc/rc.d/rc.local

and add the line 

/usr/sbin/install_ss_80x86 

at the bottom.

---

### Post by hotweiss on 2008-08-05
> **wyliecoyoteuk said:**
> I am not sure if I understand you correctly, but I think that for what you are trying to do, you need to edit the file /etc/rc.d/rc.local with a text editor.

sudo nano /etc/rc.d/rc.local

and add the line 

/usr/sbin/install_ss_80x86 

at the bottom.

Wow, congratulations for understanding that question!

Maybe the original poster could maybe post in his native language in hope of someone fully understanding his question.

---

