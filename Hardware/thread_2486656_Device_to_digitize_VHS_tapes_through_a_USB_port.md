---
title: "Device to digitize VHS tapes through a USB port"
date: 2023-05-07
forum: Hardware
---

### Post by cscj01 on 2023-05-07
I came across a piece of hardware called EZCAP that will not work under Ubuntu 22.04 from a VCR to USB input for converting VHS tapes.  I get the following when checking usb devices```
lsusb
Bus 002 Device 006: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)
Bus 002 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. 4-Port USB 3.1 Hub
Bus 002 Device 007: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 012: ID 04b0:4001 Nikon Corp. LS 50 ED/Coolscan V ED
Bus 001 Device 036: ID 0baf:0303 U.S. Robotics USR5637 56K Faxmodem
Bus 001 Device 008: ID 04b8:1194 Seiko Epson Corp. ET-8550 Series
Bus 001 Device 006: ID 0bda:5411 Realtek Semiconductor Corp. 4-Port USB 2.1 Hub
Bus 001 Device 037: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 001 Device 003: ID 04b8:013a Seiko Epson Corp. GT-X820 [Perfection V600 Photo]
Bus 001 Device 038: ID 534d:0021 MACROSIL AV TO USB2.0
Bus 001 Device 015: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 011: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 009: ID 048d:5702 Integrated Technology Express, Inc. ITE Device
Bus 001 Device 007: ID 046a:0011 Cherry GmbH G83 (RS 6000) Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```The item I have is identified as > MACROSIL AV TO USB2.0Could anyone suggest a device that works under Linux?  I checked under V4L, but the listings there only identify the devices by chip sets.  These devices do not list the chip sets they use, so maybe someone on the board has some advice there.  It seems that chip set STL1160 works under Linux.

---

### Post by cscj01 on 2023-05-07
By the way, the audio portion of this device is ```
cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x53710000 irq 137
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0x53080000 irq 17
 2 [MS210x         ]: USB-Audio - MS210x
                      MacroSilicon MS210x at usb-0000:00:14.0-2.3, high speed
 3 [C920           ]: USB-Audio - HD Pro Webcam C920
                      HD Pro Webcam C920 at usb-0000:00:14.0-4, high speed
```item 2 in the above.

---

