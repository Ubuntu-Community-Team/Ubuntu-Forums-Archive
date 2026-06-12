---
title: "ipw2100 connecting to linksys wpa wireless network"
date: 2008-10-26
forum: Hardware
---

### Post by nurv on 2008-10-26
Hi everyone!

I have an 4 year old laptop that I want to use in a wireless network with WPA Personal coming from an linksys router.

My wireless card is:

> ubuntu@ubuntu:~$ lspci -v | grep Network
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)


I tried to use both wpa_suplicant and NetworkManager applet to connect and both faild.

NetworkManager replyes me saying that the password is wrong. I can connect using another laptop that I have that runs 8.04 (its another wireless card) with that same password.

wpa_sup time's out and verbose mode doesn't help much. The only odd things i saw were

> 
...
1225069108.955348: WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f3 01 01 00 00 50 f2 02 01 00 00 50 f3 03 01 00 00 50 f3 03
1225069108.955370: No keys have been configured - skip key clearing
1225069108.955379: wpa_driver_wext_set_drop_unencrypted
...
1225069109.051244: wpa_driver_wext_set_psk
ioctl[SIOCSIWFREQ]: Operation not supported
1225069109.087219: Association request to the driver failed
...


my wpa_sup config is:
> 
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
       ssid="esp"
	#psk="magix"
psk=d7d9a7d8e7d8e789a7e98798a7da798daa89d97e89da7e89798d7a899e789de7
    proto=WPA
    key_mgmt=WPA-PSK
    group=TKIP
    pairwise=TKIP
}


Both 8.04 and 8.10RC don't work. 

I don't know if is a bug, or a driver issue, or my Wireless card doesn't suport WPA or went AWOL (I dought since I can scan for other networks)

Does any one can help?

---

### Post by emerging on 2009-02-05
Just ran into the same issue.  It would seem this is a bug in the ipw2100 module.  What was the other card you used that worked?  I may need to go out and buy a CardBus wifi adapter that works with WPA.

Thanks!

---

