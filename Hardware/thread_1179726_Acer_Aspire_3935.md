---
title: "Acer Aspire 3935"
date: 2009-06-06
forum: Hardware
---

### Post by Rocks and Water on 2009-06-06
I'm contemplating a purchase of either the new Acer Aspire 3810T or the Acer Aspire 3935, but I can't seem to find a single instance of anyone running Ubuntu on the 3935. If anyone has any experience doing so, I'd love to hear it.

---

### Post by avilella on 2009-06-06
Hi,

I can't help you with the Acer Aspire 3935, but here is some compiled information from different ubuntuforums.org threads:

Installation instructions:
[http://ubuntuforums.org/showpost.php?p=7314698&postcount=1](http://ubuntuforums.org/showpost.php?p=7314698&postcount=1)

The currently reported battery life is 8 hours. To achieve this, use a standard Jaunty distribution.

Outstanding bug: ata2 exception EMask delays/prevents booting 9.04 & 8.10:
[https://bugs.launchpad.net/ubuntu/+bug/379831](https://bugs.launchpad.net/ubuntu/+bug/379831)

It's also been reported that the laptop will try to resume from suspend but power off instead.

> **Rocks and Water said:**
> I'm contemplating a purchase of either the new Acer Aspire 3810T or the Acer Aspire 3935, but I can't seem to find a single instance of anyone running Ubuntu on the 3935. If anyone has any experience doing so, I'd love to hear it.

---

### Post by fathomssen on 2009-06-07
Hi,

I am runnning Kubuntu 9.04 on an Aspire 3935. Most things work out of the box but there are some serious flaws still present:

[LIST]
[*]The display brightness cannot be adjusted. Neither using the Fn key combination nor using ACPI. It usually is at full brightness (which is bad for battery time) but right now it is at low brightness - I don't know why or how to change it. There are some entries in /proc/acpi/video but you cannot adjust the brightness (actually, you can write 10, 20, ..., 100 to /proc/acpi/video/brightness and the file "remembers" it but nothing gets adjusted).
[*]The fan is running awfully often although it only blows cold air. /proc/acpi/fan is empty :-(
[*]Another problem is the touchpad: It is a Synaptics touchpad with the latest firmware. This firmware seems not to be fully supported by the X.org driver. I posted a workaround for multitap on [http://ubuntuforums.org/showthread.php?t=969993](http://ubuntuforums.org/showthread.php?t=969993)
[*]The special keys for media playback and volume control work out of the box. Also, the touch keys above the keyboard (for mute, vol up and down, wireless and bluetooth on/off) work out of the box. The sleep button doesn't work (I allocated the Power key for that now), so doesn't the funny looking button on Fn+F2 (don't know what it is). I have not yet tested the VGA output but when I press Fn+F6, the display goes out so I guess it has something to do with it.
[/LIST]
As mentioned above. I haven't tested the VGA output yet or the SD card reader. Also, I had no use for the cam and so did not test it either.

I would be really happy to hear a solution for the brightness and the fan problems. I guess it is just some adjustment in the corresponding ACPI drivers.

Best regards,
Freddy

---

### Post by gnawol on 2009-06-27
I also have the Acer Aspire 3935. I have installed Linux Mint, almost everything working right out of the box.

Same issues as [fathomssen]("http://ubuntuforums.org/member.php?u=832199") of course.

Followed [fathomssen]("http://ubuntuforums.org/member.php?u=832199") 's multitap advice ( thank you, was missing that support )

Also screen brightness shows that the keys are registering but nothing is changing on the screen.

I can confirm that the webcam is working as well as the bluetooth.

Regards

---

### Post by gnawol on 2009-06-30
Managed to fix the brightness issue by updating the kernel ( found this in another thread ) 
[http://ubuntuforums.org/showpost.php?p=7484088&postcount=39](http://ubuntuforums.org/showpost.php?p=7484088&postcount=39)

After updating i had an issue with the sound not working ( im using linux mint, don't know if updating the kernel will also break the sound but if it does, the link is below to fix it)

[http://ubuntuforums.org/showpost.php?p=7540567&postcount=62](http://ubuntuforums.org/showpost.php?p=7540567&postcount=62)

Hope it helps

Regards.

---

### Post by fathomssen on 2009-06-30
Hmm, I am running a 2.6.31-rc1-gitX kernel and still have the brightness issues. Could you please post your kernel config?

---

### Post by gnawol on 2009-07-01
> **fathomssen said:**
> Hmm, I am running a 2.6.31-rc1-gitX kernel and still have the brightness issues. Could you please post your kernel config?

/cat/proc/version gives me ;

```
Linux version 2.6.30-020630-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #020630 SMP Wed Jun 10 09:45:40 UTC 2009

```

Hope that helps

---

### Post by fathomssen on 2009-07-01
Could you please do

```
cat /boot/config-`uname -r`
```and post the result (or whereever your kernel config file resides)?

---

### Post by fathomssen on 2009-07-09
*bump* Could you please post your kernel config. I guess, I'm just missing a configuration parameter in the kernel...

---

### Post by LewRockwell on 2009-07-10
Acer Aspire One AOA-150-1864 with the Dell mini-wlan 1390 card

Report:

Working fine triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version), Puppy Linux 4.2.1, and with five more logical partitions for five more *nix distros!

.

---

### Post by gnawol on 2009-07-16
When i do that command i get all kinds of things:

```
# CONFIG_USB_GADGET_M66592 is not set
# CONFIG_USB_GADGET_MUSB_HDRC is not set
# CONFIG_USB_GADGET_NET2280 is not set
# CONFIG_USB_GADGET_OMAP is not set
# CONFIG_USB_GADGET_PXA25X is not set
# CONFIG_USB_GADGET_PXA27X is not set
# CONFIG_USB_GADGET_S3C2410 is not set
CONFIG_USB_GADGET_SELECTED=y
CONFIG_USB_GADGET_VBUS_DRAW=2
# CONFIG_USB_GPIO_VBUS is not set
CONFIG_USB_GSPCA=m
CONFIG_USB_GSPCA_CONEX=m
CONFIG_USB_GSPCA_ETOMS=m
CONFIG_USB_GSPCA_FINEPIX=m
CONFIG_USB_GSPCA_MARS=m
# CONFIG_USB_GSPCA_MR97310A is not set
CONFIG_USB_GSPCA_OV519=m
# CONFIG_USB_GSPCA_OV534 is not set
CONFIG_USB_GSPCA_PAC207=m
CONFIG_USB_GSPCA_PAC7311=m
CONFIG_USB_GSPCA_SONIXB=m
CONFIG_USB_GSPCA_SONIXJ=m
CONFIG_USB_GSPCA_SPCA500=m
CONFIG_USB_GSPCA_SPCA501=m
CONFIG_USB_GSPCA_SPCA505=m
CONFIG_USB_GSPCA_SPCA506=m
CONFIG_USB_GSPCA_SPCA508=m
CONFIG_USB_GSPCA_SPCA561=m
# CONFIG_USB_GSPCA_SQ905 is not set
# CONFIG_USB_GSPCA_SQ905C is not set
CONFIG_USB_GSPCA_STK014=m
CONFIG_USB_GSPCA_SUNPLUS=m
CONFIG_USB_GSPCA_T613=m
CONFIG_USB_GSPCA_TV8532=m
CONFIG_USB_GSPCA_VC032X=m
CONFIG_USB_GSPCA_ZC3XX=m
# CONFIG_USB_G_PRINTER is not set
CONFIG_USB_G_SERIAL=m
CONFIG_USB_HID=m
CONFIG_USB_HIDDEV=y
CONFIG_USB_HSO=m
CONFIG_USB_HWA_HCD=m
CONFIG_USB_IBMCAM=m
CONFIG_USB_IDMOUSE=m
CONFIG_USB_IOWARRIOR=m
# CONFIG_USB_IP_COMMON is not set
CONFIG_USB_IRDA=m
CONFIG_USB_ISIGHTFW=m
CONFIG_USB_ISP116X_HCD=m
CONFIG_USB_ISP1760_HCD=m
CONFIG_USB_KAWETH=m
CONFIG_USB_KC2190=y
CONFIG_USB_KONICAWC=m
CONFIG_USB_LCD=m
CONFIG_USB_LD=m
CONFIG_USB_LED=m
CONFIG_USB_LEGOTOWER=m
# CONFIG_USB_LIBUSUAL is not set
CONFIG_USB_M5602=m
CONFIG_USB_MDC800=m
CONFIG_USB_MICROTEK=m
# CONFIG_USB_MIDI_GADGET is not set
CONFIG_USB_MON=y
CONFIG_USB_MR800=m
CONFIG_USB_NET_AX8817X=m
CONFIG_USB_NET_CDCETHER=m
# CONFIG_USB_NET_CDC_EEM is not set
CONFIG_USB_NET_CDC_SUBSET=m
CONFIG_USB_NET_DM9601=m
CONFIG_USB_NET_GL620A=m
CONFIG_USB_NET_MCS7830=m
CONFIG_USB_NET_NET1080=m
CONFIG_USB_NET_PLUSB=m
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_RNDIS_WLAN=m
CONFIG_USB_NET_SMSC95XX=m
CONFIG_USB_NET_ZAURUS=m
# CONFIG_USB_OHCI_BIG_ENDIAN_DESC is not set
# CONFIG_USB_OHCI_BIG_ENDIAN_MMIO is not set
CONFIG_USB_OHCI_HCD=y
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
# CONFIG_USB_OTG is not set
# CONFIG_USB_OV511 is not set
# CONFIG_USB_OXU210HP_HCD is not set
CONFIG_USB_PEGASUS=m
CONFIG_USB_PRINTER=m
CONFIG_USB_PWC=m
# CONFIG_USB_PWC_DEBUG is not set
CONFIG_USB_PWC_INPUT_EVDEV=y
CONFIG_USB_QUICKCAM_MESSENGER=m
CONFIG_USB_R8A66597_HCD=m
CONFIG_USB_RIO500=m
CONFIG_USB_RTL8150=m
CONFIG_USB_S2255=m
CONFIG_USB_SE401=m
CONFIG_USB_SERIAL=m
CONFIG_USB_SERIAL_AIRCABLE=m
CONFIG_USB_SERIAL_ARK3116=m
# CONFIG_USB_SERIAL_ATEN2011 is not set
CONFIG_USB_SERIAL_BELKIN=m
CONFIG_USB_SERIAL_CH341=m
# CONFIG_USB_SERIAL_CP210X is not set
CONFIG_USB_SERIAL_CYBERJACK=m
CONFIG_USB_SERIAL_CYPRESS_M8=m
CONFIG_USB_SERIAL_DEBUG=m
CONFIG_USB_SERIAL_DIGI_ACCELEPORT=m
CONFIG_USB_SERIAL_EDGEPORT=m
CONFIG_USB_SERIAL_EDGEPORT_TI=m
CONFIG_USB_SERIAL_EMPEG=m
CONFIG_USB_SERIAL_FTDI_SIO=m
CONFIG_USB_SERIAL_FUNSOFT=m
CONFIG_USB_SERIAL_GARMIN=m
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_HP4X=m
CONFIG_USB_SERIAL_IPAQ=m
CONFIG_USB_SERIAL_IPW=m
# CONFIG_USB_SERIAL_IR is not set
# CONFIG_USB_SERIAL_IUU is not set
CONFIG_USB_SERIAL_KEYSPAN=m
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KLSI=m
CONFIG_USB_SERIAL_KOBIL_SCT=m
CONFIG_USB_SERIAL_MCT_U232=m
CONFIG_USB_SERIAL_MOS7720=m
CONFIG_USB_SERIAL_MOS7840=m
CONFIG_USB_SERIAL_MOTOROLA=m
CONFIG_USB_SERIAL_NAVMAN=m
CONFIG_USB_SERIAL_OMNINET=m
# CONFIG_USB_SERIAL_OPTICON is not set
CONFIG_USB_SERIAL_OPTION=m
CONFIG_USB_SERIAL_OTI6858=m
CONFIG_USB_SERIAL_PL2303=m
# CONFIG_USB_SERIAL_QUALCOMM is not set
# CONFIG_USB_SERIAL_QUATECH_ESU100 is not set
CONFIG_USB_SERIAL_SAFE=m
# CONFIG_USB_SERIAL_SAFE_PADDED is not set
# CONFIG_USB_SERIAL_SIEMENS_MPI is not set
CONFIG_USB_SERIAL_SIERRAWIRELESS=m
CONFIG_USB_SERIAL_SPCP8X5=m
# CONFIG_USB_SERIAL_SYMBOL is not set
CONFIG_USB_SERIAL_TI=m
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_WHITEHEAT=m
CONFIG_USB_SERIAL_XIRCOM=m
CONFIG_USB_SEVSEG=m
CONFIG_USB_SI470X=m
CONFIG_USB_SISUSBVGA=m
# CONFIG_USB_SISUSBVGA_CON is not set
CONFIG_USB_SL811_CS=m
CONFIG_USB_SL811_HCD=m
CONFIG_USB_SN9C102=m
CONFIG_USB_SPEEDTOUCH=m
CONFIG_USB_STKWEBCAM=m
CONFIG_USB_STORAGE=m
CONFIG_USB_STORAGE_ALAUDA=m
# CONFIG_USB_STORAGE_CYPRESS_ATACB is not set
CONFIG_USB_STORAGE_DATAFAB=m
# CONFIG_USB_STORAGE_DEBUG is not set
CONFIG_USB_STORAGE_FREECOM=m
CONFIG_USB_STORAGE_ISD200=m
CONFIG_USB_STORAGE_JUMPSHOT=m
CONFIG_USB_STORAGE_KARMA=m
# CONFIG_USB_STORAGE_ONETOUCH is not set
CONFIG_USB_STORAGE_SDDR09=m
CONFIG_USB_STORAGE_SDDR55=m
CONFIG_USB_STORAGE_USBAT=m
# CONFIG_USB_STV06XX is not set
CONFIG_USB_STV680=m
CONFIG_USB_SUPPORT=y
CONFIG_USB_SUSPEND=y
# CONFIG_USB_TEST is not set
CONFIG_USB_TMC=m
CONFIG_USB_TRANCEVIBRATOR=m
CONFIG_USB_U132_HCD=m
CONFIG_USB_UEAGLEATM=m
CONFIG_USB_UHCI_HCD=y
CONFIG_USB_USBNET=m
CONFIG_USB_USS720=m
CONFIG_USB_VICAM=m
CONFIG_USB_VIDEO_CLASS=m
CONFIG_USB_VIDEO_CLASS_INPUT_EVDEV=y
CONFIG_USB_VST=m
CONFIG_USB_W9968CF=m
CONFIG_USB_WDM=m
CONFIG_USB_WHCI_HCD=m
CONFIG_USB_WUSB=m
CONFIG_USB_WUSB_CBAF=m
# CONFIG_USB_WUSB_CBAF_DEBUG is not set
CONFIG_USB_XUSBATM=m
CONFIG_USB_ZC0301=m
CONFIG_USB_ZD1201=m
CONFIG_USB_ZERO=m
CONFIG_USB_ZR364XX=m
# CONFIG_USER_NS is not set
# CONFIG_USER_SCHED is not set
CONFIG_USER_STACKTRACE_SUPPORT=y
CONFIG_USE_GENERIC_SMP_HELPERS=y
CONFIG_UTS_NS=y
CONFIG_UWB=m
CONFIG_UWB_HWA=m
CONFIG_UWB_I1480U=m
CONFIG_UWB_I1480U_WLP=m
CONFIG_UWB_WHCI=m
CONFIG_UWB_WLP=m
CONFIG_V4L_USB_DRIVERS=y
CONFIG_VETH=m
CONFIG_VFAT_FS=m
# CONFIG_VGACON_SOFT_SCROLLBACK is not set
CONFIG_VGASTATE=m
CONFIG_VGA_CONSOLE=y
CONFIG_VIA_FIR=m
CONFIG_VIA_RHINE=m
CONFIG_VIA_RHINE_MMIO=y
CONFIG_VIA_VELOCITY=m
CONFIG_VIDEOBUF_DMA_SG=m
CONFIG_VIDEOBUF_DVB=m
CONFIG_VIDEOBUF_GEN=m
CONFIG_VIDEOBUF_VMALLOC=m
CONFIG_VIDEO_ADV7170=m
CONFIG_VIDEO_ADV7175=m
# CONFIG_VIDEO_ADV_DEBUG is not set
CONFIG_VIDEO_ALLOW_V4L1=y
CONFIG_VIDEO_AU0828=m
CONFIG_VIDEO_BT819=m
CONFIG_VIDEO_BT848=m
CONFIG_VIDEO_BT848_DVB=y
CONFIG_VIDEO_BT856=m
CONFIG_VIDEO_BT866=m
CONFIG_VIDEO_BTCX=m
CONFIG_VIDEO_BWQCAM=m
CONFIG_VIDEO_CAFE_CCIC=m
CONFIG_VIDEO_CAPTURE_DRIVERS=y
CONFIG_VIDEO_CPIA=m
CONFIG_VIDEO_CPIA2=m
CONFIG_VIDEO_CPIA_PP=m
CONFIG_VIDEO_CPIA_USB=m
CONFIG_VIDEO_CQCAM=m
CONFIG_VIDEO_CS5345=m
CONFIG_VIDEO_CS53L32A=m
CONFIG_VIDEO_CX18=m
# CONFIG_VIDEO_CX231XX is not set
CONFIG_VIDEO_CX2341X=m
CONFIG_VIDEO_CX23885=m
CONFIG_VIDEO_CX25840=m
CONFIG_VIDEO_CX88=m
CONFIG_VIDEO_CX88_ALSA=m
CONFIG_VIDEO_CX88_BLACKBIRD=m
CONFIG_VIDEO_CX88_DVB=m
CONFIG_VIDEO_CX88_MPEG=m
CONFIG_VIDEO_CX88_VP3054=m
CONFIG_VIDEO_DEV=m
CONFIG_VIDEO_EM28XX=m
CONFIG_VIDEO_EM28XX_ALSA=m
CONFIG_VIDEO_EM28XX_DVB=m
CONFIG_VIDEO_FB_IVTV=m
# CONFIG_VIDEO_FIXED_MINOR_RANGES is not set
# CONFIG_VIDEO_GO7007 is not set
# CONFIG_VIDEO_HDPVR is not set
CONFIG_VIDEO_HELPER_CHIPS_AUTO=y
CONFIG_VIDEO_HEXIUM_GEMINI=m
CONFIG_VIDEO_HEXIUM_ORION=m
CONFIG_VIDEO_IR=m
CONFIG_VIDEO_IR_I2C=m
CONFIG_VIDEO_IVTV=m
CONFIG_VIDEO_KS0127=m
CONFIG_VIDEO_M52790=m
CONFIG_VIDEO_MEDIA=m
CONFIG_VIDEO_MEYE=m
CONFIG_VIDEO_MSP3400=m
CONFIG_VIDEO_MXB=m
CONFIG_VIDEO_OUTPUT_CONTROL=m
CONFIG_VIDEO_OV7670=m
CONFIG_VIDEO_OVCAMCHIP=m
CONFIG_VIDEO_PMS=m
CONFIG_VIDEO_PVRUSB2=m
# CONFIG_VIDEO_PVRUSB2_DEBUGIFC is not set
CONFIG_VIDEO_PVRUSB2_DVB=y
CONFIG_VIDEO_PVRUSB2_SYSFS=y
CONFIG_VIDEO_SAA5246A=m
CONFIG_VIDEO_SAA5249=m
CONFIG_VIDEO_SAA6588=m
CONFIG_VIDEO_SAA7110=m
CONFIG_VIDEO_SAA711X=m
CONFIG_VIDEO_SAA7127=m
CONFIG_VIDEO_SAA7134=m
CONFIG_VIDEO_SAA7134_ALSA=m
CONFIG_VIDEO_SAA7134_DVB=m
CONFIG_VIDEO_SAA7146=m
CONFIG_VIDEO_SAA7146_VV=m
CONFIG_VIDEO_SAA717X=m
CONFIG_VIDEO_SAA7185=m
CONFIG_VIDEO_STRADIS=m
CONFIG_VIDEO_TDA7432=m
CONFIG_VIDEO_TDA9840=m
CONFIG_VIDEO_TEA6415C=m
CONFIG_VIDEO_TEA6420=m
CONFIG_VIDEO_TUNER=m
CONFIG_VIDEO_TVAUDIO=m
CONFIG_VIDEO_TVEEPROM=m
CONFIG_VIDEO_TVP5150=m
CONFIG_VIDEO_UPD64031A=m
CONFIG_VIDEO_UPD64083=m
CONFIG_VIDEO_USBVIDEO=m
CONFIG_VIDEO_USBVISION=m
CONFIG_VIDEO_V4L1=m
CONFIG_VIDEO_V4L1_COMPAT=y
CONFIG_VIDEO_V4L2=m
CONFIG_VIDEO_V4L2_COMMON=m
CONFIG_VIDEO_VIVI=m
CONFIG_VIDEO_VP27SMPX=m
CONFIG_VIDEO_VPX3220=m
CONFIG_VIDEO_W9966=m
CONFIG_VIDEO_WM8739=m
CONFIG_VIDEO_WM8775=m
CONFIG_VIDEO_ZORAN=m
CONFIG_VIDEO_ZORAN_AVS6EYES=m
CONFIG_VIDEO_ZORAN_BUZ=m
CONFIG_VIDEO_ZORAN_DC10=m
CONFIG_VIDEO_ZORAN_DC30=m
CONFIG_VIDEO_ZORAN_LML33=m
CONFIG_VIDEO_ZORAN_LML33R10=m
CONFIG_VIDEO_ZORAN_ZR36060=m
CONFIG_VIRTIO=m
CONFIG_VIRTIO_BALLOON=m
CONFIG_VIRTIO_BLK=m
CONFIG_VIRTIO_CONSOLE=m
CONFIG_VIRTIO_NET=m
CONFIG_VIRTIO_PCI=m
CONFIG_VIRTIO_RING=m
CONFIG_VIRTUALIZATION=y
CONFIG_VIRT_TO_BUS=y
CONFIG_VITESSE_PHY=m
CONFIG_VLAN_8021Q=m
CONFIG_VLAN_8021Q_GVRP=y
CONFIG_VLSI_FIR=m
CONFIG_VM86=y
CONFIG_VMI=y
CONFIG_VM_EVENT_COUNTERS=y
CONFIG_VORTEX=m
CONFIG_VT=y
CONFIG_VT_CONSOLE=y
CONFIG_VT_HW_CONSOLE_BINDING=y
CONFIG_VXFS_FS=m
# CONFIG_VXGE is not set
CONFIG_W1=m
CONFIG_W1_CON=y
CONFIG_W1_MASTER_DS2482=m
CONFIG_W1_MASTER_DS2490=m
CONFIG_W1_MASTER_GPIO=m
CONFIG_W1_MASTER_MATROX=m
CONFIG_W1_SLAVE_BQ27000=m
# CONFIG_W1_SLAVE_DS2431 is not set
CONFIG_W1_SLAVE_DS2433=m
# CONFIG_W1_SLAVE_DS2433_CRC is not set
CONFIG_W1_SLAVE_DS2760=m
CONFIG_W1_SLAVE_SMEM=m
CONFIG_W1_SLAVE_THERM=m
# CONFIG_W35UND is not set
CONFIG_W83627HF_WDT=m
CONFIG_W83697HF_WDT=m
CONFIG_W83697UG_WDT=m
CONFIG_W83877F_WDT=m
CONFIG_W83977F_WDT=m
CONFIG_WAFER_WDT=m
CONFIG_WAN=y
CONFIG_WANXL=m
CONFIG_WAN_ROUTER=m
CONFIG_WAN_ROUTER_DRIVERS=m
CONFIG_WATCHDOG=y
# CONFIG_WATCHDOG_NOWAYOUT is not set
CONFIG_WAVELAN=m
CONFIG_WD80x3=m
CONFIG_WDT=m
CONFIG_WDTPCI=m
CONFIG_WDT_501_PCI=y
# CONFIG_WIMAX is not set
CONFIG_WINBOND_840=m
CONFIG_WINBOND_FIR=m
CONFIG_WIRELESS=y
CONFIG_WIRELESS_EXT=y
CONFIG_WIRELESS_EXT_SYSFS=y
# CONFIG_WIRELESS_OLD_REGULATORY is not set
CONFIG_WLAN_80211=y
CONFIG_WLAN_PRE80211=y
# CONFIG_WM8350_POWER is not set
# CONFIG_WM8350_WATCHDOG is not set
# CONFIG_WORKQUEUE_TRACER is not set
CONFIG_X25=m
CONFIG_X25_ASY=m
CONFIG_X86=y
CONFIG_X86_32=y
CONFIG_X86_32_LAZY_GS=y
# CONFIG_X86_32_NON_STANDARD is not set
CONFIG_X86_32_SMP=y
# CONFIG_X86_64 is not set
CONFIG_X86_ACPI_CPUFREQ=y
CONFIG_X86_APM_BOOT=y
# CONFIG_X86_BIGSMP is not set
CONFIG_X86_BOOTPARAM_MEMORY_CORRUPTION_CHECK=y
CONFIG_X86_BSWAP=y
CONFIG_X86_CHECK_BIOS_CORRUPTION=y
CONFIG_X86_CMPXCHG=y
CONFIG_X86_CPU=y
CONFIG_X86_CPUFREQ_NFORCE2=y
CONFIG_X86_CPUID=m
# CONFIG_X86_CPU_DEBUG is not set
# CONFIG_X86_ELAN is not set
CONFIG_X86_EXTENDED_PLATFORM=y
CONFIG_X86_GENERIC=y
CONFIG_X86_GX_SUSPMOD=y
CONFIG_X86_HT=y
CONFIG_X86_INTEL_USERCOPY=y
CONFIG_X86_INTERNODE_CACHE_BYTES=64
CONFIG_X86_INVLPG=y
CONFIG_X86_IO_APIC=y
CONFIG_X86_L1_CACHE_BYTES=64
CONFIG_X86_L1_CACHE_SHIFT=5
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_LONGHAUL=y
CONFIG_X86_LONGRUN=y
# CONFIG_X86_MCE is not set
CONFIG_X86_MINIMUM_CPU_FAMILY=4
CONFIG_X86_MPPARSE=y
CONFIG_X86_MSR=m
CONFIG_X86_P4_CLOCKMOD=m
# CONFIG_X86_PAT is not set
CONFIG_X86_PLATFORM_DEVICES=y
CONFIG_X86_PM_TIMER=y
CONFIG_X86_POPAD_OK=y
CONFIG_X86_POWERNOW_K6=y
CONFIG_X86_POWERNOW_K7=y
CONFIG_X86_POWERNOW_K7_ACPI=y
CONFIG_X86_POWERNOW_K8=y
CONFIG_X86_PPRO_FENCE=y
# CONFIG_X86_PTDUMP is not set
# CONFIG_X86_RDC321X is not set
CONFIG_X86_REBOOTFIXUPS=y
# CONFIG_X86_REROUTE_FOR_BROKEN_BOOT_IRQS is not set
CONFIG_X86_RESERVE_LOW_64K=y
CONFIG_X86_SPEEDSTEP_CENTRINO=y
CONFIG_X86_SPEEDSTEP_CENTRINO_TABLE=y
CONFIG_X86_SPEEDSTEP_ICH=y
CONFIG_X86_SPEEDSTEP_LIB=y
CONFIG_X86_SPEEDSTEP_RELAXED_CAP_CHECK=y
CONFIG_X86_SPEEDSTEP_SMI=y
CONFIG_X86_TRAMPOLINE=y
# CONFIG_X86_VERBOSE_BOOTUP is not set
CONFIG_X86_WP_WORKS_OK=y
CONFIG_X86_XADD=y
CONFIG_XFRM=y
CONFIG_XFRM_IPCOMP=m
# CONFIG_XFRM_MIGRATE is not set
# CONFIG_XFRM_STATISTICS is not set
# CONFIG_XFRM_SUB_POLICY is not set
CONFIG_XFRM_USER=m
# CONFIG_XFS_DEBUG is not set
CONFIG_XFS_FS=m
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_QUOTA=y
CONFIG_XFS_RT=y
CONFIG_XOR_BLOCKS=m
CONFIG_YAM=m
CONFIG_YELLOWFIN=m
CONFIG_YENTA=m
CONFIG_YENTA_ENE_TUNE=y
CONFIG_YENTA_O2=y
CONFIG_YENTA_RICOH=y
CONFIG_YENTA_TI=y
CONFIG_YENTA_TOSHIBA=y
CONFIG_ZD1211RW=m
# CONFIG_ZD1211RW_DEBUG is not set
CONFIG_ZEROPLUS_FF=m
CONFIG_ZISOFS=y
CONFIG_ZLIB_DEFLATE=m
CONFIG_ZLIB_INFLATE=y
CONFIG_ZNET=m
CONFIG_ZONE_DMA=y
# CONFIG_ZONE_DMA32 is not set
CONFIG_ZONE_DMA_FLAG=1
#
# Config options for config.generic automatically generated by splitconfig.pl
#
# CONFIG_ARCH_PHYS_ADDR_T_64BIT is not set
# CONFIG_ASYNC_TX_DMA is not set
CONFIG_DCA=m
CONFIG_DEFAULT_CFQ=y
# CONFIG_DEFAULT_DEADLINE is not set
CONFIG_DEFAULT_IOSCHED="cfq"
CONFIG_DMADEVICES=y
# CONFIG_DMATEST is not set
CONFIG_DMA_ENGINE=y
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_HZ=250
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
CONFIG_IGB_DCA=y
CONFIG_INTEL_IOATDMA=m
CONFIG_IXGBE_DCA=y
# CONFIG_LGUEST is not set
# CONFIG_LGUEST_GUEST is not set
CONFIG_M586=y
# CONFIG_M686 is not set
CONFIG_MYRI10GE_DCA=y
CONFIG_NET_DMA=y
# CONFIG_PHYS_ADDR_T_64BIT is not set
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
CONFIG_X86_ALIGNMENT_16=y
CONFIG_X86_E_POWERSAVER=m
CONFIG_X86_F00F_BUG=y

```

---

### Post by wow666 on 2009-07-16
Cheapest Gold @ [www.Belrion.com](www.Belrion.com)
10kGold for 75usd ! Secure Manual Powerlevel + Cheap Accounts Too !
While Stock Last ^^
Paypal World Seller + Macfee Secured Site ^^
USE WOW GOLD COUPON CODE for 5% Bonus : WOW2200

---

### Post by fathomssen on 2009-07-16
> **gnawol said:**
> When i do that command i get all kinds of things:

Thanks, just what I needed!

---

### Post by gnawol on 2009-07-16
I hope it helped, it actually displayed a whole lot more but it listed more than the shell would display.. if there's another command i need to do let me know. :)

---

### Post by madturkey on 2009-10-27
Just put Ubuntu 9.04 onto an Acer 3935.  Only issues so far are:
 
- No sound from speakers but sound from headphones.  Fixed by visiting various threads to add "Acer" definition into Alsa-config file (can't remember exact fix I'm afraid)
- No ability to change brightness.  A bit too new to Linux to update the kernel myself so waiting for Karmic which I'm hoping might fix it
- Battery power going down pretty quick - only getting a little over 2 hours instead of the 5ish I was getting for Vista.  Anyone have any tips for this?  I've not yet looked into the power settings
 
Otherwise it seemed to work pretty fine out of the box, although I've not tried some of the less commonly used hardware like Bluetooth, the webcam or the card reader

---

### Post by mjcritchie on 2009-12-16
I've just installed 9.10 on my Aspire 3935 and the brightness issue is still there.

If anyone's managed to fix it, can they let me know how?
I tried using the other kernel (which now seems to be older than the current one I'm using) but that didn't seem to work :(

Any help would be much appreciated.

---

### Post by itpawn on 2010-02-24
> **mjcritchie said:**
> I've just installed 9.10 on my Aspire 3935 and the brightness issue is still there.

If anyone's managed to fix it, can they let me know how?
I tried using the other kernel (which now seems to be older than the current one I'm using) but that didn't seem to work :(

Any help would be much appreciated.

Can you please update your experience with ubuntu 9.10 on the aspire 3935? thank you very much

---

### Post by anaconda on 2010-02-24
brightness can propably be changed with giving different values to:

xbacklight -set 100

xgamma -gamma 0.7
Works too.. try different values..
(xbacklight need to be installed first: sudo apt-get install xbacklight)

---

### Post by mjcritchie on 2010-02-26
> **itpawn said:**
> Can you please update your experience with ubuntu 9.10 on the aspire 3935? thank you very much

I've managed to get pretty much everything working nicely.

I solved the brightness issue by trying some of the workarounds mentioned in this thread: [http://swiss.ubuntuforums.org/showthread.php?t=1217421](http://swiss.ubuntuforums.org/showthread.php?t=1217421)

I also had a few problems with flash video (which I think was more about running 64bit Ubuntu than the 3935) but solved that here: [http://ubuntuforums.org/showthread.php?t=1314910](http://ubuntuforums.org/showthread.php?t=1314910)

The only thing I haven't got working is the fingerprint reader, but I haven't tried and am not too bothered about it.

The biggest problem I'm having with the laptop involves the Bluetooth and wifi randomly flashing and turning off and on, as described in these posts: 
[http://forums.pcworld.com/index.php?/topic/67246-problem-with-acer-aspire-3935/](http://forums.pcworld.com/index.php?/topic/67246-problem-with-acer-aspire-3935/)
and
[http://windows7forums.com/windows-7-hardware/20016-acer-3935-64bit-ultimate-bt-wireless-off-constantly.html](http://windows7forums.com/windows-7-hardware/20016-acer-3935-64bit-ultimate-bt-wireless-off-constantly.html)

This seems to happen with other operating systems though, so doesn't seem to be an Ubuntu issue.
As yet there isn't fix for this :(

---

### Post by piruvato on 2010-02-28
thanks mjcritchie, I tried to do but I crashed GRUB, could you please post the exact solition you did??

thaks in advance

---

### Post by mjcritchie on 2010-02-28
> **piruvato said:**
> thanks mjcritchie, I tried to do but I crashed GRUB, could you please post the exact solition you did??

thaks in advance

No problem. Are you talking about fixing the brightness, or the flash support?

---

### Post by piruvato on 2010-02-28
About the brigthness problem,  thanks mjcritchie

---

### Post by mjcritchie on 2010-02-28
OK, this is what I did, based on the information here: [http://swiss.ubuntuforums.org/showthread.php?t=1217421&page=3](http://swiss.ubuntuforums.org/showthread.php?t=1217421&page=3)

Open up a terminal window and type:

```
gksudo gedit /etc/default/grub
```

You may have to enter your administrator password.

That should open up a text file in gedit. Look for the lines that look a bit like this:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"**
GRUB_CMDLINE_LINUX=" quiet"

The line that I've put in bold is the one I changed. I can't remember what the default value was, but if you copy and paste what I've got above, you should be fine.

Save and close the gedit window.

Back in your terminal type:

```
sudo update-grub
```

This should update the changes you've made to grub.

That's it!

Let me know if it works :)

---

### Post by piruvato on 2010-03-01
Ok, I did exactly what you post, and now screen brightness works well adjusting xbacklight on the console but not directly on keyboard. Perhaps is due to the fact I'm using  KDE 4, but this is enough for me.  

Thank-you very much for your help.

P.D. I will look forward for the solution of the other issues and if I find something i will let you kown.

---

### Post by mjcritchie on 2010-03-03
I'm glad it, sort of, worked! 

Yes, I should have mentioned that I'm on Ubuntu 9.10. I suppose things are a bit different on Kubuntu.

---

### Post by madturkey on 2010-03-09
I had 9.10 running fine on my laptop (upgraded from 9.04) until the speakers died and I sent it back for fixing - Acer returned it to me with new speakers and HDD and Vista installed.

Reinstalled 9.10 from DVD and now no sound and also no hardware keys for volume / bluetooth / wifi etc.  Any ideas?

---

### Post by mjcritchie on 2010-03-10
> **madturkey said:**
> I had 9.10 running fine on my laptop (upgraded from 9.04) until the speakers died and I sent it back for fixing - Acer returned it to me with new speakers and HDD and Vista installed.

Reinstalled 9.10 from DVD and now no sound and also no hardware keys for volume / bluetooth / wifi etc.  Any ideas?

Don't know if it's relevant, but take a look at post #62 on [this]("http://ubuntuforums.org/showthread.php?p=7540567") thread.

---

### Post by Fatal1ty on 2010-03-20
Hi, 
did someone tried the 10.04 beta?
how much time do you get from the standard battery (just surfing the web, and doing light stuff)? 

Thank you

---

### Post by mjcritchie on 2010-05-15
Currently got 10.04 installed. Haven't really noticed any improvement in the battery life.
Can manage three hours at a push I reckon.

---

### Post by mjcritchie on 2010-06-07
Argh. Recently the fan has been running non-stop, even though the CPU temperature never seems to go above 40°C.

I've tried various solutions posted on these forums, but to no avail. Can anyone help?

---

