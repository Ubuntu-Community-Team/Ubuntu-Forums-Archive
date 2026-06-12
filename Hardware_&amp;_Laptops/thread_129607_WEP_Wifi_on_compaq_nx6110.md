---
title: "WEP Wifi on compaq nx6110"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by Knightwise on 2006-02-14
Hi , I feel like an *** asking this question but what the hell.

I've been using ubuntu 5.10 on my compaq nx6110 laptop for about two weeks nw and love it to bitts. Thanx to the ubuntu AUTOMATIX script i've been able to get everything working on this machine and have turned into my main workstation ... EXEPT ... Wireless

The laptop boasts a WPI2200 Centrino Wifi adapter. Now i've looked around at forums here and over the internet and tried just about every manual out there (carefully downloading what i should download and copying and pasting it) but to no avail :( .. No wireless.

I was wondering if there is a little script out there (just like the automatix script) that wgets the right firmware; drovers and installs it. 

I dont need wpa just yett , just WEP encription would be fine .. please help with the last missing peace of the puzzle.

---

### Post by hollowhead on 2006-02-14
Knightwise, I've just bought the same laptop and I love it too and put breezy on it.  Unfortunately I have a broadcom wifi adapter which I have not got going yet.  I am struggling to get the modems going one PCMCIA which I am about to post about again and the winmodem which is Agere systems AC'97.  If you have this latter modem any help in simple terms would be of great assistance.  Hollowhead.

---

### Post by drakeoutlaw on 2006-02-14
Knightwise,

Does your machine connect with windows? If not then your wireless router needs to be properly configured.

---

### Post by pnael on 2006-02-14
Hello,

We need more info to help you. Please give us the output of :
lsmod | grep ipw
lsmod | grep ieee
iwconfig
ifconfig -a

I own a nc6120 with a ipw2200. I have been able to use it with WEP and WPA. Everything can be found in the ubuntufuroms to make it work. The problem is more to find out what is the problem.
Regards

---

### Post by Knightwise on 2006-02-14
Hello my friends , 

Thanx for the info 

Yes the laptop does connect to my wifi router in windows so there's no prob there.

I entered the following commands and here is the output.

lsmod | grep ipw
no output.

lsmod | grep ieee
ieee1394               90936  2 ohci1394,sbp2

iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"Rocketboom"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:9E:3B:25
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:0496-5317-10   Security mode:open
          Power Management:off
          Link Quality=26/92  Signal level=-67 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:68
          Tx excessive retries:784  Invalid misc:0   Missed beacon:0

( The ETH1 is the wireless PCMCIA Orinoco wifi card i put in as a workaround.. But as you can see the onboard wireless card is nowhere to be seen.)


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:38:05:68:AD
          inet6 addr: fe80::214:38ff:fe05:68ad/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:176 (176.0 b)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:02:2D:0E:7D:5C
          inet addr:172.16.123.12  Bcast:172.16.123.15  Mask:255.255.255.240
          inet6 addr: fe80::202:2dff:fe0e:7d5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1573127 errors:172 dropped:172 overruns:0 frame:172
          TX packets:1674940 errors:797 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1313417143 (1.2 GiB)  TX bytes:661519312 (630.8 MiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:760942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:760942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:56489340 (53.8 MiB)  TX bytes:56489340 (53.8 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

( The eth 1 is once again the orinoco PCMCIA wifi card i put in as a workaround).

Thank you for any info you might provide.

---

### Post by pnael on 2006-02-15
You don't have the correct modules loaded.
Please give me the output of lspci and then lspci -n

Did you try to load the modules manually :
sudo modprobe ipw2200

If you get an error message please let me know.
Else try again the following command if the module loaded successfully :
lsmod | grep ipw
lsmod | grep ieee
iwconfig
ifconfig -a

---

### Post by Knightwise on 2006-02-16
Here is the output of LSPCI

knightwise@zartan:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


knightwise@zartan:~$ lspci -n
0000:00:00.0 0600: 8086:2590 (rev 03)
0000:00:02.0 0300: 8086:2592 (rev 03)
0000:00:02.1 0380: 8086:2792 (rev 03)
0000:00:1d.0 0c03: 8086:2658 (rev 03)
0000:00:1d.1 0c03: 8086:2659 (rev 03)
0000:00:1d.2 0c03: 8086:265a (rev 03)
0000:00:1d.3 0c03: 8086:265b (rev 03)
0000:00:1d.7 0c03: 8086:265c (rev 03)
0000:00:1e.0 0604: 8086:2448 (rev d3)
0000:00:1e.2 0401: 8086:266e (rev 03)
0000:00:1e.3 0703: 8086:266d (rev 03)
0000:00:1f.0 0601: 8086:2641 (rev 03)
0000:00:1f.1 0101: 8086:266f (rev 03)
0000:02:04.0 0280: 14e4:4320 (rev 03)
0000:02:06.0 0607: 104c:8031
0000:02:06.2 0c00: 104c:8032
0000:02:0e.0 0200: 14e4:170c (rev 02)

and finaly : 

knightwise@zartan:~$ sudo modprobe ipw2200
Password:
FATAL: Module ipw2200 not found.

Thank you very very much for your help .. Its realy appreciated.

---

### Post by pnael on 2006-02-17
Hello,

You don't have an IPW2200 wireless card !. 

**0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**

This line means that your wireless card use a Broadcom chipset.
There is no native linux driver for this chipset. 
The workaround is to wrap a Windows driver using ndiswrapper.
Here is a quick example how to use ndiswrapper : [http://ubuntuforums.org/showthread.php?t=81461&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=81461&highlight=broadcom")

You can get more information from the ndiswrapper wiki. [http://ndiswrapper.sourceforge.net/support.html]("http://ndiswrapper.sourceforge.net/support.html")

I don't know this chipset but I seems to have some problems depending the version of ndiswrapper. 
You can look in the following list :
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
for card with same chipset.

---

