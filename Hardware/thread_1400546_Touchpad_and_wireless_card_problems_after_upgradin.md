---
title: "Touchpad and wireless card problems after upgrading on Lenovo S10-2"
date: 2010-02-07
forum: Hardware
---

### Post by Sapfeer on 2010-02-07
I have my touchpad and WiMax card don't working after upgrading to  2.6.31-19. There are no messages about touchpad, but there are some for  wireless card. Here are messages on 2.6.31-19:
```
Feb  7 09:33:43  lenovo-S102 kernel: [ 3769.502797] i2400m_usb 1-6:1.0: failed to  suspend, will reset on resume
Feb  7 09:33:43 lenovo-S102 kernel: [  3773.524634] i2400m_usb 1-6:1.0: no reset_resume for driver i2400m_usb?
Feb   7 09:33:43 lenovo-S102 kernel: [ 3774.340196] i2400m_usb 1-6:1.0:  firmware: requesting i2400m-fw-usb-1.4.sbcf
Feb  7 09:33:43  lenovo-S102 kernel: [ 3834.340246] i2400m_usb 1-6:1.0: fw  i2400m-fw-usb-1.4.sbcf: cannot load file: -2
Feb  7 09:33:43  lenovo-S102 kernel: [ 3834.340261] i2400m_usb 1-6:1.0: firmware:  requesting i2400m-fw-usb-1.3.sbcf
Feb  7 09:33:43 lenovo-S102 kernel:  [ 3894.340248] i2400m_usb 1-6:1.0: fw i2400m-fw-usb-1.3.sbcf: cannot  load file: -2
Feb  7 09:33:43 lenovo-S102 kernel: [ 3894.340260]  i2400m_usb 1-6:1.0: Could not find a usable firmware image
Feb  7  09:33:43 lenovo-S102 kernel: [ 3894.340271] i2400m_usb 1-6:1.0: cannot  bootstrap device: -2
Feb  7 09:33:43 lenovo-S102 kernel: [  3894.364158] i2400m_usb 1-6:1.0: cannot setup device: -2
Feb  7  09:33:43 lenovo-S102 kernel: [ 3894.364197] i2400m_usb: probe of 1-6:1.0  failed with error -2
Feb  7 09:36:49 lenovo-S102 kernel: [  4079.962046] usbcore: deregistering interface driver i2400m_usb
Feb  7  09:57:32 lenovo-S102 kernel: [   16.018528] i2400m_usb: Unknown symbol  i2400m_tx_msg_sent
Feb  7 09:57:32 lenovo-S102 kernel: [   16.019535]  i2400m_usb: Unknown symbol i2400m_release
Feb  7 09:57:32  lenovo-S102 kernel: [   16.019862] i2400m_usb: Unknown symbol  i2400m_bm_cmd_prepare
Feb  7 09:57:32 lenovo-S102 kernel: [    16.022904] i2400m_usb: Unknown symbol i2400m_netdev_setup
Feb  7  09:57:32 lenovo-S102 kernel: [   16.023975] i2400m_usb: Unknown symbol  i2400m_setup
Feb  7 09:57:32 lenovo-S102 kernel: [   16.025449]  i2400m_usb: Unknown symbol i2400m_rx
Feb  7 09:57:32 lenovo-S102  kernel: [   16.025814] i2400m_usb: Unknown symbol i2400m_tx_msg_get
Feb   7 09:57:32 lenovo-S102 kernel: [   16.026948] i2400m_usb: Unknown  symbol wimax_dev_init
Feb  7 09:57:32 lenovo-S102 kernel: [    16.027488] i2400m_usb: Unknown symbol i2400m_dev_reset_handle
Feb  7  09:57:32 lenovo-S102 kernel: [   16.027900] i2400m_usb: Unknown symbol  i2400m_cmd_enter_powersave
Feb  7 10:08:00 lenovo-S102 kernel: [    15.951697] i2400m_usb: Unknown symbol i2400m_tx_msg_sent
Feb  7  10:08:00 lenovo-S102 kernel: [   15.952753] i2400m_usb: Unknown symbol  i2400m_release
Feb  7 10:08:00 lenovo-S102 kernel: [   15.953089]  i2400m_usb: Unknown symbol i2400m_bm_cmd_prepare
Feb  7 10:08:00  lenovo-S102 kernel: [   15.956150] i2400m_usb: Unknown symbol  i2400m_netdev_setup
Feb  7 10:08:00 lenovo-S102 kernel: [    15.957199] i2400m_usb: Unknown symbol i2400m_setup
Feb  7 10:08:00  lenovo-S102 kernel: [   15.958491] i2400m_usb: Unknown symbol i2400m_rx
Feb   7 10:08:00 lenovo-S102 kernel: [   15.958818] i2400m_usb: Unknown  symbol i2400m_tx_msg_get
Feb  7 10:08:00 lenovo-S102 kernel: [    15.959956] i2400m_usb: Unknown symbol wimax_dev_init
Feb  7 10:08:00  lenovo-S102 kernel: [   15.960543] i2400m_usb: Unknown symbol  i2400m_dev_reset_handle
Feb  7 10:08:00 lenovo-S102 kernel: [    15.960967] i2400m_usb: Unknown symbol i2400m_cmd_enter_powersave

```And  here are on my previous version (2.6.31-17):
```
Feb  7 10:09:35  lenovo-S102 kernel: [   16.392633] i2400m_usb 1-6:1.0:  firmware: requesting i2400m-fw-usb-1.4.sbcf
Feb  7 10:09:38 lenovo-S102 kernel: [   19.469070] i2400m_usb 1-6:1.0:  firmware interface version 9.2.0
Feb  7 10:09:38 lenovo-S102 kernel: [   19.481438] i2400m_usb 1-6:1.0:  WiMAX interface wmx0 (00:1d:e1:09:68:74) ready
Feb  7 10:09:38 lenovo-S102 kernel: [   19.481663] usbcore: registered  new interface driver i2400m_usb
Feb  7 10:09:38 lenovo-S102 kernel: [   19.486063] i2400m_usb 1-6:1.0:  'RF Control' (0x4602) command failed: -84 - invalid state (3)
Feb  7 10:09:38 lenovo-S102 NetworkManager: <info>  (wmx0): driver  'i2400m_usb' does not support carrier detection.
Feb  7 10:09:38 lenovo-S102 NetworkManager: <info>  (wmx0): new  Ethernet device (driver: 'i2400m_usb')
```

It seems that new kernel incompatible with current driver version...

---

