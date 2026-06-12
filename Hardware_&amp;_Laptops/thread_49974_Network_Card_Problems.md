---
title: "Network Card Problems"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by C1ph3R on 2005-07-18
ive got a "Network Everywhere" 10/100 network card that im having trouble w/.  Ive got the floppy disk w/ the driver on it, and i go to the floppy disk, open up the linux folder, and went to the readme file... it says 

Linux Driver Installation

A. Get Source Code and Produce binary code
    Step 1. Get the source code from the following site;
      [ftp://cesdis.gsfc.nasa.gov/pub/linux/drivers/kern-2.3/tulip.c](ftp://cesdis.gsfc.nasa.gov/pub/linux/drivers/kern-2.3/tulip.c)
      [ftp://cesdis.gsfc.nasa.gov/pub/linux/drivers/kern-2.3/kern_compat.h](ftp://cesdis.gsfc.nasa.gov/pub/linux/drivers/kern-2.3/kern_compat.h)

    Step 2. : Compile the source code by using,

                "gcc -DMODULE -D __KERNEL__ -i/USR/SRC/LINUX/NET/INET
                -Wall -Wstrict -prototypes -06 -c tulip.c
                ' [ - f /usr/include/linux/modversions.h ]

Then it gives instructions on how to install it in slackware and redhat....

i cant get the websites to work, and im not sure on what im supposed to do here... any help would be appreciated

---

### Post by amohanty on 2005-07-18
Ubuntu comes with tulip drivers, which is what the link pointing to. I think you just need to plug in the hardware and reboot. After reboot you can goto either:
Applications:System:Network Tools OR
System:Administration:Networking 
and configure the card.

Or is the problem that after reboot the network card is not detected.

AM

---

### Post by C1ph3R on 2005-07-18
its not detected, theres a zip file in the linux folder and i extracted it.. its c++ code, im guessing for the driver

---

### Post by C1ph3R on 2005-07-18
[QUOTE=C1ph3R]its not detected, theres a zip file in the linux folder and i extracted it.. its c++ code, im guessing for the driver[/QUOTE]
 help please

---

### Post by wvslkr on 2005-07-18
Try opening a terminal and type>sudo modprobe tulip.  If you get no errors, type ifconfig.  You should have two listings local loopback and eth0.  If they are both listed go to your admin menu and find the network section to enable the card.  To make it permanent add tulip to /etc/modules.  Basically if this works you don't have to fool with compiling the module.

GL. :)

---

### Post by C1ph3R on 2005-07-18
[QUOTE=wvslkr]Try opening a terminal and type>sudo modprobe tulip.  If you get no errors, type ifconfig.  You should have two listings local loopback and eth0.  If they are both listed go to your admin menu and find the network section to enable the card.  To make it permanent add tulip to /etc/modules.  Basically if this works you don't have to fool with compiling the module.

GL. :)[/QUOTE]
 ok i did all this except im not sure how to add tulip to /etc/modules

---

### Post by wvslkr on 2005-07-18
In terminal type>sudo gedit /etc/modules.

Type in tulip and save it.  When you reboot your card should automatically work.

Did modprobe work?

---

### Post by C1ph3R on 2005-07-18
[QUOTE=wvslkr]In terminal type>sudo gedit /etc/modules.

Type in tulip and save it.  When you reboot your card should automatically work.

Did modprobe work?[/QUOTE]
 when i type sudo modprobe tulip, nothing happens

---

### Post by wvslkr on 2005-07-18
If it accepts the module nothing is reported back.  Did you run ifconfig?

---

### Post by C1ph3R on 2005-07-18
[QUOTE=wvslkr]If it accepts the module nothing is reported back.  Did you run ifconfig?[/QUOTE]
 ya both eth0 and loop came up..

---

### Post by wvslkr on 2005-07-18
OK.  That means your card is loaded.  You now have to go to your menu bar (I'm assuming you are using Gnome),I believe its the last menu.  There is somewhere a network settings tab.  There you have to set your card for how you are connecting and enable it.  After you do that you should be able to fire up a browser and hit the net. :)

---

### Post by C1ph3R on 2005-07-18
ok so i put tulip in modules, rebooted the machine, but still no internet... my modem/router shows that there is activity, also when i go to network tools loop is always the network device...

i already put in all the settings, ip, gateway, etc.. activated it in the admin networking setting... but still no internet

---

### Post by wvslkr on 2005-07-18
Please post your ifconfig.  Also try to ping your router and some internet address and post those.

---

### Post by C1ph3R on 2005-07-18
[QUOTE=wvslkr]Please post your ifconfig.  Also try to ping your router and some internet address and post those.[/QUOTE]
 Alright, i got it
thanks for all the help

---

### Post by wvslkr on 2005-07-18
Happy you got it up.  Have Fun :)

---

