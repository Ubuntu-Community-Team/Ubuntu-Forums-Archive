---
title: "dkms recompiling against current kernel instead of the new one being installed"
date: 2012-01-16
forum: Hardware
---

### Post by someitalian123 on 2012-01-16
O.K so I started [this thread]("http://ubuntuforums.org/showthread.php?t=1908542") and no one seemed to be able to help me. After finding out where dkms keeps it's build logs I took a look at the logs for the driver.

Here is the log for 3.0.0-14-generic

```
DKMS make.log for rt3562-2.4.1.1 for kernel 3.0.0-14-generic (i686)
Mon Jan 16 15:55:30 EST 2012
make -C tools
make[1]: Entering directory `/var/lib/dkms/rt3562/2.4.1.1/build/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/var/lib/dkms/rt3562/2.4.1.1/build/tools'
/var/lib/dkms/rt3562/2.4.1.1/build/tools/bin2h
cp -f os/linux/Makefile.6 /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/Makefile
make -C /lib/modules/3.0.0-14-generic/build SUBDIRS=/var/lib/dkms/rt3562/2.4.1.1/build/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-14-generic'
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_md5.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_sha2.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_hmac.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_arc4.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/mlme.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/mlme.c:5657:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_wep.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/action.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_data.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init.c:1391:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG’ [-Wformat]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_tkip.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_aes.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_sync.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/eeprom.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_sanity.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_info.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_cfg.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_wpa.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/dfs.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/spectrum.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_timer.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rt_channel.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_profile.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_asic.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_cmd.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/sync.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/rtmp_data.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/connect.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/wpa.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/ags.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/sta_cfg.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_profile.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:596:1: warning: the frame size of 1288 bytes is larger than 1024 bytes [-Wframe-larger-than=]
In file included from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/uaccess.h:570:0,
                 from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:351,
                 from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/include/os/rt_linux.h:40,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/include/rtmp_os.h:32,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/include/rt_config.h:60,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:28:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:3056:28:
/usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:3533:28:
/usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:5844:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:6043:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c:1699:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c:1736:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c:118:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c: In function ‘WriteDatThread’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c:1250:3: warning: ‘return’ with no value, in function returning non-void [-Wreturn-type]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/ba_action.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:36:13: warning: unused variable ‘num’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:119:16: warning: unused variable ‘IrqFlags’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:118:16: warning: unused variable ‘pPacket’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:117:15: warning: unused variable ‘pTxD’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:116:16: warning: unused variable ‘pTxRing’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:115:19: warning: unused variable ‘j’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:115:6: warning: unused variable ‘index’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:447:11: warning: unused variable ‘BufBaseVa’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:446:11: warning: unused variable ‘BufBasePaLow’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:445:11: warning: unused variable ‘BufBasePaHigh’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:432:15: warning: unused variable ‘pPacket’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:431:15: warning: unused variable ‘pDmaBuf’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:430:16: warning: unused variable ‘pTxRing’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:428:14: warning: unused variable ‘pRxD’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:427:14: warning: unused variable ‘pTxD’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:425:10: warning: unused variable ‘RingBaseVa’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:424:10: warning: unused variable ‘RingBasePaLow’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:423:10: warning: unused variable ‘RingBasePaHigh’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:489:4: warning: ‘index’ may be used uninitialized in this function [-Wuninitialized]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_data_pci.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_mcu.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/ee_prom.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/ee_efuse.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rt_rf.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../chips/rt30xx.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../chips/rt35xx.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/pci_main_dev.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/pci_main_dev.c:320:13: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/misc.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/misc.c: In function ‘RTMPHwCoexSwitch’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/misc.c:963:2: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 6 has type ‘ULONG’ [-Wformat]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../chips/rt3592cb.o
  LD [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.o
see include/linux/module.h for more information
  CC      /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.mod.o
  LD [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-14-generic'
cp -f /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.ko /tftpboot
```

Here is the log for 3.1.5-030105-generic

```
DKMS make.log for rt3562-2.4.1.1 for kernel 3.1.5-030105-generic (i686)
Mon Jan 16 16:01:52 EST 2012
make -C tools
make[1]: Entering directory `/var/lib/dkms/rt3562/2.4.1.1/build/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/var/lib/dkms/rt3562/2.4.1.1/build/tools'
/var/lib/dkms/rt3562/2.4.1.1/build/tools/bin2h
cp -f os/linux/Makefile.6 /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/Makefile
make -C /lib/modules/3.0.0-14-generic/build SUBDIRS=/var/lib/dkms/rt3562/2.4.1.1/build/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-14-generic'
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_md5.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_sha2.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_hmac.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/crypt_arc4.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/mlme.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/mlme.c:5657:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_wep.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/action.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_data.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init.c:1391:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG’ [-Wformat]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_tkip.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_aes.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_sync.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/eeprom.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_sanity.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_info.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_cfg.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_wpa.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/dfs.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/spectrum.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_timer.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rt_channel.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_profile.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_asic.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_cmd.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/sync.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/rtmp_data.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/connect.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/wpa.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/ags.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../sta/sta_cfg.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_profile.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:596:1: warning: the frame size of 1288 bytes is larger than 1024 bytes [-Wframe-larger-than=]
In file included from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/uaccess.h:570:0,
                 from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:351,
                 from /usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/include/os/rt_linux.h:40,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/include/rtmp_os.h:32,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/include/rt_config.h:60,
                 from /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:28:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:3056:28:
/usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:3533:28:
/usr/src/linux-headers-3.0.0-14-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:5844:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/sta_ioctl.c:6043:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c:1699:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_linux.c:1736:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c:118:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c: In function ‘WriteDatThread’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_main_dev.c:1250:3: warning: ‘return’ with no value, in function returning non-void [-Wreturn-type]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/ba_action.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:36:13: warning: unused variable ‘num’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:119:16: warning: unused variable ‘IrqFlags’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:118:16: warning: unused variable ‘pPacket’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:117:15: warning: unused variable ‘pTxD’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:116:16: warning: unused variable ‘pTxRing’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:115:19: warning: unused variable ‘j’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:115:6: warning: unused variable ‘index’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:447:11: warning: unused variable ‘BufBaseVa’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:446:11: warning: unused variable ‘BufBasePaLow’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:445:11: warning: unused variable ‘BufBasePaHigh’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:432:15: warning: unused variable ‘pPacket’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:431:15: warning: unused variable ‘pDmaBuf’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:430:16: warning: unused variable ‘pTxRing’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:428:14: warning: unused variable ‘pRxD’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:427:14: warning: unused variable ‘pTxD’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:425:10: warning: unused variable ‘RingBaseVa’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:424:10: warning: unused variable ‘RingBasePaLow’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:423:10: warning: unused variable ‘RingBasePaHigh’ [-Wunused-variable]
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_mac_pci.c:489:4: warning: ‘index’ may be used uninitialized in this function [-Wuninitialized]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/cmm_data_pci.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rtmp_mcu.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/ee_prom.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/ee_efuse.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/rt_rf.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../chips/rt30xx.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../chips/rt35xx.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/pci_main_dev.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../os/linux/pci_main_dev.c:320:13: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/misc.o
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/misc.c: In function ‘RTMPHwCoexSwitch’:
/var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../common/misc.c:963:2: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 6 has type ‘ULONG’ [-Wformat]
  CC [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/../../chips/rt3592cb.o
  LD [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.o
see include/linux/module.h for more information
  CC      /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.mod.o
  LD [M]  /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-14-generic'
cp -f /var/lib/dkms/rt3562/2.4.1.1/build/os/linux/rt3562sta.ko /tftpboot
```

They appear to be identical except for the first line. As you can see for 3.1.5-030105-generic several references are made to headers-3.0.0-14-generic
and none are made to headers-3.1.5-030105-generic. How do I fix this?

---

