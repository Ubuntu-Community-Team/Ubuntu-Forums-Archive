---
title: "Touch pad on Lenovo Thinkpad stop working sometime after booting"
date: 2020-07-03
forum: Hardware
---

### Post by amarbharti on 2020-07-03
Hi,
Touchpad on my thinkpad e14 stops working after boot. It happens frequently but not always. External mouse works fine even when touchpad is not working.
I've found these in logs:
20:44:37 kernel: elan_i2c 0-0015: invalid report id data (1)
20:44:29 kernel: i801_smbus 0000:00:1f.4: Transaction failed
20:44:29 kernel: elan_i2c 0-0015: failed to read report data: -110
20:44:29 kernel: i801_smbus 0000:00:1f.4: Failed terminating the transaction
20:44:29 kernel: i801_smbus 0000:00:1f.4: Failed terminating the transaction
20:44:29 kernel: i801_smbus 0000:00:1f.4: Transaction timeout
20:44:28 kernel: iwlwifi 0000:00:14.3: 0x0000025B | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
20:41:38 wpa_supplicant: nl80211: Failed to create a P2P Device interface p2p-dev-wlp0s20f3
20:27:51 kernel: ACPI Error: Aborting method \_SB.WMTF.WMTF due to previous error (AE_AML_PACKAGE_LIMIT) (20190816/psparse-529)
20:27:46 gdm-session-wor: gkr-pam: unable to locate daemon control file
20:27:44 kernel: Bluetooth: hci0: Failed to send firmware data (-110)
20:27:34 kernel: usb usb1-port10: disabled by hub (EMI?), re-enabling...


It works fine after reboot. Please help!!):P

---

