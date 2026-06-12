---
title: "Wireless problem with ubuntu 9.04"
date: 2009-05-12
forum: Hardware
---

### Post by Torleif67 on 2009-05-12
I have an HP G7000 laptop where i run Ubuntu 8.10 on. Everything works fine for me but then i upgraded to Ubuntu 9.04 the other day and since then i cannot connect to the internet with wireless connection.

Under network connection, wired i have Autho eth0, wireless is missing completely from the list. How do i get my wireless back working again?

Here are some info regarding my computer from the terminal:

uname -a
code:
Linux lybeth-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

lspci | grep -i net
code:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

iwconfig
code:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


ifconfig
code.
eth0      Link encap:Ethernet  HWaddr 00:1b:38:f5:44:86  
          inet6 addr: fe80::21b:38ff:fef5:4486/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1091266 (1.0 MB)  TX bytes:194526 (194.5 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1664 (1.6 KB)  TX bytes:1664 (1.6 KB)

Is there anybody around who knows anything about this who could please help me?

Torleif

---

### Post by banduan on 2009-05-12
Was the Atheros driver listed under Hardware Drivers before? Is it there now?

---

### Post by sir-bliant on 2009-05-12
I have an everex stepnote.  I am having exactly the same symptoms.  I don't know if the driver used to be there.  I had no reason to check.
Any help would be appreciated.
thanks,
george

---

### Post by Torleif67 on 2009-05-12
This is what i have under hardware drivers:

Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.

But if i activate this driver as it says, nothing will happen. I still cannot use my wireless...

---

### Post by Torleif67 on 2009-05-12
This is what i have under hardware drivers:

Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.

But if i activate this driver as it says, nothing will happen. I still cannot use my wireless...

---

