---
title: "Intersil 3886 ndiswrapper and iwconfig"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by philipgm on 2005-05-21
Hi All,

I've recently been through this forum, and a few others, trying to get my wireless network card working. 

My machine is:

Fujitsu Seimens Amilo A7640 
AMD 64 Mobile Athlon
512MB (128MB used for graphics)
Wireless card - Prism Javelin/Xbow

My first attempt at this was with the 64-bit distro but that llooked too hard so I switched to the 386 distro. It turned out that even though the installation process said that it had recognised and installed my wireless card (with the Prism54 driver) that this card is not supported by that driver and that I needed to install the Windows driver with ndiswrapper.

I found a How to in these forums for wireless Broadcom cards and followed that 
and found that it appeared to work - after I had de-installed and deleted the prism 54 driver.

My current problem is that although I can see the card in the network configuration tool, and using iwconfig, and dmesg reports that the card is present, and iwlist gives me a list of access points - so I know that the card is actually on and talking to the system - iwconfig does not appear to be able to set the ESSID or the AP address. 

Does anybody have any idea how I can proceed now?

---

### Post by f.prisson on 2005-05-21
What commands did you exacly try?

---

### Post by philipgm on 2005-05-21
I tried:

iwconfig wlan0 essid "myssid"

I also tried setting the access point directly

iwconfig wlan0 ap followed by the access point address

neither of these were successful - iwconfig reports ESSID any/off and AP as a string of zeros and colons.

Before

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0

After


wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:200   Missed beacon:0

No change at all.

---

### Post by f.prisson on 2005-05-21
Is it correct that there is no encryption enabled? Does iwlist see your specific accesspoint?

---

### Post by philipgm on 2005-05-21
I have just finished doing the install again so I haven't put the encryption key, in any case I have tried to make the connection with WEP on and off and there was no apparent effect.

iwlist does find and report my ESSID

---

### Post by f.prisson on 2005-05-21
Please send me the output of ```
iwlist scan
``` and tell me what's your essid.  Some times I also had problems connecting to my AP but I used encryption with the wrong authentication (open / shared)

---

### Post by philipgm on 2005-05-21
Thanks for the idea on the security mode - I had it as restricted, now it's set to open and suddenly iwconfig lets me set the essid and get the AP. Now I can ping other nodes the network - all except the wireless router that is! I think I'm doing something wrong with the encryption key so I'll check that out next.

---

### Post by f.prisson on 2005-05-21
Check your routers settings, at my router I can set whether it's pingable or not.

---

### Post by philipgm on 2005-05-22
OK, I don't know how, but now it works! 

What has changed? Because something must have! Well, I unplugged my router and an access point so that I could use the access point to let me work quietly in a corner, and stop annoying the family. Anyway, after the simple exercise of unplugging things and moving them around, I thought I'd try again.

#modprobe ndiswrapper
#dhclient wlan0 --------------------           this part never worked before

After that I have a working wireless connection. I had to put the IP addresses for my ISP's DNS servers in resolv.conf and stop it using the router for name lookup because it was really slow, and now everything works well. 

I suspect that there may have been some changes that I made to the router that were lost when I turned the power off. These could have been the true cause of my problems.

Thanks for your help

---

### Post by predator29 on 2006-04-11
Hi,

I've made a little howto for getting wireless alive, on this machine. I hope somebody will make use of this.

---

### Post by predator29 on 2006-08-18
I updated the howto for 6.06. Hope someone could get use to it.

---

### Post by TedyBear on 2007-03-24
Hi!

I have a Fujitsu-Siemens Amilo L 1300 laptop running Ubuntu 6.10.

Output of lspci:
01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

I've downloaded the driver from fujitsu-siemens homepage and ndiswrapper -l gives the following output:

Installed drivers:
prisma00                driver installed, hardware present 

I've removed the islsm_pci, islsm_device and islsm.

After this I ran sudo modprobe ndiswrapper.

The problem is ifconfig or iwconfig show wlan0, they only show eth1 (the realtek 10/100 lan) and eth2 which by running iwconfig identifies as 802.11b (altough this should be 802.11.b/g.

I'm grateful for any assistance.

---

### Post by TedyBear on 2007-03-26
Since my last posting I noticed I hadn't used the documentation for Ubuntu 6.10. I've now followed those instructions and the results are... well... Not for the better, I'm afraid.


After I've rmmoded the islsm modules and modprobed ndiswrapper, the following is the output of iwconfig:

lo        no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

No wlan0 here. I can't figure this out.

Any ideas? Getting desperate over here...

---

