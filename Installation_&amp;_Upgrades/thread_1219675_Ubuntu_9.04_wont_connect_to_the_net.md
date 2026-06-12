---
title: "Ubuntu 9.04 wont connect to the net"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by desideratha on 2009-07-22
Hi all.

I just upgraded from Ubuntu 8.10 to 9.04 and now cannot connect to the net via my wireless connection.

I tried a few things, however can't get it to see my wireless card.

Any suggestions.

Thanks

---

### Post by tommcd on 2009-07-22
> **desideratha said:**
> 
I tried a few things, however can't get it to see my wireless card.
Any suggestions.

What wireless card do you have?
What exactly have you tried to get it to work?
Post the output of:
lspci
ifconfig
ifconfig -a
iwconfig
And do you use encryption on the router? If so, is it WEP or WPA?

---

### Post by desideratha on 2009-07-22
> **tommcd said:**
> What wireless card do you have?
What exactly have you tried to get it to work?
Post the output of:
lspci
ifconfig
ifconfig -a
iwconfig
And do you use encryption on the router? If so, is it WEP or WPA?

HI and thanks for replying,

I tried lspci and ifconfig, -a , also I install ndisgtk but don't have a  windows driver to install... (actually I don't really know if i need that) 

when I cat /etc/resolv.conf I see primary and secondary domains

It's hard to post outputs since I don't have internet form my ubuntu partition (I'm on windows now) 

I think my router uses wep, however, how can I be sure?

thanks again

---

### Post by tommcd on 2009-07-22
> **desideratha said:**
> HI and thanks for replying,

I tried lspci and ifconfig, -a , also I install ndisgtk but don't have a  windows driver to install... (actually I don't really know if i need that) 
Why would you need a Windows driver in Ubuntu? Again, what wireless card do you have??? You should be able to find it from the output of **lspci**. You don't have to post all of lspci, just the part about your internet devices. 
Do you have any wireless devices in the output of ifconfig or iwconfig?? If so, can you post them here??
Do you know what wireless card you have???
> **desideratha said:**
> 
when I cat /etc/resolv.conf I see primary and secondary domains

This is normal, and it means that Ubuntu has at least found your ISPs DNS servers.
> **desideratha said:**
> 
I think my router uses wep, however, how can I be sure?

Go into the router's configuration (probably 192.168.0.1 in Firefox url window) and check your router's settings.

---

### Post by desideratha on 2009-07-22
Thanks again...

You are right, I realized that I dont need a windows driver.

I'll get back on ubuntu and post the results.

---

### Post by desideratha on 2009-07-22
Hi

here is the output

andres@andres:~$ lspci
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

andres@andres:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:80:d6:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:63:59:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-63-59-5D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


andres@andres:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS t h r: off   Fragment t h r= 2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid 
frag:0
          Tx excessive retries:0  Invalid misc:0   Missed 
beacon:0

pan0      no wireless extensions

//can't get this to work
Go into the router's configuration (probably 192.168.0.1 in Firefox url window) 
and check your router's settings.

---

### Post by tommcd on 2009-07-23
Go to: system > administration > hardware_drivers, and see if there is an option for enabling the intel wireless driver. The intel 3945 should work out of the box

Type **lsmod** in the terminal and post the output here. You should have the **iwl3945** driver loaded, if not, then run:
```
sudo modoprobe iwl3945
```
to load it.
Be sure to disable all encryption on your router. You can re-enable it after you establish a connection. 
Then run:
```
sudo iwlist wlan0 scanning
```
to see if it finds your router's essid.
If it does, then run:
```
sudo iwconfig wlan0 essid your_essid_name
```
Replace your_essid_name with the name of your essid in your router's configuration.
Then run:
```
sudo dhclient wlan0
```
This should get you an IP address. If not, then post the output of all those commands here.
You can also go to: system > preferences > network_connections, and try to configure wlan0 in the network manager.

---

### Post by desideratha on 2009-07-23
Hi, thanks again, I'll run the commands and post outputs...

// How do I do this?

Be sure to disable all encryption on your router. You can re-enable it after you establish a connection.

---

### Post by desideratha on 2009-07-23
Hi;  still dont know how to disable all encryption on my router



andres@andres:~$sudo modoprobe iwl3945

iwl3945                	89972  0  
iwlwifi_mac80211      221284  1 iwl3945 
cfg80211               	15368  1 iwlwifi_mac80211 


andres@andres:~$ sudo iwlist wlan0 scanning 
  
wlan0     Scan completed : 
          Cell 01 - Address: 00:14:A5:90:E5: DF 
                    ESSID:"Motorola" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=58/100  Signal level=-73 dBm  Noise level=-127 dBm 
                    Encryption key: on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000184d4536a11 
          
Cell 02 - Address: 00:15:E9:01:FC: 00 
                    ESSID:"Colon 3770 Depto 91" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=46/100  Signal level=-81 dBm  Noise level=-127 dBm 
                    Encryption key: on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=000001247f3f8183 
 
andres@andres:~$ sudo iwconfig wlan0 essid Motorola 

andres@andres:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:19:d2:63:59:5d 
Sending on   LPF/wlan0/00:19:d2:63:59:5d 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

//??? still no net

---

### Post by tommcd on 2009-07-24
> **desideratha said:**
> Hi;  still dont know how to disable all encryption on my router

You will have to consult your router's documentation for how to disable encryption. Usually, you would open a web browser (like firefox, for example) and go to 192.168.0.1, or possibly 192.168.1.1, then enter a password. If you have not changed the password, then it is the default password set by the manufacturer. Again, consult your router's documentation. Then you would go to the wireless tab in the router's configuration and set encryption to off, and click 'apply'.
If you don't have an owner's manual for the router, just google for the manufacturer's website and look up your router's documentation . You should be able to find a FAQ and documentation for how to access the router's configuration and change settings on it. If not, then run a google search for your router's make and model number and you should be able to find the info. Or, as a last resort, call the manufacturer's tech support.
As far as I know, most routers are shipped from the manufacturer without any encryption enabled for wireless. Did you, or someone else enable encryption on the router at some point? Did you use the software CD that came with the router to set up the wireless with encryption in Windows or something?

Your output from **sudo iwlist wlan0 scanning ** indicates it found 2 wireless access points:
1. "Motorola" 
2. "Colon 3770 Depto 91"
I assume "Motorola" is your router. Is that correct? iwlist scanning also indicates that the encryption key is on. This is likely why you can't get an IP address when you run: **sudo dhclient wlan0**
Your wireless is working because iwlist is able to find wireless access points. If you can disable encryption on the router you should be able to connect and get online. Then we can work on getting online with encryption.

---

### Post by desideratha on 2009-07-24
Hi thanks again. 
 Yes motorola is my router

I have never change the setting on the router, it was working fine before upgrading to 9.04 (in 8.10) after I upgraded I logged in to the newly installed distribution and it was working, then I run apt-get update, restart and only after that it stopped conneting to the net.

I'll try turning off encryption.

Thanks one more time.

---

### Post by desideratha on 2009-07-24
Hello 

when I type 192.168.1.1 or 192.168.0.1  I get Page load error message even if I do it in windows. 

Any ideas?

regards


*************************************

Never mind I talk to my admin, I needed  192.168.100.1

*********************************************

---

### Post by desideratha on 2009-07-24
OK, I disable encryption and ran codes again, this is the output (still no network connection), router is Pedro now...

Also I don't see any drivers for my wireless card on system-  administration- hardware drivers

andres@andres:~$ sudo modprobe iwl3945 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release. 

andres@andres:~$ sudo iwlist wlan0 scanning 
wlan0     Scan completed : 
          Cell 01 - Address: 00:14:A5:90:E5: DF 
                    ESSID:"Pedro" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=55/100  Signal level=-75 dBm  Noise level=-127 dBm 
                    Encryption key: off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=0000000125ba512d 
          
Cell 02 - Address: 00:1C:F0:3B:0A:2F 
                    ESSID:"San Francisco" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=57/100  Signal level=-74 dBm  Noise level=-127 dBm 
                    Encryption key: on 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000003ab94dab3 
          
Cell 03 - Address: 00:1C:F0:5C:F1:ED 
                    ESSID:"geepsy" 
                    Mode:Master 
                    Channel:9 
                    Frequency:2.452 GHz (Channel 9) 
                    Quality=38/100  Signal level=-86 dBm  Noise level=-127 dBm 
                    Encryption key: on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=0000007c23d71180 

  
andres@andres:~$ sudo iwconfig wlan0 essid Pedro 

andres@andres:~$ sudo dhclient wlan0 
There is already a pid file /var/run/dhclient.pid with pid 6419 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:19:d2:63:59:5d 
Sending on   LPF/wlan0/00:19:d2:63:59:5d 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

**************************

still no connection :-(

---

### Post by tommcd on 2009-07-25
> **desideratha said:**
> OK, I disable encryption and ran codes again, this is the output (still no network connection), router is Pedro now...
Also I don't see any drivers for my wireless card on system-  administration- hardware drivers
If you run **lsmod** in the terminal you should see iwl3945 in the output.
> **desideratha said:**
> 
andres@andres:~$ sudo dhclient wlan0 
**There is already a pid file /var/run/dhclient.pid with pid 6419** 

If you get the line I have outlined in bold, or something similar, then either reboot and try it again, or try running:
```
sudo rm /var/run/dhclient.pid
```
Make sure you type the file path exactly as it says in the output of "sudo dhclient wlan0". Then try "sudo dhclient wlan0" again.

Also, now that you have the encryption off, did you try just setting up the connection by going to: system > preferences > network connections? You should have a wlan0 listed in the wireless tab of the network connections applet window. 

Also, are you hooked up to the router via a wired connection while you are doing this? If so, disconnect the wired connection before you boot the computer. The wired connection may be getting the IP address and thus the wireless connection may not be able to get an IP address simultaneously.

EDIT: Since you stated your wireless was working fine in Ubuntu 8.10, and then it broke after the upgrade to Ubuntu 9.04, I'm starting to think something got screwed up during the upgrade.
(This is why I always do a clean install with new versions of Ubuntu instead of a dist-upgrade). 

Your wireless is working, since you can scan for access points. I'm not sure why you can't connect at this point.

---

### Post by desideratha on 2009-07-25
EDIT: Since you stated your wireless was working fine in Ubuntu 8.10, and then it broke after the upgrade to Ubuntu 9.04, I'm starting to think something got screwed up during the upgrade.
(This is why I always do a clean install with new versions of Ubuntu instead of a dist-upgrade). 

Your wireless is working, since you can scan for access points. I'm not sure why you can't connect at this point.[/QUOTE]

Hi, yes I can see my wireless card, however still cant connect.

I am thinking on doing a clean install at this point. However, I will loose my data, right? 

Regards

---

### Post by tommcd on 2009-07-25
> **desideratha said:**
> 
I am thinking on doing a clean install at this point. However, I will loose my data, right? 

If you have a separate home partition then all your data will be safe. If you do not have a separate home partition, then doing a clean install is a good time to create one. You will need to backup all your data first though.

---

### Post by desideratha on 2009-07-26
tommcd,

Thank you for your tremendous help, I ended up doing a clean insall, net is working now, I copied my data into an external drive. 

One last thing, If you don´t mind, Could you intruct me on how to do a separate home partition?

Thanks again,

If you'd like, visit my home page at [http://guitarte.blogspot.com](http://guitarte.blogspot.com)

best regards

---

### Post by tommcd on 2009-07-27
> **desideratha said:**
> 
One last thing, If you don´t mind, Could you intruct me on how to do a separate home partition?

The easiest way to make a separate home partition is to create it during the partitioning part of an Ubuntu install. You just choose manual partitioning and set up a partition scheme something like this:
-------------------------------------------------------------------------------------------------
1. root = 10-14GB should be way more than enough. You could go with less if you are tight on space. A default Ubuntu install is only about 3GB or so.
2. swap = 1GB.
3. /home = the rest of your hard drive.
--------------------------------------------------------------------------------------------------------
To create a separate home partition after you have already installed Ubuntu, see this page from Asiyu's site:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by desideratha on 2009-07-27
Thanks, I'll give it a try.
Also, I'll mark this thread as solved.

Regards

---

