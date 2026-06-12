---
title: "Various problems with KUBUNTU"
date: 2005-11-28
forum: General Help
---

### Post by drgreborn on 2005-11-28
Here are my difficulties with KUBUNTU. Hope someone could help me out. ^^

1: Edimax ep-4103dl pcmcia card.
The card is not detected, cant remove the loopback that was created when kubuntu was installed. After doing modprobe the card is still not detected.

2: Time setting of Kubuntu does not start. I'm trying to fix the timing on teh laptop and when I click set time and entering my password for sudo the thing just dissapears and does not start up.

Laptop is an ASUS S8600

I really hope someone can help me out. Realy sorry about this. Thank you in advance.

---

### Post by drgreborn on 2005-11-28
Oh and another question. Theres this thing called administrator mode. There is no such button to click and when I type kdesu kcontrol in the run app, nothing happens.

---

### Post by blastus on 2005-11-28
[QUOTE=drgreborn]Oh and another question. Theres this thing called administrator mode. There is no suck button to click and when I type kdesu kcontrol in the run app, nothing happens.[/QUOTE]

This is a known bug (and a highly conspicuous one I might add) in Kubuntu. See the [Adminstrator Mode fails](http://ubuntuforums.org/showthread.php?t=75114) thread for info and the workarounds.

---

### Post by drgreborn on 2005-11-28
Thanks. I noticed someone has teh same prolems about eh pcmcia card as me. But there was no follow up. Mayeb someone copuld tell me how to install a pcmcia card? It may help the problem.

---

### Post by drgreborn on 2005-11-28
Here's the readme  for the driver. But teh directory seems diferent in kubuntu.

Realtek CardBus Ethernet Card Installation on Linux



1. Compile the source code :

 ->Copy the source code rtl8139.c (ver 1.08 above) to a directory

   and execute "gcc -DCARDBUS -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes 

   -O6 -c rtl8139.c -o realtek_cb.o -I/usr/src/linux/pcmcia-cs-3.0.9/include/"

   The directory "pcmcia-cs-3.0.9" stands for the card service version you 

   use. Please change it to the version on your system in order to include 

   proper .h file. The final file is realtek_cb.o



2. Copy driver :

 ->Copy the file "realtek_cb.o" to "/lib/modules/2.2.14-5.0/pcmcia"



3. Edit config:

 ->Add 5 lines to the file "/etc/pcmcia/config"

   

   #

   # Device driver definitions

   #

  

   device "realtek_cb"					 (==>Add 1/5)

     class "network" module "cb_enabler", "realtek_cb"   (==>Add 2/5) 





   :

   :



   #

   # CardBus Cards

   #



   card "Realtek CardBus Ethernet Card"			(==>Add 3/5)

     manfid 0x0000, 0x024C				(==>Add 4/5)

     bind "realtek_cb"					(==>Add 5/5)



   

   The values 0x0000, 0x024C are JEDEC ID and can be read by typing 

   "cardctl ident" on console with one card on socket.

	          



4. Edit linuxconf

 ->Type "linuxconf" and choose "Config"-->"Networking"-->"Client tasks"-->

   "Basic host information". Select an adapter, enable it, and type "realtek_cb"

   on "Kernel module" and "eth0" (or eth1, eth2) on "Net device". Click on 

   "Accept" button and "Act/change" button.





5. Restart the computer.




6. More information about kernel compile: [http://metalab.unc.edu/mdw/HOWTO/Kernel-HOWTO.html](http://metalab.unc.edu/mdw/HOWTO/Kernel-HOWTO.html)

   More information about install: man pcmcia

---

### Post by Paul Casey on 2005-11-28
[QUOTE=drgreborn]Oh and another question. Theres this thing called administrator mode. There is no such button to click and when I type kdesu kcontrol in the run app, nothing happens.[/QUOTE]

I have noticed the non existant button.... but then on some can resize the tool window (grab the lower right corner) and enlarge the window.. then the button becomes visible.

---

### Post by drgreborn on 2005-11-28
It seems teh priblems is taht kubuntu cant read my card, when I go into teh kcontrol under pcmcia, no cards are detected. What gives? Shoudl I switch back to Gnome base Ubuntu?

---

### Post by githeko on 2005-12-03
[QUOTE=Paul Casey]I have noticed the non existant button.... but then on some can resize the tool window (grab the lower right corner) and enlarge the window.. then the button becomes visible.[/QUOTE]


On my system, the button os off the screen below the status bar.  The only way to view it is to drag the window UP by pressing Alt key then draging with the (left) mouse key pressed down.

---

### Post by teaker1s on 2005-12-03
create a launcher for affected control panel
sudo kcontrol

---

### Post by B0rsuk on 2005-12-03
Hey

I have my own share of problems.

1. I created an user using adduser command.....
If I log out of KDE, my keyboard is frozen, and i can only use mouse. I can't even type the password and have to reboot.

---

