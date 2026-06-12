---
title: "wifi trouble...big shock i know"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by quezlar on 2006-01-09
ok so im pretty new to ubuntu and wouldnt have posted except ive spent several days  working on this and i cant seem to get it. that bieng said

 ive got my linksys wpc54gx installed in breezy badger with ndiswrapper on a compaq Evo N610c notebook
 It says it works properly.

>  quezlar@ubuntu:~$ sudo ndiswrapper -l Password:
Installed ndis drivers:
netani  driver present, hardware present

the lights light up, it says wlan0 active in network settings
 however i have no internet connection. i cnat even ping my router

when i iwconfig i get

> quezlar@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Auto  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:100/100  Signal level:-57 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


and when i iwlist scan i get 

> 
quezlar@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:4C:AF:15
                    ESSID:"Linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-19 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.

i tried setting up the card to talk only to my router (i forget the command ) 
at any rate iwconfig then gives me
 
> quezlar@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Auto  ESSID:"Linksys"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:10:4C:AF:15
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


but still i have no connection any help would be greatly appreciated
thank you 
quezlar

---

### Post by redactech on 2006-01-09
please give us the result of following command :

cat /etc/network/interface

cat /etc/resolv.conf

and 

ifconfig

---

### Post by quezlar on 2006-01-09
you must mean cat /etc/network/interfaces
cat /etc/network/interface has no effect 
at any rate 

> quezlar@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface wlan0 inet dhcp
wireless-essid linksys

auto wlan0

iface eth0 inet dhcp

auto eth0


/etc/resolv.conf

> quezlar@ubuntu:~$ cat /etc/resolv.conf
domain linksys
nameserver 192.168.1.1

and finally

if config

> 
quezlar@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2180045 (2.0 MiB)  TX bytes:2180045 (2.0 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:EF:B2:CC
          inet6 addr: fe80::212:17ff:feef:b2cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:10800000-1087ffff



thank you 
quezlar

---

### Post by redactech on 2006-01-09
You don't have an IP address !!!

check if the linksys is in router mode (in advanced networking tab)
add wireless-mode managed under wlan0 in /etc/network/interfaces

try to get an ip with sudo dhclient wlan0 or restarting the network (sudo /etc/init.d/networking restart) if that does not work

---

### Post by quezlar on 2006-01-09
i assume you mean check to see if the router is in router mode...well i dont have an advanced networking tab but it works fine with my windows systems if that tells you anything.

added "wireless-mode managed"

dhclient comes back 
> quezlar@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 8013
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:12:17:ef:b2:cc
Sending on   LPF/wlan0/00:12:17:ef:b2:cc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

its seems to be searching 255.255.255.255
where my acual subnet mask is 255.255.255.0 
i dont know
quezlar

---

### Post by redactech on 2006-01-09
ok in any windows system working with wireless type in command line

ipconfig /all

and give us the result

I'm a bit stumped
meanwhile try to add ndiswrapper in the modules files and reboot your laptop

---

### Post by quezlar on 2006-01-09
>  
E:\>ipconfig /all
 
Windows IP Configuration
 
        Host Name . . . . . . . . . . . . : thelaptop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
 
Ethernet adapter Local Area Connection:
 
        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Intel(R) PRO/100 VM Network Connecti
on
        Physical Address. . . . . . . . . : 00-08-02-D9-1D-D2
 
Ethernet adapter Wireless Network Connection:
 
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Wireless-G Notebook Adapter with SRX
 
        Physical Address. . . . . . . . . : 00-12-17-EF-B2-CC
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Monday, January 09, 2006 11:45:50 PM
 
        Lease Expires . . . . . . . . . . : Tuesday, January 10, 2006 11:45:50 P
M
 

im not sure what you mean by adding ndiswrapper into the modules files

---

### Post by quezlar on 2006-01-09
i should add that ndiswrapper is allready in /lib/modules/2.6.12-9-386/kernel/drivers/net 
if thats what you mean

---

### Post by quezlar on 2006-01-10
well i really appreciate the help even though we didnt get it working
thank you

---

### Post by ruudiculus on 2006-01-10
Hi,

In the interfaces file you might want to add the line in bold
```
# wireless card
iface wlan0 inet dhcp
 wireless_essid linksys
 **wireless_keymode open**
```

My wireless card needed to know that the keymode was open (and not restricted) explicitly. After that I finally got a connection.

Hope it helps.

---

### Post by redactech on 2006-01-10
just write ndiswrapper in the following file

/etc/modules

"sudo vi /etc/reboot"

and reboot

---

### Post by quezlar on 2006-01-10
ok i added  wireless_keymode open
seemingly no effect
thank you anyway 
any other thoughts?

---

### Post by quezlar on 2006-01-10
thats what i though you ment i
ndiswrapper has been added
still not functioning

---

### Post by quezlar on 2006-01-11
So yea anybody have any ideas?

I find it hard to believe ive stumped all you ubuntu gurus :)

Well any help would be greatly appreaciated

---

### Post by ys4_sinau on 2006-01-11
hello quezlar

i think if you don't get ip from dhcp why you don't try manually

#sudo ifconfig wlan0 192.1.....

you must sure ip that you chooce didn't use in other computer.

---

### Post by ruudiculus on 2006-01-12
I think you should use **iwconfig** and just try to set it up using all the options iwconfig has (*# man iwconfig* gives you all the options). With that you should be able to set it up, since your hardware is successfully 'driven'. You can use the *iwlist* command right? So it must be a matter of configuration.

After configurating manually using *iwconfig* you should know which options are needed and those you can put into the */etc/network/interfaces* file.

Do you use WEP encryption? (I could see that in your Windows-ipconfig results). If so type:
```
iwconfig wlan0 enc *WEP-encryption code* open
```

For the rest try to configure wlan0 by not using too much *default* and *auto* settings. (So, use a known channel, transmit rate etc.) The only auto-thing should be configuring the connection with DHCP.

That's all I can help you with for the moment. Ow and: disable eth0 because I don't know if having two connections at a time will result in confused files (e.g. resolv.conf ).

Good luck!

---

### Post by quezlar on 2006-01-12
i allways disable eth0 when i try to get wlan0 working
i notice when i do iwlist rate it tells me there ar 2 avalible rates 9 mb/s and 9 mb/s.....and mycurrent bitrate is 108 Mb/s
no as far as i know "sudo iwconfig wlan0 rate 9M" shoudl change it
it however seems to have no effect
any ideas?
btw i tried configred everythign else manually and still dhclient does't connect
and idea whay dsclent says its trying o connect on 255.255.255.255?

---

### Post by ruudiculus on 2006-01-13
Before getting an IP address from your gateway/router/Internet Provider through the DHCP method, your computer first must announce on the network that it is there.

You know an IP address is somewhat like a telephone number (every computer in a network has one uniquely assigned). So the 255.255.255.255 IP address isn't an adress for just one computer. Instead it represents all computers in a given network (behind a router for example).

So to get a DHCP connection your computer announces that it is powered on and that it wants a connecion. Every computer in your network can (and maybe will) react to that (sending some sort of package) and the one(s) that can provide you with an IP address (your router/gateway/Interet Provider) sends your computer a different package in which it tells your computer that it might be able to connect to that IP address (of the router/gateway/ISP) and get a IP address from. So then the two parties send eachother some more packages (strictly between those computers so no 255.255.255.255 anymore, but between 192.168.1.1 and 192.168.1.50 for example) until all needed information (DNS1/DNS2/IP address/Gateway/netmask etc.) is there in your computer to use to connect to the Internet.

Quite a story right? Well the bottom line is that it's normal for you to see your card initially broadcasting(because that's what it's called)  to 255.255.255.255.

And about your problem: can you give us a list of all the settings you use in windows maybe? Including all wireless settings (from the System/Device Manager) etc. Maybe that'll bring us a step closer to a solution.

Till soon,

---

### Post by quezlar on 2006-01-17
sorry i didnt getback sooner been working alot hope you all didnt give up on me

not really sure which windows settings to include..works first try wits default settings in windows.

well here is everythign from device manager

PCI bus 3, device 0, function 0
802.11 mode all
802.11d support on
802.11e support eDCA
ack polocy immediate
background scan period 5000 milliseconds
enhanced rates on
fragmentation threshold 2000
longretrylimit 0
network density adaptive
rts threshold 2347
short retry limit 0
tx power high
Wi-Fi multimedia (wmm) support eDCA
driver (same as in ubuntu) linksys 1.4.4.183 microsoft windows hardware compatiility publ............wni6000.bin.....wnihdd51.sys
device instance id pci\ven_17cb&dev_0001&subsys_00371737&rev_01\5&193dd4c4&0&0030f0
hardware ids
PCI\VEN_17CB&DEV_0001&SUBSYS_00371737&REV_01
PCI\VEN_17CB&DEV_0001&SUBSYS_00371737
PCI\VEN_17CB&DEV_0001&CC_020000
PCI\VEN_17CB&DEV_0001&CC_0200

compatible ids
PCI\VEN_17CB&DEV_0001&REV_01
PCI\VEN_17CB&DEV_0001
PCI\VEN_17CB&CC_020000
PCI\VEN_17CB&CC_0200
PCI\VEN_17CB
PCI\CC_020000
PCI\CC_0200
matching device id
pci\ven_17cb&dev_0001&subsys_00371737
service airgo
enumerator PCI

capabilities CM_DEVCAP_REMOVABLE

devnode flags DN_DRIVER_LOADED
DN_STARTED
DN_DISABLEABLE
DN_REMOVABLE
DN_NT_ENUMERATOR
DN_NT_DRIVER
class installer NetCfgx.dll,NetClassInstaller
current power state D0
power capabilities  
PDCAP_D0_SUPPORTED
PDCAP_D1_SUPPORTED
PDCAP_D2_SUPPORTED
PDCAP_D3_SUPPORTED
power state mappings
S0 -> D0
S1 -> Unspecified
S2 -> Unspecified
S3 -> D3
S4 -> D3
S5 -> D3
memory range FFA60000 - FFA7FFFF
memory range FFA80000 - FFaFFFFF
IRQ 11
  

dont know if this helps but any help would be great
thank you

---

### Post by kingtutt on 2006-06-20
I know this is really late but if you're still having problems....sounds exactly like what i was going through....
try this:
cat etc/resolve.conf
anyway...maybe check your nameserver and try adding 
nameserver "Your nameserver"
Sounds like your DNS isn't reconized...
Hope this helps.

---

