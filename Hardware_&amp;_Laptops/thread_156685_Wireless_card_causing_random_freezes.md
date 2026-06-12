---
title: "Wireless card causing random freezes"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by BobTheFish on 2006-04-07
I've installed Ubuntu on my laptop and everything works wonderfully until I try to use wireless networking. When a wireless PCMCIA card is used the system freezes after a random amount of time. Sometimes it occurs before I even have time to log in. Other times it takes a while before it happens. Absolutely everthing stops. The mouse doesn't move, and any activity on the screen stops.

I have tried with two different PCMCIA cards. The first is a Belkin using the RaLink RT2500 chipset. The second is a D-Link using the Atheros ax111 chipset. In both cases I have tried the default Ubuntu drivers and NdisWrapper.

The freezes seemed to be associated with any large quantity of network activity. any reasonable sized apt-get (larger than about 5MB) causes it every time. But the freeze sometimes occur without any activity at all.

Any ideas as to where to look for the root of this problem?

edit: Just noticed the Laptop sub forum. Could moderator move this there if it is appropriate. thanks.

---

### Post by Zeroedout on 2006-04-07
[quote=BobTheFish]I've installed Ubuntu on my laptop and everything works wonderfully until I try to use wireless networking. When a wireless PCMCIA card is used the system freezes after a random amount of time. Sometimes it occurs before I even have time to log in. Other times it takes a while before it happens. Absolutely everthing stops. The mouse doesn't move, and any activity on the screen stops.

I have tried with two different PCMCIA cards. The first is a Belkin using the RaLink RT2500 chipset. The second is a D-Link using the Atheros ax111 chipset. In both cases I have tried the default Ubuntu drivers and NdisWrapper.

The freezes seemed to be associated with any large quantity of network activity. any reasonable sized apt-get (larger than about 5MB) causes it every time. But the freeze sometimes occur without any activity at all.

Any ideas as to where to look for the root of this problem?

edit: Just noticed the Laptop sub forum. Could moderator move this there if it is appropriate. thanks.[/quote]

I actually had the same problem. The freezes would only happen when I used network-admin or GTK wifi. If I do it all manually, it never freezes. I have not had time to screw around with it much (classes just finished but exams comming up), so it may just be a concidence. Try bring up everything manually, if you don't know the commands, to scan for a network, sudo iwlist [interface] scan  , so in my case ```
sudo iwlist wlan0 scan
``` then change your network card settings, sudo iwconfig [interface] essid [ESSID] so in my case ```
sudo iwconfig wlan0 essid home
``` then switch the channel if necessary, sudo iwconfig [interface] channel [channel] , I do ```
sudo iwconfig wlan0 channel 4
``` then, if the router/ap is using DHCP, sudo dhclient3 [INTERFACE] , in my case ```
sudo dhclient3 wlan0
``` see if that helps any.

---

### Post by BobTheFish on 2006-04-08
Just tried that with both cards. Still does exactly the same.

Are there any logs that might contain useful information about what is happening?

---

### Post by BobTheFish on 2006-04-11
just one final bump to see i anyone has any ideas. im still getting the same problem after a total reinstall.

---

### Post by Zeroedout on 2006-04-12
[quote=BobTheFish]just one final bump to see i anyone has any ideas. im still getting the same problem after a total reinstall.[/quote]

You should try looking through dmesg to see what went wrong. ```
sudo dmesg
```  Why I didn't suggest this in the first place, I dunno, I must've been high or drunk or somethin. The one with the rt2500 chipset should definatly work though, the corp that made that chipset released it under the GPL and it is activly worked on. If it is not working now, I can guarentee it will work soon, as there is quite alot of work being done on it (the rt2500 is one of the VERY few drivers that are GPL)

---

### Post by daWabbit on 2006-04-12
Using the same PCMCIA (actually, it's 32 bit, which makes it cardbus) card in an HP Pavillion laptop (an old one with a 550 MHz K6-3) froze it every time. Seeing as I installed with a wired nic in that slot and it worked fine. I reinatalled Breezy with the wireless card in the slot and it worked. I had to take one minor config step to make the wired nic work after. So, you might try a reinstall with the wireless card installed.

Jack

---

### Post by Topper_H on 2006-04-12
I'm also experiencing random freezes since my upgrade to dapper. Everything is locked and I've no choice but to hard-reboot.
This thread got my attention because I have a rt2500 PCI card too.
From my experience, those freezes happen anytime, system/network being idle or not.

Hope it helps

---

### Post by deadlydeathcone on 2006-04-20
This used to happen to me, and the problem was that the rt2500 was trying to assign itself the same irq as my video card when I turned it on, completely killing my machine. Try disabling the irq on your videocard and see if that helps.

---

