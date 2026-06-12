---
title: "Firefox Crash"
date: 2008-10-01
forum: General Help
---

### Post by towanda on 2008-10-01
Last week, Firefox started crashing when I attempted to log in to secure sites.  Yesterday, it started crashing at random.  This is my second attempt to post this due to a crash.  I started Firefox from a terminal and induced a crash.  Here's what I got:

> 
me@mymachine:~$ firefox
FoxyProxy settingsDir = /home/me/.mozilla/firefox/zefh1iw8.default
Error sanitizing sessions: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsISecretDecoderRing.logoutAndTeardown]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 187"  data: no]
Segmentation fault (core dumped)


Everything above "Segmentation fault (core dumped)" appeared when I started Firefox.  The segmentation fault occurred when I induced the crash.

How do I fix this?  Oh...I'm still running Feisty.

---

### Post by Meow27 on 2008-10-01
waht version of firefox?

i not an advanced user, but i know ive had extremely bad problems with it in version 3.01 and 3.02

---

### Post by jespdj on 2008-10-01
You could try deleting the hidden ".mozilla" directory in your home directory (that's Firefox's configuration directory):
```
rm -rf ~/.mozilla
```
Note, this will probably also delete any Firefox extensions that you've installed.

Disclaimer: I am not responsible to damage to your system if something goes wrong because of this.

---

### Post by towanda on 2008-10-04
It's Firefox 2.0.0.17.

I'm reluctant to remove the hidden mozilla directory because I don't want to lose my extensions and I suspect that, since it has been there for some time, it is not the source of a problem that started a week ago.

---

### Post by Ryadt on 2008-10-04
Can you also post the version of ubuntu you are using.

---

### Post by towanda on 2008-10-05
I'm running 7.04 (Feisty) and using kernel 15 because I cannot get sound to work in either kernel 16 or 17.  

This morning, I rebooted the cable modem and router.  The other computer on my home network is an iMac running OS 10.4.7 and is not having this problem, so I'm pretty sure it's confined to my machine.

Here's part of my syslog from the time of a crash.

> Oct  5 11:27:10 mymachine ntpd[5203]: synchronized to 128.105.39.11, stratum 2
Oct  5 11:27:10 mymachine ntpd[5203]: kernel time sync enabled 0001
Oct  5 11:28:38 mymachine dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 
67 interval 3
Oct  5 11:28:38 mymachine dhclient: send_packet: Network is down
Oct  5 11:28:41 mymachine dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 
67 interval 6
Oct  5 11:28:41 mymachine dhclient: send_packet: Network is down
Oct  5 11:28:47 mymachine dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 
67 interval 11
Oct  5 11:28:47 mymachine dhclient: send_packet: Network is down
Oct  5 11:28:58 mymachine dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 
67 interval 11
Oct  5 11:28:58 mymachine dhclient: send_packet: Network is down
Oct  5 11:29:09 mymachine dhclient: No DHCPOFFERS received.
Oct  5 11:29:09 mymachine dhclient: No working leases in persistent database - sl
eeping.
Oct  5 11:29:09 mymachine firmware_helper[5887]: main: error loading '/lib/firmwa
re/bcm43xx_microcode5.fw' for device '/class/firmware/0000:05:00.0' with driver 
'(unknown)'
Oct  5 11:29:09 mymachine avahi-autoipd(eth1)[5884]: SIOCSIFFLAGS failed: No such
 file or directory
Oct  5 11:29:09 mymachine kernel: [  474.644000] bcm43xx: Error: Microcode "bcm43
xx_microcode5.fw" not available or load failed.

I'm pretty sure the missing microcode is for my wireless card, which I am not currently using.

---

### Post by towanda on 2008-10-07
Yesterday I discovered that the problem is obviously with Firefox.  I installed Opera and it has been rock-steady.  I'd still like to figure out what went wrong with Firefox, though.

---

