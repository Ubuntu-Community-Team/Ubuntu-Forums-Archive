---
title: "Wlan on reboot?"
date: 2004-10-17
forum: General Help
---

### Post by jdelo on 2004-10-17
I have my wireless card installed with ndiswrapper. The only way I can get it to work is" ifconfig eth0 down and ifconfig wlan0 up", evey time I reboot my computer. Is there a way to set it so it starts at boot without the eth0 config taking over?

Thanks,
Jeff :lol:

---

### Post by auximini on 2004-10-17
Hi,

You'll want to edit your /etc/network/interfaces file. Replace:

auto eth0 
with
auto wlan0

Then configure the nework card. Heres my setup.. I have my card set to static, but if your is DHCP, replace static with dhcp:

auto wlan0
iface wlan0 inet static
        wireless-mode managed
        wireless-essid nameofssid
        address 172.16.2.50
        netmask 255.255.255.0
        gateway 172.16.2.1

iface eth0 inet dhcp

---

### Post by jdelo on 2004-10-17
How do I edit the /etc/network/interfaces file it keeps saying that I dont have permission? Is there a way it can be done in terminal?

thanks,
Jeff :lol:

---

### Post by bartleby on 2004-10-17
To edit the file, type sudo gedit in a root terminal before the file string.

---

