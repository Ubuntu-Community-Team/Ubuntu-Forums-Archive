---
title: "Wifi card almost working? Not sure."
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by Vega on 2006-02-13
alright I installed ndiswrapper and I got the inf file from the wireless driver folder. I'm using a Dell D505 celeron -m with a dell true mobile 1350. I select the card and it sees my router and I type in password and connect via DHCP. but when I hit on FF I can't connect to the net.

[[IMG]http://img104.imageshack.us/img104/4639/screenshot7ki.th.png[/IMG]](http://img104.imageshack.us/my.php?image=screenshot7ki.png)

any suggestions would be helpful.

UPDATE: I'm posting everything I got from the other articals and commands. I've tried everything but no go.
> 
z@REDSUNS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

z@REDSUNS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:D2:9E:F8
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fed2:9ef8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1108886 (1.0 MiB)  TX bytes:214519 (209.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:153556 (149.9 KiB)  TX bytes:153556 (149.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0B:7D:10:A4:0B
          inet6 addr: fe80::20b:7dff:fe10:a40b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:fcffc000-fcffdfff

z@REDSUNS:~$ arp -a
? (192.168.1.254) at 00:16:B6:05:97:A2 [ether] on eth0
z@REDSUNS:~$ sudo lshw -C network
Password:
 z@REDSUNS:~$   
bash: thunder1: command not found
z@REDSUNS:~$ sudo lshw -C network
Password:
  *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@01:03.0
       logical name: wlan0
       version: 03
       serial: 00:0b:7d:10:a4:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fcffc000-fcffdfff irq:5
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 81
       serial: 00:0f:1f:d2:9e:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A ip=192.168.1.104 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:fcffe000-fcffefff ioport:ecc0-ecff irq:11
z@REDSUNS:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device


---

### Post by moephan on 2006-02-14
Can you ping? Does firefox work over wired ethernet?

Could it be IPv6 issues?

Try this:

1. Open firefox and type &#8220;about:config&#8221; in the address box.
2. Search for "IPv6" and then set network.dns.disableIPv6 to true.

HTH

Cheers, Rick

---

### Post by tehwa on 2006-02-14
```
wlan0 Link encap:Ethernet HWaddr 00:0B:7D:10:A4:0B
inet6 addr: fe80::20b:7dff:fe10:a40b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Memory:fcffc000-fcffdfff
```
You don't have an IP address, I think your DHCP requests are failing. When you:
```
sudo ifdown wlan0
sudo ifup wlan0
```
Does the output give you clues about the outcome fo the DHCP request? Does it time out?

---

### Post by pnael on 2006-02-14
wlan0 IEEE 802.11g **ESSID:Off/any**
Mode:Managed Frequency:2.412 GHz **Access Point: 00:00:00:00:00:00**

You are not connected to any WLAN. You wifi cardis  correctly detected but you need to setup your connection to the wifi network.
If you are using WEP :
sudo iwconfig wlan0 essid your_ssid_needs_to_be_here
sudo iwconfig wlan0 key your_wep_key_here
sudo ifup wlan0

---

### Post by Vega on 2006-02-14
z@REDSUNS:~$ sudo iwconfig wlan0 essid IISD_WLAN
z@REDSUNS:~$ sudo iwconfig wlan0 key 00409646AB
z@REDSUNS:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
z@REDSUNS:~$


this is on my school wlan(don't really care about the pass to the router). I still get the same thing. On wired FF does indeed work.

z@REDSUNS:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5894

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0b:7d:10:a4:0b
Sending on   LPF/wlan0/00:0b:7d:10:a4:0b
Sending on   Socket/fallback

---

### Post by pnael on 2006-02-14
It seems that setting the ssid and the WEP key works fine since you do not get any error message, please run iwconfig
to check if you are connected to an AP :
$ iwconfig wlan0
wlan0      IEEE 802.11g  ESSID:"ssidnael"
          Mode:Managed  Frequency:2.437 GHz  **Access Point: 00:13:10:83:D4:B7**
          Bit Rate=48 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=82/100  Signal level=-48 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

You should have the AP mac address to which you are connected.
The next step is to get an IP address. You already have a dhclient   process running for wlan0. That's why you get an error message when running ifup.

After you are connected to an AP, run ifconfig wlan0 to see the current interface. If you don't have an IP. You can kill the dhclient process.
>sudo killall dhclient3 
It will kill all you dhclient process, you will loose all your dhcp IP address for all your interfaces (it's jsut for test)
Then to get back an IP address :
>sudo dhclient wlan0

If you get an IP it's done. The next step is to have it done automaticaly. The ssid/key can be set via /etc/network/interface.
see "man wireless" to have the command list.

---

