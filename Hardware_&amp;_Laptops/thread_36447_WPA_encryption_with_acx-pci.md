---
title: "WPA encryption with acx-pci"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by samba on 2005-05-23
Hi,

I am trying to connect to a wireless network using WPA encryption. My wireless card is a D-Link DWL-650+, my laptop is a Dell Inspiron 8100, and the card seems to be recognized perfectly by hotplug. it seems to work fine if i do not use WPA encryption (although i couldn't try since i don't have access to a non-WPA encrypted network at the moment), but i can't connect to my WPA-encrypted network.

I had a look at the forums and found a few threads about that, but i couldn't make it work on my computer. The DWL-650+ card uses (i think) the acx-pci driver.

I installed wpasupplicant, changed the /etc/default/wpasupplicant file, customized the /etc/wpa_supplicant.conf configuration file, but then what? i still can't connect...

anyone can help? is it that WPA encryption is not supported by the acx-pci driver? do i have to use ndiswrapper? that would be sad, since everything seems to work out of the box with acx-pci...

thanks a lot :-))
samba

---

### Post by Fab on 2005-05-23
[QUOTE=samba]Hi,

I am trying to connect to a wireless network using WPA encryption. My wireless card is a D-Link DWL-650+, my laptop is a Dell Inspiron 8100, and the card seems to be recognized perfectly by hotplug. it seems to work fine if i do not use WPA encryption (although i couldn't try since i don't have access to a non-WPA encrypted network at the moment), but i can't connect to my WPA-encrypted network.

I had a look at the forums and found a few threads about that, but i couldn't make it work on my computer. The DWL-650+ card uses (i think) the acx-pci driver.

I installed wpasupplicant, changed the /etc/default/wpasupplicant file, customized the /etc/wpa_supplicant.conf configuration file, but then what? i still can't connect...

anyone can help? is it that WPA encryption is not supported by the acx-pci driver? do i have to use ndiswrapper? that would be sad, since everything seems to work out of the box with acx-pci...

thanks a lot :-))
samba[/QUOTE]
 i dont remember, but if your card uses the acx111 chipset, wpa or wep wont work
with acx100 chipsets (like my card), wep works, but i cant check wap because i dont have a wap enabled network

Fab

---

### Post by samba on 2005-05-23
i think it uses the acx100 chipset. WEP seems to work fine, although i haven't tried it. i'm now on an unencrypted network and it works fine.

so there's no hope of making WPA work...

ciao :-)
samba

---

### Post by Fab on 2005-05-23
[QUOTE=samba]i think it uses the acx100 chipset. WEP seems to work fine, although i haven't tried it. i'm now on an unencrypted network and it works fine.

so there's no hope of making WPA work...

ciao :-)
samba[/QUOTE]
 afair not with the acx100 linux driver
ndiswrapper should work with wap toh

---

### Post by borris.morris on 2007-05-26
working on the ndiswrapper version myself.

---

