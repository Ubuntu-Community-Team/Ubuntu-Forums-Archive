---
title: "Fujitsu Siemens LIFEBOOK E4010"
date: 2009-11-27
forum: Hardware
---

### Post by n8ek on 2009-11-27
I have just installed Ubuntu 9.10 on my sons laptop  Fujitsu Siemens LIFEBOOK E4010 i think it has intel PRO/Wireless LAN 2200 BG card inside and i am unable to get the wireless to work, i have installed the windows wireless software tool and tried wireless driver's from the Fujitsu site but to no avail, do i need to black list a built in driver i download a specific 1?

Thanks in advance

---

### Post by SoftPops on 2010-01-13
Have only just seen this post otherwise I would have replied sooner.
 
I too have a Fujitsu E4010 laptop, mine has the Intel PRO/Wireless 2100 built in card. I have been using Ubuntu since 8.10 with no issues. The card works "out of the box".
 
One silly question as I am sure you will have checked this, is the card switched on?
 
Looking from the front of the laptop, on the left hand side there is a little slide switch which switches the wireless card on and off, make sure this is pushed to the back of the laptop for it to be on. The device that the card seems to use is "eth1".

---

### Post by Che69 on 2010-03-02
I've had about the same issue every now and then... Fujitsu-Siemens E8310.

In the beginning (installed on this PC Ubuntu 9.04 - updated to 9.10) I had WLAN working and, at that time, for no reaseon at all it was gone again.

With the 9.10 I had some other problems, but not wit the wireless card untill I had to switch of WLAN in the Network Manager Aplett to check if a modem was working and beeing sure wireless wasn't desturbing.

Sins then - no WLAN...

First I tried to configure access point again, but the "Enable Wireless" was greyed out. After a few restarts the "Enable Wiress" was checked...? But I think the "Kill switch" is the reason for the WLAN still not working.

When I do "lshw -C network" in terminal I still get

  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       ... and so on.

Then I tried to install the newest Network Manager 0.8
[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)
... no luck.

After Googling a while I found a alternative for Networ Manager (since I had had before - sometimes in the year "sword an shield" - trouble with it and spesially with WLAN...). Wicd - but I still not having WLAN. It just says "No wireless Networks found".

I have tiried the kill switch in both position - I coud even stand on my head and talk swedish, but I'm still not having Wireles Interface...

If anyone finds the reason for this behavior or a deasent sollution I'm all ears.

Cheers

---

### Post by Che69 on 2010-03-02
Ok - scratch that... The kill switch needs to be in the correct position at boot. NOW I have my network card connected... still struggling with the connection, but one stepp further.

I removed vicd (could not find fast a sollution for havin' both connections open at the same time) and installed NetworManager again.

Cheers

---

