---
title: "wep and linux"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by xxFelixDCatxx on 2006-04-09
Before I post this I'd like to say I didn't want to post another problem with wireless... I tried first to search for a similar problem, but didn't see any.

That said, can anyone think of a reason that ubuntu would be perfectly able to connect to a network that has no WEP, but is completely unable to connect to one that does?

Earlier I was pointed to WPAsupplicant, this looks like it provides an auth with a WPA encrypted connection... which I know is better.  But at the moment I am forced to use a 128bit wep connection.

here's the output from an iwconfig command

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"*******"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:11:95:0A:FC:E2
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

any help would be greatly appreciated.

---

### Post by Stealth on 2006-04-09
[QUOTE=xxFelixDCatxx]
That said, can anyone think of a reason that ubuntu would be perfectly able to connect to a network that has no WEP, but is completely unable to connect to one that does?

Earlier I was pointed to WPAsupplicant, this looks like it provides an auth with a WPA encrypted connection... which I know is better.  But at the moment I am forced to use a 128bit wep connection.

any help would be greatly appreciated.[/QUOTE]

I'm a little confused by your question...

Ubuntu supports WEP quite well, but you say you are unable to connect to a WEP network? Yet you mention WPA, which is another stronger encryption, but say you are forced to use a WEP connection...

So is it WEP or WPA that you are having troubles with?

If it IS WPA, what type of wireless card do you have?

---

### Post by xxFelixDCatxx on 2006-04-09
it's wep i'm having the problem with, I can connect to an open network just fine, but put any 64bit or 128bit wep key on it and suddenly nothing.

When I mentioned WPA i was just saying that I don't want any solutions for WPA, just WEP.

---

### Post by hajk on 2006-04-09
Well, you shouldn't use just *any* WEP key, you must use the WEP key set in the router. If this is your home setup, then the WEP key is probably printed on a label at the bottom of the router. You could also login to the router with an Ethernet cable (provided you have admin privileges) and check what the WEP key is.

Have fun!

---

### Post by chettyk on 2006-04-09
My computers are linked through a wireless router to a cable modem. I have not had the slightest difficulty enabling WEP. In System > Administration > Networking, click on 'Wireless connection' and then click the 'Properties' button to the right. You need to make sure that all the entries are correct. 

In my case, the wireless router acts as a DHCP server. I therefore make sure that the 'Network name (ESSID' is correct, set the 'Key type' (in the case of my router, to Hexadecimal), enter the WEP key, and set the 'Configuration' to DHCP.

Then, make sure the box for 'Enable this connection' is checked before clicking the OK button. You are then returned to the Network Settings dialog box. Click Activate. That should activate your wireless connection. Click the OK button.

Hope this is of some help to you.

---

### Post by xxFelixDCatxx on 2006-04-09
alrighty this is all good info, but I think I've narrowed down the problem just a bit

i went into the router and configured this to an 'open' system instead of 'shared'

when it's open, it works fine, so if no one has another solution is an open key less secure?  I have no idea to tell the truth.

---

### Post by hajk on 2006-04-09
This seems to be a different problem: does the router allow new connections (even if the WEP key is correct)? I suggest you read the manual (or PDF file) that came with your router. Some SpeedTouch routers, for example, require a long button push to open it for new connections during a short period (like a minute); other routers require this to be set by an administrator logging in (possibly via Ethernet cable).

---

