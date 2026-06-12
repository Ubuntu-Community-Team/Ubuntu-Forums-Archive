---
title: "Having trouble with Microsoft MN-520 wireless card (long)"
date: 2004-10-19
forum: Hardware &amp; Laptops
---

### Post by tmccartney on 2004-10-19
Apologies for the length of this - I have pasted in a lot of diagnostic info, hoping that will help you to help me. :)

I have a Dell Inspiron MN-520 wireless PCMCIA network card, and I'm having trouble getting it to work in Ubuntu.  Others have gotten it working under other Linux distros, so I think there's a way.  However, I'm a complete n00b at Linux, so I may be in over my head.

Per instructions found in several other (non-Ubuntu) forums, I added the following lines to /etc/pcmcia/config:

card "Microsoft Wireless Notebook Adapter MN-520 1.0.3"
  version "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
  bind "orinoco_cs"

No dice.  The "wireless" light on the modem is on, but it doesn't work, and when I go into Networking under System Configuration, the only network device listed is eth0, which is my regular ethernet card.   (When I go to add a wireless device, shouldn't something be in that top "wireless device" pull-down menu?) 

So I commented out the above card listing and, from reading another post, I added to /etc/pcmcia/config:

product info: "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
  manfid: 0x02d2, 0x0001
  function: 6 (network)

Nothing.

ifconfig yields this:

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:13:CC:BE
          inet addr:192.168.2.16  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe13:ccbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:790 errors:0 dropped:0 overruns:20 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80985 (79.0 KiB)  TX bytes:9475 (9.2 KiB)
          Interrupt:10 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1219390 (1.1 MiB)  TX bytes:1219390 (1.1 MiB)



iwconfig yields the following:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Access Point: 00:00:00:00:00:00  Bit Rate:11Mb/s
          Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

modprobe orinoco_cs doesn't yield any error messages.

lsmod lists among the modules:
orinoco_cs              9096  1

Part of the dmesg has this:

orinoco.c 0.13e (David Gibson &lt;hermes@gibson.dropbear.id.au&gt; and others)
orinoco_cs.c 0.13e (David Gibson &lt;hermes@gibson.dropbear.id.au&gt; and others)
eth1: Station identity 001f:0009:0001:0004
eth1: Looks like an Intersil firmware version 1.4.9
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:50:F2:xx :xx :xx
eth1: Station name "Prism  I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f

The MAC address is that of my stubborn Microsoft card.  So the card apparently is being detected, but the driver isn't being loaded.

Any ideas are welcome, keeping in mind that I'm a n00b. :)


Thanks!


Tracey

---

### Post by HungSquirrel on 2004-10-19
For a "noob", you certainly don't fear the command line.  I can't help you because I know nothing about that card, but I want to thank you for being one of the few beginners out there who isn't afraid to open a terminal.   8)

---

### Post by tmccartney on 2004-10-19
&lt;blush&gt;


 :)

---

### Post by dmartin on 2005-10-09
Looks to me like you do have eth1 configured, but its not connecting to your AP.  Notice the essid is blank.  If you have your AP set to broadcast the essid, try "iwconfig eth1 essid any".  If you are not broadcasting your AP's essid (good, a little more secure) then specify it in place of any, such as "iwconfig eth1 essid myessid".

---

### Post by _linux_ on 2006-04-05
Why is it eth1? Shouldn't it be ath0 or wlan0 since it's a wireless card?

---

