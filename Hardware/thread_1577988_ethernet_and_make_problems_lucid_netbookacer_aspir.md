---
title: "ethernet and make problems: lucid netbook/acer aspire1 D260"
date: 2010-09-19
forum: Hardware
---

### Post by _traq_ on 2010-09-19
Hi all,

I installed Ubuntu 10.04-netbook-i386 on a new Acer Aspire One D260, and found that the ethernet driver was not included.  I've followed directions [here]("http://ubuntuforums.org/showpost.php?p=9446984&postcount=6") and [here]("http://ubuntuforums.org/showpost.php?p=7808827&postcount=8"), but I seem to be running into the same problem each way: I get an error when running **make**:
```
"Makefile:118: *** Compiler not found. Stop."
```
I can't find any help with finding or updating compliers - can anyone suggest how to solve this?

thanks

---

### Post by _traq_ on 2010-09-24
Anyone have some suggestions? I'm still not having any luck.

```
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                    
Get:2 http://dl.google.com stable Release [2,544B]                                                        
Hit http://archive.canonical.com lucid Release.gpg                     
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,052B]               
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.canonical.com lucid/partner Packages
Hit http://archive.ubuntu.com lucid Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:5 http://archive.ubuntu.com lucid-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release
Get:6 http://archive.ubuntu.com lucid-updates Release [44.7kB]
Get:7 http://archive.ubuntu.com lucid-security Release [38.5kB]                                                             
Ign http://archive.ubuntu.com lucid/main Packages                                                                           
Hit http://archive.ubuntu.com lucid/restricted Packages                                                                     
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Get:8 http://archive.ubuntu.com lucid-updates/main Packages [310kB]
Get:9 http://archive.ubuntu.com lucid-updates/restricted Packages [3,240B]                                                  
Get:10 http://archive.ubuntu.com lucid-updates/main Sources [122kB]                                                         
Get:11 http://archive.ubuntu.com lucid-updates/restricted Sources [1,443B]                                                  
Get:12 http://archive.ubuntu.com lucid-updates/universe Packages [121kB]                                                    
Get:13 http://archive.ubuntu.com lucid-updates/universe Sources [48.2kB]                                                    
Get:14 http://archive.ubuntu.com lucid-updates/multiverse Packages [3,773B]                                                 
Get:15 http://archive.ubuntu.com lucid-updates/multiverse Sources [1,739B]                                                  
Get:16 http://archive.ubuntu.com lucid-security/main Packages [82.6kB]                                                      
Get:17 http://archive.ubuntu.com lucid-security/restricted Packages [14B]                                                   
Get:18 http://archive.ubuntu.com lucid-security/main Sources [29.7kB]                                                       
Get:19 http://archive.ubuntu.com lucid-security/restricted Sources [14B]                                                    
Get:20 http://archive.ubuntu.com lucid-security/universe Packages [39.8kB]                                                  
Get:21 http://archive.ubuntu.com lucid-security/universe Sources [9,810B]                                                   
Get:22 http://archive.ubuntu.com lucid-security/multiverse Packages [1,994B]                                                
Get:23 http://archive.ubuntu.com lucid-security/multiverse Sources [656B]                                                   
Ign http://archive.ubuntu.com lucid/main Packages                                                                           
Hit http://archive.ubuntu.com lucid/main Packages                                                                           
Fetched 863kB in 57s (14.9kB/s)                                                                                             
Reading package lists... Done
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  binutils dpkg-dev fakeroot g++ g++-4.4 gcc gcc-4.4 libc-dev-bin libc6-dev libstdc++6-4.4-dev linux-libc-dev manpages-dev
  patch xz-utils
Suggested packages:
  binutils-doc debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg gcc-multilib
  autoconf automake1.9 libtool flex bison gcc-doc gcc-4.4-multilib libmudflap0-4.4-dev gcc-4.4-locales libgcc1-dbg
  libgomp1-dbg libmudflap0-dbg libcloog-ppl0 libppl-c2 libppl7 glibc-doc libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  binutils build-essential dpkg-dev fakeroot g++ g++-4.4 gcc gcc-4.4 libc-dev-bin libc6-dev libstdc++6-4.4-dev
  linux-libc-dev manpages-dev patch xz-utils
0 upgraded, 15 newly installed, 0 to remove and 11 not upgraded.
Need to get 19.5MB of archives.
After this operation, 66.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main binutils 2.20.1-3ubuntu7 [1,601kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libc-dev-bin 2.11.1-0ubuntu7.2 [213kB]                           
Get:3 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-libc-dev 2.6.32-24.43 [781kB]                              
Get:4 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libc6-dev 2.11.1-0ubuntu7.2 [4,839kB]                            
Get:5 http://archive.ubuntu.com/ubuntu/ lucid/main gcc-4.4 4.4.3-4ubuntu5 [2,986kB]                                         
Get:6 http://archive.ubuntu.com/ubuntu/ lucid/main gcc 4:4.4.3-1ubuntu1 [5,066B]                                            
Get:7 http://archive.ubuntu.com/ubuntu/ lucid/main libstdc++6-4.4-dev 4.4.3-4ubuntu5 [1,491kB]                              
Get:8 http://archive.ubuntu.com/ubuntu/ lucid/main g++-4.4 4.4.3-4ubuntu5 [4,950kB]                                         
Get:9 http://archive.ubuntu.com/ubuntu/ lucid/main g++ 4:4.4.3-1ubuntu1 [1,442B]                                            
Get:10 http://archive.ubuntu.com/ubuntu/ lucid/main xz-utils 4.999.9beta+20091116-1 [228kB]                                 
Get:11 http://archive.ubuntu.com/ubuntu/ lucid/main patch 2.6-2ubuntu1 [123kB]                                              
Get:12 http://archive.ubuntu.com/ubuntu/ lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.3 [651kB]                              
Get:13 http://archive.ubuntu.com/ubuntu/ lucid/main build-essential 11.4build1 [7,278B]                                     
Get:14 http://archive.ubuntu.com/ubuntu/ lucid/main fakeroot 1.14.4-1ubuntu1 [118kB]                                        
Get:15 http://archive.ubuntu.com/ubuntu/ lucid/main manpages-dev 3.23-1 [1,547kB]                                           
Fetched 19.5MB in 8min 47s (37.0kB/s)                                                                                       
Selecting previously deselected package binutils.
(Reading database ... 141098 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.20.1-3ubuntu7_i386.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.11.1-0ubuntu7.2_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.32-24.43_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.11.1-0ubuntu7.2_i386.deb) ...
Selecting previously deselected package gcc-4.4.
Unpacking gcc-4.4 (from .../gcc-4.4_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.4-dev.
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.23-1_all.deb) ...
Processing triggers for man-db ...
Setting up binutils (2.20.1-3ubuntu7) ...

Setting up libc-dev-bin (2.11.1-0ubuntu7.2) ...
Setting up linux-libc-dev (2.6.32-24.43) ...
Setting up libc6-dev (2.11.1-0ubuntu7.2) ...
Setting up gcc-4.4 (4.4.3-4ubuntu5) ...
Setting up gcc (4:4.4.3-1ubuntu1) ...

Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.3) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up manpages-dev (3.23-1) ...
Setting up libstdc++6-4.4-dev (4.4.3-4ubuntu5) ...
Setting up g++-4.4 (4.4.3-4ubuntu5) ...
Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ cd ~/Desktop/compat-wireless-2010-09-12
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ scripts/driver-select atl1c
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/Makefile.bk
Backup exists: Makefile.bk
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ make
make -C /lib/modules/2.6.32-24-generic/build M=/home/bryan/Desktop/compat-wireless-2010-09-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  LD      /home/bryan/Desktop/compat-wireless-2010-09-12/compat/built-in.o
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/compat/main.o
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/compat/compat-2.6.33.o
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/compat/compat-2.6.35.o
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/compat/compat-2.6.37.o
  LD [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/compat/compat.o
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/compat/compat_firmware_class.o
  LD      /home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/built-in.o
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.o
/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.c: In function ‘atl1c_rx_checksum’:
/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.c:1726: error: implicit declaration of function ‘skb_checksum_none_assert’
make[4]: *** [/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.o] Error 1
make[3]: *** [/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c] Error 2
make[2]: *** [/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net] Error 2
make[1]: *** [_module_/home/bryan/Desktop/compat-wireless-2010-09-12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old bluetooth subsystem modules were left intact:

kernel/net/bluetooth/sco.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/btusb.ko
kernel/net/bluetooth/bluetooth.ko

make -C /lib/modules/2.6.32-24-generic/build M=/home/bryan/Desktop/compat-wireless-2010-09-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.o
/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.c: In function ‘atl1c_rx_checksum’:
/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.c:1726: error: implicit declaration of function ‘skb_checksum_none_assert’
make[4]: *** [/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c/atl1c_main.o] Error 1
make[3]: *** [/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net/atl1c] Error 2
make[2]: *** [/home/bryan/Desktop/compat-wireless-2010-09-12/drivers/net] Error 2
make[1]: *** [_module_/home/bryan/Desktop/compat-wireless-2010-09-12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2
bryan@bryan-laptop:~/Desktop/compat-wireless-2010-09-12$ sudo ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:b8:ec:8c  
          inet addr:172.16.11.201  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7ae4:ff:feb8:ec8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35613675 (35.6 MB)  TX bytes:1476888 (1.4 MB)

```

---

### Post by AmericasCup222 on 2010-10-02
As the owner of the same netbook with the same problem, I would also love to see this fixed!

---

