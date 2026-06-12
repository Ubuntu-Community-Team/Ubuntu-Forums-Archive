---
title: "Netgear WG311T Wireless Router"
date: 2010-03-02
forum: Hardware
---

### Post by Rip-Saw on 2010-03-02
I just installed Ubuntu and am trying to get the Netgear WG311T Wireless Router to find the network. The wireless network is not listed in the menu.

---

### Post by Greenwidth on 2010-03-03
Looks like you will need to be using ndiswrapper as there are no linux drivers:
[http://www.linuxquestions.org/blog/drask-180603/2010/2/1/fix-the-arrow-keys-in-the-ubuntu-perl-debugger-2580/?goto=prev](http://www.linuxquestions.org/blog/drask-180603/2010/2/1/fix-the-arrow-keys-in-the-ubuntu-perl-debugger-2580/?goto=prev)

and

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

---

### Post by Rip-Saw on 2010-03-05
I put the folder with the driver in it in the user home folder and this happens:
kat@kattard:~$ cd /home/kat/"windows 2000"
kat@kattard:~/windows 2000$ sudo ndiswrapper -i wg311t13.inf
couldn't open wg311t13.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by Rip-Saw on 2010-03-11
I also tried the GUI and I get "Unable to see if hardware is present."

---

### Post by Rip-Saw on 2010-03-17
Really need help on this. I followed guides and they did nothing. I'm ready to abandon ubuntu over this :/

---

### Post by Greenwidth on 2010-03-17
Are you sure the file is lower case (it is case sensitive) - The links I posted refer to "WG311v3.INF". 

I was going to d/l and have a look at the zip, but it's going so slow it would take c.3hours..

---

### Post by Rip-Saw on 2010-03-18
I managed to install the driver using the GUI, I get the message "Unable to see if hardware is present." Also, when I search for errors, it seems the driver is installed, just something is not right.

kat@kattard:~$ tail /var/log/messages
Mar 17 23:03:44 kattard kernel: [18362.139698] usbcore: deregistering interface driver ndiswrapper
Mar 17 23:03:44 kattard kernel: [18362.159326] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 17 23:03:45 kattard kernel: [18362.180449] ndiswrapper: driver wg311t13 (NETGEAR, Inc.,10/25/2004,3.3.2.4) loaded
Mar 17 23:03:45 kattard kernel: [18362.180797] ndiswrapper 0000:01:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 17 23:03:45 kattard kernel: [18362.181163] ndiswrapper (NdisMAllocateMapRegisters:971): Windows driver wg311t13 requesting too many (256) map registers
Mar 17 23:03:45 kattard kernel: [18362.664654] ndiswrapper: using IRQ 17
Mar 17 23:03:45 kattard kernel: [18362.865014] wlan0: ethernet device 00:0f:b5:86:ea:11 using serialized NDIS driver: wg311t13, version: 0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0013.5.conf
Mar 17 23:03:45 kattard kernel: [18362.876962] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 17 23:03:45 kattard kernel: [18362.877108] usbcore: registered new interface driver ndiswrapper
Mar 17 23:03:45 kattard kernel: [18362.894272] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by Rip-Saw on 2010-03-18
Also, my friend let me borrow a 100 foot Ethernet cord to use for now; it didn't work. I brought it back to him and he tried it on his Windows box and it worked fine, but he had to run it at 10mbps. he also has a nicer network card but I'd like to see if I can configure mine for 10mbps as well. It's a very temporary solution though.

Edit: I figured this out and it works now. At least I can put my computer elsewhere.

---

### Post by norseman-has-a-laptop on 2010-03-18
i had the same problem at my friendshouse trying to fix her computer

---

### Post by Goveynetcom on 2010-03-18
> **Rip-Saw said:**
> I managed to install the driver using the GUI, I get the message "Unable to see if hardware is present." Also, when I search for errors, it seems the driver is installed, just something is not right.

kat@kattard:~$ tail /var/log/messages
Mar 17 23:03:44 kattard kernel: [18362.139698] usbcore: deregistering interface driver ndiswrapper
Mar 17 23:03:44 kattard kernel: [18362.159326] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 17 23:03:45 kattard kernel: [18362.180449] ndiswrapper: driver wg311t13 (NETGEAR, Inc.,10/25/2004,3.3.2.4) loaded
Mar 17 23:03:45 kattard kernel: [18362.180797] ndiswrapper 0000:01:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 17 23:03:45 kattard kernel: [18362.181163] ndiswrapper (NdisMAllocateMapRegisters:971): Windows driver wg311t13 requesting too many (256) map registers
Mar 17 23:03:45 kattard kernel: [18362.664654] ndiswrapper: using IRQ 17
Mar 17 23:03:45 kattard kernel: [18362.865014] wlan0: ethernet device 00:0f:b5:86:ea:11 using serialized NDIS driver: wg311t13, version: 0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0013.5.conf
Mar 17 23:03:45 kattard kernel: [18362.876962] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Mar 17 23:03:45 kattard kernel: [18362.877108] usbcore: registered new interface driver ndiswrapper
Mar 17 23:03:45 kattard kernel: [18362.894272] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Ndiswrapper is tough to get working....

Keep trying though.

triple check every step of the procedure.

I had one offline desktop with 9.10, then tried to get a USB wireless access card working.

Took me like 2 months or something, but I got it.

If someone has gotten it to work, chances are it is possible.

---

### Post by norseman-has-a-laptop on 2010-03-18
come to think of it i never did finish that job lol

i should save this page or screen shoot it

---

### Post by mfernandez on 2010-08-07
I installed xubuntu 10.04 on my old pc (Gateway 2000 PII) and it is working with the Netgear WG311T wireless card.  It was found and configured automatically.  It appears to be using the ath5k driver.  

It works but appears to drop connection speed sporadically.  I have seen it up to 54 Mb/s (although only for a short time) and down to 1 Mb/s.  Unfortunately it seems to hover at the slower speeds than the higher ones.  usually around 11 Mb/s.

---

