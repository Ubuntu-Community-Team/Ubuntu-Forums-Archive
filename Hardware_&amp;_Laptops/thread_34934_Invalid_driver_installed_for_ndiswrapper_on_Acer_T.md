---
title: "Invalid driver installed for ndiswrapper on Acer Travelmate 2308"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by ssck on 2005-05-16
Hi ALL,

I am having a problem with my wireless card.I get this error after installing the driver :

Installed ndis drivers:
neti2220        invalid driver!

This is what was detected by Ubuntu :

0000:02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

Am I using the wrong driver ? I got this driver from my Acer CD.

Can anybody help me ? I am desperate to get my wireless up.

Thanks.

---

### Post by jacobo on 2005-05-17
make sure you're using the windows XP version of the driver from your acer cd, i've found for some reason it tends to work better than using the generic driver. 

you also want to use ndiswrapper on the .inf file included with the driver, not the actual .sys or .dll file that contains the actual driver data.

you've probably tried this, but make sure ubuntu hasn't already configured it...check under System > Administration > Networking, for a wireless connection, in ubuntu the only wireless cards that have ever needed addition driver configuration are generally usb cards, at that i've seen.

---

### Post by ssck on 2005-05-17
[QUOTE=jacobo]make sure you're using the windows XP version of the driver from your acer cd, i've found for some reason it tends to work better than using the generic driver. 

you also want to use ndiswrapper on the .inf file included with the driver, not the actual .sys or .dll file that contains the actual driver data.

you've probably tried this, but make sure ubuntu hasn't already configured it...check under System > Administration > Networking, for a wireless connection, in ubuntu the only wireless cards that have ever needed addition driver configuration are generally usb cards, at that i've seen.[/QUOTE]

hi jacobo,

i checked under system > administration > networking, there are only settings configured, modem and ethernet (eth0). i 

i used the xp neti2220.inf file and it still gives me the same error.is there anything else i can do ?
 
appreciate your help as i find ubuntu very easy to use eventhough i have been a windows user for years.

one question though : how do i ensure that the wireless card is already switched on ? is it under irq ? if so, how do i check ? how do i switch it on ?

thanks again.

---

### Post by ssck on 2005-05-18
[QUOTE=ssck]hi jacobo,

i checked under system > administration > networking, there are only settings configured, modem and ethernet (eth0). i 

i used the xp neti2220.inf file and it still gives me the same error.is there anything else i can do ?
 
appreciate your help as i find ubuntu very easy to use eventhough i have been a windows user for years.

one question though : how do i ensure that the wireless card is already switched on ? is it under irq ? if so, how do i check ? how do i switch it on ?

thanks again.[/QUOTE]


i finally managed to get the wireless up.it seems like i have to copy not just the inf files but also all other related files such as sys files, etc into the same folder.

now, the wireless is lighted up on my laptop.however, i don't seem to be able to get connected on my access point.

my settings are these :

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:7E2C-5A33-88   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


the error that i am getting is :

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0e:9b:9b:c5:13
Sending on   LPF/wlan0/00:0e:9b:9b:c5:13
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Anyone who has faced the same problem ? I have no problems connecting to the access point using win xp.



what seems to be the problem ?

---

### Post by alessios on 2005-05-18
Same problem for me (travelmate 2300 serie with INPROCOMM IPN2200)

Driver load correctly and ndiswrapper tell me that hardware is present.

The problem is that most parameters could'nt be modified throught iwconfig.

I'm using Kubuntu 5.04, stock ndiswrapper, stock kernel, Winxp driver coming from acer installation cd (A802)

Any idea?

Alessio

---

### Post by ssck on 2005-05-19
[QUOTE=alessios]Same problem for me (travelmate 2300 serie with INPROCOMM IPN2200)

Driver load correctly and ndiswrapper tell me that hardware is present.

The problem is that most parameters could'nt be modified throught iwconfig.

I'm using Kubuntu 5.04, stock ndiswrapper, stock kernel, Winxp driver coming from acer installation cd (A802)

Any idea?

Alessio[/QUOTE

i put the parameters thru the system -> network settings


i am having problems with the access point.i don't seem to be able to ping the access point.it gives me a 'destination not found' error.

i put in a fixed ip add, and fixed gateway.

any ideas ?

---

### Post by alessios on 2005-05-19
I have really no idea... my brother managed to make it works in Ad-hoc mode in the past, if i manage to recall his configuration i'll make you know.
The strange thing is that other people claim that the card works with the very same procedure we follow, while other report the same problems...

This post 

[http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=233&start=0&postdays=0&postorder=asc&highlight=](http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=233&start=0&postdays=0&postorder=asc&highlight=).

suggest that the problem is encryption-related, but i tried all kaind of configuration/driver version/ndiswrapper version/you name it without luck...

---

### Post by ssck on 2005-05-19
[QUOTE=alessios]I have really no idea... my brother managed to make it works in Ad-hoc mode in the past, if i manage to recall his configuration i'll make you know.
The strange thing is that other people claim that the card works with the very same procedure we follow, while other report the same problems...

This post 

[http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=233&start=0&postdays=0&postorder=asc&highlight=](http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=233&start=0&postdays=0&postorder=asc&highlight=).

suggest that the problem is encryption-related, but i tried all kaind of configuration/driver version/ndiswrapper version/you name it without luck...[/QUOTE]


the access point that i usually use does not have wep.i put in the exact essid name, with a fixed ip, and gateway that i see in win xp but still it gets a destination not found error .... it is very frustrating ...

the access point is linksys.

anyone has any idea how to fix this ??????

i am really confused ??? you see the notebook's wireless indicator coming on but you can't get connected ...

---

### Post by alessios on 2005-05-20
\\:D/ Got it!

Found this package

[http://rpm.pbone.net/index.php3/stat/4/idpl/1756488/com/driver-ipn2220-2.10.03.2004-1ark.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1756488/com/driver-ipn2220-2.10.03.2004-1ark.i586.rpm.html)

which provide a winxp driver suitable for ndiswrapper, converted it with

sudo alien --to-deb driver-ipn2220-2.10.03.2004-1ark.i586.rpm 

and installed the resulting .deb with dpkg -i

Now loading the driver with ndiswrapper and setting the ssid works (not yet tried with WEP)

HTH,
Alessio

---

### Post by alessios on 2005-05-20
Update: works also with WEP enabled

Bye,
Alessio

---

### Post by ssck on 2005-05-21
[QUOTE=alessios]\\:D/ Got it!

Found this package

[http://rpm.pbone.net/index.php3/stat/4/idpl/1756488/com/driver-ipn2220-2.10.03.2004-1ark.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1756488/com/driver-ipn2220-2.10.03.2004-1ark.i586.rpm.html)

which provide a winxp driver suitable for ndiswrapper, converted it with

sudo alien --to-deb driver-ipn2220-2.10.03.2004-1ark.i586.rpm 

and installed the resulting .deb with dpkg -i

Now loading the driver with ndiswrapper and setting the ssid works (not yet tried with WEP)

HTH,
Alessio[/QUOTE]

hi alessio thanks for helping.

these are my settings in the interfaces file :

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

# The primary network interface
iface eth0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1


iface wlan0 inet static
wireless_keymode open
wireless_mode managed
#wireless_nick REPLACE WITH YOUR HOST NAME
address 192.168.2.239
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 202.188.0.133
wireless-essid Hex3
wireless-key open

auto wlan0


auto eth0

the problem is in the iwconfig file, the essid is not updated.when i try to update it manually, it doesn't work.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

in the ifconfig file, these are my settings :

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:81:A4:4F
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe81:a44f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1157316 (1.1 MiB)  TX bytes:205930 (201.1 KiB)
          Interrupt:6

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1117546 (1.0 MiB)  TX bytes:1117546 (1.0 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:9B:C5:13
          inet addr:192.168.2.239  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe9b:c513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e0203000-e02037ff


i am really not sure what is the problem.the card and router definitely works in win xp.what else can i do ? what are your settings ?

---

### Post by ssck on 2005-05-21
hi allesio,

thank you for your help.it is ok now.

regards  :smile:

---

