---
title: "how to install acerhk"
date: 2009-11-07
forum: Hardware
---

### Post by arjunchandkn on 2009-11-07
hello ppl

I am using ubuntu from past 2 month, recently upgraded from 9.04 to 9.10
gnome 2.28.1
kernel 2.6.31-14-generic

I have problem with installing WLAN for my acer travelmate 290.

I installed acerhk gui. In preferences it shows driver not found, so I downloaded acerhk-0.5.35 

what to do next? I am not able to activate my WLAN.

I did search for solution but did not help me as i dont know how to add header to the kernel

Some more info about my lappy




$ lspci -nn


00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 21)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 21)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev 80)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
02:03.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)




$ lshw -C Network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:14:6a:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.10 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=128 maxlatency=34 mingnt=2
       resources: memory:d0000000-d0000fff



$ uname -m

i686

---

### Post by darkshadow on 2009-11-07
Your problem is not acerhk since it has been along time since I had to install it in Ubuntu since it is incorporated.

In the lspci output no driver has claimed your wireless card. Here a site with info on the driver and binary firmware
[http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

You probably just need the firmware but I have not used this exact card to know.

---

### Post by arjunchandkn on 2009-11-07
thanks for the reply. I know i have installed only the GUI but not the driver... I have just downloaded "acerhk-0.5.35" from source forge which i understood as the required drive...

can anyone say the procedure to install acer hot keys

---

### Post by pytheas22 on 2009-11-07
You can follow darkshadow's link for installing the ipw2100 driver, or another way to get the card working is to use ndiswrapper.  To go that route, first go [here]("http://downloadcenter.intel.com/detail_desc.aspx?agr=N&ProductID=944&DwnldID=11918&strOSs=44&OSFullName=Windows") and download the .zip file (scroll to the bottom of the page for the link).  Save it to your desktop.  Then run:

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
cd ~/Desktop
unzip Intel*zip
sudo ndiswrapper -i w70n501.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot and hopefully the card will work.  If not, let me know the output of:
```

dmesg | grep -e ndis -e wlan
uname -rm
ndiswrapper -l
sudo iwlist scan
```

---

### Post by arjunchandkn on 2009-11-08
Still not able to connect... but there is some improvement

after restarting my system i did " create new connection " under wireless networks on the panel, gave the network name and pass key. It showed me signal lines on the panel and "connection established" message.. tried accessing internet but nothing happened
[B]
$ dmesg | grep -e ndis -e wlan[/B]

[   12.982770] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.795047] ndiswrapper: driver w70n501 (Intel,08/02/2006,1.2.5.37) loaded
[   13.795385] ndiswrapper 0000:02:02.0: power state changed by ACPI to D0
[   13.795402] ndiswrapper 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   13.812889] ndiswrapper: using IRQ 10
[   13.926172] ndiswrapper (NdisMIndicateStatus:2123): radio is turned off by hardware
[   14.130302] wlan0: ethernet device 00:0c:f1:1e:3f:24 using NDIS driver: w70n501, version: 0x10002, NDIS version: 0x501, vendor: 'Intel(R) PRO/Wireless 7100 LAN Card Driver', 8086:1043.5.conf
[   14.130331] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   14.130414] usbcore: registered new interface driver ndiswrapper
[   19.292470] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.297546] ndiswrapper (set_packet_filter:795): filter not set: 0x00000000, 0x0000000b
[   72.380193] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   72.380216] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 5 failed (C0010015)
[   72.648824] ndiswrapper (set_packet_filter:795): filter not set: 0x00000000, 0x00000002
[  267.477007] ndiswrapper (set_packet_filter:795): filter not set: 0x00000000, 0x00000002
[  639.220644] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  639.220661] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 5 failed (C0010015)
[  639.225507] ndiswrapper (set_packet_filter:795): filter not set: 0x00000000, 0x00000002
[  677.156883] ndiswrapper (set_packet_filter:795): filter not set: 0x00000000, 0x00000002
[ 1658.827146] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1658.827162] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 5 failed (C0010015)
[ 1658.837833] ndiswrapper (set_packet_filter:795): filter not set: 0x00000000, 0x00000002


**$ uname -rm**

2.6.31-14-generic i686


**$ ndiswrapper -l**

WARNING: All config files need .conf: /etc/modprobe.d/ipw2100, it will be ignored in a future release.
w70n501 : driver installed
    device (8086:1043) present (alternate driver: ipw2100)

 **$ sudo iwlist scan**

 lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by pytheas22 on 2009-11-08
Note this line from your dmesg output:
```

[ 13.926172] ndiswrapper (NdisMIndicateStatus:2123): radio is turned off by hardware
```

Do you have a physical switch or hotkey that you use to turn the wireless on and off?  If so, please make sure it's on.  This is probably the problem.  When the card is turned on properly, the command "sudo iwlist scan" should return a list of wireless networks in range of your computer.

On some computers, the wireless card may also be enabled or disabled in BIOS, so if you don't have a switch or hotkey for controlling it, check there.

---

### Post by arjunchandkn on 2009-11-08
I have a physical button to turn on the wifi and it is in** ON** position.

---

### Post by pytheas22 on 2009-11-08
Please post the output of these commands (some commands may have no output):
```

sudo rmmod ndiswrapper
sudo rmmod ipw2100
sudo modprobe ipw2100
lshw -C Network
dmesg | grep -e ipw -e wlan -ie radio
sudo iwlist scan
```

---

### Post by arjunchandkn on 2009-11-08
arjun@arjun-laptop:~$ **sudo rmmod ndiswrapper**  /*after executing this command the wifi signal at panel is gone and disconnecting msg  appeared*/

arjun@arjun-laptop:~$** sudo rmmod ipw2100**
ERROR: Module ipw2100 does not exist in /proc/modules
arjun@arjun-laptop:~$ sudo modprobe ipw2100
WARNING: All config files need .conf: /etc/modprobe.d/ipw2100, it will be ignored in a future release.
FATAL: Error inserting ipw2100 (/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ipw2x00/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)

arjun@arjun-laptop:~$ **lshw -C Network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:14:6a:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=128 maxlatency=34 mingnt=2
       resources: memory:d0000000-d0000fff

arjun@arjun-laptop:~$ **dmesg | grep -e ipw -e wlan -ie radio**
[   12.682925] ipw2100: Unknown parameter `led'
[   13.175029] ndiswrapper (NdisMIndicateStatus:2123): radio is turned off by hardware
[   13.373110] wlan0: ethernet device 00:0c:f1:1e:3f:24 using NDIS driver: w70n501, version: 0x10002, NDIS version: 0x501, vendor: 'Intel(R) PRO/Wireless 7100 LAN Card Driver', 8086:1043.5.conf
[   13.373137] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   29.650818] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4675.320983] Unknown OutputIN= OUT=wlan0 SRC=10.42.43.1 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=33007 DPT=1900 LEN=141 
[ 4675.321043] Unknown OutputIN= OUT=wlan0 SRC=10.42.43.1 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=33007 DPT=1900 LEN=140 
[ 4710.360343] Unknown OutputIN= OUT=wlan0 SRC=10.42.43.1 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=46955 DPT=1900 LEN=141 
[ 4710.360373] Unknown OutputIN= OUT=wlan0 SRC=10.42.43.1 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=46955 DPT=1900 LEN=140 
[ 4865.440568] Unknown OutputIN= OUT=wlan0 SRC=10.42.43.1 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=55871 DPT=1900 LEN=141 
[ 4865.440597] Unknown OutputIN= OUT=wlan0 SRC=10.42.43.1 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=55871 DPT=1900 LEN=140 
[ 8780.281440] ndiswrapper: device wlan0 removed
[ 8898.561297] ipw2100: Unknown parameter `led'


arjun@arjun-laptop:~$ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2009-11-08
We're closer.  What is the output of:

```
grep -R ipw /etc/modprobe.d/*
cat /etc/issue

```

---

### Post by arjunchandkn on 2009-11-08
I am using single boot( only ubuntu) and did not partition my hard disk


arjun@arjun-laptop:~$ grep -R ipw / etc/modprobe.d/*
grep: /home/lost+found: Permission denied
Binary file /home/arjun/Videos/[DVD-Rip] Padikathavan [Ayn].Rip By_Desman/[DVD-Rip] Padikathavan [Ayn].Rip By_Desman.avi matches
Binary file /home/arjun/Videos/Masillamani_Original_TC_1CDRip[DesiBBrG.com]/Masillamani_Original_TC_1CDRip[DesiBBrG.com].avi matches
Binary file /home/arjun/Desktop/movies/No Smoking-2.DAT matches
Binary file /home/arjun/Desktop/movies/Ghatikudu(2009) - Camrip - XviD - Mp3 - 1 CD  - Team Tolly.avi matches
Binary file /home/arjun/Desktop/movies/Ninnu Kal  2009 679mb(camrip)  x264mp3 128Kpbs.mp4 matches
Binary file /home/arjun/Desktop/movies/No Smoking-1.DAT matches
Binary file /home/arjun/Desktop/IS ass3/shakey2.pdf matches
Binary file /home/arjun/.thumbnails/normal/73ee730bf4e98fb63817cb3ded600b32.png matches
Binary file /home/arjun/.thumbnails/normal/e00ab7ddf2083d8f6baa25b50356a30a.png matches
Binary file /home/arjun/.thumbnails/normal/fd5a6d2d37392237878b7fc602274356.png matches
/home/arjun/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/org.eclipse.osgi/bundles/114/1/.cp/dictionaries/en_GB.dictionary:shipwreck
/home/arjun/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/org.eclipse.osgi/bundles/114/1/.cp/dictionaries/en_GB.dictionary:shipwrecked
/home/arjun/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/org.eclipse.osgi/bundles/114/1/.cp/dictionaries/en_GB.dictionary:shipwrecks
/home/arjun/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/org.eclipse.osgi/bundles/114/1/.cp/dictionaries/en_US.dictionary:shipwreck
/home/arjun/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/org.eclipse.osgi/bundles/114/1/.cp/dictionaries/en_US.dictionary:shipwrecked
/home/arjun/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/org.eclipse.osgi/bundles/114/1/.cp/dictionaries/en_US.dictionary:shipwrecks
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-1.2.0.tgz" added="2009-11-08T02:38:03Z" modified="2009-11-08T02:38:04Z" visited="2009-11-08T02:38:03Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-1.2.0/README.ipw2100" added="2009-11-08T02:43:43Z" modified="2009-11-08T02:43:45Z" visited="2009-11-08T02:43:43Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-1.2.0/restart" added="2009-11-08T02:43:57Z" modified="2009-11-08T02:43:59Z" visited="2009-11-08T02:43:57Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-1.2.0/verify_wifi_hw" added="2009-11-08T02:44:28Z" modified="2009-11-08T02:44:29Z" visited="2009-11-08T02:44:28Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-1.2.0/status" added="2009-11-08T02:44:48Z" modified="2009-11-08T02:44:49Z" visited="2009-11-08T02:44:48Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-1.2.0/ISSUES" added="2009-11-08T02:45:28Z" modified="2009-11-08T02:45:29Z" visited="2009-11-08T02:45:28Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Desktop/ipw2100-fw-1.3.tgz" added="2009-11-08T17:07:32Z" modified="2009-11-08T17:07:32Z" visited="2009-11-08T17:07:32Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/ipw2100-fw-1.3.tgz" added="2009-11-08T17:08:25Z" modified="2009-11-08T17:08:26Z" visited="2009-11-08T17:08:25Z">
/home/arjun/.recently-used.xbel:  <bookmark href="file:///home/arjun/Setups/3/ipw2100-fw-1.3.tgz" added="2009-11-08T17:09:09Z" modified="2009-11-08T17:09:09Z" visited="2009-11-08T17:09:09Z">
Binary file /home/arjun/Pictures/motocross/(41).jpg matches
cat /etc/issue

---

### Post by pytheas22 on 2009-11-09
It looks like you made a typo when running the command.  It should be:
```

grep -R ipw /etc/modprobe.d/*
```

Note that there's no space between the first / and etc.  Please try it again and let me know the output (it's possible that there will be no output).

---

### Post by arjunchandkn on 2009-11-09
i cant find any typo.... can you pls highlight where the typo is....

any how i have copied ur code in terminal and got this output

grep -R ipw /etc/modprobe.d/*
/etc/modprobe.d/ipw2100:options ipw2100 led=1 hwcrypto=0

---

### Post by arjunchandkn on 2009-11-09
the above smiley is (colon O)

$ cat /etc/issue
Ubuntu 9.10 \n \l

---

### Post by pytheas22 on 2009-11-09
You pasted the command correctly the second time.  The first time there was a blank space that was throwing it off.

In any case, I now have the information I was looking for and that I hope is the key to solving your problem.  I think the issue is that for some reason you have a configuration file that's telling the system to load the ipw2100 module with special options, which are causing it to fail (I assume you created the file yourself, because it shouldn't be in Ubuntu 9.10 by default).

To solve the problem, please run these commands and post the output:
```

sudo rmmod ndiswrapper
sudo rm /etc/modprobe.d/ipw2100ptions ipw2100 led=1 hwcrypto=0
sudo modprobe ipw2100
dmesg | grep ipw
sudo iwlist scan
```

If all goes as expected, at this point your wireless should be up.  If it's not, please post the output of the commands above so I can see what went wrong.

---

### Post by arjunchandkn on 2009-11-09
sudo rmmod ndiswrapper

my system hung up . capslock and cpu lights were blinking synchronously ... and no response... I had to restart to get control

sudo rmmod ndiswrapper

arjun@arjun-laptop:~$ sudo rm /etc/modprobe.d/ipw2100ptions ipw2100 led=1 hwcrypto=0
[sudo] password for arjun: 
rm: cannot remove `/etc/modprobe.d/ipw2100ptions': No such file or directory
rm: cannot remove `ipw2100': No such file or directory
rm: cannot remove `led=1': No such file or directory
rm: cannot remove `hwcrypto=0': No such file or directory
arjun@arjun-laptop:~$ sudo modprobe ipw2100
WARNING: All config files need .conf: /etc/modprobe.d/ipw2100, it will be ignored in a future release.
FATAL: Error inserting ipw2100 (/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ipw2x00/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)
arjun@arjun-laptop:~$ dmesg | grep ipw
[  553.198637] ipw2100: Unknown parameter `led'
arjun@arjun-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by arjunchandkn on 2009-11-09
I have executed all these commands with Ethernet cable plugged in...

---

### Post by pytheas22 on 2009-11-09
It looks like there was a typo again in the following command:

```
sudo rm /etc/modprobe.d/ipw2100 options ipw2100 led=1 hwcrypto=0

```

As you typed it, there was no space between "ipw2100" and "options".  Please try the following commands again, and if possible, copy and paste instead of typing them out by hand.
```

sudo rmmod ndiswrapper
sudo rm /etc/modprobe.d/ipw2100ptions ipw2100 led=1 hwcrypto=0
sudo modprobe ipw2100
dmesg | grep ipw
sudo iwlist scan
```

As for your system freezing on the first command, I apologize for that; hopefully it won't happen again.  ndiswrapper can be unstable (and doesn't appear to really be working for you anyway), which is why I want to use the native ipw2100 driver instead.  It should be much more stable, and offers more functionality.  The problem is just that we need to get rid of this error message you receive when typing "sudo modprobe ipw2100".

---

### Post by arjunchandkn on 2009-11-10
arjun@arjun-laptop:~$ sudo rm /etc/modprobe.d/ipw2100ptions ipw2100 led=1 hwcrypto=0
[sudo] password for arjun: 
rm: cannot remove `/etc/modprobe.d/ipw2100ptions': No such file or directory
rm: cannot remove `ipw2100': No such file or directory
rm: cannot remove `led=1': No such file or directory
rm: cannot remove `hwcrypto=0': No such file or directory
arjun@arjun-laptop:~$ sudo modprobe ipw2100
WARNING: All config files need .conf: /etc/modprobe.d/ipw2100, it will be ignored in a future release.
FATAL: Error inserting ipw2100 (/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/ipw2x00/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)
arjun@arjun-laptop:~$ dmesg | grep ipw
[   17.843717] ipw2100: Unknown parameter `led'
[ 1190.168568] ipw2100: Unknown parameter `led'

arjun@arjun-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by darkshadow on 2009-11-10
ignore: sudo rm /etc/modprobe.d/ipw2100ptions ipw2100 led=1 hwcrypto=0
fixed: sudo rm /etc/modprobe.d/ipw2100

---

### Post by arjunchandkn on 2009-11-10
arjun@arjun-laptop:~$ sudo rm /etc/modprobe.d/ipw2100
[sudo] password for arjun: 
arjun@arjun-laptop:~$ sudo modprobe ipw2100
arjun@arjun-laptop:~$ dmesg | grep ipw
[   13.215545] ipw2100: Unknown parameter `led'
[  485.578867] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[  485.578878] ipw2100: Copyright(c) 2003-2006 Intel Corporation

arjun@arjun-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by pytheas22 on 2009-11-10
darkshadow is right.  I was stupidly giving you the wrong command to run.  Please try:
```

sudo rmmod ndiswrapper
sudo rm /etc/modprobe.d/ipw2100ptions
sudo modprobe ipw2100
dmesg | grep ipw
sudo iwlist scan
```

This time, it should finally work.  All you need to do (probably) is get rid of this /etc/modprobe.d/ipw2100ptions file...

---

### Post by pytheas22 on 2009-11-10
It looks like ipw2100 driver is finally bringing up the card correctly, although you still can't detect any networks.

Are you positive the wireless card is turned on and that there are networks in range?  Do you know which channel your network is on?

---

### Post by arjunchandkn on 2009-11-10
on the panel at the top it is showing as wireless is "turned on" and connected to my router but i cant access internet...

there is a led indicator for wifi in my laptop which is not glowing.. 

my friends are accessing wifi rite now except me....

channel is 1- 2.412 Ghz


arjun@arjun-laptop:~$ sudo rm /etc/modprobe.d/ipw2100ptions
[sudo] password for arjun: 
rm: cannot remove `/etc/modprobe.d/ipw2100ptions': No such file or directory
arjun@arjun-laptop:~$ sudo modprobe ipw2100
arjun@arjun-laptop:~$ dmesg | grep ipw
[ 1521.324502] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[ 1521.324513] ipw2100: Copyright(c) 2003-2006 Intel Corporation
arjun@arjun-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by arjunchandkn on 2009-11-10
when i was using Windows XP, wifi led indicator used to glow when i switch-on wifi ... now it is not glowing where as on the top panel it is still showing as if i am connected to my WLAN even when my wifi physical switch is off.

---

### Post by pytheas22 on 2009-11-10
That's strange.  I suspect the radio for the wireless card is not coming on for some reason.  Are you sure you can't control it from BIOS?  Also, nothing happens when you press the switch to turn it on (i.e., the LED doesn't light up)?

Please also run this command to ensure the ipw2100 module is inserted at boot:
```

echo ipw2100 | sudo tee -a /etc/modules
```

Then reboot, and run the following commands:
```

dmesg | grep -e ipw -ie radio
sudo iwlist scan
cat /sys/bus/pci/drivers/ipw2100/*/rf_kill
```

Then try turning the wireless card on using the switch, and run the commands again and post the output:

```

dmesg | grep -e ipw -ie radio
sudo iwlist scan
cat /sys/bus/pci/drivers/ipw2100/*/rf_kill
```

Hopefully this will help figure out what's going on.

---

### Post by arjunchandkn on 2009-11-10
echo ipw2100 | sudo tee -a /etc/modules
ipw2100
-----------------------
 after restarting
-----------------------

arjun@arjun-laptop:~$ dmesg | grep -e ipw -ie radio
[   18.309294] ndiswrapper (NdisMIndicateStatus:2123): radio is turned off by hardware
[   21.648192] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   21.648197] ipw2100: Copyright(c) 2003-2006 Intel Corporation
arjun@arjun-laptop:~$ sudo iwlist scan
[sudo] password for arjun: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

arjun@arjun-laptop:~$ cat /sys/bus/pci/drivers/ipw2100/*/rf_kill
cat: /sys/bus/pci/drivers/ipw2100/*/rf_kill: No such file or directory
------------------------
switched off and again switched on the wifi physical switch... still no light glowing
-------------------------
dmesg | grep -e ipw -ie radio
[   18.309294] ndiswrapper (NdisMIndicateStatus:2123): radio is turned off by hardware
[   21.648192] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   21.648197] ipw2100: Copyright(c) 2003-2006 Intel Corporation
arjun@arjun-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

arjun@arjun-laptop:~$ cat /sys/bus/pci/drivers/ipw2100/*/rf_kill
cat: /sys/bus/pci/drivers/ipw2100/*/rf_kill: No such file or directory

---

### Post by darkshadow on 2009-11-10
as a wild guess try these commands as root (note I can't get these type of commands to with with sudo at the start so that is why I added the first line)

sudo bash
echo 1 > /sys/devices/platform/acer-wmi/rfkill/rfkill0/state
echo 1 > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state

---

### Post by arjunchandkn on 2009-11-11
arjun@arjun-laptop:~$ sudo bash
[sudo] password for arjun: 
root@arjun-laptop:~# echo 1 > /sys/devices/platform/acer-wmi/rfkill/rfkill0/state
bash: /sys/devices/platform/acer-wmi/rfkill/rfkill0/state: No such file or directory
root@arjun-laptop:~# echo 1 > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state
bash: /sys/devices/platform/acer-wmi/rfkill/rfkill1/state: No such file or directory
root@arjun-laptop:~#

---

### Post by arjunchandkn on 2009-11-11
[IMG]http://lh5.ggpht.com/_-3PV295qsQg/SvrpNjAgi0I/AAAAAAAACf8/tLeCiKD2BBs/s640/Screenshot.png[/IMG]

---

### Post by pytheas22 on 2009-11-11
What do the other tabs in the "AcerHK:: GUI Preferences" window say?  I didn't realize you need to have a module loaded to make the LED for your wireless card work.  Perhaps this is part of the problem.  If you could please post screenshots (or copy and paste the text of) the other tabs, that might help figure out what's going on.

Also, what's the output (if any) of:
```

locate rf | grep kill
locate radio | grep sys
```

---

### Post by arjunchandkn on 2009-11-11
arjun@arjun-laptop:~$ locate rf | grep kill
/lib/modules/2.6.28-11-generic/kernel/net/rfkill
/lib/modules/2.6.28-11-generic/kernel/net/rfkill/rfkill-input.ko
/lib/modules/2.6.28-11-generic/kernel/ubuntu/rfkill
/lib/modules/2.6.28-11-generic/kernel/ubuntu/rfkill/av5100.ko
/lib/modules/2.6.28-11-generic/kernel/ubuntu/rfkill/pbe5.ko
/lib/modules/2.6.28-15-generic/kernel/net/rfkill
/lib/modules/2.6.28-15-generic/kernel/net/rfkill/rfkill-input.ko
/lib/modules/2.6.28-15-generic/kernel/ubuntu/rfkill
/lib/modules/2.6.28-15-generic/kernel/ubuntu/rfkill/av5100.ko
/lib/modules/2.6.28-15-generic/kernel/ubuntu/rfkill/pbe5.ko
/lib/modules/2.6.28-16-generic/kernel/net/rfkill
/lib/modules/2.6.28-16-generic/kernel/net/rfkill/rfkill-input.ko
/lib/modules/2.6.28-16-generic/kernel/ubuntu/rfkill
/lib/modules/2.6.28-16-generic/kernel/ubuntu/rfkill/av5100.ko
/lib/modules/2.6.28-16-generic/kernel/ubuntu/rfkill/pbe5.ko
/lib/modules/2.6.31-14-generic/kernel/ubuntu/rfkill
/lib/modules/2.6.31-14-generic/kernel/ubuntu/rfkill/av5100.ko
/lib/modules/2.6.31-14-generic/kernel/ubuntu/rfkill/pbe5.ko
/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules
/sbin/rfkill
/usr/include/linux/rfkill.h
/usr/lib/hal/hald-addon-rfkill-killswitch
/usr/share/hal/fdi/information/10freedesktop/10-ipw-rfkill-switch.fdi
/usr/share/hal/fdi/information/10freedesktop/10-iwl-rfkill-switch.fdi
/usr/share/hal/fdi/information/10freedesktop/10-thinkpad-rfkill-switch-bluetooth.fdi
/usr/share/hal/fdi/policy/10osvendor/10-rfkill-switch.fdi
/usr/share/man/man1/rfkill.1.gz
/usr/src/linux-headers-2.6.28-15/include/linux/rfkill.h
/usr/src/linux-headers-2.6.28-15/net/rfkill
/usr/src/linux-headers-2.6.28-15/net/rfkill/Kconfig
/usr/src/linux-headers-2.6.28-15/net/rfkill/Makefile
/usr/src/linux-headers-2.6.28-15/ubuntu/rfkill
/usr/src/linux-headers-2.6.28-15/ubuntu/rfkill/Kconfig
/usr/src/linux-headers-2.6.28-15/ubuntu/rfkill/Makefile
/usr/src/linux-headers-2.6.28-15-generic/include/config/rfkill
/usr/src/linux-headers-2.6.28-15-generic/include/config/rfkill.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/b43/rfkill.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/b43legacy/rfkill.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/iwl3945/rfkill.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/iwlwifi/rfkill.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/rfkill/input.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/rfkill/leds.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/rt2x00/lib/rfkill.h
/usr/src/linux-headers-2.6.28-15-generic/include/linux/rfkill.h
/usr/src/linux-headers-2.6.28-16/include/linux/rfkill.h
/usr/src/linux-headers-2.6.28-16/net/rfkill
/usr/src/linux-headers-2.6.28-16/net/rfkill/Kconfig
/usr/src/linux-headers-2.6.28-16/net/rfkill/Makefile
/usr/src/linux-headers-2.6.28-16/ubuntu/rfkill
/usr/src/linux-headers-2.6.28-16/ubuntu/rfkill/Kconfig
/usr/src/linux-headers-2.6.28-16/ubuntu/rfkill/Makefile
/usr/src/linux-headers-2.6.28-16-generic/include/config/rfkill
/usr/src/linux-headers-2.6.28-16-generic/include/config/rfkill.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/b43/rfkill.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/b43legacy/rfkill.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/iwl3945/rfkill.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/iwlwifi/rfkill.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/rfkill/input.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/rfkill/leds.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/rt2x00/lib/rfkill.h
/usr/src/linux-headers-2.6.28-16-generic/include/linux/rfkill.h
/usr/src/linux-headers-2.6.31-14/include/linux/rfkill.h
/usr/src/linux-headers-2.6.31-14/net/rfkill
/usr/src/linux-headers-2.6.31-14/net/rfkill/Kconfig
/usr/src/linux-headers-2.6.31-14/net/rfkill/Makefile
/usr/src/linux-headers-2.6.31-14/ubuntu/rfkill
/usr/src/linux-headers-2.6.31-14/ubuntu/rfkill/Kconfig
/usr/src/linux-headers-2.6.31-14/ubuntu/rfkill/Makefile
/usr/src/linux-headers-2.6.31-14-generic/include/config/rfkill
/usr/src/linux-headers-2.6.31-14-generic/include/config/rfkill.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/rfkill/input.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/rfkill/leds.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/rt2x00/lib/rfkill.h
/usr/src/linux-headers-2.6.31-14-generic/include/linux/rfkill.h
arjun@arjun-laptop:~$ locate radio | grep sys
/usr/lib/jruby1.1/share/ri/1.8/system/CGI/HtmlExtension/radio_button-i.yaml
/usr/lib/jruby1.1/share/ri/1.8/system/CGI/HtmlExtension/radio_group-i.yaml
arjun@arjun-laptop:~$

---

### Post by arjunchandkn on 2009-11-11
did u observe on the panel the wifi signal..... if i remove the ethernet cable it shows as if it is connected through wireless... but still cant access internet

---

### Post by arjunchandkn on 2009-11-11
[http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072872406491938](http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072872406491938)[IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072872406491938[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072870466196626[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072870484279426[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072874878601282[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403072874607229474[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403073455790489090[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403073060744460706[/IMG][IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5403073067017692322[/IMG]


i have uploaded all the screen shots

---

### Post by pytheas22 on 2009-11-12
Thanks for the screenshots.  I've done some more research and it looks like the acerhk module is deprecated (see [here]("http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt") for example) in favor of a new one called acer-wmi.  If you type these commands, what happens:
```

sudo -s
modprobe acer-wmi
rfkill unblock all
echo 1 > /sys/devices/platform/acer-wmi/wireless
iwlist scan
```

Do you see a list of wireless networks?  If so, can you connect?
> 
did u observe on the panel the wifi signal..... if i remove the ethernet cable it shows as if it is connected through wireless... but still cant access internet

I think it's not actually indicating that you're connected to a network.  If you were connected, you would see some of the bars filled in; also, the command "sudo iwlist scan" would return a list of networks.  I think the problem is still that the radio for the wireless card is turned off; we need to fix that before anything else will work.

---

### Post by arjunchandkn on 2009-11-13
arjun@arjun-laptop:~$ sudo -s
root@arjun-laptop:~# modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.31-14-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
root@arjun-laptop:~# rfkill unblock all
root@arjun-laptop:~# echo 1 > /sys/devices/platform/acer-wmi/wireless
bash: /sys/devices/platform/acer-wmi/wireless: No such file or directory
root@arjun-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by pytheas22 on 2009-11-14
> FATAL: Error inserting acer_wmi (/lib/modules/2.6.31-14-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device

That means acer-wmi (the new version of acerhk) may not be supported by your BIOS.  What is the actual make and model of your laptop?

I'm sorry this is taking so long to figure out, but there actually appear to be multiple issues going on that are making things very complicated.  Thanks for your patience.

---

### Post by pytheas22 on 2009-11-14
Also please try running these commands and post the output:
```

sudo apt-get install build-essential
wget http://www.edbl.no/karmic/acerhk-fixed.tar.bz2
tar -xjvf acerhk-fixed.tar.bz2 
cd acer*
make
sudo make install
sudo -s
/sbin/modprobe acerhk autowlan=1
echo 1 > /proc/driver/acerhk/wirelessled
iwlist scan
```

This will compile and install a custom version of the acerhk module from [here]("http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt") that may work better than acer-wmi.

---

### Post by arjunchandkn on 2009-11-14
arjun@arjun-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev gnustep-base-common gappletviewer-4.3 kdelibs4c2a
  libecj-java libcommons-pool-java gnustep-base-runtime liblucene-java
  libbtctl4 libosp5 libcommons-el-java antlr libbeecrypt6 g++-4.3
  libboost-program-options1.35.0 liblog4j1.2-java-gcj gnustep-gui-common
  ttf-kannada-fonts w3c-dtd-xhtml kdelibs-data libcommons-modeler-java
  libjaxp1.3-java-gcj epiphany-extensions liblualib50 libantlr-java
  gnustep-back0.14 libass1 ecj-gcj libswt3.2-gtk-java koffice-data
  libgnustep-gui0.14 libgnustep-gui0.16 libtomcat5.5-java libsdl-net1.2
  libxerces2-java-gcj libmysqlclient15off ruby1.8 libgoffice-0-6-common
  xulrunner-1.9-dom-inspector libcommons-launcher-java libsdl-sound1.2 gcj-4.3
  ruby ecj libavahi-qt3-1 libmikmod2 gjdoc libgnustep-base1.16
  ttf-telugu-fonts libgnustep-base1.19 libgcj9-dev gnustep-common libxul0d
  libcommons-dbcp-java libffado0 gnustep-gpbs libcommons-collections-java
  libgoffice-0-6 khelpcenter libphonon4 libmozjs0d python-setuptools
  java-gcj-compat-dev libgcj9-src libkadm55 dacco-common libffcall1
  ttf-oriya-fonts gnustep-back-common libswt3.2-gtk-gcj libgmyth0 libgnomebt0
  liblrdf0 libservlet2.3-java libobjc2 liblucene-java-doc libxul-common
  liblua50 libruby1.8 gnustep-gui-runtime libswt3.2-gtk-jni koffice-libs
  libecj-java-gcj gnustep-back0.14-art ttf-bengali-fonts libantlr-java-gcj
  gstreamer0.10-gnonlin libpqxx-2.6.9ldbl libqdaccolib0.7 qt4-qtconfig
  libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 74 not upgraded.
arjun@arjun-laptop:~$ wget [http://www.edbl.no/karmic/acerhk-fixed.tar.bz2](http://www.edbl.no/karmic/acerhk-fixed.tar.bz2)
--2009-11-14 11:49:09--  [http://www.edbl.no/karmic/acerhk-fixed.tar.bz2](http://www.edbl.no/karmic/acerhk-fixed.tar.bz2)
Resolving [www.edbl.no](www.edbl.no)... 62.89.32.153
Connecting to [www.edbl.no|62.89.32.153|:80](www.edbl.no|62.89.32.153|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33505 (33K) [application/x-tar]
Saving to: `acerhk-fixed.tar.bz2'

100%[======================================>] 33,505      19.0K/s   in 1.7s    

2009-11-14 11:49:24 (19.0 KB/s) - `acerhk-fixed.tar.bz2' saved [33505/33505]

arjun@arjun-laptop:~$ tar -xjvf acerhk-fixed.tar.bz2 
acerhk-0.5.35/
acerhk-0.5.35/.tmp_versions/
acerhk-0.5.35/doc/
acerhk-0.5.35/NEWS
acerhk-0.5.35/INSTALL
acerhk-0.5.35/README
acerhk-0.5.35/COPYING
acerhk-0.5.35/AUTHORS
acerhk-0.5.35/acerhk.c
acerhk-0.5.35/acerhk.h
acerhk-0.5.35/modules.order
acerhk-0.5.35/Module.symvers
acerhk-0.5.35/Makefile
acerhk-0.5.35/Module.markers
acerhk-0.5.35/.tmp_versions/acerhk.mod
acerhk-0.5.35/doc/FAQ
acerhk-0.5.35/doc/IOCTL
acerhk-0.5.35/doc/acertm.def
acerhk-0.5.35/doc/md95400.def
acerhk-0.5.35/doc/keycodes
arjun@arjun-laptop:~$ cd acer*
arjun@arjun-laptop:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/arjun/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/arjun/acerhk-0.5.35/acerhk.o
/home/arjun/acerhk-0.5.35/acerhk.c: In function &#8216;set_mail_led&#8217;:
/home/arjun/acerhk-0.5.35/acerhk.c:814: warning: &#8216;regs&#8217; may be used uninitialized in this function
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 2 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/arjun/acerhk-0.5.35/acerhk.mod.o
  LD [M]  /home/arjun/acerhk-0.5.35/acerhk.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
arjun@arjun-laptop:~/acerhk-0.5.35$ sudo make install
mkdir -p /lib/modules/"`uname -r`"/extra
cp -v acerhk.ko /lib/modules/"`uname -r`"/extra/
`acerhk.ko' -> `/lib/modules/2.6.31-14-generic/extra/acerhk.ko'
depmod -a
arjun@arjun-laptop:~/acerhk-0.5.35$ sudo -s
root@arjun-laptop:~/acerhk-0.5.35# /sbin/modprobe acerhk autowlan=1
root@arjun-laptop:~/acerhk-0.5.35# echo 1 > /proc/driver/acerhk/wirelessled
root@arjun-laptop:~/acerhk-0.5.35# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

root@arjun-laptop:~/acerhk-0.5.35#

---

### Post by pytheas22 on 2009-11-14
You now at least have the acerhk module installed, which is good.  Unfortunately, you apparently still can't scan for networks.  Does the led work?  If not, does it if you type:
```

sudo -s 
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessled
```

Also, does the switch for your wireless card do anything now?  If you flip it and type "sudo iwlist scan" do you get any results?

Finally, please let me know the model of your laptop.

---

### Post by arjunchandkn on 2009-11-14
the led still does not work. i cant find any difference moving switch in both the positions.. When i open acerhk gui it shows 

The AcerHK module was not found. 

Attempting to run 'modprobe' to load driver.
Your sudo password will be required. press ok
entered password

Modprobe was successful! 

Acerhk is now loaded. press ok

Would you like to add 'acerhk' to
your /etc/modules file?

AcerHK GUI just finished running modprobe.

If this is the first time, it is recommended
that you test AcerHK GUI to ensure that it functions
by pressing NO.

If this is a second and successful first run, answer YES
to modify your /etc/modules file with acerhk.

I pressed NO... i second run i tried YES but no use

he acerhk driver was not found at:
  /home/arjun/Setups/acerhk-0.5.35/wirelessled.

The GUI will not function!

2nd run ... I pressed yes
***********************************************************
The /etc/modules file already has acerhk in it.

For some reason, the driver is not loading.  Your hardware
may not be compatable with the acerhk driver.
***********************************************************

Troubleshooting Tip:  Use 'sudo locate wirelessled' to find driver path and borwse to path.

The acerhk driver was not found at:
  /home/arjun/Setups/ipw2100-1.2.0/wirelessled.

The GUI will not function!

Troubleshooting Tip:  Use 'sudo locate wirelessled' to find driver path
 and borwse to path.

////////////////////////
arjun@arjun-laptop:~$ sudo -s
root@arjun-laptop:~# modprobe acerhk
root@arjun-laptop:~# echo 1 > /proc/driver/acerhk/wirelessled
root@arjun-laptop:~# 
//////////////////////

acer travelmate 291LMi

---

### Post by pytheas22 on 2009-11-15
Try changing the path under the AcerHK:GUI path for "Driver Path" to /proc/driver/acerhk.  Does this change anything?

---

### Post by arjunchandkn on 2009-11-15
screen shot

[http://picasaweb.google.com/arjunchandkn/Ubuntu#5404384520636134834](http://picasaweb.google.com/arjunchandkn/Ubuntu#5404384520636134834)


my physical switch is ON
led indicator is not glowing..


even after restarting system there was no change

now drivers are detected in acerhk gui[IMG]http://http://picasaweb.google.com/arjunchandkn/Ubuntu#5404384520636134834[/IMG]

---

### Post by pytheas22 on 2009-11-15
Even if you press the "Wireless Radio" on button in the GUI, then type "sudo iwlist scan", you don't see any networks?

---

### Post by arjunchandkn on 2009-11-15
i pressed wireless radio.... but no change
Driver Info (in acerhk gui)..... still it shows switch disabled even though the switch is in ON position
Acer hotkeys version 0.5.35
Model(Type)    : (old)
request handler    : 0xc00fdf1a
CMOS index    : 0x10
events pending    : 0
kernel polling    : active
autoswitch wlan    : disabled
preg400        : 0xe1000400

/////////

arjun@arjun-laptop:~$ sudo iwlist scan
[sudo] password for arjun: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning.


eth1      No scan results

---

### Post by arjunchandkn on 2009-11-15
here is some solution for the problem similar to mine....hope this helps you to customise solution for my problem
[http://ubuntuforums.org/archive/index.php/t-541953.html](http://ubuntuforums.org/archive/index.php/t-541953.html)

---

### Post by pytheas22 on 2009-11-16
Sorry for the slow response.  I did actually see that link before unfortunately, it covers laptops with Intel 2200 wireless, but yours is 2100, so the commands there for getting the LED to work won't apply.  But some of the other stuff might be helpful.  For instance, what is the output of:
```

sudo -s
cat /sys/class/net/*/device/rf_kill
echo 1 > /sys/class/net/*/device/rf_kill
rmmod acerhk
modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk/wirelessled
iwlist scan
uname -m
```

Does your LED work now?  If not, try flipping the switch and see if that helps.

---

### Post by arjunchandkn on 2009-11-17
finally the led is glowing and responding to the physical switch....

arjun@arjun-laptop:~$ sudo -s
[sudo] password for arjun: 
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill
2
root@arjun-laptop:~# echo 1 > /sys/class/net/*/device/rf_kill
root@arjun-laptop:~# rmmod acerhk
root@arjun-laptop:~# modprobe acerhk force_series=290 usedritek=1 verbose=1
root@arjun-laptop:~# echo 1 > /proc/driver/acerhk/wirelessled
root@arjun-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

root@arjun-laptop:~# uname -m
i686

---

### Post by arjunchandkn on 2009-11-17
finally the led responds to my physicsl switch.... it glowing.

BUT in acerhk gui preferences it shows

Acer hotkeys version 0.5.35
Model(Type)    : (Dritek)
request handler    : 0xc00fdf1a
CMOS index    : not available
kernel polling    : active
autoswitch wlan    : disabled
use of Dritek EC: enabled
---------------------

arjun@arjun-laptop:~$ sudo -s
[sudo] password for arjun: 
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill
2
root@arjun-laptop:~# echo 1 > /sys/class/net/*/device/rf_kill
root@arjun-laptop:~# rmmod acerhk
root@arjun-laptop:~# modprobe acerhk force_series=290 usedritek=1 verbose=1
root@arjun-laptop:~# echo 1 > /proc/driver/acerhk/wirelessled
root@arjun-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

root@arjun-laptop:~# uname -m
i686

---

### Post by pytheas22 on 2009-11-17
It's definitely good news that the LED lights up.  Does it turn off if you flip the switch for the wireless, or is it always on?

The trick to getting the wireless radio to turn on is to make the value of the file /sys/class/net/*/device/rf_kill be 1 instead of 2.  What happens if you type:
```

sudo -s
cat /sys/class/net/*/device/rf_kill
echo 1 > /sys/class/net/*/device/rf_kill
cat /sys/class/net/*/device/rf_kill
```

And if you flip the switch to turn wireless on and off, then type "cat /sys/class/net/*/device/rf_kill", is the value always 2 or does it change to 1?

Also, you should run this command once so the acerhk module is always loaded with the correct options when you boot:
```

echo acerhk force_series=290 usedritek=1 verbose=1 | sudo tee -a /etc/modules
```

Finally, it would not hurt to see the output of this command after doing all of the stuff above to check if any useful information shows up in dmesg about all this:

```
dmesg | grep -ie acerhk -ie radio -e wlan -e ipw
```

---

### Post by arjunchandkn on 2009-11-17
after restart again wifi led not glowing.....before restart the led would come when i switch ON wifi switch and led goes off when wifi switch is OFF.


arjun@arjun-laptop:~$ sudo -s
[sudo] password for arjun: 
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill
2
root@arjun-laptop:~# echo 1 > /sys/class/net/*/device/rf_kill     
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill                                -------------//physical switch on
3
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill--------------                               //physical switch off
3
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill
3
root@arjun-laptop:~# echo acerhk force_series=290 usedritek=1 verbose=1 | sudo tee -a /etc/modules
acerhk force_series=290 usedritek=1 verbose=1
root@arjun-laptop:~# dmesg | grep -ie acerhk -ie radio -e wlan -e ipw
[   11.980884] acerhk: Could not find model string, will assume type 200 series
[   12.205842] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   12.205848] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   12.206042] ipw2100 0000:02:02.0: power state changed by ACPI to D0
[   12.206058] ipw2100 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   12.206735] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   12.206759] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3.fw
[   14.320259] eth1: Radio is disabled by RF switch.
[   72.336306] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3-i.fw
[   72.944274] eth1: Radio is disabled by RF switch.


**since the led was not working i tried the set of code which u gave earlier but still led not glowing.. the output is**


arjun@arjun-laptop:~$ sudo -s
[sudo] password for arjun: 
root@arjun-laptop:~# cat /sys/class/net/*/device/rf_kill3
root@arjun-laptop:~# echo 1 > /sys/class/net/*/device/rf_kill
root@arjun-laptop:~# rmmod acerhk
root@arjun-laptop:~# modprobe acerhk force_series=290 usedritek=1 verbose=1echo 1 > /proc/driver/acerhk/wirelessled
bash: /proc/driver/acerhk/wirelessled: No such file or directory
root@arjun-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

root@arjun-laptop:~# uname -m
i686


[B]still the led is not glowing


acerhkgui preference 

[/B]Acer hotkeys version 0.5.35
Model(Type)    : (old)
request handler    : 0xc00fdf1a
CMOS index    : 0x10
events pending    : 0
kernel polling    : active
autoswitch wlan    : disabled
preg400        : 0xe190c400

do observe the change in preferences of acerhk gui[B]...
[/B]

---

### Post by pytheas22 on 2009-11-17
I'm not really sure what the changes in acerhk preferences mean, unfortunately. But I'm wondering if there's another file somewhere that might relate to forcing the wireless on.  What is the output of:
```

sudo updatedb
locate rfkill | grep -e sys -e proc
locate wireless | grep -e sys -e proc
locate radio | grep -e sys -e proc
```

---

### Post by arjunchandkn on 2009-11-18
arjun@arjun-laptop:~$ sudo updatedb
[sudo] password for arjun: 
arjun@arjun-laptop:~$ sudo updatedb
arjun@arjun-laptop:~$ locate rfkill | grep -e sys -e proc
arjun@arjun-laptop:~$ locate wireless | grep -e sys -e proc
/home/arjun/.gconf/system/networking/connections/1/802-11-wireless
/home/arjun/.gconf/system/networking/connections/1/802-11-wireless-security
/home/arjun/.gconf/system/networking/connections/1/802-11-wireless/%gconf.xml
/home/arjun/.gconf/system/networking/connections/1/802-11-wireless-security/%gconf.xml
/home/arjun/.gconf/system/networking/connections/2/802-11-wireless
/home/arjun/.gconf/system/networking/connections/2/802-11-wireless-security
/home/arjun/.gconf/system/networking/connections/2/802-11-wireless/%gconf.xml
/home/arjun/.gconf/system/networking/connections/2/802-11-wireless-security/%gconf.xml
/usr/src/linux-headers-2.6.28-15-generic/include/config/wireless/ext/sysfs.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/wireless/ext/sysfs.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/wireless/ext/sysfs.h
arjun@arjun-laptop:~$ locate radio | grep -e sys -e proc
/usr/lib/jruby1.1/share/ri/1.8/system/CGI/HtmlExtension/radio_button-i.yaml
/usr/lib/jruby1.1/share/ri/1.8/system/CGI/HtmlExtension/radio_group-i.yaml
/usr/src/linux-headers-2.6.28-15-generic/include/config/radio/typhoon/proc
/usr/src/linux-headers-2.6.28-15-generic/include/config/radio/typhoon/proc/fs.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/radio/typhoon/proc
/usr/src/linux-headers-2.6.28-16-generic/include/config/radio/typhoon/proc/fs.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/radio/typhoon/proc
/usr/src/linux-headers-2.6.31-14-generic/include/config/radio/typhoon/proc/fs.h
arjun@arjun-laptop:~$

---------------------------------------

why is the led glow only once???? is every thing ok???

---

### Post by pytheas22 on 2009-11-18
Try rebooting, then type:
```

sudo modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
```

Does the led light up now?

---

### Post by arjunchandkn on 2009-11-18
**when the physicall switch is ON**
arjun@arjun-laptop:~$ sudo modprobe acerhk force_series=290 usedritek=1 verbose=1
[sudo] password for arjun: 
arjun@arjun-laptop:~$ echo 1 | sudo tee /proc/driver/acerhk/wirelessled
1


**when the physicall switch is OFF**
arjun@arjun-laptop:~$ sudo modprobe acerhk force_series=290 usedritek=1 verbose=1
arjun@arjun-laptop:~$ echo 1 | sudo tee /proc/driver/acerhk/wirelessled1

no wifi led is not working

---

### Post by pytheas22 on 2009-11-18
hmmmm, maybe it doesn't like the tee.  Does the led glow after a fresh reboot if you do:
```

sudo -s
rmmod acerhk
modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk/wirelessled
```

Again, I'm really sorry this is not going as smoothly as I'm sure you'd like.  I'm doing my best but a lot of this is new territory for me, and I can't find anyone on Google who's dealt with this same issue before (the thread you linked to a couple days ago was close, but in that case the wireless card was a little different than yours).

---

### Post by arjunchandkn on 2009-11-19
arjun@arjun-laptop:~$ sudo -s
[sudo] password for arjun: 
root@arjun-laptop:~# rmmod acerhk
root@arjun-laptop:~# modprobe acerhk force_series=290 usedritek=1 verbose=1
root@arjun-laptop:~# echo 1 > /proc/driver/acerhk/wirelessled
-------------

ya... after executing the code led responds to the switch....

OMG!!!!!!!!  my wifi is working..... i can connect to internet via wifi

[COLOR=Red]THANKS A TON[/COLOR] for ur time....

Can you give me exactly what all to be done to rectify this problem..... will be helpful for others and also me if this problem arises again...

[COLOR=Red]THANKS AGAIN[/COLOR]

---

### Post by arjunchandkn on 2009-11-19
i have a lot of files related to wifi which we have downloaded on the desktop.... can i delete those?????

what to do to make this settings work permanently

---

### Post by pytheas22 on 2009-11-19
I'm really, really glad to hear it worked :)  I was beginning to lose hope and was really perplexed as to what was wrong.

> i have a lot of files related to wifi which we have downloaded on the desktop.... can i delete those?????

Yes.  Anything on your desktop or in your /home folder can be deleted.
> 
what to do to make this settings work permanently

To make this permanent, the easiest way will probably be to write a boot script that will run those three commands (the ones that made things work) each time you boot.  To do that, type:
```

sudo -s
echo -e "#/bin/bash\n\nrmmod acerhk\nmodprobe acerhk force_series=290 usedritek=1 verbose=1\necho 1 > /proc/driver/acerhk/wirelessled" > /etc/init.d/wifi-fix.sh
cd /etc/init.d
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults
```

(Make sure to copy those commands exactly; copy and paste if possible.)

Then reboot and hopefully the wireless will be working on its own.  If not, please post the output of:
```

cat /etc/init.d/wifi-fix.sh
ls -l /etc/init.d/wifi-fix.sh
```

---

### Post by arjunchandkn on 2009-11-20
write a boot script???? 

I have to just copy and paste the commands into the terminal....am i correct?

-------------------------------
arjun@arjun-laptop:~$ sudo -s
[sudo] password for arjun: 
Sorry, try again.
[sudo] password for arjun: 
root@arjun-laptop:~# echo -e "#/bin/bash\n\nrmmod acerhk\nmodprobe acerhk force_series=290 usedritek=1 verbose=1\necho 1 > /proc/driver/acerhk/wirelessled" > /etc/init.d/wifi-fix.sh
root@arjun-laptop:~# cd /etc/init.d
root@arjun-laptop:/etc/init.d# chmod +x wifi-fix.sh
root@arjun-laptop:/etc/init.d# update-rc.d wifi-fix.sh defaultsupdate-rc.d: warning: /etc/init.d/wifi-fix.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/wifi-fix.sh ...
   /etc/rc0.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc1.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc6.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc2.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc3.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc4.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc5.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
root@arjun-laptop:/etc/init.d# 
-----------------------------------------------
after restart wifi led started responding to the switch
its identifying all the all the available networks..... but not able to connect.... i dont know why.

did restart again and still no use... wifi led and every thing is OK but not able to connect to internet
when i elect network name and give network key it keeps on searching.... does not connect

where did i go wrong

//////////////////////////////////

arjun@arjun-laptop:~$ cat /etc/init.d/wifi-fix.sh
#/bin/bash

rmmod acerhk
modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk/wirelessled
arjun@arjun-laptop:~$ ls -l /etc/init.d/wifi-fix.sh
-rwxr-xr-x 1 root root 121 2009-11-20 01:51 /etc/init.d/wifi-fix.sh
arjun@arjun-laptop:~$

---

### Post by pytheas22 on 2009-11-20
Yes, you just needed to copy and paste those commands.  The boot script should be working.  It does the same thing that you did when manually entering the commands before, so I'm not sure why you can't connect now.  But you may have better luck connecting using wicd.  To install wicd, type:
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Are you able to connect with this program?

Note that installing wicd will force you to uninstall NetworkManager (your current connection manager).  If you want NM back, just type:
```

sudo apt-get install network-manager-gnome
```

---

### Post by arjunchandkn on 2009-11-20
[http://picasaweb.google.com/arjunchandkn/Ubuntu#5406334190482374290](http://picasaweb.google.com/arjunchandkn/Ubuntu#5406334190482374290)

i tried with other networks also but its showing the same thing..."connection failed unable to get ip address"

i tried changing from wpa2 to wpe, reset my password... still getting the same message
[IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5406334190482374290[/IMG][IMG]http://ubuntuforums.org/home/arjun/Desktop/Screenshot.png[/IMG]

---

### Post by pytheas22 on 2009-11-21
That's strange.  Please try connecting to your network a few times, then run the following commands and post the output:
```

dmesg | grep -e wlan -e ipw
grep -e wlan -i ipw /var/log/syslog
sudo iwlist scan
```

That should hopefully provide some feedback that can be used for troubleshooting.

---

### Post by arjunchandkn on 2009-11-21
after reinstalling wicd now my wifi is working perfectly.... thanks

---

### Post by pytheas22 on 2009-11-22
Very good to hear; let me know if you have any other problems; otherwise, thanks for your patience through all this and hope you enjoy Ubuntu.

---

### Post by arjunchandkn on 2009-11-22
:Dok... thanks for your help and support.... keep going

---

### Post by apmjoshi on 2010-01-19
Hello pytheas22,

I tried your solution on my old ACER Travelmate 290 which also uses ipw2100 but it does not work. I have a dual-boot set-up with Win XP and Ubuntu 9.10. There is a hardware switch on the laptop and it is always in the ON position. My symptoms are
- wireless always works on Windows
- if I boot in Windows and then restart into Ubuntu (wireless LED glowing throughout this process) then wireless works in Ubuntu
- if I boot into Ubuntu directly, wireless does not work.

Based on this I can infer that this is something to do with the sequence of loading the driver, but am not able to progress further. Any help in resolving this is much appreciated.

Aniruddha

---

### Post by pytheas22 on 2010-01-19
apmjoshi: what exactly did you already do in trying to get this working?  Did you install the acerhk module by following the commands in post #38 of this thread?  What is the output of these commands:

```
dmesg | grep -ie radio
sudo updatedb; locate acer
sudo iwlist scan
lshw -C Network
```

---

### Post by apmjoshi on 2010-01-20
pytheas22,

First of all, thanks for your quick reply. My responses may be a little delayed given the time difference.

I did not follow the instructions in post #38 since I could already see [FONT="Courier New"]acerhk.ko[/FONT] file in [FONT="Courier New"]/lib/modules/2.6.31-17-generic/extra[/FONT]
Instead I followed the steps in post #59 assuming those gave the 'final' solution[FONT="Arial"][/FONT]

The output of the diagnostic commands you asked for is as follows:

```
andy@andy-laptop:~$ dmesg | grep -ie radio
[   25.836259] eth1: Radio is disabled by RF switch.
```

```
andy@andy-laptop:~$ sudo updatedb; locate acer
[sudo] password for andy: 
/etc/alternatives/traceroute6
/etc/alternatives/traceroute6.8.gz
/etc/init.d/acerhkwireless
/etc/java-6-sun/security/cacerts
/etc/rcS.d/S39acerhkwireless
/etc/ssl/certs/cacert.org.pem
/etc/ssl/certs/spi-cacert-2008.pem
/home/andy/acerhk-0.5.35
/home/andy/acerhk.ko.1
/home/andy/acerwificontroller
/home/andy/.config/acerhkgui
/home/andy/.config/acerhkgui/acerhkgui.conf
/home/andy/.config/acerhkgui/acerhkgui.conf.bak
/home/andy/.cpan/build/Crypt-SSLeay-0.57/certs/notacacert.pem
/home/andy/Downloaded Stuff/acerhkgui_0.7_i386.deb
/home/andy/Downloaded Stuff/acerwificontroller.c
/home/andy/Downloaded Stuff/acerwificontroller_disable.sh
/home/andy/Downloaded Stuff/acerwificontroller_enable.sh
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts/BTCTRoot.crt
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts/Class3PCA_G2_v2.crt
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts/Class4PCA_G2_v2.crt
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts/GTECTGlobalRoot.crt
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts/Pcs3ss_v4.crt
/home/andy/Downloaded Stuff/citrix-install/linuxx86/linuxx86.cor/keystore/cacerts/SecureServer.crt
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts/BTCTRoot.crt
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts/Class3PCA_G2_v2.crt
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts/Class4PCA_G2_v2.crt
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts/GTECTGlobalRoot.crt
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts/Pcs3ss_v4.crt
/home/andy/Downloaded Stuff/linuxx86/linuxx86.cor/keystore/cacerts/SecureServer.crt
/home/andy/acerhk-0.5.35/AUTHORS
/home/andy/acerhk-0.5.35/COPYING
/home/andy/acerhk-0.5.35/INSTALL
/home/andy/acerhk-0.5.35/Makefile
/home/andy/acerhk-0.5.35/NEWS
/home/andy/acerhk-0.5.35/README
/home/andy/acerhk-0.5.35/acerhk.c
/home/andy/acerhk-0.5.35/acerhk.h
/home/andy/acerhk-0.5.35/doc
/home/andy/acerhk-0.5.35/doc/FAQ
/home/andy/acerhk-0.5.35/doc/IOCTL
/home/andy/acerhk-0.5.35/doc/acertm.def
/home/andy/acerhk-0.5.35/doc/keycodes
/home/andy/acerhk-0.5.35/doc/md95400.def
/home/andy/acerwificontroller/AUTHORS
/home/andy/acerwificontroller/AcerWifiController_Factory.server
/home/andy/acerwificontroller/COPYING
/home/andy/acerwificontroller/ChangeLog
/home/andy/acerwificontroller/INSTALL
/home/andy/acerwificontroller/Makefile
/home/andy/acerwificontroller/NEWS
/home/andy/acerwificontroller/README
/home/andy/acerwificontroller/acerwificontroller.c
/home/andy/acerwificontroller/acerwificontroller_disable.sh
/home/andy/acerwificontroller/acerwificontroller_enable.sh
/lib/modules/2.6.31-14-generic/extra/acerhk.ko
/lib/modules/2.6.31-16-generic/kernel/drivers/platform/x86/acer-wmi.ko
/lib/modules/2.6.31-16-generic/kernel/drivers/platform/x86/acerhdf.ko
/lib/modules/2.6.31-17-generic/extra/acerhk.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/platform/x86/acer-wmi.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/platform/x86/acerhdf.ko
/lib/udev/keymaps/acer
/lib/udev/keymaps/acer-aspire_5920g
/lib/udev/keymaps/acer-aspire_6920
/lib/udev/keymaps/acer-travelmate_c300
/usr/bin/acerhkgui
/usr/bin/traceroute6
/usr/bin/traceroute6.iputils
/usr/lib/ICAClient/keystore/cacerts
/usr/lib/ICAClient/keystore/cacerts/BTCTRoot.crt
/usr/lib/ICAClient/keystore/cacerts/Class3PCA_G2_v2.crt
/usr/lib/ICAClient/keystore/cacerts/Class4PCA_G2_v2.crt
/usr/lib/ICAClient/keystore/cacerts/GTECTGlobalRoot.crt
/usr/lib/ICAClient/keystore/cacerts/Pcs3ss_v4.crt
/usr/lib/ICAClient/keystore/cacerts/SecureServer.crt
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/security/cacerts
/usr/share/acerhkgui
/usr/share/acerhkgui/AcerHK.png
/usr/share/acerhkgui/AcerHK_50.png
/usr/share/acerhkgui/acerhkgui-prefs.glade
/usr/share/acerhkgui/acerhkgui.glade
/usr/share/acerhkgui/acerhkguiPreferences.py
/usr/share/acerhkgui/acerhkguiPreferences.py.bak
/usr/share/acerhkgui/acerhkguiPreferences.py~
/usr/share/acerhkgui/gpl.txt
/usr/share/acerhkgui/readme.txt
/usr/share/acerhkgui/source
/usr/share/acerhkgui/source/Unsaved Document 1
/usr/share/acerhkgui/source/acerhk_bt_gui.wxg
/usr/share/acerhkgui/source/acerhk_classes-functions-variables.txt
/usr/share/acerhkgui/source/acerhkgui_gtk-gui_prefs_DriverPathSelect.jpeg
/usr/share/acerhkgui/source/acerhkgui_gtk-gui_prefs_driverInfo.jpeg
/usr/share/acerhkgui/source/acerhkgui_gtk-gui_v3_screenshot.jpg
/usr/share/app-install/desktop/extremetuxracer.desktop
/usr/share/app-install/desktop/pyracerz.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_etracer.xpm
/usr/share/app-install/icons/_usr_share_pixmaps_pyracerz.xpm
/usr/share/applications/acerhkgui.desktop
/usr/share/ca-certificates/cacert.org
/usr/share/ca-certificates/cacert.org/cacert.org.crt
/usr/share/ca-certificates/spi-inc.org/spi-cacert-2008.crt
/usr/share/doc/acerhkgui
/usr/share/doc/acerhkgui/acerhkgui.text.gz
/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-acer.fdi
/usr/share/man/man1/acerhkgui.txt
/usr/share/man/man8/traceroute6.8.gz
/usr/share/man/man8/traceroute6.iputils.8.gz
/usr/src/linux-headers-2.6.31-14-generic/include/config/acer
/usr/src/linux-headers-2.6.31-14-generic/include/config/acerhdf.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/acer/wmi.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/context/switch/tracer.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/generic/tracer.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/have/function/tracer.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/have/function/graph/tracer.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/nop/tracer.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/acer
/usr/src/linux-headers-2.6.31-15-generic/include/config/acerhdf.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/acer/wmi.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/context/switch/tracer.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/generic/tracer.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/have/function/tracer.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/have/function/graph/tracer.h
/usr/src/linux-headers-2.6.31-15-generic/include/config/nop/tracer.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/acer
/usr/src/linux-headers-2.6.31-16-generic/include/config/acerhdf.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/acer/wmi.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/context/switch/tracer.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/generic/tracer.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/have/function/tracer.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/have/function/graph/tracer.h
/usr/src/linux-headers-2.6.31-16-generic/include/config/nop/tracer.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/acer
/usr/src/linux-headers-2.6.31-17-generic/include/config/acerhdf.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/acer/wmi.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/context/switch/tracer.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/generic/tracer.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/have/function/tracer.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/have/function/graph/tracer.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/nop/tracer.h
/var/lib/dpkg/alternatives/traceroute6
/var/lib/dpkg/info/acerhkgui.README
/var/lib/dpkg/info/acerhkgui.changelog
/var/lib/dpkg/info/acerhkgui.copyright
/var/lib/dpkg/info/acerhkgui.dirs
/var/lib/dpkg/info/acerhkgui.list
/var/lib/dpkg/info/acerhkgui.rules
```

```
andy@andy-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
```

```
andy@andy-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:14:ba:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:20:77:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:10 memory:d0000000-d0000fff


```

Thanks for your help once again.

---

### Post by pytheas22 on 2010-01-20
Do you have the acerhk GUI program installed?  Does that allow you to toggle the wireless radio on and off?

What happens if you type:
```

sudo -s
modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk
```

Does the wireless work now?

---

### Post by apmjoshi on 2010-01-21
Hi,

I have acerhk GUI installed, but it does not work i.e. has no effect on wireless. When it starts, it says that acerhk was found in the expected location (probably because I did set the driver path correctly) but after that gives error that the driver did not load. The code you asked me to run also gives the same error

```
andy@andy-laptop:~$ sudo -s 
[sudo] password for andy: 
root@andy-laptop:~# modprobe acerhk force_series=290 usedritek=1 verbose=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'options'
FATAL: Module acerhk not found.
root@andy-laptop:~# echo 1 > /proc/driver/acerhk
bash: /proc/driver/acerhk: No such file or directory
root@andy-laptop:~# cd /proc/driver
root@andy-laptop:/proc/driver# ls
pktcdvd  rtc  snd-page-alloc
root@andy-laptop:/proc/driver# ls -l
total 0
dr-xr-xr-x 2 root root 0 2010-01-21 22:43 pktcdvd
-r--r--r-- 1 root root 0 2010-01-21 22:43 rtc
-rw-r--r-- 1 root root 0 2010-01-21 22:43 snd-page-alloc
root@andy-laptop:/proc/driver# echo 1 > acerhk
bash: acerhk: No such file or directory
root@andy-laptop:/proc/driver# 


```

I don't know why the last echo does not work. That should just create a file with 1 in it, correct?

I have tried instructions from this post [http://ubuntuforums.org/showthread.php?t=541953](http://ubuntuforums.org/showthread.php?t=541953) also by changing ipw2200 to ipw2100 but it did not work. 

Anyway, thanks for your continued help.

Regards
Andy

---

### Post by apmjoshi on 2010-01-21
I realised that even with sudo I don't have permissions to write to /proc/driver so I did
```
chmod +w .
```
and tried again, but get the same error (no such file or directory).

---

### Post by pytheas22 on 2010-01-21
This error:
```

FATAL: Module acerhk not found
```

means that you actually don't have the acerhk driver installed.  You might have the other utilities, but without the acerhk module, it won't work.

Please try running the commands in post #38; they will compile and install the acerhk module for you.  After it's installed, please run these commands again:
```

sudo rmmod acerhk
sudo modprobe acerhk force_series=290 usedritek=1 verbose=1
```

Then see if you can turn the wireless radio on either using the acerhk GUI, or by echoing 1 into the file /proc/driver/acerhk.

Also, what did you give the acerhk GUI as the driver path?

---

### Post by apmjoshi on 2010-01-22
Ok, I will give it a try, but don't understand how wireless works when I restart from Windows. Will post the results later on.

The driver path that I gave was /lib/modules/2.6.31-17-generic/extra/ where there is a file called acerhk.ko

Regards
Andy

---

### Post by apmjoshi on 2010-01-28
Hello all,

After recompiling acerhk module as suggested by pytheas22 my wireless is working fine now. I am an Ubuntu fan once again :-)
I have not tried to use the Acerhk GUI again as I don't want to screw up the set-up again.

Pytheas22, thanks a lot for your help.

Just out of curiosity, if anyone has any theories about why wireless would work when the laptop was restarted from Windows XP, I will be interested to learn more.

Regards
Andy

---

### Post by pytheas22 on 2010-01-28
Glad you got it working.  There are still some aspects of your situation that remain unclear to me--e.g., why the wireless worked after booting from Windows--but good to know it's fixed now.

Keep in mind that if you upgrade your kernel via the Ubuntu updates, you will probably need to compile the acerhk module again in order for it to work on the new kernel.

---

### Post by arjunchandkn on 2010-05-28
sorry to ask again.:(

I have now updates from 9.10 to 10.04... again I am not able to activate wifi.. 

i tried the previous steps but failed to activate wifi... can you help me again in this????

my kernel is 2.6.32-22-generic

i have installed latest acerhk gui and it shows

[COLOR=Purple]The AcerHK module was not found. [/COLOR]

[COLOR=Purple]Checking for plugin (acerhk.ko).
If not found, will attempt to download 
and install the 32bit version if required.

Then it will try to run 'modprobe' to load driver.

Your sudo password will be required. 

CANCEL if you are running a 64-bit OS.

OK button
[/COLOR]

when i press ok  i get 

[COLOR=Purple]The acerhk.ko module was not found at expected location.

 It has been downloaded and installed if you have
a working internet connection.[/COLOR]
[COLOR=Cyan]
[COLOR=Black]after giving password i get [/COLOR][/COLOR]

[COLOR=Purple]NOTE:  The acerhk module failed to load!

Your hardware maynot be compatable!

Check website [http://rfswitch.sourceforge.net](http://rfswitch.sourceforge.net) 
for more information.[/COLOR]

---

### Post by arjunchandkn on 2010-05-28
arjun@ubuntu:/$ **[COLOR=Red]dmesg | grep -ie radio[/COLOR]**     //when the physical switch is off
[    7.660279] eth1: Radio is disabled by RF switch.

arjun@ubuntu:/$ [COLOR=Red]**dmesg | grep -ie radio** [/COLOR]    //when the physical switch is on
[    7.660279] eth1: Radio is disabled by RF switch.

arjun@ubuntu:/$ **[COLOR=Red]sudo updatedb; locate acer[/COLOR]**
[sudo] password for arjun: 
/etc/alternatives/traceroute6
/etc/alternatives/traceroute6.8.gz
/etc/default/cacerts
/etc/java/cacerts-gcj
/etc/ssl/certs/cacert.org.pem
/etc/ssl/certs/spi-cacert-2008.pem
/etc/ssl/certs/java/cacerts
/home/arjun/acerhk-0.5.35
/home/arjun/acerhk-fixed.tar.bz2
/home/arjun/acerhk-fixed.tar.bz2.1
/home/arjun/acerhk-fixed.tar.bz2.2
/home/arjun/acerhk-fixed.tar.bz2.3
/home/arjun/acerhk-fixed.tar.bz2.4
/home/arjun/acerhkgui_0.6_i386.deb
/home/arjun/.config/acerhkgui
/home/arjun/.config/acerhkgui/acerhkgui.conf
/home/arjun/Downloads/acerhkgui_0.7.1_all.deb
/home/arjun/Downloads/acerhkgui_0.7_i386(2).deb
/home/arjun/Downloads/acerhkgui_0.7_i386.deb
/home/arjun/acerhk-0.5.35/.tmp_versions
/home/arjun/acerhk-0.5.35/AUTHORS
/home/arjun/acerhk-0.5.35/COPYING
/home/arjun/acerhk-0.5.35/INSTALL
/home/arjun/acerhk-0.5.35/Makefile
/home/arjun/acerhk-0.5.35/Module.markers
/home/arjun/acerhk-0.5.35/Module.symvers
/home/arjun/acerhk-0.5.35/NEWS
/home/arjun/acerhk-0.5.35/README
/home/arjun/acerhk-0.5.35/acerhk.c
/home/arjun/acerhk-0.5.35/acerhk.h
/home/arjun/acerhk-0.5.35/doc
/home/arjun/acerhk-0.5.35/modules.order
/home/arjun/acerhk-0.5.35/.tmp_versions/acerhk.mod
/home/arjun/acerhk-0.5.35/doc/FAQ
/home/arjun/acerhk-0.5.35/doc/IOCTL
/home/arjun/acerhk-0.5.35/doc/acertm.def
/home/arjun/acerhk-0.5.35/doc/keycodes
/home/arjun/acerhk-0.5.35/doc/md95400.def
/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/acer-wmi.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/acerhdf.ko
/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acer-wmi.ko
/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acerhdf.ko
/lib/udev/keymaps/acer
/lib/udev/keymaps/acer-aspire_5720
/lib/udev/keymaps/acer-aspire_5920g
/lib/udev/keymaps/acer-aspire_6920
/lib/udev/keymaps/acer-travelmate_c300
/usr/bin/acerhkgui
/usr/bin/traceroute6
/usr/bin/traceroute6.iputils
/usr/lib/jvm/java-1.5.0-gcj-4.4/jre/lib/cacerts
/usr/lib/jvm/java-6-openjdk/jre/lib/security/cacerts
/usr/lib/pm-utils/video-quirks/20-video-quirk-pm-acer.quirkdb
/usr/share/acerhkgui
/usr/share/acerhkgui/AcerHK.png
/usr/share/acerhkgui/AcerHK_50.png
/usr/share/acerhkgui/acerhkgui-prefs.glade
/usr/share/acerhkgui/acerhkgui.glade
/usr/share/acerhkgui/acerhkguiPreferences.py
/usr/share/acerhkgui/acerhkguiPreferences.py.bak
/usr/share/acerhkgui/acerhkguiPreferences.py~
/usr/share/acerhkgui/gpl.txt
/usr/share/acerhkgui/readme.txt
/usr/share/acerhkgui/source
/usr/share/acerhkgui/source/Unsaved Document 1
/usr/share/acerhkgui/source/acerhk_bt_gui.wxg
/usr/share/acerhkgui/source/acerhk_classes-functions-variables.txt
/usr/share/acerhkgui/source/acerhkgui_gtk-gui_prefs_DriverPathSelect.jpeg
/usr/share/acerhkgui/source/acerhkgui_gtk-gui_prefs_driverInfo.jpeg
/usr/share/acerhkgui/source/acerhkgui_gtk-gui_v3_screenshot.jpg
/usr/share/app-install/desktop/extremetuxracer.desktop
/usr/share/app-install/desktop/pyracerz.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_etracer.xpm
/usr/share/app-install/icons/pyracerz.xpm
/usr/share/applications/acerhkgui.desktop
/usr/share/ca-certificates/cacert.org
/usr/share/ca-certificates/cacert.org/cacert.org.crt
/usr/share/ca-certificates/spi-inc.org/spi-cacert-2008.crt
/usr/share/ca-certificates-java/cacerts
/usr/share/doc/acerhk-source
/usr/share/doc/acerhkgui
/usr/share/doc/acerhk-source/FAQ.gz
/usr/share/doc/acerhk-source/NEWS.gz
/usr/share/doc/acerhk-source/README.Debian
/usr/share/doc/acerhk-source/README.gz
/usr/share/doc/acerhk-source/changelog.Debian.gz
/usr/share/doc/acerhk-source/copyright
/usr/share/doc/acerhkgui/acerhkgui.text.gz
/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-acer.fdi
/usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi
/usr/share/man/man1/acerhkgui.txt
/usr/share/man/man8/traceroute6.8.gz
/usr/share/man/man8/traceroute6.iputils.8.gz
/usr/src/acerhk.tar.bz2
/usr/src/linux-headers-2.6.32-22-generic/include/config/acer
/usr/src/linux-headers-2.6.32-22-generic/include/config/acerhdf.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/acer/wmi.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/context/switch/tracer.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/function/tracer.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/function/graph/tracer.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/generic/tracer.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/have/function/tracer.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/have/function/graph/tracer.h
/usr/src/linux-headers-2.6.32-22-generic/include/config/nop/tracer.h
/var/cache/apt/archives/acerhk-source_0.5.35-8_all.deb
/var/lib/dpkg/alternatives/traceroute6
/var/lib/dpkg/info/acerhk-source.list
/var/lib/dpkg/info/acerhk-source.md5sums
/var/lib/dpkg/info/acerhkgui.README
/var/lib/dpkg/info/acerhkgui.changelog
/var/lib/dpkg/info/acerhkgui.control~
/var/lib/dpkg/info/acerhkgui.copyright
/var/lib/dpkg/info/acerhkgui.dirs
/var/lib/dpkg/info/acerhkgui.list
/var/lib/dpkg/info/acerhkgui.rules
arjun@ubuntu:/$ s[COLOR=Red]udo locate wirelessled[/COLOR]

arjun@ubuntu:/$ [COLOR=Red]sudo iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

arjun@ubuntu:/$[COLOR=Red]** lshw -C Network**[/COLOR]
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:14:6a:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.11 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:1e:3f:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:10 memory:d0000000-d0000fff
arjun@ubuntu:/$

---

### Post by arjunchandkn on 2010-05-28
i forgot to say one more thing.... now i am using dual boot.... windows7 and lucid.... I have the same problem what [apmjoshi ]("http://ubuntuforums.org/member.php?u=365157")
was saying.... my wifi led responds to hardware switch if i first go to win7 and then go to lucid..... ( no need to install  acerhk at all )

If i directly go to lucid wifi led doesnot respond to hardware switch.

---

### Post by pytheas22 on 2010-05-29
Please try running this command, which will insert the acer-wmi module and should allow you to turn on your wireless:

```
sudo modprobe acer-wmi
```

If you get an error message, post it here, along with the output of:
```

dmesg | grep -e acer -ie radio
```

If you don't get any errors, see if you can enable the wireless after the module is inserted.

---

### Post by arjunchandkn on 2010-05-29
arjun@ubuntu:~$ [COLOR=DarkGreen]sudo modprobe acer-wmi[/COLOR]
[sudo] password for arjun: 
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device

arjun@ubuntu:~$ [COLOR=DarkGreen]dmesg | grep -e acer -ie radio[/COLOR]                           // my physical switch is swithced ON
[    0.000000] ACPI: FACP 4ffffb00 00074 (v01 ACER   DCL56    00000200 _CSI 00010101)
[    0.000000] ACPI: DSDT 4fffac70 04E8A (v01 ACER     0860   00000006 MSFT 0100000E)
[   23.491039] acer-wmi: Acer Laptop ACPI-WMI Extras
[   23.491064] acer-wmi: No or unsupported WMI interface, unable to load
[   24.293049] eth1: Radio is disabled by RF switch.
[10816.552257] eth1: Radio is disabled by RF switch.
[10861.768251] eth1: Radio is disabled by RF switch.
[10903.136466] eth1: Radio is disabled by RF switch.
[11455.109796] acer-wmi: Acer Laptop ACPI-WMI Extras
[11455.109843] acer-wmi: No or unsupported WMI interface, unable to load

---

### Post by pytheas22 on 2010-05-30
That's kind of a strange error when trying to insert the acer-wmi module.  Does it work any better if you type:
```

sudo modprobe acerhk force-series=290 dritek=1
```

If that proceeds without error, try turning the wireless on.  If the wireless key still doesn't work, try forcing it on with:

```
sudo -s
echo 1 > /proc/driver/acerhk/wirelessled
```

Hopefully that will make the wireless LED light up.

For reference, I'm getting most of this from [here]("http://www.linux-club.de/viewtopic.php?f=19&t=107018&start=0").

---

### Post by arjunchandkn on 2010-05-30
```
arjun@ubuntu:~/acerhk-0.5.35$ sudo modprobe acerhk force-series=290 dritek=1
FATAL: Module acerhk not found.

```I tried installing acerhk module... but did not succeed

```

arjun@ubuntu:~$ wget [http://www.edbl.no/karmic/acerhk-fixed.tar.bz2](http://www.edbl.no/karmic/acerhk-fixed.tar.bz2)
--2010-05-30 21:47:52--  [http://www.edbl.no/karmic/acerhk-fixed.tar.bz2](http://www.edbl.no/karmic/acerhk-fixed.tar.bz2)
Resolving [www.edbl.no]("http://www.edbl.no")... 62.89.32.153
Connecting to [www.edbl.no|62.89.32.153|:80]("http://www.edbl.no%7C62.89.32.153%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33505 (33K) [application/x-tar]
Saving to: `acerhk-fixed.tar.bz2.7'

100%[======================================>] 33,505      77.7K/s   in 0.4s    

2010-05-30 21:47:53 (77.7 KB/s) - `acerhk-fixed.tar.bz2.7' saved [33505/33505]

arjun@ubuntu:~$ tar -xjvf acerhk-fixed.tar.bz2 
tar: Record size = 8 blocks
acerhk-0.5.35/
acerhk-0.5.35/.tmp_versions/
acerhk-0.5.35/doc/
acerhk-0.5.35/NEWS
acerhk-0.5.35/INSTALL
acerhk-0.5.35/README
acerhk-0.5.35/COPYING
acerhk-0.5.35/AUTHORS
acerhk-0.5.35/acerhk.c
acerhk-0.5.35/acerhk.h
acerhk-0.5.35/modules.order
acerhk-0.5.35/Module.symvers
acerhk-0.5.35/Makefile
acerhk-0.5.35/Module.markers
acerhk-0.5.35/.tmp_versions/acerhk.mod
acerhk-0.5.35/doc/FAQ
acerhk-0.5.35/doc/IOCTL
acerhk-0.5.35/doc/acertm.def
acerhk-0.5.35/doc/md95400.def
acerhk-0.5.35/doc/keycodes
arjun@ubuntu:~$ cd acer*
arjun@ubuntu:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/arjun/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/arjun/acerhk-0.5.35/acerhk.o
gcc: -pg and -fomit-frame-pointer are incompatible
make[2]: *** [/home/arjun/acerhk-0.5.35/acerhk.o] Error 1
make[1]: *** [_module_/home/arjun/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [acerhk.ko] Error 2
arjun@ubuntu:~/acerhk-0.5.35$ sudo make install
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [acerhk.ko] Error 2


```

---

### Post by pytheas22 on 2010-05-31
I tried compiling acerhk too and it didn't work.  I think probably it needs to be patched to compile against the Ubuntu 10.04 kernel.

However, acer-wmi is supposed to be a replacement for acerhk, if I understand correctly.  What happens if you run:
```

sudo modprobe acer-wmi force-series=290
```

Are you then able to enable the wireless?

---

### Post by arjunchandkn on 2010-05-31
arjun@ubuntu:~$ sudo modprobe acer-wmi force-series=290
[sudo] password for arjun: 
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device

---

### Post by pytheas22 on 2010-05-31
Thanks to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/555828"), I figured out how to compile acerhk from source on Ubuntu 10.04.

First, download Ubuntu's version of the source code by typing:
```

sudo apt-get install acerhk-source
```

After it's installed, type:
```

sudo gedit /usr/src/linux-headers-`uname -r`/Makefile
```

A file should open.  Search for the line that looks like this:
```

KBUILD_CFLAGS  += -pg
```

Comment out that line by placing a # in front of it, so it looks like:

```
#KBUILD_CFLAGS  += -pg
```

Then save and close the file.  You can now compile acerhk with these commands:

```
sudo -s
apt-get install build-essential
cd /usr/src/
tar -xjvf acerhk.tar.bz2
cd modules/acerhk
make
make install
```

After that's done, type:
```

sudo gedit /usr/src/linux-headers-`uname -r`/Makefile
```

again and undo the change you made previously to that file.

With all of the above completed, try inserting the module with:
```

sudo modprobe acerhk force-series=290 dritek=1
```

and hopefully it will finally do the trick and work!

---

### Post by arjunchandkn on 2010-06-01
still it is not working

```

arjun@ubuntu:~$ sudo apt-get install acerhk-source
[sudo] password for arjun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acerhk-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
arjun@ubuntu:~$ sudo gedit /usr/src/linux-headers-`uname -r`/Makefile
arjun@ubuntu:~$ sudo -s
root@ubuntu:~# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# cd /usr/src/
root@ubuntu:/usr/src# tar -xjvf acerhk.tar.bz2
tar: Record size = 8 blocks
modules/
modules/acerhk/
modules/acerhk/debian/
modules/acerhk/debian/control.modules.in
modules/acerhk/debian/docs
modules/acerhk/debian/rules
modules/acerhk/debian/changelog
modules/acerhk/debian/copyright
modules/acerhk/debian/compat
modules/acerhk/acerhk.c
modules/acerhk/acerhk.h
modules/acerhk/README
modules/acerhk/NEWS
modules/acerhk/Makefile
modules/acerhk/doc/
modules/acerhk/doc/FAQ
modules/acerhk/doc/IOCTL
modules/acerhk/doc/acertm.def
modules/acerhk/doc/md95400.def
modules/acerhk/doc/keycodes
root@ubuntu:/usr/src# cd modules/acerhk
root@ubuntu:/usr/src/modules/acerhk# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/acerhk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /usr/src/modules/acerhk/acerhk.o
/usr/src/modules/acerhk/acerhk.c: In function &#8216;set_mail_led&#8217;:
/usr/src/modules/acerhk/acerhk.c:814: warning: &#8216;regs&#8217; may be used uninitialized in this function
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 2 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/src/modules/acerhk/acerhk.mod.o
  LD [M]  /usr/src/modules/acerhk/acerhk.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
root@ubuntu:/usr/src/modules/acerhk# make install
mkdir -p /lib/modules/2.6.32.11+drm33.2/extra
cp -v acerhk.ko /lib/modules/2.6.32.11+drm33.2/extra/
`acerhk.ko' -> `/lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko'
depmod -a
root@ubuntu:/usr/src/modules/acerhk# sudo gedit /usr/src/linux-headers-`uname -r`/Makefile
root@ubuntu:/usr/src/modules/acerhk# sudo modprobe acerhk force-series=290 dritek=1
FATAL: Module acerhk not found.
root@ubuntu:/usr/src/modules/acerhk#

```

---

### Post by pytheas22 on 2010-06-01
Ah, what is the output of:
```

sudo updatedb
locate acerhk.ko
```

---

### Post by arjunchandkn on 2010-06-01
```

arjun@ubuntu:~$ sudo updatedb
[sudo] password for arjun: 
arjun@ubuntu:~$ locate acerhk.ko
/lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko
/usr/src/modules/acerhk/.acerhk.ko.cmd
/usr/src/modules/acerhk/acerhk.ko


```

---

### Post by pytheas22 on 2010-06-02
What happens if you type:
```

sudo insmod /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko
```

You might also want to try:
```

sudo insmod /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko force-series=290 dritek=1
```

---

### Post by arjunchandkn on 2010-06-02
```

arjun@ubuntu:~$ sudo insmod /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko
[sudo] password for arjun: 


```after executing the first code acerhk gui has started loading properly without any pop-ups  but still neither wifi is activated nor the led.... I tried the pysical switch also..[IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5478039591520750274[/IMG]

I have uploaded the screen shot of  driver info shown in GUI
[http://picasaweb.google.com/arjunchandkn/Ubuntu#5478039591520750274](http://picasaweb.google.com/arjunchandkn/Ubuntu#5478039591520750274)
[IMG]http://picasaweb.google.com/arjunchandkn/Ubuntu#5478039591520750274[/IMG]


```

arjun@ubuntu:~$ sudo insmod  /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko force-series=290 dritek=1
insmod: error inserting  '/lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko': -1 File exists

```

---

### Post by pytheas22 on 2010-06-02
We at least seem to be getting closer.  I think the trick may be to load the module with the special options (the force-series=... stuff).  Please try:
```

sudo -s
rmmod acerhk
insmod  /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko force_series=290 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk/wirelessled
```

Then see if you can enable the radio.

---

### Post by arjunchandkn on 2010-06-03
sorry for the late reply...
```

arjun@ubuntu:~$ sudo -s
[sudo] password for arjun: 
root@ubuntu:~# rmmod acerhk
ERROR: Module acerhk does not exist in /proc/modules
root@ubuntu:~# insmod  /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko force_series=290 usedritek=1 verbose=1
root@ubuntu:~# echo 1 > /proc/driver/acerhk/wirelessled


```

After executing the last code my wifi switch is responding to the physical switch and i am able to connect to the internet

---

### Post by pytheas22 on 2010-06-03
Good to hear.  You can make the system run those commands automatically at boot by creating an init script.  First, type:

```
sudo gedit /etc/init.d/acerhk.sh
```

A file will open.  Add these lines:
```

#!/bin/bash

insmod  /lib/modules/2.6.32.11+drm33.2/extra/acerhk.ko force_series=290 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk/wirelessled
```

Save and close the file, then run these commands so the system will execute it at boot:
```

cd /etc/init.d
sudo chmod +x acerhk.sh
sudo update-rc.d acerhk.sh defaults
```

You should then be all set.  Keep in mind that whenever you get a kernel update from Ubuntu Updates, you will need to recompile the acerhk module against the new kernel.  You will also need to edit the script at /etc/init.d/acerhk.sh so that the "insmod" line reflects the path to the correct module for your new kernel.  To find the correct path, you can boot into your newest kernel and type this command (after compiling the acerhk module):

```

ls /lib/modules/`uname -r`/extra/acerhk.ko
```

The output will be the path to the module.

---

### Post by arjunchandkn on 2010-06-03
thankyou pytheas22 for your prompt and quick help....you are rocking

---

### Post by arm-c on 2010-08-21
All,

I posted an updated AcerHK GUI.  It has a few new features focused around the acerhk.ko module.

I wish I had seen this post a while ago, as I would have chimed in to try and lend a hand.  Since I wrote the python program acerhk gui, I could at least have provided some insight into what it would do.  I will talk about that in conjunction with the new version.

There are no enhancements to the GUI.  I just returned from an extended time away from connectivity.  I realized that the Ubuntu 10.04 broke the ability to compile the acerhk driver from the "fixed" source.  (Thanks much to Momo for that).  The solution to that has already been addressed here in the forum.

My efforts in this version focused on working out a way to have the program compile the source code for you and install the module.  The package includes the source code for acerhk referenced above.  It does not use the source from the package repository, as I couldn't get that to work.

This new release will be a bit verbose (as the others were) during the initial run AND on kernel upgrades.  After that, it should just launch quickly and work as long as you have the right hardware.  I have noticed a bit more needing the DRITEC setting and I had hopes last year of enhancing the application to enable you to update your config files based upon what you knew you needed.  For now, it just uses the default setting, so changes beyond that need to be addressed in your configuration files.

This version on launch:

a.  checks for existence of the driver.
b.  If not found, tries to load.
c.  If unsuccessful on loading, tries to compile the driver module and install that.  THIS appears to be working presently, but could break if the "issue" of needing to comment out the line in your kernel source gets fixed.  I have tested it out several times on my computer with various kernels.  It appears to work.
d.  If successful, will ask to add to the /etc/modules file.
    NOTE:  This caused a litle problem earlier because the reader was directed to append the acerhk line to the modules file with additional parameters.  It didn't take for him because the initial line appended was done by the acerhkgui program, hence the module ended up loading first with default settings.

I don't know how to detect the particular hardware variations, but wanted to enable the user to be able to select additional parameters for the driver, and update the configuration files.  Regardless, I am not there with the program and may never end up there.

[https://sourceforge.net/projects/acerhkgui/](https://sourceforge.net/projects/acerhkgui/)

I do hope the program helps more than hinders.

v/r
ARM-C

---

### Post by pytheas22 on 2010-08-22
**arm-c**: many thanks for your message--it's always great to be in touch with the actual developers!  I don't use acerhk myself because I don't have any relevant hardware, but I'll certainly keep your points in mind if I try helping someone again.

Also, have you ever tried getting acerhkgui into the repositories?  (Or maybe it is already and I just don't know, but I can't seem to find it.)

---

