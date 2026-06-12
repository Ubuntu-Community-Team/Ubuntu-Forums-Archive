---
title: "centrino wlan 2200BG"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by sabin on 2005-07-18
hi guys I'm trying to establish a wlan connection running hoary..

seems my wlancard has been detected on install (I'm using the intel wireless pro 2200BG with a centrino laptop) my problem is that it seems like everything works fine. I can list the ap's with "iwlist eth1 scan" I can configure the interface I even seem to get a connection to the ap by entering the right essid, enc, etc... though I cannot ping any ip nor host in the lan. here some outputs:

[PHP]root@lappy:~ # ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:6D:58:CD
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe6d:58cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:869 errors:0 dropped:44 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:348 (348.0 b)
          Interrupt:18 Base address:0x2000 Memory:e0206000-e0206fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)



root@lappy:~ # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Linuxp-G"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:17:CC:E9:82
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:0118-B29F-my-secret-839C-key-here   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0

sit0      no wireless extensions.

root@lappy:~ # iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:12:17:CC:E9:82
                    ESSID:"Linuxp-G"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Extra: RSSI: -33  dBm
                    Extra: Last beacon: 7ms ago[/PHP]

see what I mean? The gateway was set in the control center... but it doesn't work! anyone an idea what could be wrong here?

greets!

---

### Post by sabin on 2005-07-18
channel, essid, enc, dns, gateway were set correct, though I wonder where to set the gateway instead of the controlcenter.

here the output when I try to ping the ap:

[PHP]root@lappy:~ # ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1)
56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
[/PHP] 

I wonder why I get a reply from 192.168.1.2 (which is $wlan interface) even if I ping 192.168.1.1...

it's so strange!

sorry for the crossposting, seems I choosed the wrong section..

---

### Post by Davor281 on 2005-07-18
Hello! 

First your second post.

You are not getting ping from your wlan, the message which you receive means exactly what it says - "From" which means pinging from to, and 192.168.1.2 is your wlan IP address.

Now to the first post.

Have you set the gateway and DNS adrresses correctly? No typo?
Try to ping your gateway, any reply?
Try to ping your access point or router, any reply?

Also, try to change your IP to 192.168.0.2
As far as I know, access points or routers usually have the default 192.168.0.1 adrress, at least my access point does.

Hope I was of some help.

ENjoY!

Davor.

---

### Post by sabin on 2005-07-18
dns and gateway are correct.. pinging the wlan router 192.168.1.1 gives the same output like pinging the router (server) 192.168.0.1 does. No my wlan router has the ip 192.168.1.1 which is the ip I set as GW. I have no idea why it doesn't work.. dns is fine, gateway is set, interface is fine (ip, essid, enc, channel, key mode, etc.) according to kwifimanager I do have a connection though.. no clue how to go on!

greets

---

### Post by luca_linux on 2005-07-18
Are you sure you don't have MAC Address Filtering or any other block on your router?

---

### Post by sabin on 2005-07-18
well I use the same laptop with windoof XP, same mac, same key... and it works.. it must be some settings in ubuntu or something!

---

### Post by luca_linux on 2005-07-18
Try to update the ipw2200 driver.
Just follow this HowTo: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

---

### Post by jc3835 on 2005-07-18
I have a thread that I outline my issues and resolutions with the 2200BG...
[http://ubuntuforums.org/showthread.php?t=45142](http://ubuntuforums.org/showthread.php?t=45142)
Make sure you're inputting the key as the alphanumeric and not as s:passphrase... that gave me issues. make sure you have MAC address filtering issues resolved, like someone else said.
then do:
```
dhclient eth1
``` 
and see if your router accepts your adapter.

---

