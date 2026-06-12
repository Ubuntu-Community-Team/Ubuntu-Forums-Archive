---
title: "Wifi &amp; Laptop built in mousepad"
date: 2008-10-10
forum: Hardware
---

### Post by PogoMonkey on 2008-10-10
Hi,
I recently made the change to ubuntu 8.04 desktop from Windows Vista.
So far, its all good apart from 2 problems.
I'm having trouble with my wifi, doing a search on the forum I found a tutorial on how to install drivers for the atheros wireless card, wasn't my specific model but now I am atleast finding wireless networks. I just cant connect to them, whenever I enter the WEP password, it takes about 30 seconds and then stops.

Also, the mousepad on my laptop doesn't seem to work
I have an Acer Aspire 5315.

*edit, Also, whenever I plug in an external hard drive, it says Unable to Mount.
Does anyone know how this can be fixed?

Thanks alot,
just ask if you need any specific details for anything.

---

### Post by mike.pms on 2008-10-10
How strange lol, i just made a post like 3 mins before you with the same problem, not just the same problem... same card! lol You at least managed to get your Atheros to see networks. Hope we get help with this :)

---

### Post by ubunny on 2008-10-10
sudo lspci -v will confirm your chipset type
I just use command lines, so 

sudo ifconfig ath0 down
sudo iwconfig ath0 essid apname key somewepkey
sudo ifconfig ath0 up
sudo dhclient ath0 

I usually dump into a text file then chmod +x to run it as a script.  The dhclient ath0 goes and gets an IP via dhcp.  For a specific IP you can go to System->Administration->Network for more GUI options.

---

### Post by PogoMonkey on 2008-10-10
Thankyou! Worked perfectly.

If anyone knows anythihng about the mousepad, would be wonderful :)

---

