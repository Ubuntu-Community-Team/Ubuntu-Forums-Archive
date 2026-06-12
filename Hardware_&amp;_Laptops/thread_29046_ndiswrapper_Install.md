---
title: "ndiswrapper Install"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by Amdmhz on 2005-04-22
HI all. I searched for the answer before I posted and didn't find it. I did an apt-get ndiswrapper-source and it said I had the newest version.

So I did a ndiswrapper -i bcmwl5.inf and it tells me ndiswrapper command not found. I am in root when I am typing the command. So I guess it did not install? When I try to apt-get again it just tells me I have the newest verison. I read the how tos and still get this error. Could someone help me figure this out? I am running hoary.

Thanks

---

### Post by XDevHald on 2005-04-22
If you don't have the ndiswrapper-utils then you will need that as it is needed for the bcmwl5 to run, which is why when I ran the command **ndiswrapper -i bcmwl5.inf** it gave me [b]bcmwl5 is already installed. Use -e to remove it

[/b]Check to see if you have the utils for ndiswrapper and then try the command again.

---

### Post by Amdmhz on 2005-04-22
Hi Doc, Thanks that installed the other packages. This is what it gave me when I typed ndiswrapper -i bcmwl5.inf:

root@Laptop:/home/amdmhz # sudo ndiswrapper -i bcmwl5.inf
ls: /etc/ndiswrapper: No such file or directory
Installing bcmwl5
Forcing parameter RadioState|0 to RadioState|1

Don't know if this is what it is suppose to do or not.

---

### Post by XDevHald on 2005-04-22
Ok, you'll need to create the directory for ndiswrapper by root do: **mkdir /etc/ndiswrapper **

Then follow the command as you did before.

---

### Post by Amdmhz on 2005-04-22
Thanks again for your help. This is what I get now which is good.

root@Laptop:/etc/ndiswrapper # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
root@Laptop:/etc/ndiswrapper #

Then I do a iwconfig:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

now I am not sure where to go from here. I don't see an IP address for wlan0

Thanks again

---

### Post by XDevHald on 2005-04-22
Nice to see you're on the right track here :D good job by the way, next step is type **ifconfig **this will display **lo **& **eth0 **IP's and submasks etc...

---

### Post by Amdmhz on 2005-04-22
Thanks Doc, When I type ifconfig I get :

root@Laptop:/etc/ndiswrapper # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:7F:73:FC:68
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7fff:fe73:fc68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:668641 (652.9 KiB)  TX bytes:286563 (279.8 KiB)
          Interrupt:10 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:909518 (888.2 KiB)  TX bytes:909518 (888.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:49:0F:E0
          inet6 addr: fe80::290:4bff:fe49:fe0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d4002000-d4003f

still no IP address for Wlan0 so I dont know how to test my link. is there a way to set an IP for wlan0? Or am I off track of what to do? Thanks again for all your help. :grin:

---

### Post by XDevHald on 2005-04-22
The following steps MIGHT work

To bring the wlan0 up in use type: 

**Step 1 **dhclient wlan0[b]

Step 2 [/b]ifconfig wlan0 up **or** ifup wlan0


Another quick note, If you want to do it by hand, you will need to add the following to /etc/network/interfaces. since your wireless interface is wlan0, but it may be eth0 or eth1, so change it as necessary.
 
 
 auto wlan0
 iface wlan0 inet dhcp
     wireless_essid MyESSID
 
 
 If you need a fixed IP address, use the following:
 
 
 auto wlan0
 iface wlan0 inet dhcp
     address 192.168.0.1
     netmask 255.255.255.0
     gateway 192.168.0.254
     wireless_essid MyESSID

Also note to replace the address, netmask, and gateway ip addresses with the ones that you would normally use.

---

### Post by Amdmhz on 2005-04-22
when I run dhclient this is what I get:

root@Laptop:/etc/ndiswrapper # dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:49:0f:e0
Sending on   LPF/wlan0/00:90:4b:49:0f:e0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@Laptop:/etc/ndiswrapper #

hmm...do you think If I manual set an IP address for wlan0 that might work? If so, how would I set this?

Thanks Doc, your help is appreciated.

---

### Post by XDevHald on 2005-04-22
Not a problem Amdhmz, that's what we do best ;) look 2 posts above and see the manual config for this setup, it should work.

---

### Post by Amdmhz on 2005-04-22
well Doc, I made those changes decided to reboot and boom now it lost wlan0, hehehe... Hmmm.. Don't know why but it did.

---

### Post by Amdmhz on 2005-04-22
Well, Doc. I have great signal strength, static IP but I can not ping my router. So I am very close. Any suggests.

Thanks :razz:

---

### Post by XDevHald on 2005-04-22
very interesting....here's a howto for this, I should've gave it to you before but, sorry to hear about that outage :(

[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)

I hope it gets fixed, keep me posted!

---

### Post by Amdmhz on 2005-04-22
Close Doc..... Just cant ping my router ...  :razz:

---

### Post by XDevHald on 2005-04-22
If you have a manual book that came with the router, then it will give you the IP information there. Having a hard time picking my brain on an easy question like this one :(

If not, then check out [http://ubuntuforums.org/archive/index.php/t-25557.html](http://ubuntuforums.org/archive/index.php/t-25557.html)

***Doc goes to grab a bag of ice for his head* ;)**

---

### Post by Amdmhz on 2005-04-23
Well Doc, I am to the point where I have signal strength, on the right Channel but when I look at the connected to network it says any instead of my AP. I have done, iwconfig wlan0 essid Amdmhz but it does not seem to take. Any ideas?

---

### Post by Sully on 2005-07-03
I have had recent success with these issues, so if it's not too late, your situation is one of several traps that can lead to total frustration.  I'm using ndiswrapper v. 1.2 with a Linksys WPC54g wireless PC card NIC on a IBM Thinkpad A21m.  The wireless NIC is working nicely for me at this point, btw in Libranet (Debian Sarge), kernel 2.6.8.

The ndiswrapper kernel module will NOT load either at boot or with modprobe until AFTER the Windows XP NIC driver is loaded:
```
ndiswrapper -i /path/to/winXPdriver.inf
``` 
Add ndiswrapper to /etc/modules if it's not already there.

When you first get iwconfig to recognize your wireless NIC, if you are using WEP encryption (I am) the FIRST thing you must do is set the key !  The command looks like:   ```
iwconfig wlan0 key XXXXXXXXX
``` (key is in hex)
Then all other changes will be accepted and will appear in the output of  ```
iwconfig wlan0
``` THEN you will be able to ping your router!

The other trap that took me weeks to figure out:  my wireless NIC only worked after I disabled the primary, wired NIC with ```
ifconfig eth0 down
```   Obviously, I also ran ```
ifconfig wlan0 up
``` This is probably due to some error on my part in my routing table.

You have to set the IP address of the wireless NIC through ifconfig !
```
ifconfig wlan0 192.168.1.xx netmask 255.255.255.0
```

Lastly, don't forget to use route !
```
route add default gw 192.168.1.1 wlan0
``` 

To make the changes permanent you have to make an entry for wlan0 in /etc/network/interfaces.  Check the man page and your current file, and it will be apparent how to do this.

Good luck!
Sully

---

