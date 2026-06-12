---
title: "Wireless is connected, but sometimes cuts out."
date: 2005-11-16
forum: General Help
---

### Post by jimmah6786 on 2005-11-16
Hello All!!

Heres the problem, my wireless network connection gets connected fine when I activate it via the Network configuration GUI. As soon as its activated it works fine with firefox(surfing the web), gaim(chattin), and downloading packages with Syanptis. After about a minute or two pages in firefox will stop coming up and it sits in wait, if i am downloading a package at like 300kbs it will drop to unknown and sit. At this time I notice that the wireless icon in the top right corner has full signal, but no activity. Eventually atfter like 5min activity will come back and resume were everything has left off, unless the downloading or transmission has timed out.

I have checked to see if it is my AP, but I do not beleive so since my windows partition on the same Laptop(ThinkPad R51) works without this activity slumping.
Also I am on a University network so I know the WAN is working as well as the LAN + WLAN.

If this helps here is my iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"#bryant#"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:8F:9D:BC:A0
          Bit Rate=24 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-53 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:8

sit0      no wireless extensions.

Here is my network/interface  output:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid #bryant#
wireless-key /*wep key goes here*/

auto eth0
auto eth1

THANKS ALL

Jim

---

### Post by soulestream on 2005-11-16
if this is a IPW2200 card, do a search on here. 

I had this issue for awhile(i havent had it in breezy) and taking the card down and bringing it back up would fix the issue. Someone wrote a startup script to do just that. 

after it is done once, I never needed to do it again.(until reboot anyway.. and the script takes care of that)

soule

---

### Post by jimmah6786 on 2005-11-16
I will try that...but

I get an IP address and still have one when the transmission of packets just sits. I wounder if it is something else.

---

