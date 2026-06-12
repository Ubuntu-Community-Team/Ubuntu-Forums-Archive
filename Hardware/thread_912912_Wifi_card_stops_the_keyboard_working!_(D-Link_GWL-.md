---
title: "Wifi card stops the keyboard working! (D-Link GWL-G650+)"
date: 2008-09-07
forum: Hardware
---

### Post by mcld on 2008-09-07
Hi - I have Xubuntu 8.04 on a Dell Latitude laptop. I also have a D-Link wifi card (GWL-G650+), which I have managed to get working a couple of times. But now plugging in the wifi card reliably prevents my keyboard from working! If I boot without the card, all is fine (but no network access). If I boot with the card, then the keyboard works on the login screen (and for selecting boot options in grub, etc), but as soon as the desktop appears, it seems to prevent keyboard typing - e.g. in a Terminal window, or in a Firefox window, or Alt-F4 no longer closes a window, etc etc.

I also tried booting without the card, then plugging it in after the desktop appeared. The keyboard worked fine, then the moment I plugged it in, the keyboard stopped responding. (The trackpad always continues to respond BTW, and I can use that to start/switch/close applications etc.) I get the same behaviour with the laptop-keyboard or with a USB keyboard.

In order to get some dmesg output I ran "sleep 30; dmesg" before plugging the card in. Then here's (below) the hopefully-relevant output (typed out by hand, timestamps not included). Thanks for any suggestions!

pccard: CardBus card inserted into slot 1
acx: Loaded combined PCI/USB driver, firmware_ver=default
acx: compiled to use 32bit I/O acces. I/O timing issues might occur, such as non-working firmware upload. Report them
PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:06:00.0 to 64
acx: found ACX111-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x2C020000, phymem2:0x2C000000, mem1:0xccb34000, mem1_size:8192, mem2:0xccc00000, mem2_size:131072
acx: loading firmware for acx1111 chipset with radio ID 16
NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
AntennaID:00 Len:02 Data:01 02
PowerLevelID:01 Len:02 Data:001E 000A
DataRatesID:02 Len:05 Data:TI ACX100
ManufacturerID:05 Len:07 Data:TI Test
acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
usbcore: registered new interface driver acx_usb
ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by heavyduty on 2008-11-26
FWIW, I have a similar problem with my Dell Inspiron 8600, on Xubuntu 8.10.

With the wifi (built-in) enabled, the keyboard doesn't respond at all when I logon. I need to logout and then logon again, and only then does the keyboard work. With the wifi disabled, everything works fine.

---

