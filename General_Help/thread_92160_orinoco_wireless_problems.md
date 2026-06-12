---
title: "orinoco wireless problems"
date: 2005-11-18
forum: General Help
---

### Post by embrodak on 2005-11-18
Hello,

I have an orinoco wireless card that I'm trying to configure to work in ubuntu and nothing i've tried has worked. Here's what I've done so far (as root):

```

# iwconfig
  lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

# modprobe orinoco
# modprobe orinoco_cs
# modprobe hermes
# lsmod | grep orinoco

orinoco_cs              8456  0
orinoco                33932  1 orinoco_cs
hermes                  6912  2 orinoco_cs,orinoco
pcmcia                 24584  5 orinoco_cs
pcmcia_core            44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

# /etc/init.d/networking restart
# iwconfig

  lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

#  cardctl eject   :: pulled out the card and put it back in again::
# cardctl insert
# /etc/init.d/networking restart
# iwconfig

  lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extension

```
I'm getting frustrated now. Does anybody have any idea what's wrong?  

Thanks!
~*~Embrodak~*~

---

### Post by Lambert on 2005-11-18
This link shows wavelan as being used (not sure what card you have)

[http://linux-wless.passys.nl/query_chipset.php?chipset=Orinoco&zoek=chipset](http://linux-wless.passys.nl/query_chipset.php?chipset=Orinoco&zoek=chipset)

/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/wavelan.ko


I show this in breezy so maybe you need this driver instead?

---

### Post by ecobuntu on 2005-11-18
I have an orinoco gold pc card with a proxim chip that works out of the box.  What kind of chip does your orinoco card use?  Have you tried using network-admin?

---

### Post by embrodak on 2005-11-20
It's a PCWA-C150 manufactured by Sony.  I tried using network-admin but it didn't have a wireless category and I didn't know how to do anything from there. I'm more command-line oriented, really. haha.

---

### Post by ecobuntu on 2005-11-20
did you try this...

sudo /etc/init.d/pcmcia restart

---

### Post by balak on 2005-12-09
Hi, I am having similar problems with breezy: Exactly the same outputs as the first post: 

Orinoco silver card (lucent/hermes chipset) on a dell inspiron 5100 running breezy 5.10 kernel 2.6.12.9-386

when the card is inserted

:~$lsmod | grep orinoco
orinoco_cs              8456  1
orinoco                33932  1 orinoco_cs
hermes                  6912  2 orinoco_cs,orinoco
pcmcia                 24584  3 orinoco_cs
pcmcia_core            44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

when it is removed:
:~$ lsmod | grep orinoco
orinoco_cs              8456  0
orinoco                33932  1 orinoco_cs
hermes                  6912  2 orinoco_cs,orinoco
pcmcia                 24584  3 orinoco_cs
pcmcia_core            44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic


It looks like my card is connecting to my access network but not able to get an IP address

iwconfig:

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"Lapaz"  Nickname:"sardar"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:9A:BF:43
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe9a:bf43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1520637 (1.4 MiB)  TX bytes:203398 (198.6 KiB)
          Interrupt:7

eth1      Link encap:Ethernet  HWaddr 00:02:2D:04:16:78
          inet6 addr: fe80::202:2dff:fe04:1678/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4632006 (4.4 MiB)  TX bytes:4632006 (4.4 MiB)

My wireless network has WEP enabled. I removed WEP but no change..

Anybody facing this problem found solutions?? Any suggestions? 

Thanks!

---

