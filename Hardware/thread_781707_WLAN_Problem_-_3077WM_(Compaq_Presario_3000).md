---
title: "WLAN Problem - 3077WM (Compaq Presario 3000)"
date: 2008-05-04
forum: Hardware
---

### Post by madhtr on 2008-05-04
elo board :)

I am a recent Linux convert so be patient with me ;)

My Laptop is a 3077WM (Compaq Presario 3000), and the WLAN is a Broadcom BCM4306. I cannot get it to work. I've tried Windows Wireless Drivers with bcmwl5.inf.  no errors are reported, the wlan is switched on via FN->F2, the light on the laptop indicates that it is active. however,lshw shows:

*-network DISABLED

for the WLAN. If i cannot get it to work, I'm afraid im gonna have to split the partition, and install winders again.  and i REALLY don't wanna do that. can anyone save me?

TY:)

---

### Post by biophysics on 2008-05-04
can you post (type in a terminal):
uname -a
ls -lR /lib/firmware
cat /etc/issue

---

### Post by madhtr on 2008-05-04
sure, thanx! :)

Linux useroneublt000.u21701.com 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

/lib/firmware:
total 4
drwxr-xr-x 4 root root 4096 2008-04-22 13:54 2.6.24-16-generic

/lib/firmware/2.6.24-16-generic:
total 5088
drwxr-xr-x 13 root root   4096 2008-04-22 13:54 acx
-rw-r--r--  1 root root  22622 2008-04-21 13:47 aic94xx-seq.fw
-rw-r--r--  1 root root  30348 2008-04-21 13:47 atmel_at76c502_3com.bin
-rw-r--r--  1 root root  35184 2008-04-21 13:47 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root  31764 2008-04-21 13:47 atmel_at76c502.bin
-rw-r--r--  1 root root  31764 2008-04-21 13:47 atmel_at76c502d.bin
-rw-r--r--  1 root root  35276 2008-04-21 13:47 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root  31776 2008-04-21 13:47 atmel_at76c502e.bin
-rw-r--r--  1 root root  35272 2008-04-21 13:47 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root  35276 2008-04-21 13:47 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root  28164 2008-04-21 13:47 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root  28040 2008-04-21 13:47 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root  35372 2008-04-21 13:47 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root  37804 2008-04-21 13:47 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root  37964 2008-04-21 13:47 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root  35180 2008-04-21 13:47 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root  39928 2008-04-21 13:47 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root  31748 2008-04-21 13:47 atmel_at76c504.bin
-rw-r--r--  1 root root  35196 2008-04-21 13:47 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root  37009 2008-04-21 13:47 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root  37000 2008-04-21 13:47 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root  35532 2008-04-21 13:47 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root  31824 2008-04-21 13:47 atmel_at76c506.bin
-rw-r--r--  1 root root  35228 2008-04-21 13:47 atmel_at76c506-wpa.bin
-rw-r--r--  1 root root  12772 2005-12-01 16:10 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root  17532 2005-12-01 16:10 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root   8518 2005-12-01 16:10 dvb-fe-or51211.fw
-rw-r--r--  1 root root  24478 2006-06-25 11:52 dvb-fe-tda10046.fw
-rw-r--r--  1 root root 239956 2005-12-01 16:10 dvb-ttpci-01.fw
-rw-r--r--  1 root root  10757 2005-12-01 16:10 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root   9025 2006-01-09 11:21 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root  34306 2007-09-10 05:09 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root   9180 2005-12-01 16:10 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   7558 2005-12-01 16:10 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root   7431 2005-12-01 16:10 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   3360 2007-03-02 22:19 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root   4286 2005-12-01 16:10 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root  10752 2005-12-01 16:10 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root  10752 2005-12-01 16:10 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root   8480 2006-01-26 16:17 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root  12902 2007-01-01 19:24 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root   8518 2007-01-01 19:24 dvb-usb-wt220u-zl0353-01.fw
-rw-r--r--  1 root root 209190 2008-04-21 13:47 ipw2100-1.3.fw
-rw-r--r--  1 root root 201138 2008-04-21 13:47 ipw2100-1.3-i.fw
-rw-r--r--  1 root root 196458 2008-04-21 13:47 ipw2100-1.3-p.fw
-rw-r--r--  1 root root 191142 2008-04-21 13:47 ipw2200-bss.fw
-rw-r--r--  1 root root 185660 2008-04-21 13:47 ipw2200-ibss.fw
-rw-r--r--  1 root root 187836 2008-04-21 13:47 ipw2200-sniffer.fw
-rw-r--r--  1 root root 112128 2008-04-21 13:47 isl3877
-rw-r--r--  1 root root  29024 2008-04-21 13:47 isl3886
-rw-r--r--  1 root root  30060 2008-04-21 13:47 isl3887usb_bare
-rw-r--r--  1 root root  93996 2008-04-21 13:47 isl3890
-rw-r--r--  1 root root  29468 2008-04-21 13:47 isl3890usb
-rw-r--r--  1 root root 149652 2008-04-21 13:47 iwlwifi-3945-1.ucode
-rw-r--r--  1 root root 149652 2008-04-21 13:47 iwlwifi-3945.ucode
-rw-r--r--  1 root root 185764 2008-04-21 13:47 iwlwifi-4965-1.ucode
-rw-r--r--  1 root root 191336 2008-04-21 13:47 iwlwifi-4965.ucode
-rw-r--r--  1 root root  76802 2008-04-21 13:47 ql2100_fw.bin
-rw-r--r--  1 root root  84566 2008-04-21 13:47 ql2200_fw.bin
-rw-r--r--  1 root root 123170 2008-04-21 13:47 ql2300_fw.bin
-rw-r--r--  1 root root 132978 2008-04-21 13:47 ql2322_fw.bin
-rw-r--r--  1 root root 206500 2008-04-21 13:47 ql2400_fw.bin
-rw-r--r--  1 root root   8192 2008-04-21 13:47 rt2561.bin
-rw-r--r--  1 root root   8192 2008-04-21 13:47 rt2561s.bin
-rw-r--r--  1 root root   8192 2008-04-21 13:47 rt2661.bin
-rw-r--r--  1 root root   2048 2008-04-21 13:47 rt73.bin
-rw-r--r--  1 root root 262144 2008-04-21 13:47 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root 376836 2008-04-21 13:47 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2008-04-21 13:47 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root  16382 2008-04-21 13:47 v4l-cx25840.fw
-rw-r--r--  1 root root   8192 2008-04-21 13:47 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root   8192 2008-04-21 13:47 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root  62484 2008-04-21 13:47 zd1201-ap.fw
-rw-r--r--  1 root root  70612 2008-04-21 13:47 zd1201.fw
drwxr-xr-x  2 root root   4096 2008-04-22 13:51 zd1211

/lib/firmware/2.6.24-16-generic/acx:
total 48
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 0.1.0.11
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 0.4.11.4
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 0.4.11.9
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 1.0.7
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 1.0.9
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 1.2.0.30
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 1.2.1.34
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 1.7.0
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 1.9.8.b
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 2.3.1.31
drwxr-xr-x 2 root root 4096 2008-04-22 13:54 default
-rw-r--r-- 1 root root  479 2005-12-29 21:33 readme.txt

/lib/firmware/2.6.24-16-generic/acx/0.1.0.11:
total 68
-rw-r--r-- 1 root root 62772 2003-06-29 03:54 tiacx111c16

/lib/firmware/2.6.24-16-generic/acx/0.4.11.4:
total 80
-rw-r--r-- 1 root root 76208 2004-10-21 16:19 tiacx111c16

/lib/firmware/2.6.24-16-generic/acx/0.4.11.9:
total 164
-rw-r--r-- 1 root root 70876 2003-12-10 21:06 tiacx111
-rw-r--r-- 1 root root 77384 2005-08-12 06:57 tiacx111c16
-rw-r--r-- 1 root root  6964 2003-12-10 21:06 tiacx111r16

/lib/firmware/2.6.24-16-generic/acx/1.0.7:
total 44
-rw-r--r-- 1 root root 42324 2004-09-24 23:15 tiacx100usb

/lib/firmware/2.6.24-16-generic/acx/1.0.9:
total 44
-rw-r--r-- 1 root root 42344 2005-08-07 10:17 tiacx100usb

/lib/firmware/2.6.24-16-generic/acx/1.2.0.30:
total 276
-rw-r--r-- 1 root root 76268 2004-03-10 14:13 tiacx111
-rw-r--r-- 1 root root 83024 2004-03-10 14:13 tiacx111c16
-rw-r--r-- 1 root root 84644 2004-03-10 14:13 tiacx111c17
-rw-r--r-- 1 root root  7208 2004-03-10 14:13 tiacx111r16
-rw-r--r-- 1 root root  8984 2004-03-10 14:13 tiacx111r17

/lib/firmware/2.6.24-16-generic/acx/1.2.1.34:
total 276
-rw-r--r-- 1 root root 76568 2004-04-04 06:07 tiacx111
-rw-r--r-- 1 root root 83320 2005-08-12 06:55 tiacx111c16
-rw-r--r-- 1 root root 84912 2004-04-04 06:07 tiacx111c17
-rw-r--r-- 1 root root  7204 2004-04-04 06:07 tiacx111r16
-rw-r--r-- 1 root root  8952 2004-04-04 06:07 tiacx111r17

/lib/firmware/2.6.24-16-generic/acx/1.7.0:
total 40
-rw-r--r-- 1 root root 32400 2002-05-30 02:57 tiacx100
-rw-r--r-- 1 root root   932 2002-05-30 02:57 tiacx100r0D
-rw-r--r-- 1 root root  1020 2002-05-30 02:57 tiacx100r11

/lib/firmware/2.6.24-16-generic/acx/1.9.8.b:
total 52
-rw-r--r-- 1 root root 40636 2005-04-28 05:14 tiacx100
-rw-r--r-- 1 root root   936 2005-04-28 05:14 tiacx100r0D
-rw-r--r-- 1 root root   964 2005-04-28 05:14 tiacx100r11
-rw-r--r-- 1 root root   912 2005-04-28 05:14 tiacx100r15

/lib/firmware/2.6.24-16-generic/acx/2.3.1.31:
total 292
-rw-r--r-- 1 root root 92836 2004-11-04 11:55 tiacx111c16
-rw-r--r-- 1 root root 94192 2004-11-04 11:55 tiacx111c17
-rw-r--r-- 1 root root 96336 2004-11-04 11:56 tiacx111c19

/lib/firmware/2.6.24-16-generic/acx/default:
total 0
lrwxrwxrwx 1 root root 19 2008-05-02 06:23 tiacx100 -> ../1.9.8.b/tiacx100
lrwxrwxrwx 1 root root 22 2008-05-02 06:23 tiacx100r0D -> ../1.9.8.b/tiacx100r0D
lrwxrwxrwx 1 root root 22 2008-05-02 06:23 tiacx100r11 -> ../1.9.8.b/tiacx100r11
lrwxrwxrwx 1 root root 22 2008-05-02 06:23 tiacx100r15 -> ../1.9.8.b/tiacx100r15
lrwxrwxrwx 1 root root 20 2008-05-02 06:23 tiacx100usb -> ../1.0.9/tiacx100usb
lrwxrwxrwx 1 root root 23 2008-05-02 06:23 tiacx111c16 -> ../1.2.1.34/tiacx111c16
lrwxrwxrwx 1 root root 23 2008-05-02 06:23 tiacx111c17 -> ../1.2.1.34/tiacx111c17
lrwxrwxrwx 1 root root 23 2008-05-02 06:23 tiacx111c19 -> ../2.3.1.31/tiacx111c19

/lib/firmware/2.6.24-16-generic/zd1211:
total 64
-rw-r--r-- 1 root root 4018 2008-04-18 08:48 zd1211b_ub
-rw-r--r-- 1 root root 5120 2008-04-18 08:48 zd1211b_uph
-rw-r--r-- 1 root root 5120 2008-04-18 08:48 zd1211b_uphm
-rw-r--r-- 1 root root 5120 2008-04-18 08:48 zd1211b_uphr
-rw-r--r-- 1 root root 3584 2008-04-18 08:48 zd1211b_ur
-rw-r--r-- 1 root root 4018 2008-04-18 08:48 zd1211_ub
-rw-r--r-- 1 root root 5120 2008-04-18 08:48 zd1211_uph
-rw-r--r-- 1 root root 5120 2008-04-18 08:48 zd1211_uphm
-rw-r--r-- 1 root root 5120 2008-04-18 08:48 zd1211_uphr
-rw-r--r-- 1 root root 3584 2008-04-18 08:48 zd1211_ur

Ubuntu 8.04 \n \l

---

