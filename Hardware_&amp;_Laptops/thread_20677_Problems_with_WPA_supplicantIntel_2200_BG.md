---
title: "Problems with WPA supplicant/Intel 2200 BG"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by Skaan on 2005-03-17
Hi.

I tried to post this at the Hoary forum, but I didn't get any response, so I'll try again here. 

I have installed the Hoary release on my Fujitsu laptop but I have some problems getting WPA to function on my Centrino WLAN card. I upgraded the ipw2200 drivers from 0.19 to 1.0.1 using the guide in this forum and installed wpasupplicant using apt-get with no errors. The WLAN card is functioning properly and is able to detect networks. When I start wpasupplicant however I get the following error message:

skaan@oracle:~$ sudo /usr/sbin/wpa_supplicant -ieth1 -Dipw2100 -c /etc/wpa_supplicant.conf
Password:
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
...

Any suggestions on how to get this to work? Could it have something to do with the kernel not being properly configured? (I have not recompiled the kernel, used the one included in the installation)

I really need to get this thing working if I ever should be able to migrate from Windows to Linux.

Skaan

---

### Post by jerome bettis on 2005-03-18
first you say ipw2200 in the title and in your first paragraph, and then you try to load ipw2100.  not sure if that's just a typo here or a big mistake.

no need to use that supplicant thing.  what is it / why are you using it?  if you can scan for networks, the card / kernel is working fine.  just edit /etc/network/interfaces to look something like this

auto eth0
iface eth0 inet dhcp
        wireless_mode: Managed
        wireless_essid: your_essid
        wireless_key: your_wireless_key_in_hexadecimal

then do sudo modprobe ipw2200 ; ifup eth0

of course if it's mapped to eth1 say that instead of eth0, and if your network doesn't use dhcp it's different but i've never had to do that so i don't know.

---

### Post by Houmie on 2005-03-18
[QUOTE=jerome bettis]
 if you can scan for networks, the card / kernel is working fine.  just edit /etc/network/interfaces to look something like this

auto eth0
iface eth0 inet dhcp
        wireless_mode: Managed
        wireless_essid: your_essid
        wireless_key: your_wireless_key_in_hexadecimal

then do sudo modprobe ipw2200 ; ifup eth0

[/QUOTE]

I have a similar problem. BUt no one can really help me since everyone is using WEP instead of WPA.

I have a ipw2100 though.  The only thing I did differently was to input the key in string instead of Hexadecimal.  How can I convert my String to Hexadecimal?

If I do that, it should work I guess...  ](*,) 

Houmie

---

### Post by jerome bettis on 2005-03-18
wireless_key s:your_ascii_key

notice the s before the :

[ascii to hex converter](http://www.mikezilla.com/exp0012.html)

---

### Post by Houmie on 2005-03-19
great, I'll give it a shot.

Thanks

---

