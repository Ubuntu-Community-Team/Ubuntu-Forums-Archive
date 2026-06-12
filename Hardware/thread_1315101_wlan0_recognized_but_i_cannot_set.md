---
title: "wlan0 recognized but i cannot set"
date: 2009-11-05
forum: Hardware
---

### Post by cliffk on 2009-11-05
running karmic on dell inspiron and have identified wireless (lspci):[INDENT]*Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)*
[/INDENT]
[LIST]
[*]i have installed the fw-cutter package (sudo apt-get install b43-fwcutter /extract firmware:yes) and iwconfig reports back:
[/LIST]
[INDENT][I]wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=[COLOR=Red]20 dBm   [/COLOR][/I]
[/INDENT]
[LIST]
[*]System/Preferences/Network Connections/Wireless is blank
[/LIST]

[LIST]
[*]tried *[FONT=Courier New]apt-get install gnome-network-admin[/FONT]*, and *network-admi*n allowed me to set essid and wep password and these items persist, but iwconfig (see above) reports back blank essid.
[/LIST]
it seems that my wireless is active but the tools i used cannot get it to work. also, enabling/disabling wireless (Fn-F2 on my laptop) turns on and off Tx at will:
[INDENT] [I]wlan0     IEEE 802.11bg  ESSID:""
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated[/I][I]
Tx-Power=[COLOR=Red]off[/COLOR][/I]
[/INDENT]so it seems i have a functioning wireless and i can twiddle the [COLOR=Red]Tx-Power[/COLOR] with a keystroke. But i cannot make it work with the network tools.

Any help? please?

---

### Post by sliketymo on 2009-11-05
Are you not able to just add the connection information using the network connection tool?

---

### Post by cliffk on 2009-11-05
i tried network connections (under menu system/preferences) but there is no entry in the wireless tab. it let's me set an ID and wep code and this "creates" an entry, but this doesn't seem to do anything. there is nothing active in the system to suggest that it is aware of the wireless. just iwconfig seems to know, as noted previously

---

### Post by cliffk on 2009-11-05
i'll mark this as solved, but i'm not sure what i did. thanks to all for the suggestions. something worked....

i found something called NetworkManager and ran it. the man page says it autohandles network connections....  i'm not sure if that made a difference. it may have already been running for all i know (default in karmic? don't know)

i also found nm-tools which reports on network connections. that's where i first noticed i had a DNS listed (so at some point it started working and didn't notify me)

that's when i tried iwconfig and noticed the ESSID was changed to my router name, and the wireless tab of my menu/system/preferences/network connections had an entry.

still confused why it works; wonder if a reboot will turn it off and wish i could report something more concise for future forum searchers.

(this is strictly off topic and i will post it elsewhere if i can figure out where it will make a difference, but.... these issues with wireless are a real show stopper for ubuntu, particularly on laptops. i wish it were otherwise. for me, as a gui and embedded systems programmer, this has been a ... tedious... experience. as for me, as a rank user it really isn't going to work... the information is either too disparate, inconsistent, contradictory or ad hoc. give microsoft credit in exactly one place... extensive user testing. there's got to be a way to match that. i still believe in the ubuntu revolution ;))

---

