---
title: "ALPHA AWUS048NH  with RALINK Chipset. Can't install drivers"
date: 2010-07-20
forum: Hardware
---

### Post by sieger007 on 2010-07-20
Just for this card ALPHA AWUS048NH for better injection with Airmon-ng suite and following the instructions in there I cannot install the driver.
My system
Linux bt 2.6.30.9 #1 SMP Tue Dec 1 21:51:08 EST 2009 i686 GNU/Linux

when I do make file this is the error I get 
```
root@bt:~/Linux# make
make[1]: Entering directory `/usr/src/linux-source-2.6.30.9'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.30.9/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Linux/ieee80211/ieee80211_rx.o
  CC [M]  /root/Linux/ieee80211/ieee80211_softmac.o
  CC [M]  /root/Linux/ieee80211/ieee80211_tx.o
  CC [M]  /root/Linux/ieee80211/ieee80211_wx.o
/root/Linux/ieee80211/ieee80211_wx.c: In function 'ieee80211_wx_set_encode_ext_rsl':
/root/Linux/ieee80211/ieee80211_wx.c:734: warning: format not a string literal and no format arguments
  CC [M]  /root/Linux/ieee80211/ieee80211_module.o
  CC [M]  /root/Linux/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /root/Linux/ieee80211/rtl819x_HTProc.o
  CC [M]  /root/Linux/ieee80211/rtl819x_TSProc.o
  CC [M]  /root/Linux/ieee80211/rtl819x_BAProc.o
  CC [M]  /root/Linux/ieee80211/dot11d.o
  CC [M]  /root/Linux/ieee80211/ieee80211_crypt.o
  CC [M]  /root/Linux/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /root/Linux/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /root/Linux/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /root/Linux/ieee80211/ieee80211-rsl.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt-rsl.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt_wep-rsl.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt_tkip-rsl.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt_ccmp-rsl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /root/Linux/ieee80211/ieee80211-rsl.mod.o
  LD [M]  /root/Linux/ieee80211/ieee80211-rsl.ko
  CC      /root/Linux/ieee80211/ieee80211_crypt-rsl.mod.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt-rsl.ko
  CC      /root/Linux/ieee80211/ieee80211_crypt_ccmp-rsl.mod.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt_ccmp-rsl.ko
  CC      /root/Linux/ieee80211/ieee80211_crypt_tkip-rsl.mod.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt_tkip-rsl.ko
  CC      /root/Linux/ieee80211/ieee80211_crypt_wep-rsl.mod.o
  LD [M]  /root/Linux/ieee80211/ieee80211_crypt_wep-rsl.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.30.9'
make[1]: Entering directory `/usr/src/linux-source-2.6.30.9'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.30.9/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Linux/HAL/rtl8192u/r8180_93cx6.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192U_wx.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192S_phy.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192S_rtl6052.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192S_rtl8225.o
  CC [M]  /root/Linux/HAL/rtl8192u/r819xU_cmdpkt.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192U_dm.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192SU_HWImg.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192S_firmware.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192S_Efuse.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192U_core.o
  CC [M]  /root/Linux/HAL/rtl8192u/r8192U_pm.o
  LD [M]  /root/Linux/HAL/rtl8192u/r8192s_usb.o
  Building modules, stage 2.
  MODPOST 1 modules
/root/Linux/HAL/rtl8192u/r8192s_usb: struct usb_device_id is 20 bytes.  The last of 10 is:
0x03 0x00 0xda 0x0b 0x71 0x81 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
FATAL: /root/Linux/HAL/rtl8192u/r8192s_usb: struct usb_device_id is not terminated with a NULL entry!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directo
```


Anyone had better luck installing ALPHA Drivers. I 'd think they are amongst the most widely supported Linux WLAN Drivers with Wireless Extensions available . 
So what is it that I should be further doing - pl help ..!!!

---

