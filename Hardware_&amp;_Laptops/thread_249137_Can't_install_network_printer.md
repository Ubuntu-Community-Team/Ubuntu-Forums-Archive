---
title: "Can't install network printer"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by torbjorn_cederlov on 2006-09-02
I am currently trying to install a HP Deskjet 3745, connected to a D-link DI-524UP wireless router with a USB printer server. The printer works fine if I plug the USB-cable directly to my computer, but when I try to install the printer, when it's connected to the router, the "new printer" program crashes when I click "install driver"

Here are what the router says about my printer:
Queue Name: lp1
Printer Name: HP Deskjet 3740 CN53A170B9040Q 	                 
Printer Server Status: Idle
        	 
btw: In windows the printing works fine.

I relly need help with this problem! It's really annoying to have to restart into windows every time I need to print something... (it's the only use I have for my windows partition, :-D )

---

### Post by Pawe76 on 2006-09-10
I use the same router and this worked for me:

You'll need the hostname or IP Address of the printer (usually 192.168.0.1) and the connection protocol details (UNIX Printer LPD, Port: 515, Queue: lp1 ).

1. Go to system/administration/printing
2. Click on New Printer
3. Click on Network Printer
4. Select how you connect to the printer - UNIX Printer (LPD)
5. Enter the Host (192.168.0.1) and queue (lp1).

---

### Post by torbjorn_cederlov on 2006-09-11
Thanks for the reply!

I have tried what you suggested, but when I come to the second step of the printer installastion, there is no printers in dhte lists, and when I click 'install driver' there is an error message telling that the program has crashed... 

[IMG]http://www.stud.ntnu.no/~cederlov/Screenshot.png[/IMG]

Any idea what I can do?

---

### Post by the_zoor on 2007-02-11
> **Pawe76 said:**
> I use the same router and this worked for me:

You'll need the hostname or IP Address of the printer (usually 192.168.0.1) and the connection protocol details (UNIX Printer LPD, Port: 515, Queue: lp1 ).

1. Go to system/administration/printing
2. Click on New Printer
3. Click on Network Printer
4. Select how you connect to the printer - UNIX Printer (LPD)
5. Enter the Host (192.168.0.1) and queue (lp1).

I have that exact router but I didn't get it to work. It actually starts "warming up", which I guess means that it gets some form of info from my computer. But then it just freezes. I've even tried to change the IP number to 192.168.0.1:515 according to your tip but the same results. What can be wrong?

---

