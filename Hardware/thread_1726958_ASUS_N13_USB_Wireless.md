---
title: "ASUS N13 USB Wireless"
date: 2011-04-11
forum: Hardware
---

### Post by xgenwares on 2011-04-11
I have been trying despertly to get my ASUS n13 wireless usb adapter to work under ubuntu. I have the correct drivers for linux, but everytime I try to com pile them, I get this error.

```
make -C tools
make[1]: Entering directory `/home/otakustream/Desktop/driver/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/otakustream/Desktop/driver/tools'
/home/otakustream/Desktop/driver/tools/bin2h
cp -f os/linux/Makefile.6 /home/otakustream/Desktop/driver/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/otakustream/Desktop/driver/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/crypt_md5.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/mlme.o
/home/otakustream/Desktop/driver/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/otakustream/Desktop/driver/os/linux/../../common/mlme.c:4406: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_wep.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/action.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_data.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/rtmp_init.o
/home/otakustream/Desktop/driver/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/otakustream/Desktop/driver/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/otakustream/Desktop/driver/include/rtmp.h:5704: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_aes.o
/home/otakustream/Desktop/driver/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/otakustream/Desktop/driver/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_sync.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/eeprom.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_info.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/dfs.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/spectrum.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/rt_channel.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_profile.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_asic.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/assoc.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/auth.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/sync.o
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c:657: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c:1435: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c:935: warning: the frame size of 1260 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/otakustream/Desktop/driver/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/sanity.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/connect.o
/home/otakustream/Desktop/driver/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/otakustream/Desktop/driver/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/otakustream/Desktop/driver/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/otakustream/Desktop/driver/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../sta/wpa.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../os/linux/rt_linux.o
/home/otakustream/Desktop/driver/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/rt_linux.c:982: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.o
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:1839: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:7179: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_32.h:27: note: expected ‘const char *’ but argument is of type ‘CHAR *’
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:7179: warning: pointer targets in assignment differ in signedness
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:1037: warning: the frame size of 1288 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:2321: warning: the frame size of 1584 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:7315: warning: the frame size of 2328 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:7131: warning: the frame size of 1348 bytes is larger than 1024 bytes
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/sta_ioctl.c:6933: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/ba_action.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../os/linux/usb_main_dev.o
/home/otakustream/Desktop/driver/os/linux/../../os/linux/usb_main_dev.c: In function ‘RTUSBWatchDog’:
/home/otakustream/Desktop/driver/os/linux/../../os/linux/usb_main_dev.c:758: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/otakustream/Desktop/driver/os/linux/../../common/cmm_mac_usb.o
/home/otakustream/Desktop/driver/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/otakustream/Desktop/driver/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/otakustream/Desktop/driver/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/otakustream/Desktop/driver/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/otakustream/Desktop/driver/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/otakustream/Desktop/driver/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

```

Please help me out here, I really dont want to have to go back to windows!

---

### Post by ZephyrXero on 2011-04-21
Having the same problem myself...but don't give up! I'll post results as soon as I get it working ;)

Update1: Got the drivers from RaLink proper to compile. Something appears to be wrong with the driver on ASUS's site. See: [http://ubuntuforums.org/showthread.php?t=1715693](http://ubuntuforums.org/showthread.php?t=1715693)

Update2: Something's still not right, keep getting "unknown signal" errors now...more updates to come

---

### Post by notslony on 2011-04-21
Easy Dont Need Install Files This Is How I Did Mines 
Go Into terminal

Step 1:
sudo gedit /etc/udev/rules.d/network_drivers.rules



Step 2 (add the follow text to the file and save):
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"




Step 3:
sudo gedit /etc/modprobe.d/network_drivers.conf

Step 4 (add the follow text to the file then save):
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id

---

### Post by ZephyrXero on 2011-05-06
As a follow up...notslony's method above did the trick ;)

---

### Post by fjgaude on 2011-05-06
AFAIK, in 10.10 and 11.04 the wifi driver is in the kernel. Nothing more is needed to get N13 to work; just click enable wireless in the network monitor drop-down menu. That's it!

---

