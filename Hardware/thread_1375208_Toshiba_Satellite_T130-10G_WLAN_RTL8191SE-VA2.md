---
title: "Toshiba Satellite T130-10G WLAN RTL8191SE-VA2"
date: 2010-01-07
forum: Hardware
---

### Post by diabolo0815 on 2010-01-07
Hi,

just bought a Toshiba Satellite T130-10G laptop, which is equipped with Realteks RTL8191SE-VA2.
WLAN won't run.

Checked Realtek's site, but they don't seem to have the Linux driver up, dead link (ref http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262)

iwconfig says
lo        no wireless extensions.

wlan6     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dhclient says
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan6/00:e0:4c:81:92:05
Sending on   LPF/wlan6/00:e0:4c:81:92:05
Sending on   Socket/fallback
DHCPDISCOVER on wlan6 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan6 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan6 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan6 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan6 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan6 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Can anyone help, please?
THX Diabolo

---

### Post by filipejps on 2010-01-29
same problem here... :(

---

### Post by IcarusR on 2010-01-30
Look at this post..

[http://ubuntuforums.org/showthread.php?t=1267961&highlight=RTL8191SE-VA2&page=2#13]("http://ubuntuforums.org/showthread.php?t=1267961&highlight=RTL8191SE-VA2&page=2#13")

---

### Post by filipejps on 2010-02-02
I've tried that but after installing there's no network detected.

In the menu "System->Hardware drivers" there's an entry with "Linux driver for Realtek RTL819x Wifi cards".

Also command "ifconfig" list a new entry "wlan1"...

I've tried to add a Hidden network using the parameters I know about my network (name, security and password) but without success: it's always asking for the password.

There are multiple networks in this room but none is detected...

---

### Post by filipejps on 2010-02-02
I also don't have wired connectivity because network card is not detected.

diabolo0815, you just asked for wireless... do you have wired network?

---

### Post by centro_com on 2010-05-05
hi,

well i had the same problem with UBUNTU 9.10 i tried a lot of solutions then ubuntu 10.04 came up....and the network works well.

I use WiCd for wlan. anyway i experienced some issues with WEP acces point...seems my laptop is not able to detect those devices...anyway ethernet works well.

---

