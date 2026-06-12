---
title: "help with installing a driver"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by icecube76 on 2007-06-27
im trying to use usb 3g modem with 7.4
the manual i got from the manufacturer says

            To install Modem on Linux you need add a line:

                                   usbserial vendor=0xaf0 product=0x6501
            To this file:

                                   /etc/module
            Reboot Linux

Example

To connect to the internet over GPRS using wvdial dialer you can use the following configuration file
(/etc/wvdial.conf):

Launch terminal in Linux, you must enter as root
Then launch

                                   wvdialconf /etc/wvdial.conf

It will create wvdial.conf file in /etc/ folder, when edit this file and enter such parameters

                                   [Dialer Defaults]
                                   Modem = /dev/ttyUSB0
                                   Baud = 460800
                                   Init1 = ATZ
                                   Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
                                   Username= your login
                                   Password= your password
                                   [Dialer ModemUSB/H1.8]
                                   Carrier Check=no
                                   Check Def Route=on
                                   Dial Command=ATD
                                   Phone =*99#
                                   Init3= AT+CGDCONT=1,"IP","your.apn.here"

Note: You need to replace 'your login', 'your password' and 'your.apn.here' with values appropriate for
your GSM operator after that enter in terminal such command

                                   wvdial --config /etc/wvdial.conf ModemUSB/H1.8

Modem will connect to the internet, to stop connection press in the terminal CTRL+C.

but there is no /etc/module in Ubuntu

help please

---

### Post by Ayuthia on 2007-06-27
I think that /etc/module is supposed to be /etc/modules.  Have you tried that?

---

