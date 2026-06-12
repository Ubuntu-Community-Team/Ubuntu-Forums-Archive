---
title: "How do you configure tha Atheros Wireless Driver?"
date: 2009-09-15
forum: Hardware
---

### Post by chris1950 on 2009-09-15
I installed a TP-Link wireless adapter in my PC to network with a TP-Link ADSL Wireless router and UE 2.3 installed the Atheros driver for it. It came with a windows install mini CD (in Chinese as I am in China). Since I can't use the CD how do I configure the Atheros driver so I can use the wireless adapter?:confused:

Router info TP- Link Adsl Wireless  TD-W89541G
Adapter  TP-Link 54 Mbps, PCI, TL-WN350G

---

### Post by chris1950 on 2009-09-15
need help please. bump

---

### Post by chris1950 on 2009-09-19
After installing wireless_tools.29, I ran iwconfig and got the following:

chris@chris-PC:/data/Dowmloads/wireless/wireless_tools.29$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

chris@chris-PC:/data/Dowmloads/wireless/wireless_tools.29$

---

### Post by Bucky Ball on 2009-09-19
Plug in an ethernet cable and get your updates. The driver should be picked up and you will be offered the required drivers for wireless.

Check System->Administration->Hardware Drivers and make sure there is nothing pertaining to wireless switched off. You should not need to be downloading wireless tools etc. TP-Link should work out of the box. (built a machine early in the year for someone and used one of their cards specifically for that reason and it did work out of the box - all I needed was to plug in a cable and get updates ... it was at TL-WN351G).

---

### Post by chris1950 on 2009-09-20
Deactivated the madwifi driver rebooted. still get same results in iwconfig. used update manager - NO WIRELESS updates?????

Wicd doesn't find ant wireless networks.
next option is to open box and reseat adapter.

---

### Post by drpjkurian on 2009-09-20
> **chris1950 said:**
> Deactivated the madwifi driver rebooted. still get same results in iwconfig. used update manager - NO WIRELESS updates?????

Wicd doesn't find ant wireless networks.
next option is to open box and reseat adapter.

Hi Chris.

Please try my thread it may work for you,[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

With regards
Dr Kurian

---

### Post by chris1950 on 2009-09-20
> **drpjkurian said:**
> Hi Chris.

Please try my thread it may work for you,[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

With regards
Dr Kurian

Did everything from top to bottom wicd still can not find wireless networks (says network is down??(- see code output below:
dmesg | grep -e wlan -e ath
lsmod | grep ath
sudo iwlist scan

chris@chris-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

chris@chris-PC:~$ dmesg | grep -e wlan -e ath
[    4.276737] device-mapper: multipath: version 1.0.5 loaded
[    4.276739] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.742970] ath_pci 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.004282]  sdd:<6>MadWifi: ath_attach: Switching rfkill capability off.
[   10.250740] ath_pci: wifi0: Atheros 2417: mem=0xea100000, irq=20
[   10.404119] ath9k: 0.1
chris@chris-PC:~$ lsmod | grep ath
ath9k                 310584  0 
mac80211              251528  1 ath9k
led_class              13064  1 ath9k
ath_rate_sample        21632  1 
ath_pci               223936  0 
wlan                  260768  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               399584  3 ath_rate_sample,ath_pci
chris@chris-PC:~$ sudo iwlist scan
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

chris@chris-PC:~$ sudo iwlist scan
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

chris@chris-PC:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

chris@chris-PC:~$

---

### Post by Bucky Ball on 2009-09-20
```
sudo /etc/init.d/networking start
```... or reboot your machine.

Whatever router you are using, make sure it is set up correctly as a wireless access point and/or serving IP addresses (DHCP server). If you have a static IP make sure the router is not also trying to send you one. 

Once you know the details in the router, eg. an ESSID (name of access point) and WEP or WPA security key, make sure you have all details correct in wicd. Can't help you with that as never had cause to use it. You can translate the following I'm sure. 

I use System->Admin->Network then check the wireless properties. Make sure ESSID and security key match what is in your router. 'Configuration' should be set to 'Auto-Config (DHCP)' if you are being served an IP or with the correct details in there for a static IP.

You should be able to work out how to do all this in wicd. After you have made all changes run these two commands, if networking is already running on the machine, one at a time.

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
``````
Please use code tags when posting big chunks of code else it gets kinda confusing. :)
```

---

### Post by erictherev on 2009-09-22
I'm having similar issues. I bought my laptop yesterday. After bringing it home, I completely broke Vista. No big loss. I then formatted, installed XP (since I need this system to be a dual-boot system) and then installed Kubuntu 9.04 Jaunty. 

Everything worked. Then I updated and installed a few utilities like etherape, conky and feh. I activated the proprietary Atheros driver. Now when I go into the System Settings->Network Settings, I have the first three tabs, but the Network Management tab is missing. I have tried all of the following:

Deactivated the proprietary drivers
pump
```
root@Myrkr:/home/nomad# lshw -C network
  *-network                            
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.                        
       physical id: 0                                                 
       bus info: pci@0000:02:00.0                                     
       logical name: eth0                                             
       version: 02                                                    
       serial: 00:23:8b:d9:20:43                                      
       size: 10MB/s                                                   
       capacity: 100MB/s                                              
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.2.235 latency=0 link=yes module=r8169 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:6a:94:30:7e:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
```
root@Myrkr:/home/nomad# dmesg | grep -e wlan -e ath
[    3.881077] device-mapper: multipath: version 1.0.5 loaded
[    3.881087] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.472064] ath_hal: module license 'Proprietary' taints kernel.
[   11.477390] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.529773] wlan: 0.9.4
[   11.586413] ath_pci: 0.9.4
[   11.586615] ath_pci 0000:03:00.0: enabling device (0004 -> 0006)
[   11.586636] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.586655] ath_pci 0000:03:00.0: setting latency timer to 64
[   11.635125] ath_pci 0000:03:00.0: PCI INT A disabled

```
```
root@Myrkr:/home/nomad# wicd
/var/run/wicd/wicd.pid
```
```
root@Myrkr:/home/nomad# /etc/init.d/networking stop
root@Myrkr:/home/nomad# /etc/init.d/networking start

```
```
root@Myrkr:/home/nomad# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:d9:20:43
          inet addr:192.168.2.235  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fed9:2043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15185399 (15.1 MB)  TX bytes:684727 (684.7 KB)
          Interrupt:255 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5120 (5.1 KB)  TX bytes:5120 (5.1 KB)

root@Myrkr:/home/nomad# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

I managed to completely break Vista, but I think the chances of me doing the same in any Nix system are pretty low.

Any help here would be greatly appreciated.

*Update: I have listed some steps I have taken and the results [here]("http://ubuntuforums.org/showthread.php?p=7995955#post7995955").*

---

### Post by chris1950 on 2009-09-23
> **Bucky Ball said:**
> ```
sudo /etc/init.d/networking start
```... or reboot your machine.

Whatever router you are using, make sure it is set up correctly as a wireless access point and/or serving IP addresses (DHCP server). If you have a static IP make sure the router is not also trying to send you one. 

Once you know the details in the router, eg. an ESSID (name of access point) and WEP or WPA security key, make sure you have all details correct in wicd. Can't help you with that as never had cause to use it. You can translate the following I'm sure. 

I use System->Admin->Network then check the wireless properties. Make sure ESSID and security key match what is in your router. 'Configuration' should be set to 'Auto-Config (DHCP)' if you are being served an IP or with the correct details in there for a static IP.

You should be able to work out how to do all this in wicd. After you have made all changes run these two commands, if networking is already running on the machine, one at a time.

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
``````
Please use code tags when posting big chunks of code else it gets kinda confusing. :)
```

Used - code
chris@chris-PC:~$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                          /usr/bin/poff: No pppd is running.  None stopped.
                                                                         [ OK ]
chris@chris-PC:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
 * if-up.d/mountnfs[dsl-provider]: waiting for interface eth0 before doing NFS mounts
                                                                         [ OK ]
chris@chris-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

Still can not get to the adapter to configure it for the wireless router as wicd does not see the router so can not enter required information. Laptop wicd in below signature found it no problem, configured works fine.

---

### Post by darknight2183 on 2009-09-23
Seems like you tried a lot; but I've a couple of dumb questions.  First: if you lspci do you see something similar to your dmesg?  should output something like ath242x.....  If you do, it doesn't seem like there is a problem with the ath5k drivers, you should double check to see if "ifconfig wlan0 up" produces the missing.  Second: have you tried checking to see if the card is working when you're booted to a Live CD (USB)?  If not, I'd check that first.

---

### Post by chris1950 on 2009-09-23
> **darknight2183 said:**
> Seems like you tried a lot; but I've a couple of dumb questions.  First: if you lspci do you see something similar to your dmesg?  should output something like ath242x.....  If you do, it doesn't seem like there is a problem with the ath5k drivers, you should double check to see if "ifconfig wlan0 up" produces the missing.  Second: have you tried checking to see if the card is working when you're booted to a Live CD (USB)?  If not, I'd check that first.

Just booted using the same Live CD I used to install and it found the wireless and I was able to connect. This I don't understand:confused: I think I need to reinstall but this time without the wireless adapter then after all updates  plug in the adapter and see if it is picked up by the network manager.

---

### Post by chris1950 on 2009-09-24
Thanks for all the help guys, I found out what was the problem and fixed it. Went to wicd preferences and under wireless nothing was listed - I put ath0 save refresh and the wireless router was found entered the password and was connected. duh something so simple that was not checked was causing all my headaches.

---

### Post by Bucky Ball on 2009-09-24
Pleasure. More brains the better. Love it when it all comes together. Enjoy!

---

### Post by erictherev on 2009-09-25
I found the solution for the same problem with my Acer Aspire One netbook... Reinstall Kubuntu, and NEVER activate the proprietary drivers! :mrgreen:

---

