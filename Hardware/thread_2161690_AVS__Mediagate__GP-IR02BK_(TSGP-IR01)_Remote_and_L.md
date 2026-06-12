---
title: "AVS / Mediagate  GP-IR02BK (TSGP-IR01) Remote and LIRC"
date: 2013-07-11
forum: Hardware
---

### Post by aesalazar on 2013-07-11
Hi Guys.  Trying to get an XBMC HTP up and running using ubuntu as the os.  Running 13.04 since 12.04 would not install on the pc - I have a Gigabyte Birx mini with the i3 chip and a 64 gb msata drive.

To control it, I got a Mediagate (aka AVS) from here:

[http://www.rakuten.com/pr/product.aspx?sku=206225418](http://www.rakuten.com/pr/product.aspx?sku=206225418)

I have spent hours trying to get LIRC to pick it up.  If I use irrecord it finds it with out issue.  Here is the initial start results:

```

root@xbmc:~# irrecord  --device=/dev/lirc0 myremote.conf
...
...
...
Found const length: 93657
Please keep on pressing buttons like described above.
................................................................................
RC-6 remote control found.
Found possible header: 2694 863
No repeat code found.
Unknown encoding found.
Creating config file in raw mode.
Now enter the names for the buttons.
```

I record a few buttons and myremote.conf looks like this:

```

begin remote

  name  myremote.conf
  flags RAW_CODES|CONST_LENGTH
  eps            30
  aeps          100

  gap          93657

      begin raw_codes

          name KEY_UP
             2800     750     550     350     550     350
              500     800     550     800    1400     800
              550     350     550     350     500     400
              500     400     500     350     550     350
              500     400     500     400     500     350
              550    7500     450     400     950     850
              500     400     500     400     450     400
              500     400     950     400     500     400
              450     400     500     850     500

          name KEY_DOWN ......

```
So everything seems to be work so far.  I start lirc with the conf file and test with irw but irw does not output anything no matter which key I press.  
```

root@xbmc:~# lircd --device=/dev/lirc0 myremote.conf
root@xbmc:~# irw
```
The USB receiver blinks to confirm it is receiving a signal.  if I watch the port directly I do get output:
```

root@xbmc:/dev# cat /dev/lirc0
ÿÿÿð
 ô^&^& ô ª ôô^&^&^ôôô^&^ôPuTTYô ÈRÂôô¶Û¾
 &,&^& ô ª ôôPuTTYô^&^ôôôô^ôô¶ô^ôôôRÂôôð¾
 ôôôRÂRxRÂôôôôÂôôôPuTTYBÂÂÂÂô#ð
î&^&^& &îª ôô^&^&^ôô^&^ôôPuTTYôLô¶ ôôôô
                                       ôôôÂJ
RôÂôRôRFRôôÂÂÂôPuTTYôôÂÂÂô
                          ÂÂÂÂÂÂRÂÂÂÂÂÂÂ¶RÂÂÂð
î&^&^ô & xRô^&^&PuTTY^ôôô^&^ôôô
                               ôôôÂRôôôì^C
```


Here is how the device shows in the system:
```

root@xbmc:/etc# dmesg|tail

[  572.793310] usb 3-1: Product: eHome Infrared Transceiver
[  572.793315] usb 3-1: Manufacturer: Topseed Technology Corp.
[  572.793319] usb 3-1: SerialNumber: TS000KMN
[  572.795264] Registered IR keymap rc-rc6-mce
[  572.795475] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/pci0000:00/00                                                              00:00:14.0/usb3/3-1/3-1:1.0/rc/rc1/input11
[  572.795668] rc1: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/pci0000:00/0000                                                              :00:14.0/usb3/3-1/3-1:1.0/rc/rc1
[  572.795920] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input12
[  572.796312] rc rc1: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[  572.937660] mceusb 3-1:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver with mce emulato                                                              r interface version 1
[  572.937671] mceusb 3-1:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)

root@xbmc:/etc$ cat /proc/bus/input/devices

I: Bus=0003 Vendor=1784 Product=0008 Version=0101
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (1784:0008)"
P: Phys=usb-0000:00:14.0-1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/rc/rc1/input11
U: Uniq=
H: Handlers=kbd event2
B: PROP=0
B: EV=100013
B: KEY=fff 0 200108fc32e 237605100000000 0 700158000 419200004001 8e968000000000 10000000
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="MCE IR Keyboard/Mouse (mceusb)"
P: Phys=/input0
S: Sysfs=/devices/virtual/input/input12
U: Uniq=
H: Handlers=sysrq kbd mouse0 event3
B: PROP=0
B: EV=100017
B: KEY=30000 7 ff87207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=3
B: MSC=10
```

Any ideas?

Thanks
Ernie

---

