---
title: "wireless problem Dell E6410 and Ultimate-N 6300"
date: 2011-02-24
forum: Hardware
---

### Post by otnateos on 2011-02-24
Hi all,

Ubuntu 10.10 cannot use my Dell E6410 wireless. 

I read some posts, normally they had problem with N connection, but I can't can't use the wireless device at all.
```

**$ uname -sr**
Linux 2.6.35-25-generic-pae
**$ lspci | grep 6300**
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
**$ sudo ifconfig wlan0 up**
SIOCSIFFLAGS: Connection timed out

```

output from **dmesg** related to **iwlagn**
```

[   25.131439] iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.
[   25.170835] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   25.170929] iwlagn 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
[   25.171014] iwlagn 0000:03:00.0: Not valid error log pointer 0x00000000 for RT uCode
[   25.171088] iwlagn 0000:03:00.0: CSR values:
[   25.171146] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   25.171223] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   25.171288] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   25.171353] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[   25.171417] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   25.171481] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   25.171546] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[   25.171611] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[   25.171676] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   25.171742] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[   25.171806] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[   25.171872] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000004
[   25.171936] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00020000
[   25.172003] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[   25.172072] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   25.172140] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   25.172205] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   25.172269] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   25.172335] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   25.172399] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   25.172464] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   25.172530] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   25.172595] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   25.172660] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   25.172722] iwlagn 0000:03:00.0: FH register values:
[   25.172795] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X030c3c00
[   25.172884] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00316920
[   25.172971] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   25.173060] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   25.173148] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   25.173236] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   25.173327] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   25.173415] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   25.173503] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   25.173580] iwlagn 0000:03:00.0: Invalid event log pointer 0x00000000 for RT uCode
[   25.173658] iwlagn 0000:03:00.0: uCode did not respond OK.
[   29.133627] iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.


```

Anybody has the same problem or know how to fix it? Thanks beforehand for any replies

---

