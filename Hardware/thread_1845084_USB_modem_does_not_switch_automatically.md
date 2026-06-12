---
title: "USB modem does not switch automatically"
date: 2011-09-16
forum: Hardware
---

### Post by Iqbal_ on 2011-09-16
Hi,
 I have a Micromax 352G usb modem. After plugging-in the modem, NM  does not react to it. I have installed wvdial and usb_modeswitch.
 The vendor is 1c9e and product is 9605.
 However sakis3g switches the device to modem mode. But without sakis3g, usb_modeswitch does not switch the device to modem mode.
 When I run wvdial, it prints the following lines
 ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","gprsppsdel"
AT+CGDCONT=1,"IP","gprsppsdel"
OK
--> Modem initialized.
--> Sending: ATDP*99#
--> Waiting for carrier.
ATDP*99#
ERROR
--> Invalid dial command.
 How to solve this problem?
 I want to use this modem on Ubuntu 10.04 (32bits) and 11.04 (64 bits).

---

