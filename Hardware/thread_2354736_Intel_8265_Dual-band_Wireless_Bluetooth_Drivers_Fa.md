---
title: "Intel 8265 Dual-band Wireless Bluetooth Drivers Failing to Load"
date: 2017-03-05
forum: Hardware
---

### Post by cmuell89 on 2017-03-05
Hello all,

I am not sure if this is the correct location for this post, however, I wanted to share a little Wifi/Bluetooth troubleshooting I've experienced. This is might be useful to the Dell/Canonical team devoted to churning out the Dell developer editions that support Ubuntu.

_System:_Dell Precision 5520
7820HQ
Nvidia Quadro 1200M
16gb Memory
512 NVME Samsung Class 40

Intel® Dual Band Wireless-AC 8265

[U]OS/Kernel
[/U] 4.8.0-34-generic #36~16.04.1-Ubuntu (Currently using linux-generic-hwe-16.04-edge)

[U]Issue
[/U]After dealing with hardware issues with my new computer (coil whine) Dell replaced my motherboard, fans, and A/C adaptor. Upon boot-up. I did not have working wifi or bluetooth and no online resource or forum post helped resolve the issue except kernel upgrades. I updated to the latest stable version of kernel 4.9 (I believe 4.9.7) and regained wifi support but not bluetooth. Since kernel version is not yet supported by Ubuntu, I resorted to the HWE kernel releases. I first tried the hwe-16.04 (4.8.39 image) to no avail. However switching to hwe-16.04-edge (4.8.34) restored the bluetooth functionality. 

rfkill list produced the following for all failure situations (all kernels etc,.):
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

dmesg | egrep -i 'blue|firm' gives the following with wifi and bluetooth BOTH working:

```
[    0.201550] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored[    1.278151] i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
[    1.278152] i915 0000:00:02.0: Failed to load DMC firmware [https://01.org/linuxgraphics/intel-linux-graphics-firmwares], disabling runtime power management.
[    1.287230] [drm] GuC firmware load skipped
[    1.850982] Bluetooth: Core ver 2.21
[    1.850988] Bluetooth: HCI device and connection manager initialized
[    1.850990] Bluetooth: HCI socket layer initialized
[    1.850991] Bluetooth: L2CAP socket layer initialized
[    1.850993] Bluetooth: SCO socket layer initialized
[    1.855369] Bluetooth: hci0: Firmware revision 0.1 build 60 week 18 2016
[    3.721583] Bluetooth: HCI UART driver ver 2.3
[    3.721584] Bluetooth: HCI UART protocol H4 registered
[    3.721584] Bluetooth: HCI UART protocol BCSP registered
[    3.721585] Bluetooth: HCI UART protocol LL registered
[    3.721585] Bluetooth: HCI UART protocol ATH3K registered
[    3.721586] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.721598] Bluetooth: HCI UART protocol Intel registered
[    3.721606] Bluetooth: HCI UART protocol BCM registered
[    3.721606] Bluetooth: HCI UART protocol QCA registered
[    3.721606] Bluetooth: HCI UART protocol AG6XX registered
[    3.804003] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    3.804255] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    3.804267] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-22.ucode failed with error -2
[    3.810525] iwlwifi 0000:02:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[    5.785450] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.785451] Bluetooth: BNEP filters: protocol multicast
[    5.785453] Bluetooth: BNEP socket layer initialized

```

During bluetooth failure on other kernels, I did receive the following additional error message:
```
Bluetooth: hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
```

Perhaps there is a specific error in loading this driver module for my device?

Curious if this is an upstream bug that was missed in the update from kernel 4.8.34 to 4.8.39 and beyond.

If anyone has additional information in regards to this issue or if this is helpful please let me know.

Cheers,
Carl

---

### Post by ajgreeny on 2017-03-05
I think with that new wifi chip you will need to install 16.10 where I believe the 8265 is supported.
I had wondered if the HWE update would do it as well but apparently not.

Try 16.10 live first to check if it will work.

---

### Post by cmuell89 on 2017-03-07
Driver seems to be failing with HWE-Edge now as well:

```

$ dmesg | egrep -i 'blue|firm'
[    0.202945] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.288775] i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
[    1.288776] i915 0000:00:02.0: Failed to load DMC firmware [https://01.org/linuxgraphics/intel-linux-graphics-firmwares], disabling runtime power management.
[    1.296220] [drm] GuC firmware load skipped
[    1.614898] Bluetooth: Core ver 2.21
[    1.614904] Bluetooth: HCI device and connection manager initialized
[    1.614906] Bluetooth: HCI socket layer initialized
[    1.614907] Bluetooth: L2CAP socket layer initialized
[    1.614909] Bluetooth: SCO socket layer initialized
[    1.906059] Bluetooth: hci0: Bootloader revision 0.0 build 26 week 38 2015
[    1.907063] Bluetooth: hci0: Device revision is 16
[    1.907063] Bluetooth: hci0: Secure boot is enabled
[    1.907063] Bluetooth: hci0: OTP lock is enabled
[    1.907064] Bluetooth: hci0: API lock is enabled
[    1.907064] Bluetooth: hci0: Debug lock is disabled
[    1.907064] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    1.907074] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
[    1.907075] Bluetooth: hci0: Failed to load Intel firmware file (-2)
[    3.520054] Bluetooth: HCI UART driver ver 2.3
[    3.520056] Bluetooth: HCI UART protocol H4 registered
[    3.520056] Bluetooth: HCI UART protocol BCSP registered
[    3.520057] Bluetooth: HCI UART protocol LL registered
[    3.520057] Bluetooth: HCI UART protocol ATH3K registered
[    3.520058] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.520086] Bluetooth: HCI UART protocol Intel registered
[    3.520099] Bluetooth: HCI UART protocol BCM registered
[    3.520099] Bluetooth: HCI UART protocol QCA registered
[    3.520100] Bluetooth: HCI UART protocol AG6XX registered
[    3.575352] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    3.575440] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    3.575448] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8265-22.ucode failed with error -2
[    3.579486] iwlwifi 0000:02:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[    4.221451] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.221452] Bluetooth: BNEP filters: protocol multicast
[    4.221454] Bluetooth: BNEP socket layer initialized
[    4.715941] Bluetooth: hci0: Bootloader revision 0.0 build 26 week 38 2015
[    4.716953] Bluetooth: hci0: Device revision is 16
[    4.716953] Bluetooth: hci0: Secure boot is enabled
[    4.716954] Bluetooth: hci0: OTP lock is enabled
[    4.716954] Bluetooth: hci0: API lock is enabled
[    4.716955] Bluetooth: hci0: Debug lock is disabled
[    4.716955] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    4.717074] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
[    4.717075] Bluetooth: hci0: Failed to load Intel firmware file (-2)

```

Besides the updated kernel, what would 16.10 bring to the table?

---

### Post by jeremy31 on 2017-03-07
Post results for ```
cat /lib/firmware/intel
```

---

### Post by cmuell89 on 2017-03-07
```

$ cat /lib/firmware/intel
cat: /lib/firmware/intel: Is a directory


$ ls /lib/firmware/intel
dsp_fw_bxtn.bin
dsp_fw_bxtn_v1118.bin
dsp_fw_bxtn_v430.bin
dsp_fw_bxtn_v702.bin
dsp_fw_kbl.bin
dsp_fw_kbl_v1037.bin
dsp_fw_kbl_v701.bin
dsp_fw_release.bin
dsp_fw_release_v827.bin
dsp_fw_release_v869.bin
dsp_fw_release_v896.bin
dsp_fw_release_v927.bin
dsp_fw_release_v948.bin
dsp_fw_release_v951.bin
dsp_fw_release_v958.bin
fw_sst_0f28.bin
fw_sst_0f28.bin-48kHz_i2s_master
fw_sst_22a8.bin
ibt-11-16.ddc
ibt-11-16.ddc.oem-bluetooth-firmware-intel-8265
ibt-11-16.sfi
ibt-11-16.sfi.oem-bluetooth-firmware-intel-8265
ibt-11-5.ddc
ibt-11-5.sfi
ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
ibt-hw-37.7.10-fw-1.0.2.3.d.bseq
ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
ibt-hw-37.7.bseq
ibt-hw-37.8.10-fw-1.10.2.27.d.bseq
ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
ibt-hw-37.8.10-fw-22.50.19.14.f.bseq
ibt-hw-37.8.bseq
IntcSST2.bin

```

Also here is what is in /lib/firmware:

```

$ ls /lib/firmware/
3com                         iwlwifi-8000C-13.ucode
4.4.0-62-generic             iwlwifi-8000C-13.ucode.wifi-intel8260
4.4.0-65-generic             iwlwifi-8000C-14.ucode
4.8.0-34-generic             iwlwifi-8000C-15.ucode
acenic                       iwlwifi-8000C-16.ucode
adaptec                      iwlwifi-8000C-16.ucode.wifi-intel8260
advansys                     iwlwifi-8000C-21.ucode
agere_ap_fw.bin              iwlwifi-8265-21.ucode
agere_sta_fw.bin             iwlwifi-8265-27.ucode
amdgpu                       kaweth
ar3k                         keyspan
ar5523.bin                   keyspan_pda
as102_data1_st.hex           korg
as102_data2_st.hex           lbtf_usb.bin
asihpi                       lgs8g75.fw
ath10k                       libertas
ath3k-1.fw                   liquidio
ath6k                        Makefile
ath9k_htc                    matrox
atmel                        moxa
atmel_at76c504_2958.bin      mrvl
atmel_at76c504a_2958.bin     mt7601u.bin
atmsar11.fw                  mt7650.bin
atusb                        mts_cdma.fw
av7110                       mts_edge.fw
bnx2x                        mts_gsm.fw
brcm                         mts_mt9234mu.fw
carl9170-1.fw                mts_mt9234zba.fw
carl9170fw                   mwl8k
cbfw-3.2.1.1.bin             mwlwifi
cbfw-3.2.3.0.bin             myri10ge_eth_big_z8e.dat
cbfw-3.2.5.1.bin             myri10ge_ethp_big_z8e.dat
cis                          myri10ge_ethp_z8e.dat
configure                    myri10ge_eth_z8e.dat
cpia2                        myri10ge_rss_eth_big_z8e.dat
ct2fw-3.2.1.1.bin            myri10ge_rss_ethp_big_z8e.dat
ct2fw-3.2.3.0.bin            myri10ge_rss_ethp_z8e.dat
ct2fw-3.2.5.1.bin            myri10ge_rss_eth_z8e.dat
ctefx.bin                    NPE-B
ctfw-3.2.1.1.bin             NPE-C
ctfw-3.2.3.0.bin             nvidia
ctfw-3.2.5.1.bin             ositech
ctspeq.bin                   phanfw.bin
cxgb3                        qat_895xcc.bin
cxgb4                        qat_895xcc_mmp.bin
dsp56k                       qat_c3xxx.bin
dvb-fe-xc4000-1.4.1.fw       qat_c3xxx_mmp.bin
dvb-fe-xc5000-1.6.114.fw     qat_c62x.bin
dvb-fe-xc5000c-4.1.30.7.fw   qat_c62x_mmp.bin
dvb-usb-dib0700-1.20.fw      qat_mmp.bin
dvb-usb-it9135-01.fw         qca
dvb-usb-it9135-02.fw         qed
dvb-usb-terratec-h5-drxk.fw  ql2100_fw.bin
ea                           ql2200_fw.bin
edgeport                     ql2300_fw.bin
emi26                        ql2322_fw.bin
emi62                        ql2400_fw.bin
ene-ub6250                   ql2500_fw.bin
ess                          r128
f2255usb.bin                 r8a779x_usb3_v1.dlmem
go7007                       r8a779x_usb3_v2.dlmem
GPL-3                        radeon
hfi1_dc8051.fw               README
hfi1_fabric.fw               rp2.fw
hfi1_pcie.fw                 rsi_91x.fw
hfi1_sbus.fw                 rt2561.bin
hp                           rt2561s.bin
htc_7010.fw                  rt2661.bin
htc_9271.fw                  rt2860.bin
i2400m-fw-usb-1.4.sbcf       rt2870.bin
i2400m-fw-usb-1.5.sbcf       rt3070.bin
i6050-fw-usb-1.5.sbcf        rt3090.bin
i915                         rt3290.bin
intel                        rt73.bin
intel-ucode                  RTL8192E
ipw2100-1.3.fw               rtl_bt
ipw2100-1.3-i.fw             rtl_nic
ipw2100-1.3-p.fw             rtlwifi
ipw2200-bss.fw               s2250.fw
ipw2200-ibss.fw              s2250_loader.fw
ipw2200-sniffer.fw           s5p-mfc.fw
isci                         s5p-mfc-v6.fw
iwlwifi-1000-5.ucode         s5p-mfc-v6-v2.fw
iwlwifi-100-5.ucode          s5p-mfc-v7.fw
iwlwifi-105-6.ucode          s5p-mfc-v8.fw
iwlwifi-135-6.ucode          sb16
iwlwifi-2000-6.ucode         scripts
iwlwifi-2030-6.ucode         sdd_sagrad_1091_1098.bin
iwlwifi-3160-10.ucode        slicoss
iwlwifi-3160-12.ucode        sun
iwlwifi-3160-13.ucode        tehuti
iwlwifi-3160-16.ucode        ti_3410.fw
iwlwifi-3160-17.ucode        ti_5052.fw
iwlwifi-3160-7.ucode         ti-connectivity
iwlwifi-3160-8.ucode         tigon
iwlwifi-3160-9.ucode         ti-keystone
iwlwifi-3168-21.ucode        tlg2300_firmware.bin
iwlwifi-3168-22.ucode        ttusb-budget
iwlwifi-3945-2.ucode         ueagle-atm
iwlwifi-4965-2.ucode         usbdux
iwlwifi-5000-5.ucode         usbduxfast_firmware.bin
iwlwifi-5150-2.ucode         usbdux_firmware.bin
iwlwifi-6000-4.ucode         usbduxsigma_firmware.bin
iwlwifi-6000g2a-5.ucode      v4l-cx231xx-avcore-01.fw
iwlwifi-6000g2a-6.ucode      v4l-cx23418-apu.fw
iwlwifi-6000g2b-6.ucode      v4l-cx23418-cpu.fw
iwlwifi-6050-5.ucode         v4l-cx23418-dig.fw
iwlwifi-7260-10.ucode        v4l-cx2341x-dec.fw
iwlwifi-7260-12.ucode        v4l-cx2341x-enc.fw
iwlwifi-7260-13.ucode        v4l-cx2341x-init.mpg
iwlwifi-7260-16.ucode        v4l-cx23885-avcore-01.fw
iwlwifi-7260-17.ucode        v4l-cx25840.fw
iwlwifi-7260-7.ucode         v4l-pvrusb2-24xxx-01.fw
iwlwifi-7260-8.ucode         v4l-pvrusb2-29xxx-01.fw
iwlwifi-7260-9.ucode         vicam
iwlwifi-7265-10.ucode        vntwusb.fw
iwlwifi-7265-12.ucode        vpu_d.bin
iwlwifi-7265-13.ucode        vpu_p.bin
iwlwifi-7265-16.ucode        vxge
iwlwifi-7265-17.ucode        WHENCE.ubuntu
iwlwifi-7265-8.ucode         whiteheat.fw
iwlwifi-7265-9.ucode         whiteheat_loader.fw
iwlwifi-7265D-10.ucode       wsm_22.bin
iwlwifi-7265D-12.ucode       yam
iwlwifi-7265D-13.ucode       yamaha
iwlwifi-7265D-16.ucode       zd1201-ap.fw
iwlwifi-7265D-17.ucode       zd1201.fw
iwlwifi-7265D-21.ucode       zd1211
iwlwifi-7265D-22.ucode

```

---

### Post by lambda30 on 2017-03-08
I think I'm getting this as well, but don't know if it's the same problem or not.

**Laptop:** Lenovo Y520
**Wifi:** Intel 8265
**Ubuntu** 16.10 (upgraded from 16.04)
**Kernel: **4.8.0-41-generic

Wi-Fi is not working (if I try to set the Network Manager switch to ON, it jumps to OFF), Wired is working. As far as I can see, iwlwifi-8265-23 and iwlwifi-8265-24 are missing from /lib/firmware. Is this why the Wi-Fi is not starting? The webpage over at [http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html) states that the last driver for Linux is iwlwifi-8265-22, which I already have apparently. Any ideas? I'm currently stuck...


**rfkill list**
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```


**dmesg | egrep -i 'blue|firm'**

```
[    0.177602] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.137514] [drm] GuC firmware load skipped
[    1.367249] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    1.714367] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x6d4f00)
[    3.205904] Bluetooth: Core ver 2.21
[    3.205912] Bluetooth: HCI device and connection manager initialized
[    3.205915] Bluetooth: HCI socket layer initialized
[    3.205916] Bluetooth: L2CAP socket layer initialized
[    3.205919] Bluetooth: SCO socket layer initialized
[    3.214448] Bluetooth: HCI UART driver ver 2.3
[    3.214449] Bluetooth: HCI UART protocol H4 registered
[    3.214450] Bluetooth: HCI UART protocol BCSP registered
[    3.214450] Bluetooth: HCI UART protocol LL registered
[    3.214451] Bluetooth: HCI UART protocol ATH3K registered
[    3.214451] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.214467] Bluetooth: HCI UART protocol Intel registered
[    3.214473] Bluetooth: HCI UART protocol BCM registered
[    3.214474] Bluetooth: HCI UART protocol QCA registered
[    3.214474] Bluetooth: HCI UART protocol AG6XX registered
[    3.259665] Bluetooth: hci0: Firmware revision 0.1 build 107 week 1 2017
[    3.274453] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    3.276343] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    3.293157] iwlwifi 0000:03:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    3.707832] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.707833] Bluetooth: BNEP filters: protocol multicast
[    3.707835] Bluetooth: BNEP socket layer initialized
[    6.357715] Bluetooth: RFCOMM TTY layer initialized
[    6.357723] Bluetooth: RFCOMM socket layer initialized
[    6.357727] Bluetooth: RFCOMM ver 1.11
```


**ls /lib/firmware/**
```
3.19.0-31-generic            iwlwifi-7265D-22.ucode
3com                         iwlwifi-8000C-13.ucode
4.4.0-66-generic             iwlwifi-8000C-16.ucode
4.8.0-41-generic             iwlwifi-8000C-21.ucode
acenic                       iwlwifi-8265-21.ucode
adaptec                      iwlwifi-8265-22.ucode
advansys                     kaweth
agere_ap_fw.bin              keyspan
agere_sta_fw.bin             keyspan_pda
amdgpu                       korg
ar3k                         lbtf_usb.bin
ar5523.bin                   lgs8g75.fw
as102_data1_st.hex           libertas
as102_data2_st.hex           liquidio
asihpi                       Makefile
ath10k                       matrox
ath3k-1.fw                   moxa
ath6k                        mrvl
ath9k_htc                    mt7601u.bin
atmel                        mt7650.bin
atmel_at76c504_2958.bin      mts_cdma.fw
atmel_at76c504a_2958.bin     mts_edge.fw
atmsar11.fw                  mts_gsm.fw
atusb                        mts_mt9234mu.fw
av7110                       mts_mt9234zba.fw
bnx2x                        mwl8k
brcm                         mwlwifi
carl9170-1.fw                myri10ge_eth_big_z8e.dat
carl9170fw                   myri10ge_ethp_big_z8e.dat
cbfw-3.2.1.1.bin             myri10ge_ethp_z8e.dat
cbfw-3.2.3.0.bin             myri10ge_eth_z8e.dat
cbfw-3.2.5.1.bin             myri10ge_rss_eth_big_z8e.dat
cis                          myri10ge_rss_ethp_big_z8e.dat
configure                    myri10ge_rss_ethp_z8e.dat
cpia2                        myri10ge_rss_eth_z8e.dat
ct2fw-3.2.1.1.bin            NPE-B
ct2fw-3.2.3.0.bin            NPE-C
ct2fw-3.2.5.1.bin            nvidia
ctefx.bin                    ositech
ctfw-3.2.1.1.bin             phanfw.bin
ctfw-3.2.3.0.bin             qat_895xcc.bin
ctfw-3.2.5.1.bin             qat_895xcc_mmp.bin
ctspeq.bin                   qat_c3xxx.bin
cxgb3                        qat_c3xxx_mmp.bin
cxgb4                        qat_c62x.bin
dsp56k                       qat_c62x_mmp.bin
dvb-fe-xc4000-1.4.1.fw       qat_mmp.bin
dvb-fe-xc5000-1.6.114.fw     qca
dvb-fe-xc5000c-4.1.30.7.fw   qed
dvb-usb-dib0700-1.20.fw      ql2100_fw.bin
dvb-usb-it9135-01.fw         ql2200_fw.bin
dvb-usb-it9135-02.fw         ql2300_fw.bin
dvb-usb-terratec-h5-drxk.fw  ql2322_fw.bin
ea                           ql2400_fw.bin
edgeport                     ql2500_fw.bin
emi26                        r128
emi62                        r8a779x_usb3_v1.dlmem
ene-ub6250                   r8a779x_usb3_v2.dlmem
ess                          r8a779x_usb3_v3.dlmem
f2255usb.bin                 radeon
go7007                       README
GPL-3                        rockchip
hfi1_dc8051.fw               rp2.fw
hfi1_fabric.fw               rsi_91x.fw
hfi1_pcie.fw                 rt2561.bin
hfi1_sbus.fw                 rt2561s.bin
hp                           rt2661.bin
htc_7010.fw                  rt2860.bin
htc_9271.fw                  rt2870.bin
i2400m-fw-usb-1.4.sbcf       rt3070.bin
i2400m-fw-usb-1.5.sbcf       rt3090.bin
i6050-fw-usb-1.5.sbcf        rt3290.bin
i915                         rt73.bin
intel                        RTL8192E
intel-ucode                  rtl_bt
ipw2100-1.3.fw               rtl_nic
ipw2100-1.3-i.fw             rtlwifi
ipw2100-1.3-p.fw             s2250.fw
ipw2200-bss.fw               s2250_loader.fw
ipw2200-ibss.fw              s5p-mfc.fw
ipw2200-sniffer.fw           s5p-mfc-v6.fw
isci                         s5p-mfc-v6-v2.fw
iwlwifi-1000-5.ucode         s5p-mfc-v7.fw
iwlwifi-100-5.ucode          s5p-mfc-v8.fw
iwlwifi-105-6.ucode          sb16
iwlwifi-135-6.ucode          scripts
iwlwifi-2000-6.ucode         sdd_sagrad_1091_1098.bin
iwlwifi-2030-6.ucode         slicoss
iwlwifi-3160-10.ucode        sun
iwlwifi-3160-12.ucode        tehuti
iwlwifi-3160-13.ucode        ti_3410.fw
iwlwifi-3160-16.ucode        ti_5052.fw
iwlwifi-3160-17.ucode        ti-connectivity
iwlwifi-3160-7.ucode         tigon
iwlwifi-3160-8.ucode         ti-keystone
iwlwifi-3160-9.ucode         tlg2300_firmware.bin
iwlwifi-3168-21.ucode        ttusb-budget
iwlwifi-3168-22.ucode        ueagle-atm
iwlwifi-3945-2.ucode         usbdux
iwlwifi-4965-2.ucode         usbduxfast_firmware.bin
iwlwifi-5000-5.ucode         usbdux_firmware.bin
iwlwifi-5150-2.ucode         usbduxsigma_firmware.bin
iwlwifi-6000-4.ucode         v4l-cx231xx-avcore-01.fw
iwlwifi-6000g2a-5.ucode      v4l-cx23418-apu.fw
iwlwifi-6000g2a-6.ucode      v4l-cx23418-cpu.fw
iwlwifi-6000g2b-6.ucode      v4l-cx23418-dig.fw
iwlwifi-6050-5.ucode         v4l-cx2341x-dec.fw
iwlwifi-7260-10.ucode        v4l-cx2341x-enc.fw
iwlwifi-7260-12.ucode        v4l-cx2341x-init.mpg
iwlwifi-7260-13.ucode        v4l-cx23885-avcore-01.fw
iwlwifi-7260-16.ucode        v4l-cx25840.fw
iwlwifi-7260-17.ucode        v4l-pvrusb2-24xxx-01.fw
iwlwifi-7260-7.ucode         v4l-pvrusb2-29xxx-01.fw
iwlwifi-7260-8.ucode         vicam
iwlwifi-7260-9.ucode         vntwusb.fw
iwlwifi-7265-10.ucode        vpu_d.bin
iwlwifi-7265-12.ucode        vpu_p.bin
iwlwifi-7265-13.ucode        vxge
iwlwifi-7265-16.ucode        WHENCE.ubuntu
iwlwifi-7265-17.ucode        whiteheat.fw
iwlwifi-7265-8.ucode         whiteheat_loader.fw
iwlwifi-7265-9.ucode         wsm_22.bin
iwlwifi-7265D-10.ucode       yam
iwlwifi-7265D-12.ucode       yamaha
iwlwifi-7265D-13.ucode       zd1201-ap.fw
iwlwifi-7265D-16.ucode       zd1201.fw
iwlwifi-7265D-17.ucode       zd1211
iwlwifi-7265D-21.ucode
```

---

### Post by CrazyDesi on 2017-03-10
I am also having problems with the new x1 Carbon 5th gen, which has 8265.  The wifi works some of the times, but the bluetooth does not.  I have 16.04.2 so the hwe is enabled.  Is there a workaround?  I really do not want a non LTS version for my main workstation.

---

### Post by CrazyDesi on 2017-03-10
Got it working.  Run the following and reboot:

```

 sudo apt-get install linux-generic-hwe-16.04-edge xserver-xorg-input-libinput-hwe-16.04 && wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161.1_all.deb && sudo dpkg -i linux-firmware_1.161.1_all.deb 

```

Also, when  linux firmware is updated to a version greater than 1.161.1 in the official repositories will apt overwrite the older dpkg file or will I need to do it manually?

---

### Post by lambda30 on 2017-03-11
Manged to fix this issue. Apparently there was a module called ideapad-laptop which was setting the hardware block on the Wi-Fi and bluetooth connections. So has nothing to do with drivers and/or kernels.

> **lambda30 said:**
> I think I'm getting this as well, but don't know if it's the same problem or not.

**Laptop:** Lenovo Y520
**Wifi:** Intel 8265
**Ubuntu** 16.10 (upgraded from 16.04)
**Kernel: **4.8.0-41-generic

Wi-Fi is not working (if I try to set the Network Manager switch to ON, it jumps to OFF), Wired is working. As far as I can see, iwlwifi-8265-23 and iwlwifi-8265-24 are missing from /lib/firmware. Is this why the Wi-Fi is not starting? The webpage over at [http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html) states that the last driver for Linux is iwlwifi-8265-22, which I already have apparently. Any ideas? I'm currently stuck...


---

### Post by jeremy31 on 2017-03-13
Actually it is a kernel issue as ideapad-laptop is part of the kernel.  You should file a bug report against package linux so this can be fixed.

[This](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/ideapad-laptop.c?id=e297046875f2c5a43684f54f0fd098249b4f293a) is an example of how they fixed the Y700 in the kernel source code

cmuell89
In terminal do ```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161.1_all.deb
```
```
sudo dpkg -i linux-firmware_1.161.1_all.deb
```

Reboot

---

### Post by cmuell89 on 2017-03-13
Unfortunately I ran a clean installtion using Dell's provided backup image. I have reverted back to kernel 4.4.0-66 and thus far wireless and bluetooth working consistently. I hate to have changed my kernel etc as this doesn't exactly help with the issue but I need my computer for function properly to do work :/

Is there anything information I can provide about this kernel that would help illuminate what might need to be patched as clearly something happened earlier on this same kernel that caused the issue in the first place.

---

### Post by timmiroon on 2017-05-14
> **CrazyDesi said:**
> Got it working.  Run the following and reboot:

```

 sudo apt-get install linux-generic-hwe-16.04-edge xserver-xorg-input-libinput-hwe-16.04 && wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161.1_all.deb && sudo dpkg -i linux-firmware_1.161.1_all.deb 

```

Also, when  linux firmware is updated to a version greater than 1.161.1 in the official repositories will apt overwrite the older dpkg file or will I need to do it manually?


This also worked for me. 

Scenario: [HP Spectre 13-w030nd x360]("https://www.laptopshop.nl/product/741530/?utm_source=vanessa&utm_medium=mail&utm_campaign=notspecified&") with fresh, updated 16.04. Wireless working fine but Bluey not. Fishing around in dmesg turned up the same errors as noted above about iwlwifi-8265-23 and 24.ucode not being found which was not surprising as they were not and still are not present on the filesystem. 

I also found:

**Wi-Fi / Bluetooth coexistence**

    Having Wi-Fi and Bluetooth running at the same time is a challenge.  These scenarios have been tested thoroughly on 7260 and up, less so on  earlier devices. This is why some people may face issues with devices  that are handled by iwldvm. For users of these devices who have problems  when Wi-Fi and Bluetooth are running concurrently, we suggest to  disable BT Coex by loading iwlwifi with bt_coex_active=0 as a module  parameter. 

at: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#wi-fibluetooth_coexistence](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#wi-fibluetooth_coexistence) so it's a known issue. 

I've followed this advice and not experianced any negative side effects yet ...

---

### Post by reinaldo-bocchi on 2017-05-23
Thanks man, this solved my problem! (Bluetooth was not active)

---

