---
title: "PCMCIA wireless modem changes the ttySx identifier on boot"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by Carlos Santiago on 2006-10-21
Hi,

I have an Acer TravelMate 4150 laptop with a PCMCIA wireless modem (Novatel UMTS modem, model Merlin U630), and I am using Ubuntu 6.06 (dapper). My questions are:

  1) The serial identification of the modem device changes from reboot to reboot (ex ttyS0, ttyS1 or even ttyS4). How can I force it to be always the same ttySx?

  2) How can I make the ppp connection to starts on the laptop boot, even before a login is done? For instance as a service. Plz notice the behave declared in 1).

  3) I connect using wvconf because is the only way I know to autodetect which ttySx serial port identifies the modem. Notice that the physical connection is always the same, the only PCMCIA port that I have. Moreover, I dont have any other PCMCIA device, so it is permantly connected. However, wvconf forces me to keep a console open, is there a way to avoid this? 

  4) The network properties icon on the top bar says that ppp0 is inactive (as which is not!), but shows the correct traffic activity ;-/ How can I make it to present the correct status?

  5) When i try to configure the connection using the GUI network config, I have to set the serial port (the reason why i use wvconf), but I also have to reenter the ISP phone number. Why the ISP phone number box opens always empty? Where can I define the modem speed (because I have to change the predefined maximum 115200 to 460800)?

Thank you!

Cheers,

Carlos

---

