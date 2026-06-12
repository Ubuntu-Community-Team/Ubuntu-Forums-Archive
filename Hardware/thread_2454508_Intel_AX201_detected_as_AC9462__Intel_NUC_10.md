---
title: "Intel AX201 detected as AC9462 / Intel NUC 10"
date: 2020-11-30
forum: Hardware
---

### Post by darkdelirium on 2020-11-30
Hi


Platform:  NUC10i5FNH 

OS: Linux 5.8.0-29-generic #31~20.04.1-Ubuntu SMP Fri Nov 6 16:10:42 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Dmesg Log:
```
[    3.559159] iwlwifi 0000:03:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    3.559161] iwlwifi 0000:03:00.0: Found debug destination: EXTERNAL_DRAM
[    3.559162] iwlwifi 0000:03:00.0: Found debug configuration: 0
[    3.559393] iwlwifi 0000:03:00.0: loaded firmware version 48.4fa0041f.0 QuZ-a0-hr-b0-56.ucode op_mode iwlmvm
[    3.559411] iwlwifi 0000:03:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[    3.581554] iwlwifi 0000:03:00.0: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x354
[    3.595472] iwlwifi 0000:03:00.0: Applying debug destination EXTERNAL_DRAM
[    3.596585] iwlwifi 0000:03:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    4.614806] iwlwifi 0000:03:00.0: SecBoot CPU1 Status: 0x5f41, CPU2 Status: 0x3
[    4.615506] iwlwifi 0000:03:00.0: UMAC PC: 0x8048d43c
[    4.616189] iwlwifi 0000:03:00.0: LMAC PC: 0x0
[    4.616858] iwlwifi 0000:03:00.0: Collecting data: trigger 15 fired.
[    4.863731] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[    4.864017] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 945430701
[    4.864290] iwlwifi 0000:03:00.0: Loaded firmware version: 48.4fa0041f.0 QuZ-a0-hr-b0-56.ucode
[    4.864569] iwlwifi 0000:03:00.0: 0xE2D0DB2A | ADVANCED_SYSASSERT          
[    4.864852] iwlwifi 0000:03:00.0: 0xBB5AFEC6 | trm_hw_status0
[    4.865125] iwlwifi 0000:03:00.0: 0xBDB3F9DB | trm_hw_status1
[    4.865393] iwlwifi 0000:03:00.0: 0xF46AA281 | branchlink2
[    4.865656] iwlwifi 0000:03:00.0: 0xEA9EAA4C | interruptlink1
[    4.865917] iwlwifi 0000:03:00.0: 0xDECA8E99 | interruptlink2
[    4.866177] iwlwifi 0000:03:00.0: 0x5D4ADEC9 | data1
[    4.866430] iwlwifi 0000:03:00.0: 0x928C1614 | data2
[    4.866690] iwlwifi 0000:03:00.0: 0xAEE08620 | data3
[    4.866944] iwlwifi 0000:03:00.0: 0x8FE9321F | beacon time
[    4.867187] iwlwifi 0000:03:00.0: 0x6C2B7F44 | tsf low
[    4.867427] iwlwifi 0000:03:00.0: 0xA95A150D | tsf hi
[    4.867662] iwlwifi 0000:03:00.0: 0xA5A1E23B | time gp1
[    4.867890] iwlwifi 0000:03:00.0: 0x26BE9209 | time gp2
[    4.868111] iwlwifi 0000:03:00.0: 0xAFEBA88A | uCode revision type
[    4.868330] iwlwifi 0000:03:00.0: 0xF7D4BE4E | uCode version major
[    4.868544] iwlwifi 0000:03:00.0: 0x88C23F12 | uCode version minor
[    4.868760] iwlwifi 0000:03:00.0: 0x92177AAF | hw version
[    4.868973] iwlwifi 0000:03:00.0: 0x6BFBC85D | board version
[    4.869181] iwlwifi 0000:03:00.0: 0x3EFD9B30 | hcmd
[    4.869379] iwlwifi 0000:03:00.0: 0x3CEA8196 | isr0
[    4.869564] iwlwifi 0000:03:00.0: 0x230A7196 | isr1
[    4.869742] iwlwifi 0000:03:00.0: 0xF1059A86 | isr2
[    4.869915] iwlwifi 0000:03:00.0: 0x7674EFD9 | isr3
[    4.870084] iwlwifi 0000:03:00.0: 0x831852CC | isr4
[    4.870251] iwlwifi 0000:03:00.0: 0x56842D62 | last cmd Id
[    4.870415] iwlwifi 0000:03:00.0: 0xB3F5CDB4 | wait_event
[    4.870577] iwlwifi 0000:03:00.0: 0xBF46C33B | l2p_control
[    4.870749] iwlwifi 0000:03:00.0: 0xB89A0F19 | l2p_duration
[    4.870908] iwlwifi 0000:03:00.0: 0x4C9498A8 | l2p_mhvalid
[    4.871064] iwlwifi 0000:03:00.0: 0x1A7397FF | l2p_addr_match
[    4.871213] iwlwifi 0000:03:00.0: 0x9DBEA744 | lmpm_pmg_sel
[    4.871359] iwlwifi 0000:03:00.0: 0x7AEA0FEC | timestamp
[    4.871505] iwlwifi 0000:03:00.0: 0x8A134E18 | flow_handler
[    4.871687] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[    4.871832] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 7
[    4.871973] iwlwifi 0000:03:00.0: 0x201013F1 | ADVANCED_SYSASSERT
[    4.872110] iwlwifi 0000:03:00.0: 0x00000000 | umac branchlink1
[    4.872246] iwlwifi 0000:03:00.0: 0xC008D49C | umac branchlink2
[    4.872382] iwlwifi 0000:03:00.0: 0x00000000 | umac interruptlink1
[    4.872519] iwlwifi 0000:03:00.0: 0x00000000 | umac interruptlink2
[    4.872652] iwlwifi 0000:03:00.0: 0x00000003 | umac data1
[    4.872785] iwlwifi 0000:03:00.0: 0x20000302 | umac data2
[    4.872915] iwlwifi 0000:03:00.0: 0x01300504 | umac data3
[    4.873046] iwlwifi 0000:03:00.0: 0x00000030 | umac major
[    4.873177] iwlwifi 0000:03:00.0: 0x4FA0041F | umac minor
[    4.873306] iwlwifi 0000:03:00.0: 0x00005FCE | frame pointer
[    4.873436] iwlwifi 0000:03:00.0: 0xC0887F58 | stack pointer
[    4.873566] iwlwifi 0000:03:00.0: 0x00000000 | last host cmd
[    4.873696] iwlwifi 0000:03:00.0: 0x00000000 | isr status reg
[    4.873848] iwlwifi 0000:03:00.0: Fseq Registers:
[    4.873991] iwlwifi 0000:03:00.0: 0x00000003 | FSEQ_ERROR_CODE
[    4.874135] iwlwifi 0000:03:00.0: 0x80290033 | FSEQ_TOP_INIT_VERSION
[    4.874282] iwlwifi 0000:03:00.0: 0x80070043 | FSEQ_CNVIO_INIT_VERSION
[    4.874429] iwlwifi 0000:03:00.0: 0x0000A481 | FSEQ_OTP_VERSION
[    4.874575] iwlwifi 0000:03:00.0: 0x00000003 | FSEQ_TOP_CONTENT_VERSION
[    4.874729] iwlwifi 0000:03:00.0: 0x4552414E | FSEQ_ALIVE_TOKEN
[    4.874878] iwlwifi 0000:03:00.0: 0x20000302 | FSEQ_CNVI_ID
[    4.875028] iwlwifi 0000:03:00.0: 0x01300504 | FSEQ_CNVR_ID
[    4.875178] iwlwifi 0000:03:00.0: 0x20000302 | CNVI_AUX_MISC_CHIP
[    4.875333] iwlwifi 0000:03:00.0: 0x01300504 | CNVR_AUX_MISC_CHIP
[    4.875488] iwlwifi 0000:03:00.0: 0x05B0905B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    4.875648] iwlwifi 0000:03:00.0: 0x0000025B | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    4.875818] iwlwifi 0000:03:00.0: Failed to start RT ucode: -110
[    4.876009] iwlwifi 0000:03:00.0: Collecting data: trigger 16 fired.
[    5.722286] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -110
```lspci:

```
03:00.0 Network controller: Intel Corporation Wireless-AC 9462
``` 
I  tried to install Ubuntu Server 20.04 on Intel NUC 10, but I couldn't  make wireless card AX201 work properly under linux. I tried multiple  linux distros (ubuntu server/desktop, mint, arch) and have exact same  error message in dmesg log, the only difference was firmware version.  The card listed as AC9462 under lspci but it's not correct, hower when  iwlwifi tries to load firmware it's detected correctly as AX201. I also  tried different kernel versions, 5.2, 5.4, 5.6 but got same errors in  dmesg. I think the problem is that card detected incorrectly.


Does  anyone know solution? Is this iwlwifi driver/linux kernel problem? Do we  have any chance that it can be fixed in future?

---

