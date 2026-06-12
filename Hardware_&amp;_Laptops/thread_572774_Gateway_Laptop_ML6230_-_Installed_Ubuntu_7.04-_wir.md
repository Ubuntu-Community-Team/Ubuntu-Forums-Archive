---
title: "Gateway Laptop ML6230 - Installed Ubuntu 7.04- wireless LAN does not work"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by homexyz1 on 2007-10-10
Hi All,

Just installed U-7.04, on GW ML6230, and everything seems to work fine (sound, internet, etc...), except can not get the wireless LAN working. 

Downloaded the Realtek driver for linux 

[http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

unzip and Untar
made driver (./makedrv) WORKED 

tried to ./wlan0up  (doesn't work)  

The script is trying to :

-------------------
cd ieee80211/
insmod ieee80211_crypt-rtl.ko
insmod ieee80211_crypt_wep-rtl.ko
insmod ieee80211_crypt_tkip-rtl.ko
insmod ieee80211_crypt_ccmp-rtl.ko
insmod ieee80211-rtl.ko

cd ../rtl8187/
insmod r8187.ko

cd ../

ifconfig wlan0 up

---------------------end script ------------------------------------

None of the above files are in ieee80211 dir.

content of my ieee80211 dir is as follows:


rwxr-xr-x 1 asic1 asic1  7699 2007-01-14 18:00 readme
-rwxr-xr-x 1 asic1 asic1 18671 2007-01-14 18:00 license
-rwxr-xr-x 1 asic1 asic1 14136 2007-01-14 18:00 ieee80211_wx.c
-rwxr-xr-x 1 asic1 asic1 12029 2007-01-14 18:00 ieee80211_softmac_wx.c
-rwxr-xr-x 1 asic1 asic1 39547 2007-01-14 18:00 ieee80211_rx.c
-rwxr-xr-x 1 asic1 asic1  6299 2007-01-14 18:00 ieee80211_crypt_wep.c
-rwxr-xr-x 1 asic1 asic1 18944 2007-01-14 18:00 ieee80211_crypt_tkip.c
-rwxr-xr-x 1 asic1 asic1  3107 2007-01-14 18:00 ieee80211_crypt.h
-rwxr-xr-x 1 asic1 asic1 11324 2007-01-14 18:00 ieee80211_crypt_ccmp.c
-rwxr-xr-x 1 asic1 asic1  6138 2007-01-14 18:00 ieee80211_crypt.c
-rwxr-xr-x 1 asic1 asic1   920 2007-02-09 00:01 Makefile
drwxr-xr-x 5 asic1 asic1  4096 2007-10-10 16:40 ..
drwxr-xr-x 2 asic1 asic1  4096 2007-10-10 16:40 .tmp_versions
-rw-r--r-- 1 asic1 asic1     0 2007-10-10 16:40 .ieee80211_softmac.o.d
drwxr-xr-x 3 asic1 asic1  4096 2007-10-10 16:40 .
-rw-r--r-- 1 asic1 asic1 79142 2007-12-03 01:06 tags
-rwxr-xr-x 1 asic1 asic1  7871 2007-12-03 01:07 ieee80211_module.c
-rwxr-xr-x 1 asic1 asic1 70485 2007-12-05 00:26 ieee80211_softmac.c
-rwxr-xr-x 1 asic1 asic1 44361 2007-12-05 00:27 ieee80211.h
-rwxr-xr-x 1 asic1 asic1 16406 2007-12-05 00:53 ieee80211_tx.c[/COLOR][/B]


------------------------------------------end dir. content----------------

Please help,

Regards,

---

