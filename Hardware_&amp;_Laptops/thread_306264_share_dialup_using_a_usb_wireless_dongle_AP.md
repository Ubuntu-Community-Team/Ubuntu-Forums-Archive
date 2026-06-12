---
title: "share dialup using a usb wireless dongle AP?"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by wargames on 2006-11-24
ok, I have a Airlink AWLL3026 USB wireless dongle that I would like to use as an access point so that other PC's can share the dialup internet access through this laptop.

So it's:
Internet-->dialup modem-->latop-->airlink usb wireless AP-->other PC's, etc.

I seems that Dapper doesn't like this AWLL3026 so I followed this How to in order to get it to recognize it.
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

I even tried this How to as well:
[http://www.ubuntuforums.org/showthread.php?t=195259](http://www.ubuntuforums.org/showthread.php?t=195259)

Just to try to get it to work. Nothing has worked so far. It seems to say that it's active in Networking but I cannot connect with this USB dongle. The light on it just keeps flashing, but it never seems to work. I tried seting a static IP address 196.186.0.2 and subnet 255.255.255.0 and still nothing. So how do I get this USB wireless dongle to act like a AP and share my dialup internet connection?

I told Firestart that my Internet connection is the PPP0 dialup and my Local connection is the wlan0. And I checked the ICS option.

So how do I finish setting this up.

Be gentle, I'm still learning. :)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"wlanap"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

after I sudo iwconfig wlan0 mode master

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"wlanap"
          Mode:Master  Frequency=2.462 GHz  Access Point: 00:11:A3:02:9D:08
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:440 (440.0 b)  TX bytes:440 (440.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:209.131.234.121  P-t-P:209.131.232.11  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5092 errors:41 dropped:0 overruns:0 frame:0
          TX packets:5428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:5285943 (5.0 MiB)  TX bytes:416472 (406.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:A3:02:9D:08
          inet addr:196.168.0.2  Bcast:196.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Now what?

---

