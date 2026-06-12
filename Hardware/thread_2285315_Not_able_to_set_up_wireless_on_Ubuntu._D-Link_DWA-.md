---
title: "Not able to set up wireless on Ubuntu. D-Link DWA-180 Wireless Dongle"
date: 2015-07-04
forum: Hardware
---

### Post by nathan80 on 2015-07-04
Hi, just installed Ubuntu and am now trying to get the wifi to work. I have a Dlink DWA-180 wireless dongle. I went on the dlink website and downloaded the linux drivers. When executing the provided install.sh file, I get an error. I've seen similar posts and their respective solutions; however, none of the solutions are working for me.  Here's the terminal script. Any help is appreciated

Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0


[CODE][/CODE ]##################################################
Decompress the driver source tar ball:
    rtl8812AU_linux_v4.3.2_11100.20140411.tar.gz
rtl8812AU_linux_v4.3.2_11100.20140411/
rtl8812AU_linux_v4.3.2_11100.20140411/core/
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_wapi_sms4.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_mlme_ext.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_sta_mgt.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_pwrctrl.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_bt_mp.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_io.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_cmd.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_xmit.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_ioctl_rtl.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_ioctl_set.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_ieee80211.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_btcoex.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_beamforming.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/efuse/
rtl8812AU_linux_v4.3.2_11100.20140411/core/efuse/rtw_efuse.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_wapi.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_mp_ioctl.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_vht.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_sreset.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_p2p.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_mlme.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_rf.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_ap.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_recv.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_ioctl_query.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_mp.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_br_ext.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_security.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_eeprom.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_tdls.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_odm.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_iol.c
rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_wlan_util.c
rtl8812AU_linux_v4.3.2_11100.20140411/wlan0dhcp
rtl8812AU_linux_v4.3.2_11100.20140411/Makefile
rtl8812AU_linux_v4.3.2_11100.20140411/clean
rtl8812AU_linux_v4.3.2_11100.20140411/include/
rtl8812AU_linux_v4.3.2_11100.20140411/include/gspi_ops_linux.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8723BPwrSeq.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types_linux.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_p2p.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/pci_osintf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_version.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8821APwrSeq.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sdio_ops.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_odm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sta_info.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/circ_buf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_mp_phy_regdef.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_ap.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_io.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_eeprom.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sdio_osintf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/autoconf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types_sdio.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8188EPwrSeq.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_btcoex.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192EPhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_pg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sdio_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_mlme_ext.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sdio_ops_xp.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/osdep_service_ce.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_debug.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/osdep_service_bsd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/gspi_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/ioctl_cfg80211.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_vht.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8821a_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192CPhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/usb_ops_linux.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_btcoex.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8188EPhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/recv_osdep.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_com_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_tdls.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/usb_ops.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/cmd_osdep.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192CPhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_wapi.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8812PwrSeq.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8723APhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_data.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types_xp.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_security.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_com_reg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_ioctl_rtl.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192DPhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_conf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/usb_vendor_req.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_com_phycfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/osdep_service_xp.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/linux/
rtl8812AU_linux_v4.3.2_11100.20140411/include/linux/wireless.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_event.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8723BPhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/usb_osintf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192EPhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_iol.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_qos.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_event.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/h2clbk.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8812PhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_ht.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sdio_ops_ce.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/ip.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_sdio.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/gspi_osintf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/HalPwrSeqCmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_ioctl.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types_pci.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/mlme_osdep.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/sdio_ops_linux.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8723PwrSeq.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/pci_ops.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_ioctl_query.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/gspi_ops.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8723BPhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types_gspi.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8188EPhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192EPwrSeq.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/HalVerDef.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/nic_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_mp.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/custom_gpio.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/mp_custom_oid.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_mp_ioctl.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/xmit_osdep.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/ieee80211.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_ioctl_set.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/byteorder/
rtl8812AU_linux_v4.3.2_11100.20140411/include/byteorder/generic.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/byteorder/big_endian.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/byteorder/swab.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/byteorder/swabb.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/byteorder/little_endian.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/osdep_service.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_bt_mp.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/basic_types.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/if_ether.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8812PhyReg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8821a_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_mlme.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_br_ext.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_byteorder.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_com.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/usb_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_pwrctrl.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/osdep_service_linux.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_intf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192d_dm.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_android.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_phy_reg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_pg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/wlan_bssdef.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_wifi_regd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_phy.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/drv_types_ce.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723a_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8192DPhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/hal_com_h2c.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_beamforming.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/wifi.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/ieee80211_ext.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_led.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8812a_cmd.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_sreset.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/pci_hal.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/Hal8723APhyCfg.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtw_efuse.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_recv.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192e_xmit.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/ethernet.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8723b_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8188e_rf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/osdep_intf.h
rtl8812AU_linux_v4.3.2_11100.20140411/include/rtl8192c_spec.h
rtl8812AU_linux_v4.3.2_11100.20140411/runwpa
rtl8812AU_linux_v4.3.2_11100.20140411/platform/
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_ops.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_ARM_SUNnI_sdio.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_ARM_SUNxI_usb.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_ARM_SUNxI_sdio.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_sprd_sdio.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_RTK_DMP_usb.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_ARM_WMT_sdio.c
rtl8812AU_linux_v4.3.2_11100.20140411/platform/platform_ops.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_com_phycfg.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/led/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/led/hal_usb_led.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_xmit.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_hal_init.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_sreset.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/Hal8821APwrSeq.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_cmd.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/Hal8812PwrSeq.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_rf6052.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_dm.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/usb/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/usb/usb_halinit.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/usb/rtl8812au_xmit.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/usb/rtl8812au_recv.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/usb/usb_ops_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/usb/rtl8812au_led.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_mp.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_phycfg.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/rtl8812a/rtl8812a_rxdesc.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_AntDiv.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_PathDiv.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_RegDefine11AC.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_precomp.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_DIG.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_reg.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/HalPhyRf.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_HWConfig.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_AntDiv.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_debug.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_DIG.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_EdcaTurboCheck.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_RegDefine11N.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_interface.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/odm_RTL8812A.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/odm_RTL8812A.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_HWConfig.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_EdcaTurboCheck.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_interface.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_PathDiv.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_DynamicBBPowerSaving.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_debug.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_types.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/odm_DynamicBBPowerSaving.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC/HalPhyRf.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_com.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/Mp_Precomp.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtcOutSrc.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.h
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_hci/
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_hci/hal_usb.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_intf.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_phy.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/hal_btcoex.c
rtl8812AU_linux_v4.3.2_11100.20140411/hal/HalPwrSeqCmd.c
rtl8812AU_linux_v4.3.2_11100.20140411/Kconfig
rtl8812AU_linux_v4.3.2_11100.20140411/ifcfg-wlan0
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/osdep_service.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/os_intfs.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/mlme_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/xmit_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/rtw_proc.h
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/custom_gpio_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/wifi_regd.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/rtw_android.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/usb_ops_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/usb_intf.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/ioctl_cfg80211.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/rtw_proc.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/ioctl_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411/os_dep/linux/recv_linux.c
rtl8812AU_linux_v4.3.2_11100.20140411
Authentication requested [root] for make clean:
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.19.0-21-generic/build M=/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411  modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-21-generic'
  CC [M]  /home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_cmd.o
  CC [M]  /home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_security.o
  CC [M]  /home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.o
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c: In function ‘dump_drv_version’:
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c:66:64: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
  DBG_871X_SEL_NL(sel, "build time: %s %s\n", __DATE__, __TIME__);
                                                                ^
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c:66:1: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
  DBG_871X_SEL_NL(sel, "build time: %s %s\n", __DATE__, __TIME__);
 ^
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c:66:1: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c:66:1: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c:66:1: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.c:66:1: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.o' failed
make[2]: *** [/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411/core/rtw_debug.o] Error 1
Makefile:1394: recipe for target '_module_/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411' failed
make[1]: *** [_module_/home/nathan/Desktop/RTL8812AU_linux_v4.3.2_11100.20140411/driver/rtl8812AU_linux_v4.3.2_11100.20140411] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-21-generic'
Makefile:1350: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

---

### Post by weatherman2 on 2015-07-04
The D-Link driver may be too old to compile on the latest Ubuntu.  Try to get a newer driver for the Realtek 8812AU chipset.  Try this:

[http://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/](http://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/)

It's possible you should not have the USB wireless card plugged in until you have completed building the driver.

---

### Post by Geoffrey_Arndt on 2015-07-05
Weatherman2's link is worth a try, but as a backup, a wireless dongle that has/is working "out of the box" is Panda's Ultra 150 wireless dongle.   Available on Amazon for about $10.00 . . . no compiling, solid connections.

[http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?ie=UTF8&qid=1436070791&sr=8-1&keywords=panda+ultra+wireless+n+usb](http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?ie=UTF8&qid=1436070791&sr=8-1&keywords=panda+ultra+wireless+n+usb)

---

### Post by nathan80 on 2015-07-05
Hey weatherman2, thanks for the website. I tried it out and received a similar if not identical result as with other methods. Geoffrey, the only problem is that I've had the cheap dongles before and the internet connection and reliability sucks, at best.

```

```nathan@nathan-home:~/rtl8812AU_8821AU_linux$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.19.0-21-generic/build M=/home/nathan/rtl8812AU_8821AU_linux  modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-21-generic'
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_cmd.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_security.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_debug.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_io.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_ioctl_query.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_ioctl_set.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_ieee80211.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_mlme.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_mlme_ext.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_wlan_util.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_vht.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_pwrctrl.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_rf.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_recv.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_sta_mgt.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_ap.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_xmit.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_p2p.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_tdls.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_br_ext.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_iol.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/rtw_sreset.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/core/efuse/rtw_efuse.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/osdep_service.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/os_intfs.o
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/os_intfs.c:1695:2: warning: initialization from incompatible pointer type
  .ndo_select_queue = rtw_select_queue,
  ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/os_intfs.c:1695:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’)
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/usb_intf.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_linux.o
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_linux.c: In function ‘rtw_mp_efuse_get’:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_linux.c:8887:65: warning: iteration 16u invokes undefined behavior [-Waggressive-loop-optimizations]
     sprintf(extra, "%s%02X ", extra, pEfuseHal->fakeEfuseInitMap[i+j]);
                                                                 ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_linux.c:8875:3: note: containing loop
   for (i = 0; i < EFUSE_MAP_SIZE; i += 16)
   ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_linux.c:9307:69: warning: iteration 16u invokes undefined behavior [-Waggressive-loop-optimizations]
     sprintf(extra, "%s %02X", extra, pEfuseHal->fakeEfuseModifiedMap[i+j]);
                                                                     ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_linux.c:9295:3: note: containing loop
   for (i=0; i<EFUSE_MAP_SIZE; i+=16)
   ^
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/xmit_linux.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/mlme_linux.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/recv_linux.o
  CC [M]  /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘cfg80211_rtw_add_key’:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:1250:35: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ qualifier from pointer target type
   _rtw_memcpy(param->u.crypt.seq, params->seq, params->seq_len);
                                   ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz);
             ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:1256:35: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ qualifier from pointer target type
   _rtw_memcpy(param->u.crypt.key, params->key, params->key_len);
                                   ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz);
             ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘cfg80211_rtw_connect’:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2550:30: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ qualifier from pointer target type
  _rtw_memcpy(ndis_ssid.Ssid, sme->ssid, sme->ssid_len);
                              ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz);
             ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2587:49: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ qualifier from pointer target type
    if(_rtw_memcmp(pnetwork->network.MacAddress, sme->bssid, ETH_ALEN) == _FALSE)
                                                 ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern int _rtw_memcmp(void *dst, void *src, u32 sz);
            ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2593:49: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ qualifier from pointer target type
     || _rtw_memcmp(pnetwork->network.Ssid.Ssid, sme->ssid, sme->ssid_len) == _FALSE
                                                 ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern int _rtw_memcmp(void *dst, void *src, u32 sz);
            ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2601:14: warning: assignment discards ‘const’ qualifier from pointer target type
    src_bssid = sme->bssid;
              ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2682:42: warning: passing argument 2 of ‘rtw_cfg80211_set_wpa_ie’ discards ‘const’ qualifier from pointer target type
  ret = rtw_cfg80211_set_wpa_ie(padapter, sme->ie, sme->ie_len);
                                          ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2243:12: note: expected ‘u8 *’ but argument is of type ‘const u8 *’
 static int rtw_cfg80211_set_wpa_ie(_adapter *padapter, u8 *pie, size_t ielen)
            ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘cfg80211_rtw_set_pmksa’:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2913:20: warning: passing argument 1 of ‘_rtw_memcmp’ discards ‘const’ qualifier from pointer target type
  if ( _rtw_memcmp( pmksa->bssid, strZeroMacAddress, ETH_ALEN ) == _TRUE )
                    ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern int _rtw_memcmp(void *dst, void *src, u32 sz);
            ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2923:59: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ qualifier from pointer target type
   if( _rtw_memcmp( psecuritypriv->PMKIDList[index].Bssid, pmksa->bssid, ETH_ALEN) ==_TRUE )
                                                           ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern int _rtw_memcmp(void *dst, void *src, u32 sz);
            ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2927:56: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ qualifier from pointer target type
    _rtw_memcpy( psecuritypriv->PMKIDList[index].PMKID, pmksa->pmkid, WLAN_PMKID_LEN);
                                                        ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz);
             ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2941:74: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ qualifier from pointer target type
   _rtw_memcpy(psecuritypriv->PMKIDList[psecuritypriv->PMKIDIndex].Bssid, pmksa->bssid, ETH_ALEN);
                                                                          ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz);
             ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2942:74: warning: passing argument 2 of ‘_rtw_memcpy’ discards ‘const’ qualifier from pointer target type
   _rtw_memcpy(psecuritypriv->PMKIDList[psecuritypriv->PMKIDIndex].PMKID, pmksa->pmkid, WLAN_PMKID_LEN);
                                                                          ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:167:13: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void _rtw_memcpy(void* dec, void* sour, u32 sz);
             ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘cfg80211_rtw_del_pmksa’:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2967:59: warning: passing argument 2 of ‘_rtw_memcmp’ discards ‘const’ qualifier from pointer target type
   if( _rtw_memcmp( psecuritypriv->PMKIDList[index].Bssid, pmksa->bssid, ETH_ALEN) ==_TRUE )
                                                           ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:168:12: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern int _rtw_memcmp(void *dst, void *src, u32 sz);
            ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:141:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_rx_action_p2p’:
/home/nathan/rtl8812AU_8821AU_linux/include/ioctl_cfg80211.h:114:71: error: too many arguments to function ‘cfg80211_rx_mgmt’
   #define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp)
                                                                       ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:3883:2: note: in expansion of macro ‘rtw_cfg80211_rx_mgmt’
  rtw_cfg80211_rx_mgmt(padapter, freq, 0, pmgmt_frame, frame_len, GFP_ATOMIC);
  ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/osdep_service_linux.h:76:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:41,
                 from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
include/net/cfg80211.h:4612:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:141:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_rx_p2p_action_public’:
/home/nathan/rtl8812AU_8821AU_linux/include/ioctl_cfg80211.h:114:71: error: too many arguments to function ‘cfg80211_rx_mgmt’
   #define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp)
                                                                       ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:3921:2: note: in expansion of macro ‘rtw_cfg80211_rx_mgmt’
  rtw_cfg80211_rx_mgmt(padapter, freq, 0, pmgmt_frame, frame_len, GFP_ATOMIC);
  ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/osdep_service_linux.h:76:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:41,
                 from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
include/net/cfg80211.h:4612:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:141:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_rx_action’:
/home/nathan/rtl8812AU_8821AU_linux/include/ioctl_cfg80211.h:114:71: error: too many arguments to function ‘cfg80211_rx_mgmt’
   #define rtw_cfg80211_rx_mgmt(adapter, freq, sig_dbm, buf, len, gfp) cfg80211_rx_mgmt((adapter)->rtw_wdev, freq, sig_dbm, buf, len, 0, gfp)
                                                                       ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:3951:2: note: in expansion of macro ‘rtw_cfg80211_rx_mgmt’
  rtw_cfg80211_rx_mgmt(adapter, freq, 0, frame, frame_len, GFP_ATOMIC);
  ^
In file included from /home/nathan/rtl8812AU_8821AU_linux/include/osdep_service_linux.h:76:0,
                 from /home/nathan/rtl8812AU_8821AU_linux/include/osdep_service.h:41,
                 from /home/nathan/rtl8812AU_8821AU_linux/include/drv_types.h:32,
                 from /home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:22:
include/net/cfg80211.h:4612:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: At top level:
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5041:2: warning: initialization from incompatible pointer type
  .get_station = cfg80211_rtw_get_station,
  ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5041:2: warning: (near initialization for ‘rtw_cfg80211_ops.get_station’)
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5069:2: warning: initialization from incompatible pointer type
  .add_station = cfg80211_rtw_add_station,
  ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5069:2: warning: (near initialization for ‘rtw_cfg80211_ops.add_station’)
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5070:2: warning: initialization from incompatible pointer type
  .del_station = cfg80211_rtw_del_station,
  ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5070:2: warning: (near initialization for ‘rtw_cfg80211_ops.del_station’)
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5071:2: warning: initialization from incompatible pointer type
  .change_station = cfg80211_rtw_change_station,
  ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5071:2: warning: (near initialization for ‘rtw_cfg80211_ops.change_station’)
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5087:2: warning: initialization from incompatible pointer type
  .mgmt_tx = cfg80211_rtw_mgmt_tx,
  ^
/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5087:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’)
scripts/Makefile.build:257: recipe for target '/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o' failed
make[2]: *** [/home/nathan/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o] Error 1
Makefile:1394: recipe for target '_module_/home/nathan/rtl8812AU_8821AU_linux' failed
make[1]: *** [_module_/home/nathan/rtl8812AU_8821AU_linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-21-generic'
Makefile:1040: recipe for target 'modules' failed
make: *** [modules] Error 2

---

### Post by weatherman2 on 2015-07-05
Actually, you seem to have a different error with this version of the driver: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217; .

You might try googling that exact error message to see what suggestions you might come up with.  Maybe you have to install another package or something.

These days, I don't bother with USB wireless cards for desktop computers.  Instead I use refurbished wireless routers configured as wireless ethernet bridges.  That does mean one extra device plugged in, but you at least never have to mess with wireless drivers again (wired ethernet cards don't always work out of the box either, but their average success seems to be a lot higher than for those USB wireless cards).  And you can also use the wireless ethernet bridge (router that is always on) to Wake-On Lan the computer, something you can't do with a regular wireless card.  Of course, I don't know if you are using a desktop or a laptop.  If you have a laptop and it is not HP or Lenovo, I'd recommend upgrading the internal wireless card if you can.

---

### Post by Yellow Pasque on 2015-07-06
Use this repo, as it is updated over the link weatherman2 gave: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
It should fix your compile error: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/52](https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/52)

---

### Post by Geoffrey_Arndt on 2015-07-06
Nathan80,    . . it's good to build any app/driver just for the learning experience if nothing else (that is, if you have the free time).   However, the Panda wireless dongle is one I've actually run, and know other Ubuntu users who have done the same.   Right now, it's been running and up for over 36 months on 1 desktop & 1 notebook, and D/L speeds average at 34 mbs, and top out at 39-40.   "Virtually" (2/3) no drops in that time (due to the device).   BTW, it also uses the realtek chipset.

---

### Post by nathan80 on 2015-07-08
Temujin, It worked!. Thank you, you are awesome.

---

