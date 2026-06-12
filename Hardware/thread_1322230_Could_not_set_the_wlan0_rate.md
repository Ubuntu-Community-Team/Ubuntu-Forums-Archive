---
title: "Could not set the wlan0 rate"
date: 2009-11-10
forum: Hardware
---

### Post by alikebabay on 2009-11-10
Hello everyone! I was trying to set wireless rate on my sony vaio fz21m to 60 megabit (card supports 144 mbit in windows vista) but the command failed.

sudo iwconfig wlan0 rate 60m


This is the output of command:
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Invalid argument.

I am currently running ubuntu karmic 9.04 and my wireless card is Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61). (taken from lspci)
This command used to work before, I am not sure what is the problem now.
P.S. Internet speed test gives me 36 mbit speed and I can download on the speed of 32mbit. I have installed and set up the samba and smbclient, so may be they cause this troubl. Regards.

---

### Post by lswb on 2009-11-10
Sorry, posted by accident.

---

