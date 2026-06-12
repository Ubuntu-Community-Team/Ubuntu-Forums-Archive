---
title: "rtl8192xSE Wireless Card"
date: 2010-04-13
forum: Hardware
---

### Post by mett demon on 2010-04-13
Hi Everybody;
I was wondering if anyone has a fix for rtl8192xSE wireless card and ubuntu in all its flavours????
I have tried almost everything (that I am aware of as a noob) to get this installed. I can find my router and can connect but not much else happens...... I have tried a few fixes that I have found in these forums with the exception of ndiswrapper as I read it won't work with a 64-bit machine.
I have a compaq 615 laptop with a realtek wlan 8192xse wireless card.
Any suggestions would help as I do not want to tell the missus that she was right when she was against a  Linux OS.
Thanks in advance

---

### Post by khelben1979 on 2010-04-13
[This page]("http://rtl-wifi.sourceforge.net/wiki/Main_Page") seems like a good starting point.

Also, what version of Ubuntu are you using? (including kernel version)

---

### Post by mett demon on 2010-04-13
Hi there thank you for reply, in answer to your question:

Linux benjamin-laptop 2.6.32-20-generic #30-Ubuntu SMP Mon Apr 12 15:20:57 UTC 2010 x86_64 GNU/Linux


Ubuntu 10.04 lucid...... but I have tried a variety of versions and can't seem to get any to work. 
Just downloading 9.04 to give it a go as there seem to be a few solved cases of the same issue. Will keep you posted.

---

### Post by mett demon on 2010-04-13
this is what I have done so far.

[CODE][/benjamin@benjamin-laptop:~$ cd '/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010' 
benjamin@benjamin-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-18-generic'
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_core.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_rfkill.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_dm.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_dev.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_Efuse.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_phy.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.o
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.c: In function ‘FirmwareSetH2CCmd’:
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.c:714: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_rtl6052.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_hwimg.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_led.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_mp.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_scan.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/wapi.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/wapi_interface.o
  LD [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-18-generic'
benjamin@benjamin-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-18-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-18-generic'
make[1]: Entering directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
make -C /lib/modules/2.6.28-18-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-18-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:104: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:306: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-18-generic'
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-18-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-18-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
make: *** [install] Error 2
benjamin@benjamin-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ 
CODE]
I have swapped on to 9.04 now as there seem to be more threads. Hope this can get sorted soon.

---

### Post by khelben1979 on 2010-04-14
[Wireless Network Cards RealTek]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek")

Is it true that the laptop uses the Broadcom 4312G chipset? (use lspci if uncertain)

---

### Post by mett demon on 2010-04-14
Well I am querying this myself as any product description I read relating to the Compaq 615 notebook describes the wlan card as Broadcom, but when I lspci it shows a realtek wlan card which is why I was confused for a while. I have e-mailed the supplier to see what the score is with this confusion.
Thanks for your advice and interest in my predicament so far.
regards ben

---

### Post by mett demon on 2010-04-14
for your information:

benjamin@benjamin-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
benjamin@benjamin-laptop:~$

---

### Post by mett demon on 2010-04-14
> **khelben1979 said:**
> [Wireless Network Cards RealTek]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek")

Is it true that the laptop uses the Broadcom 4312G chipset? (use lspci if uncertain)
I have checked this out before, but have read somewhere that the ndiswrapper won't work if you are running on 64-bit.
Thanks for your help, at least I know I am looking in the right places.:-)

---

