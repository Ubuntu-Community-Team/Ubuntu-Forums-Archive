---
title: "Netgear wg511v2 issues"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by ZosoPage on 2005-09-30
Made in china version, tried using ndiswrapper with the driver on the cd, getting message that the driver is installed, but is an invalid driver:
root@mlaptop:/home/mychal/Desktop # ndiswrapper -i WG511v2.INF Installing wg511v2
root@mlaptop:/home/mychal/Desktop # ndiswrapper -l
Installed ndis drivers:
wg511v2 invalid driver!
root@mlaptop:/home/mychal/Desktop # ndiswrapper -e wg511v2 root@mlaptop:/home/mychal/Desktop # ndiswrapper -l
No drivers installed
root@mlaptop:/home/mychal/Desktop # cardctl status
Socket 0:
3.3V CardBus card
function 0: [ready]
root@mlaptop:/home/mychal/Desktop # cardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
root@mlaptop:/home/mychal/Desktop # modprobe prism54
root@mlaptop:/home/mychal/Desktop # iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.
root@mlaptop:/home/mychal/Desktop # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:E3:59:CC
inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::208:74ff:fee3:59cc/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:2070 errors:0 dropped:0 overruns:0 frame:0
TX packets:1988 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1803691 (1.7 MiB)  TX bytes:280682 (274.1 KiB)
Interrupt:10 Base address:0x3000
lo        Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:5252 errors:0 dropped:0 overruns:0 frame:0
TX packets:5252 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:478790 (467.5 KiB)  TX bytes:478790 (467.5 KiB)
I am a COMPLETE newbie at this, but from my reading, it looks like prism54 is installed and will not allow ndiswrapper to install the drivers.  Am I on the correct path?  If someone can help, please do, I would sincerly appreciate it.  Also, please be sure to list steps one by one, since I am still learning, thanks

---

### Post by beefsprocket on 2005-09-30
I could be very very off on this, but don't you have to run "modprobe ndiswrapper" at some point? Having never used ndiswrapper I really have no clue, but I think I've read that in a few places (netstumbler forum perhaps?).

---

### Post by ZosoPage on 2005-10-01
ran modprobe ndiswrapper and received this:
root@mlaptop:/home/mychal # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
root@mlaptop:/home/mychal #



thanks for the reply!

---

### Post by G Sizzle on 2005-10-13
I'm am having the same exact problem.  I'm about to breaksomething because I got the fcuking made in China card.  Please help.  I cannot seem to find the correct drivers to insert with ndis.  If anyone has the drivers or knows of where to get them that would be great.  Thanks in advance.  Peace.

---

### Post by spd106 on 2005-10-21
[QUOTE=ZosoPage]ran modprobe ndiswrapper and received this:
root@mlaptop:/home/mychal # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/QUOTE]

Make sure you have the ndiswwrapper module that is compatible with your kernel. If you are using the stock ubuntu kernel chances are the ndiswrapper-utils package will provide the right module. However, if you have a custom kernel or if the card just won't work then you will have to compile ndiswrapper from source.

---

