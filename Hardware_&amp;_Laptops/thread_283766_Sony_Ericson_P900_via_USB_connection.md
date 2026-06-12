---
title: "Sony Ericson P900 via USB connection ?"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by phibuntu on 2006-10-24
I am now the owner of a Sony Ericson P900.

To connect it to my Dell INSPIRON 9300, I want to use the USB craddle connection.

lsusb lists the "Future Technology Devices International, Ltd" Device.

What do I need more to connect?

---

### Post by madmetal on 2006-10-24
i think wammu will help you..
[http://cihar.com/gammu/wammu/](http://cihar.com/gammu/wammu/)

---

### Post by phibuntu on 2006-10-26
Thanks for your prompt answer

Unfortunately the P900 Model is not listed in the gammu phone database on the mentioned website.

Other ideas?

---

### Post by phibuntu on 2006-10-28
Here some other tries, which all failed.

**Preparations**

  - Install the cable connection on the phone as follows:
           PC-Verb 
           Baudrate: 115200
           Parity: none
           Stopp-Bits: 1
           Character length: 8 Bit
           Controll-flow: none

**a)** I tried ```
>lsusb -v
```  and it leads to the following good looking output for the device

```
Bus 004 Device 002: ID 0403:fc82 Future Technology Devices International, Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0xfc82
  bcdDevice            4.00
  iManufacturer           1
  iProduct                2
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               40mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
```
This (a) means, the device is recognized by the linux usb system.


**b)** Triing to connect via pppd
I tried the following command, which I found on several pages on the internet:

```
/usr/sbin/pppd /dev/ttyUSB0 115200 crtscts nodetach defaultroute usepeerdns lcp-echo-failure 10 lcp-echo-interval 86400 connect '/usr/sbin/chat -t 6 -s -v "" ATZ OK ATD*99***1# CONNECT \d\c'
```

I also tried "ATDT*99***1#" instead of "ATD*99***1#" but both lead to the following error:

```
/usr/sbin/pppd: The remote system is required to authenticate itself
/usr/sbin/pppd: but I couldn't find any suitable secret (password) for it to use to do so.
```

**c)** finally I tried the minicom application to see, what comes from outside:

Entering the ATZ command the following code comes from the P900:

```
~mRouter - Are you there?~
```

So, there is someone out there. But how do I connect?
Do I need to install some software on the P900 to setup a proper ppp-Server :?:

**d)** So I changed the connection to MODEM (instead of PC connection)

My Minicom Session now looks as follows (all small-letter commands are type d by myself, the capitals come from the device). This means, I get a connection to the phone, but how do I start from here :?: :?:

```
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK
ati
P900

OK
atdt*99***1#
CONNECT
```

after the "CONNECT" response from the modem, I am not able to enter more commands.

---

