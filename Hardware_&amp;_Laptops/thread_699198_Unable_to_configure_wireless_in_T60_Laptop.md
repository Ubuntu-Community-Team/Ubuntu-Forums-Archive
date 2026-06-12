---
title: "Unable to configure wireless in T60 Laptop"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by debtaru on 2008-02-17
I am using Lenovo T60 Laptop. I am unable to configure my wireless card.

I get this message :

debtaru@debtaru-laptop:~/Desktop$ sudo dhclient ath0
[sudo] password for debtaru:
There is already a pid file /var/run/dhclient.pid with pid 7993
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7d:b8:b4:d7
Sending on   LPF/ath0/00:19:7d:b8:b4:d7
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 


When I do a iwconfig I get the following mesage:

debtaru@debtaru-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"deb"  Nickname:""
          Mode:Managed  Frequency:5.2 GHz  Access Point: 00:90:4C:7E:00:29   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:72  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also the Wireless light is not enabled.
Can anyone help me to get this configured?

---

### Post by Yellow Pasque on 2008-02-17
Go to System -> Administration -> Software Sources and make sure the all the boxes are checked on the first tab. Now, go to System -> Administration -> Restricted Driver Manager
Does Ubuntu offer to install a driver for your Intel wireless chip?

---

### Post by debtaru on 2008-02-17
Yes all are checked under System -> Administration -> Software Sources...

But the Restricted Drivers list shows Driver as Artheros Hardware Access Layer(HAL) and is enabled and the status is in Use.

Still I am unable to connect to wireless...

---

### Post by loe on 2008-02-17
Is it possilbe that you turned the hardware-wifi-switch off? On my thinkpad the switch is located on the front side. 

good luck

loe

---

### Post by debtaru on 2008-02-17
Yes, the hardware switch is turned on... 
But I still do not get the wireless light on...

Can you tell me how to connect to wireless?

---

### Post by debtaru on 2008-02-17
When I do ifconfig I get the following message:

ath0      Link encap:Ethernet  HWaddr 00:19:7D:B8:B4:D7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:19:7D:B8:B4:D7  
          inet addr:169.254.10.63  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:15:58:81:9B:05  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:29117 (28.4 KB)  TX bytes:7053 (6.8 KB)
          Base address:0x3000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-B8-B4-D7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:62617
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1152 (1.1 KB)  TX bytes:1058 (1.0 KB)
          Interrupt:17 

I guess there is something wrong with wifi0. Can you tell me what can be done?

---

### Post by loe on 2008-02-17
> HWaddr 00-19-7D-B8-B4-D7-00-00-00-00-00-00-00-00-00-00 

I have never seen such a long mac adress... :( I have no Idea whats wrong - maybe your wifi card is broken? Have you tried using the card with Win? Does it work fine under xp?

Just a thought - but I think it could be serious a problem if the mac adress wrong dedected. Perhaps you just have to edit one config file and write the correct mac address into... But do not ask me how to do this.

---

### Post by Siph0n on 2008-02-17
What does your /etc/network/interfaces file look like? I don't like network manager (not sure if you're using it)... Mine looks like this: 

auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid "ESSID NAME"
wireless-key "WEPKEY"
wireless-channel auto
auto ath0

Try that, without the quotes, and using your essid and wep key. And make sure Network Manager is off or not in use. Than you can do "sudo /etc/init.d/networking restart" (again without the quotes of course. Please tell me if that helps, Thanks!

---

### Post by loe on 2008-02-17
> debtaru@debtaru-laptop:~/Desktop$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11a ESSID:"deb" Nickname:""
Mode:Managed Frequency:5.2 GHz Access Point: 00:90:4C:7E:00:29
Bit Rate:0 kb/s Tx-Power:8 dBm Sensitivity=1/1
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=0/70 Signal level=-96 dBm Noise level=-96 dBm
Rx invalid nwid:72 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I have just read your first post again - you know that your wireless card is ath0 and connected to the access Point with the mac 00-90-ac-7e-00-29? 
I am just wondering whats up with the device called wifi0.

---

### Post by debtaru on 2008-02-17
In /etc/interfaces I get the folowing:


debtaru@debtaru-laptop:/etc/network$ more interfaces
auto lo
iface lo inet loopback




iface ath0 inet dhcp
wpa-psk 445d26194edcb93a745123677aadc93c81008706bd85c7e95455b7677618d545
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid deb

auto ath0



Should I delete these lines:

wpa-psk 445d26194edcb93a745123677aadc93c81008706bd85c7e95455b7677618d545
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA



and include yours?

---

### Post by Yellow Pasque on 2008-02-17
Uh, you probably should edit out your wireless key, just to be on the safe side.

---

### Post by Siph0n on 2008-02-17
Sorry, didn't realize u were using WPA... I never used WPA before..... It is WAY more secure than WEP though :) So no, you should not use mine if u are using WPA... I think there are some tutorials on getting WPA to work. Something about getting WPA Supplicant or something? Try doing a search for wpa tutorial?

Are you meaning to use WPA? or did you set it up like that by mistake? Also next time you may not want to post your key to a public forum :( That is why I erased mine before I posted.

---

### Post by debtaru on 2008-02-17
When I restarted the network I get the following message:


debtaru@debtaru-laptop:/etc/network$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 5606
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7d:b8:b4:d7
Sending on   LPF/ath0/00:19:7d:b8:b4:d7
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "debtaru1".
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; Invalid argument.
There is already a pid file /var/run/dhclient.ath0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7d:b8:b4:d7
Sending on   LPF/ath0/00:19:7d:b8:b4:d7
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                     

Still the problem persists....

Any resolutions?

---

### Post by xc3RnbFO8P on 2008-02-17
Try this:
> 
[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

---

### Post by debtaru on 2008-02-17
Hello Ringi,

I followed your steps but I get a problem when I type : sudo dhclient

debtaru@debtaru-laptop:/etc/network$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6821
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:15:58:81:9b:05
Sending on   LPF/eth0/00:15:58:81:9b:05
Listening on LPF/ath0/00:19:7d:b8:b4:d7
Sending on   LPF/ath0/00:19:7d:b8:b4:d7
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I think that its unable to get an IP.

Can you tell me what is the problem?

---

### Post by Yellow Pasque on 2008-02-17
Do you have a dynamic IP or does your Internet provider give you a static IP?

---

### Post by debtaru on 2008-02-17
I have  a dynamic IP. But somehow I am unable to get IP Address in ath0.

This explains:

debtaru@debtaru-laptop:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0        U     0        0        0 eth0
link-local          *                  255.255.0.0        U     0        0        0 ath0
default         192.168.0.1     0.0.0.0               UG    0        0        0 eth0
default         *                   0.0.0.0                 U     1000    0        0 ath0

---

### Post by xc3RnbFO8P on 2008-02-17
I am thinking if your wireless hotkey isnt working.

Can you see /etc/modules.d/ibm-acpi in your computer?

---

### Post by debtaru on 2008-02-17
This is what I get:

debtaru@debtaru-laptop:/etc/modprobe.d$ ls -al
total 92
drwxr-xr-x   3 root root 4096 2008-02-17 18:04 .
drwxr-xr-x 111 root root 4096 2008-02-17 20:21 ..
-rw-r--r--   1 root root 4623 2008-02-17 18:04 aliases
-rw-r--r--   1 root root 4624 2007-10-05 22:40 aliases~
-rw-r--r--   1 root root 2184 2007-10-05 19:36 alsa-base
drwxr-xr-x   2 root root 4096 2007-10-16 04:48 arch
lrwxrwxrwx   1 root root    9 2008-02-14 08:28 arch-aliases -> arch/i386
-rw-r--r--   1 root root  741 2007-10-05 22:40 blacklist
-rw-r--r--   1 root root  628 2007-10-05 22:40 blacklist-framebuffer
-rw-r--r--   1 root root  156 2007-10-05 19:36 blacklist-modem
lrwxrwxrwx   1 root root   41 2008-02-14 08:28 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   38 2007-10-05 20:33 blacklist-scanner
-rw-r--r--   1 root root  838 2007-10-05 22:40 blacklist-watchdog
-rw-r--r--   1 root root  484 2007-10-03 14:29 bluez
-rw-r--r--   1 root root  343 2007-09-19 05:54 fuse
-rw-r--r--   1 root root  205 2007-10-15 17:11 ipw3945
-rw-r--r--   1 root root  299 2007-10-05 22:40 isapnp
-rw-r--r--   1 root root   16 2007-09-07 13:35 libpisock9
-rw-r--r--   1 root root  294 2007-10-15 17:11 lrm-video
-rw-r--r--   1 root root   29 2006-10-09 19:03 nvidia-kernel-nkc
-rw-r--r--   1 root root  173 2007-10-05 22:40 options
-rw-r--r--   1 root root   60 2007-09-19 15:29 thinkpad_acpi.modprobe
-rw-r--r--   1 root root   41 2007-09-19 15:29 toshiba_acpi.modprobe
debtaru@debtaru-laptop:/etc/modprobe.d$ more thinkpad_acpi.modprobe
options thinkpad_acpi hotkey=enable,0xffff8f experimental=1

---

### Post by xc3RnbFO8P on 2008-02-17
> 
debtaru@debtaru-laptop:/etc/modprobe.d$ more thinkpad_acpi.modprobe
options thinkpad_acpi hotkey=enable,0xffff8f experimental=1

If you can use this information from: > [http://thomasgersdorf.com/linux/index.php/Gentoo_Linux_on_IBM_ThinkPad_T60#Wireless_LAN](http://thomasgersdorf.com/linux/index.php/Gentoo_Linux_on_IBM_ThinkPad_T60#Wireless_LAN)


Fn-Keys

Hardware controlled keys work without any tweaking.

To make other keys work make sure you build the ibm-acpi module and

>  echo "options ibm_acpi experimental=1 hotkey=enable,0xffef" > /etc/modules.d/ibm-acpi 
 modules-update

0xffef specifies which keys should send ACPI events. I think Fn-F5 isn't enabled. 0xffff sends all events (but then the default actions don't always happen).

Also if you haven't already done so

>  emerge -av acpid
 rc-update add acpid default

Now if you tail /var/log/acpid you should see ACPI events happening as you press Fn-F* (and the others) assuming you have the ibm-acpi module loaded with the right options. To listen to the events add an event scripts in /etc/acpi/events and the corresponding action script in /etc/acpi/actions:

>  echo 'event=ibm/
 action=/etc/acpi/actions/ibm.sh "%e"' > /etc/acpi/ibm

Here an exemplary ibm.sh. In addition to the usual commands I have Fn-F1 set up to restart wireless by removing the wireless kernel module and then reinserting it. Its useful because for some reason wireless doesn't always come up when booting (but works fine resuming from a suspend). The only problems I have is xscreensaver takes a second or so to activate or lock so the keys can feel a bit sluggish sometimes. Files: modipw, suspend-ram, suspend-disk. Note: my scripts assume the currently logged in user is 'john'. Theres probably a better way to activate the screensaver but anyway..

---

### Post by debtaru on 2008-02-17
The modules file has the folowing contents:

debtaru@debtaru-laptop:/etc$ more modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc

---

### Post by debtaru on 2008-02-17
When I doa  route, i get this output....


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 ath0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
default         *               0.0.0.0         U     1000   0        0 ath0


Can anyone please help who to enable W-Fi in since I am unable to connect?

---

### Post by xc3RnbFO8P on 2008-02-17
delete

---

### Post by xc3RnbFO8P on 2008-02-17
In /etc/modprobe.d/thinkpad_acpi.modprobe change **0xffff8f** to **0xffffff**

> sudo gedit /etc/modprobe.d/thinkpad_acpi.modprobe

---

