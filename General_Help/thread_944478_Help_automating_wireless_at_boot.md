---
title: "Help automating wireless at boot"
date: 2008-10-11
forum: General Help
---

### Post by razta on 2008-10-11
Hello,
Ive recently reinstalled Ubuntu on my Desktop machine. Every time I reboot I have to open 'The Network Administration Tool' (System > Aministration > Network), then I have enable/disable the wireless card by ticking/unticking the box to the left of the wireless connection image, then I have to go to properties enter my WPA password, then enable/disable the card again, to get the wireless card up and running.

Is there any way I can automate the above so that I dont have to do it every time I reboot?

Thanks in advance!

P.S. I tried 

sudo /etc/init.d/networking restart

sudo ifconfig wlan0 down
sudo ifconfig wlan up

None of the above get the wireless working, I have to use the GUI for some reason.

EDIT---------------------------------------------

Updated to 8.10 BETA and that seems to have sorted it out.

---

