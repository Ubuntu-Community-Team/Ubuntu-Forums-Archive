---
title: "After upgrade the kernel to 4.10.0-22 in my xps 9560 it freezes every boots"
date: 2017-05-24
forum: Hardware
---

### Post by fox887 on 2017-05-24
After I upgrade the kernel of my xps 9560 to 4.10.0-22 it freezes at every boot. 
To fix I uninstalled the kernel and after reboot everything is working fine. Anyway, after I buy this new notebook I never saw so many errors in logs as I see in this. 

Command executed to fix the boot using recovery mode...
 apt remove --purge linux-image-4.10.0-22-generic  linux-image-extra-4.10.0-22-generic linux-headers-4.10.0-22-generic linux-headers-4.10.0-22

I don't know if this is helfull....
 root@noteeduardo:~# lspci00:00.0 Host bridge: Intel Corporation Device 5910 (rev 05)
00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 05)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.1 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1d.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #13 (rev f1)
00:1d.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Device a171 (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
04:00.0 Non-Volatile memory controller: Device 1c5c:1284
root@noteeduardo:~# dmesg |grep -i -3 error
[    0.000023] Calibrating delay loop (skipped), value calculated using timer frequency.. 5616.00 BogoMIPS (lpj=11232000)
[    0.000025] pid_max: default: 32768 minimum: 301
[    0.000033] ACPI: Core revision 20160930
[    0.035702] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20160930/dswload-210)
[    0.035708] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20160930/psobject-227)
[    0.035753] ACPI Exception: AE_NOT_FOUND, (SSDT:xh_rvp11) while loading table (20160930/tbxfload-228)
[    0.038744] ACPI Error: 1 table load failures, 12 successful (20160930/tbxfload-246)
[    0.038769] Security Framework initialized
[    0.038769] Yama: becoming mindful.
[    0.038782] AppArmor: AppArmor initialized
--
[    2.603697] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[    2.603698] nouveau: detected PR support, will not use DSM
[    2.603781] nouveau 0000:01:00.0: unknown chipset (137000a1)
[    2.603785] nouveau: probe of 0000:01:00.0 failed with error -12
[    2.606024] [drm] Memory usable by graphics device = 4096M
[    2.606025] checking generic (80000000 1fb0000) vs hw (80000000 10000000)
[    2.606025] fb: switching to inteldrmfb from VESA VGA
--
[    4.015431] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    4.026665] lp: driver loaded but no devices found
[    4.028349] ppdev: user-space parallel port driver
[    4.057871] EXT4-fs (nvme0n1p3): re-mounted. Opts: errors=remount-ro
[    4.061114] systemd-journald[289]: Received request to flush runtime journal from PID 1
[    4.117726] ACPI Warning: \_SB.IETM._TRT: Return Package has no elements (empty) (20160930/nsprepkg-130)
[    4.117910] input: Intel HID events as /devices/platform/INT33D5:00/input/input10
--
[    4.138345] Bluetooth: HCI UART protocol QCA registered
[    4.138345] Bluetooth: HCI UART protocol AG6XX registered
[    4.138345] Bluetooth: HCI UART protocol Marvell registered
[    4.153971] int3403 thermal: probe of INT3403:06 failed with error -22
[    4.154232] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[    4.160513] intel-lpss 0000:00:15.0: enabling device (0000 -> 0002)
[    4.164190] idma64 idma64.0: Found Intel integrated DMA 64-bit
--
[    4.283800] dell_wmi: Detected Dell WMI interface version 1
[    4.283842] input: Dell WMI hotkeys as /devices/virtual/input/input16
[    4.321502] Adding 4847612k swap on /dev/nvme0n1p5.  Priority:-1 extents:1 across:4847612k SSFS
[    4.491810] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
[    4.491815] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    4.492227] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    4.492228] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.493346] ath10k_pci 0000:02:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    4.493347] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
--
[   15.525600] logitech-djreceiver 0003:046D:C52B.0009: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-1/input2
[   15.683323] input: Logitech Anywhere MX as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.2/0003:046D:C52B.0009/0003:046D:1017.000A/input/input27
[   15.683452] logitech-hidpp-device 0003:046D:1017.000A: input,hidraw1: USB HID v1.11 Mouse [Logitech Anywhere MX] on usb-0000:00:14.0-1:1
[   15.721319] pcieport 0000:00:1d.6: AER: Corrected error received: id=00ee
[   15.721329] pcieport 0000:00:1d.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ee(Receiver ID)
[   15.721333] pcieport 0000:00:1d.6:   device [8086:a11e] error status/mask=00000001/00002000
[   15.721336] pcieport 0000:00:1d.6:    [ 0] Receiver Error         (First)
[   16.383321] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   16.445615] wlp2s0: authenticate with 00:04:ed:f9:9c:d8
[   16.486811] wlp2s0: send auth to 00:04:ed:f9:9c:d8 (try 1/3)
--
[   16.490988] wlp2s0: RX AssocResp from 00:04:ed:f9:9c:d8 (capab=0x11 status=0 aid=4)
[   16.493795] wlp2s0: associated
[   16.493839] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   16.822475] ACPI Error: [SPRT] Namespace lookup failure, AE_ALREADY_EXISTS (20160930/dswload2-330)
[   16.822481] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20160930/psobject-227)
[   16.822484] ACPI Error: Method parse/execution failed [\_GPE.XTBT] (Node ffff8fdbaecee7a8), AE_ALREADY_EXISTS (20160930/psparse-543)
[   16.822489] ACPI Error: Method parse/execution failed [\_GPE.XTBT] (Node ffff8fdbaecee7a8), AE_ALREADY_EXISTS (20160930/psparse-543)
[   16.822494] ACPI Error: Method parse/execution failed [\_GPE._E42] (Node ffff8fdbaeceebb8), AE_ALREADY_EXISTS (20160930/psparse-543)
[   16.822497] ACPI: Marking method _E42 as Serialized because of AE_ALREADY_EXISTS error
[   16.822500] ACPI Exception: AE_ALREADY_EXISTS, while evaluating GPE method [_E42] (20160930/evgpe-646)
[   16.969917] pci 0000:06:00.0: [8086:1576] type 01 class 0x060400
[   16.970067] pci 0000:06:00.0: supports D1 D2
--
[   22.034157] pcieport 0000:07:02.0: BAR 13: failed to assign [io  size 0x1000]
[   22.034158] pcieport 0000:07:01.0: BAR 13: no space for [io  size 0x1000]
[   22.034159] pcieport 0000:07:01.0: BAR 13: failed to assign [io  size 0x1000]
[   26.988714] pcieport 0000:00:1d.6: AER: Corrected error received: id=00ee
[   26.988721] pcieport 0000:00:1d.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ee(Receiver ID)
[   26.988723] pcieport 0000:00:1d.6:   device [8086:a11e] error status/mask=00000001/00002000
[   26.988724] pcieport 0000:00:1d.6:    [ 0] Receiver Error         (First)
[   27.062614] pci_raw_set_power_state: 78 callbacks suppressed
[   27.062628] pcieport 0000:07:00.0: Refused to change power state, currently in D3
[   27.063882] pci_bus 0000:08: busn_res: [bus 08] is released
--
[   27.063975] pci_bus 0000:3e: busn_res: [bus 3e] is released
[   27.064021] pci_bus 0000:07: busn_res: [bus 07-3e] is released
[   75.181363] input: 16:10:13:23:0B:3A as /devices/virtual/input/input28
[  295.854482] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[  295.854492] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e8(Transmitter ID)
[  295.854497] pcieport 0000:00:1d.0:   device [8086:a118] error status/mask=00001000/00002000
[  295.854499] pcieport 0000:00:1d.0:    [12] Replay Timer Timeout  
[  374.157504] traps: unity-settings-[1939] trap int3 ip:7f76002c4de1 sp:7fff91501140 error:0
[  374.157512]  in libglib-2.0.so.0.5200.0[7f7600275000+111000]
[  447.159403] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[  447.165669] JFS: nTxBlock = 8192, nTxLock = 65536
--
[  447.767292] xor: automatically using best checksumming function   avx       
[  447.784023] Btrfs loaded, crc32c=crc32c-intel
[ 1103.679676] perf: interrupt took too long (2618 > 2500), lowering kernel.perf_event_max_sample_rate to 76250
[ 1217.866183] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[ 1217.866195] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e8(Transmitter ID)
[ 1217.866201] pcieport 0000:00:1d.0:   device [8086:a118] error status/mask=00001000/00002000
[ 1217.866205] pcieport 0000:00:1d.0:    [12] Replay Timer Timeout  
[ 1445.872375] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[ 1445.872391] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e8(Transmitter ID)
[ 1445.872401] pcieport 0000:00:1d.0:   device [8086:a118] error status/mask=00001000/00002000
[ 1445.872411] pcieport 0000:00:1d.0:    [12] Replay Timer Timeout  
[ 2204.825739] perf: interrupt took too long (3279 > 3272), lowering kernel.perf_event_max_sample_rate to 61000
[ 2253.564753] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[ 2253.564761] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e8(Transmitter ID)
[ 2253.564763] pcieport 0000:00:1d.0:   device [8086:a118] error status/mask=00001000/00002000
[ 2253.564764] pcieport 0000:00:1d.0:    [12] Replay Timer Timeout

---

### Post by tarjeihuse on 2017-10-04
Hi, did you find a solution to this problem? It seems to have struck me just yesterday.

---

