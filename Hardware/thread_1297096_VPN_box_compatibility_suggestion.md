---
title: "VPN box compatibility suggestion"
date: 2009-10-21
forum: Hardware
---

### Post by sandrocchio_0.1 on 2009-10-21
Hi there,
it's already a while that I am trying and sadly failing, to establish a VPN PPTP connection toward a CISCO VPN box.
Although that server supports IPSec, we cannot consider to make any configuration activity, we don't want to take the risk.

Is there a compatibility report for VPN IPSEC box and Ubuntu 8.10 and following releases?
Which VPN Box would you suggest me, considering that MS and MAC clients must access too.

thank you in advance

---

### Post by Dark_Stang on 2009-10-21
Most Cisco vpn equipment works fine with Linux. The gnome network manager has plugins available to handle vpn connections. Open up synaptic. Scroll down to where you start seeing "network-manager". You will see a few vpn plugins for it... vpnc, pptp, openvpn, etc. Check the ones you want installed and hit apply. After they are installed you can manage your vpn connections through the network manager applet.

---

