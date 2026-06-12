---
title: "status lights off with BCM4306"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by hohllp on 2005-04-03
Hi all,

I've been wrestling with installing my wireless pcmcia card. I have a trendnet tew401pcplus, broadcom BCM4306 chipset. I've gotten it to work previously using debian sarge, and it work fine in windows. I've went through the install procedure for ndiswrapper:

ndiswrapper -i <inf_fiele> (I've tried both netgtks.inf and bcmwl5.inf and bcmwl5a.inf ... with matching drivers, of course) 
modprobe ndiswrapper

which should make the status light turn on (a la debian sarge), but they do not. As a result I cannot scan for my router using iwlist wlan0 scan (gives "no scan results), wven though iwconfig seems to work:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:17 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



I checked if the problem was related to the pcmcia bus, and checking the system log when I insert the card gives:

Apr  3 18:19:50 localhost kernel: ndiswrapper: device wlan0 removed
Apr  3 18:19:50 localhost kernel: ndiswrapper: using irq 10
Apr  3 18:19:50 localhost kernel: wlan0: ndiswrapper ethernet device 00:0e:8e:00:50:95 using driver bcmwl5a
Apr  3 18:19:50 localhost kernel: ndiswrapper: device wlan0 removed

I don't know if it normal for the log to state that the wlan0 device was removed, when it it clearly still plugged in. Other log info for lspci:

0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Also results from cardctl:
root@vfpc:/home/vince # cardctl status
Socket 0:
  3.3V CardBus card
  function 0: [ready]
root@vfpc:/home/vince # cardctl ident
Socket 0:
  product info: "Broadcom", "802.11b CardBus", "8.0"
  manfid: 0x02d0, 0x0406
  function: 6 (network)
root@vfpc:/home/vince # cardctl info
PRODID_1="Broadcom"
PRODID_2="802.11b CardBus"
PRODID_3="8.0"
PRODID_4=""
MANFID=02d0,0406
FUNCID=6

makes it seem like the bus is working fine. Another little tidbit is when I run "lsmod | grep ndis":

ndiswrapper           109044  0
usbcore               107384  4 ndiswrapper,ehci_hcd,uhci_hcd

should ndiswrapper be apearing under usbcore as well?

Anyone have ideas on how to get this working?

Thanks

Vince

---

### Post by acascianelli on 2005-04-05
edit your /etc/ndiswrapper/14E4:4320.conf (or whichever file is the link).  scroll down to the line that says "RadioState|1", change the '1' to a '0'.

---

### Post by hohllp on 2005-04-05
Hi,

Thanks for the help.

I changed the 1 to 0, but when I run ndiswrapper -i <inf_file> I get:

Forcing parameter RadioState|0 to RadioState|1

then I try "modprobe ndiswrapper" and the lights still do not turn on. argh !

Vince

---

### Post by hohllp on 2005-04-05
Sorry, ignore the stupidity of my last message. all I needed to do was change from 1 to 0 and reboot. very cool Thanks again

---

### Post by vtrac on 2005-05-11
Which driver did you use to get it to work?

---

