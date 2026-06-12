---
title: "IR remote control on USB DVB-T  TDT TV player"
date: 2009-06-15
forum: Hardware
---

### Post by rforcen on 2009-06-15
hi,

i've got an USB based DVB TV player based on the EC168/MXL5005S chipset working fine with kaffeine on 9.04 jaunty,

the problem is with the remote control that doesn't work,

dmesg reports:

> [ 1094.453175] input: HID 18b4:1001 as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input9

so **input9** seems to be the device channel for this IR remote,

how to link the channel to the keyboards services so i can configure the remote keys to match TV applications?,

thanxs


full dmesg reports:
[ 1094.453175] input: HID 18b4:1001 as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input9
[ 1094.456602] generic-usb 0003:18B4:1001.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 18b4:1001] on usb-0000:00:1d.7-1/input0
[ 1094.456623] usbcore: registered new interface driver usbhid
[ 1094.456626] usbhid: v2.6:USB HID core driver
[ 1094.574964] dvb-usb: found a 'E3C EC168 DVB-T USB2.0 reference design' in cold state, will try to load a firmware
[ 1094.574969] usb 1-1: firmware: requesting dvb-usb-ec168.fw
[ 1094.604259] dvb-usb: downloading firmware from file 'dvb-usb-ec168.fw'
[ 1094.659372] dvb-usb: found a 'E3C EC168 DVB-T USB2.0 reference design' in warm state.
[ 1094.659418] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 1094.659637] DVB: registering new adapter (E3C EC168 DVB-T USB2.0 reference design)
[ 1094.703237] DVB: registering adapter 0 frontend 0 (E3C EC100 DVB-T)...
[ 1094.761250] MXL5005S: Attached at address 0xc6
[ 1094.761257] dvb-usb: E3C EC168 DVB-T USB2.0 reference design successfully initialized and connected.
[ 1094.761294] usbcore: registered new interface driver dvb_usb_ec168

---

