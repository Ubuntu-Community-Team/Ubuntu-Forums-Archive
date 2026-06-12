---
title: "Connecting Using WEP"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by cl2312 on 2005-11-20
Hi.  I have a linksys wpc54g wireless pcmia card in my dell laptop and want to get the wireless internet running.  I read through the other related threads and was able to get the computer to recognize the card using ndiswrapper.  However I wasn't able to actually surf the web with WEP encryption and static ip.  Packets would be sent but never received.  According to iwconfig I didn't have an ip either.  I have tried to connect from the terminal and also the network settings window.

However, once I turned off the wireless security I could connect to the router and access the internet just fine.  Any suggestions on what could be causing trouble with WEP?

some output that may be useful, from the /etc/network interfaces file
wlan0     IEEE 802.11g  ESSID:"walter"  Nickname:"foghorn2"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:47:F6:DC
          Bit Rate=54 Mb/s
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-44 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:191   Missed beacon:0

---

### Post by Lambert on 2005-11-20
What are the basics to your wep settings? 

Are you using open or shared?

ascii or hexadecimal?

Try with an open setting and ascii and if that doesn't work then open with hexadecimal.

If you prefer shared then go that way but I've read posts where some couldn't get a shared setting to work at all.

---

### Post by quietglow on 2005-11-20
I just spent last evening trying to connect via an ascii key with zero luck. It worked without wep, and it worked with wep+ascii key on my daughter's powerbook, but not on my machine. Bummer.

---

### Post by cl2312 on 2005-11-20
It is 64 bit 10 digit hexadecimal password.  What is the difference between open and shared settings?

---

### Post by Lambert on 2005-11-20
> In the 1999 version of the standard, 2 Authentication methods are defined: Open and Shared. In Open, any device can Authenticate to the AP. In Shared, only devices with the WEP key can successfully Authenticate. Sounds good so far.....

The problem with Authenticate, is that were it is in the process of establishing connectivity, none of the higher-level protocols, like 802.1X can be run inside of the Authenticate 802.11 frames. So 802.11i does not use it, just uses Open Authenticate.

Shared Authenticate has a serious flaw, in that it is a simple challenge/response protocol. This design is very open to offline dictionary attacks. A WEP key would easily be exposed. Additionally, even in Open Authentication, a device that did not have the WEP key would not be able to communicate via the AP, as the AP would discard all data packets from the device.

Bottom line:  Shared Authentication does not add any security, and may weaken your security.  Don't bother with it.

You may be able to search around and find a difference in opinion on this.  Basically wep is obsolete replaced with wpa which is growing in support for linux.

---

