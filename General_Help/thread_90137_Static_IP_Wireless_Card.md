---
title: "Static IP Wireless Card?"
date: 2005-11-14
forum: General Help
---

### Post by thechitowncubs on 2005-11-14
How can I set a static IP to my wireless card, ipw2200?
I set the static ip in the Newtorking admin tool within the system menu, but when I reboot I can't access the internet because it seems like it doesn't apply the settings until I set it to dhcp and then back.

Can anyone explain the steps that I could perform in order to set a static ip successfully?

---

### Post by LorenzoD on 2005-11-14
Are you using NetworkManager? If that is the case, and you spend a lot of time on networks that don't use DHCP, I would consider removing NetworkManager.
Without network manager, you shouldn't have a problem keeping you static IP address over reboots.

---

### Post by soulestream on 2005-11-14
You can set all you settings in /etc/network/interfaces. This way when the system boots everything is set.

iface eth1 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid YOURSSID
        wireless-key1 1982...... <- wep key

soule

---

### Post by thechitowncubs on 2005-11-14
[QUOTE=soulestream]You can set all you settings in /etc/network/interfaces. This way when the system boots everything is set.

iface eth1 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid YOURSSID
        wireless-key1 1982...... <- wep key

soule[/QUOTE]

thanks soo much for the detail, i'll try it out

---

### Post by thechitowncubs on 2005-11-14
it works, thanks for your help

---

