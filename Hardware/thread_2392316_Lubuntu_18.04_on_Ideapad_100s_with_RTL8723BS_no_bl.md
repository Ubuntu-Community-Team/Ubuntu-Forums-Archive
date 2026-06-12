---
title: "Lubuntu 18.04 on Ideapad 100s with RTL8723BS no bluetooth"
date: 2018-05-19
forum: Hardware
---

### Post by OmegaOne on 2018-05-19
Im running lubuntu 18.04 on my Lenovo Ideapad 100s-11iby, and it uses the RTL8723BS wifi/ bluetooth combo module. the wifi is working fine, but the bluetooth icon just says "No bluetooth adapter found", and when I try start->preferences->bluetooth manager it says "Bluez daemon is not running, Blueman manager cannot continue". How do i fix this? with the audio UCM driver thing i've basically got everything else working, I dont want to go back to windows :(

thanks

---

### Post by danielkgo on 2018-07-04
Same for me, with Intel Stick STCK1A8LFC (Atom Z3735), Lubuntu 18.04, kernel 4.15.0-24. I get the same message.

 Everything works but the bluetooth - not even mentioned in (1) lshw (2) lsusb (3) lspci (4) rfkill (5) dmesg.

I have tried to manually compile and install only the bluetooth part of the driver ([https://github.com/lwfinger/rtl8723bs_bt](https://github.com/lwfinger/rtl8723bs_bt)) but nothing happened (not even an error). 

As said everything else is working 100%.

Maybe BT-Coex?...

[    6.608891] r8723bs: module is from the staging directory, the quality is unknown, you have been warned.
[    6.624450] r8723bs: module verification failed: signature and/or required key missing - tainting kernel
[    6.628955] RTL8723BS: module init start
[    6.628960] RTL8723BS: rtl8723bs v4.3.5.5_12290.20140916_BTCOEX20140507-4E40
[    6.628962] RTL8723BS: rtl8723bs BT-Coex version = BTCOEX20140507-4E40
[    6.772312] RTL8723BS: rtw_ndev_init(wlan0)
[    6.776342] RTL8723BS: module init ret =0
[   25.098555] rtl8723bs: acquire FW from file:rtlwifi/rtl8723bs_nic.bin
[   28.663273] RTL8723BS: rtw_set_802_11_connect(wlan0)  fw_state = 0x00000008
[   36.369040] RTL8723BS: rtw_set_802_11_connect(wlan0)  fw_state = 0x00000008
[   36.641835] RTL8723BS: start auth

This has been addressed and resolved on a different dev board (tinkerboard?): [https://github.com/Miouyouyou/MyyQi/issues/7](https://github.com/Miouyouyou/MyyQi/issues/7) , [https://github.com/Miouyouyou/tinkerboard_rtl8723bs](https://github.com/Miouyouyou/tinkerboard_rtl8723bs)

Help anyone ?

---

### Post by ubfan1 on 2018-08-09
I'm starting to look at xubuntu 18.04 on a 1G stick.  Just for info, here's a successful wireless/bt setup sequence from the 14.04 system with a 4.4 kernel, using the chestermills ppa (from original stick distribution) for the source of the rtl8723bs code  (note that it has a more recent date than your code).   Also note the mac address on the rtw_ndev_init line.  
[   14.935676] RTL871X: module init start
[   14.935684] RTL871X: rtl8723bs v4.4.1_17245.20160325_BTCOEX20151223-654a
[   14.935688] RTL871X: build time: Aug  4 2018 18:43:11
[   14.935691] RTL871X: rtl8723bs BT-Coex version = BTCOEX20151223-654a
[   15.122494] RTL871X: hal_com_config_channel_plan chplan:0x20
[   15.130275] RTL871X: rtw_ndev_init(wlan0) if1 mac_addr=28:c2:dd:a0:e8:43
[   15.131108] RTL871X: module init ret=0
[   21.013600] RTL871X: rtw_set_802_11_connect(wlan0)  fw_state=0x00000008
[   23.006616] RTL871X: start auth
[   23.031211] RTL871X: auth success, start assoc
[   23.056698] RTL871X: rtw_cfg80211_indicate_connect(wlan0) BSS not found !!
[   23.056721] RTL871X: assoc success
[   23.067999] RTL871X: recv eapol packet
[   23.069911] RTL871X: send eapol packet
[   23.084030] RTL871X: recv eapol packet
[   23.084258] RTL871X: send eapol packet
[   23.084385] RTL871X: set pairwise key camid:4, addr:c0:56:27:ce:27:40, kid:0, type:AES
[   23.085123] RTL871X: set group key camid:5, addr:c0:56:27:ce:27:40, kid:2, type:AES
...

---

