---
title: "How to set up a SmartUPS (USB)"
date: 2010-07-06
forum: Hardware
---

### Post by kovacslajcsi on 2010-07-06
Hi,

I try to set up my APC Smat UPS 750 (SUA750I), with apcuspd, but i faild :(

I installed the apcupsd, edited the conf file, for USB UPS, but the test failed. It seems, that the USB HID driver is not installed..

see here:

root@cserebogar:/etc/default# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0bda:8150 Realtek Semiconductor Corp. RTL8150 Fast Ethernet Adapter
Bus 003 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@cserebogar:/etc/default# lsusb -v -s 3:2

Bus 003 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x051d American Power Conversion
  idProduct          0x0002 Uninterruptible Power Supply
  bcdDevice            0.06
  iManufacturer           3 American Power Conversion
  iProduct                1 Smart-UPS 750 FW:651.11.I USB FW:4.2
  iSerial                 2 QS0421343874
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         11 1
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower               30mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength    1064
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval             100
Device Status:     0x0001
  Self Powered
root@cserebogar:/etc/default# lsmod | grep usb
usbhid                 42336  1 
root@cserebogar:/etc/default# apctest


2010-07-06 12:21:03 apctest 3.14.4 (18 May 2008) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = CUSTOM_SMART

You are using a SMART cable type, so I'm entering SMART test mode
mode.type = USB_UPS
Setting up the port ...
Hello, this is the apcupsd Cable Test program.
This part of apctest is for testing Smart UPSes.
Please select the function you want to perform.

1) Query the UPS for all known values
2) Perform a Battery Runtime Calibration
3) Abort Battery Calibration
4) Monitor Battery Calibration progress
5) Program EEPROM
6) Enter TTY mode communicating with UPS
7) Quit

Select function number: 1
YWrote: Y Got: P&#271;&#380;&#733;&#271;&#380;&#733;&#271;&#380;&#733;&#271;&#380;&#733;&#271;&#380;&#733;6&#271;&#380;&#733;
getline failed. Apparently the link is not up.
Giving up.

1) Query the UPS for all known values
2) Perform a Battery Runtime Calibration
3) Abort Battery Calibration
4) Monitor Battery Calibration progress
5) Program EEPROM
6) Enter TTY mode communicating with UPS
7) Quit

Select function number: 7

2010-07-06 12:21:41 End apctest.

when I enter: cat /proc/bus/usb/devices from a shell, it  prompt shows that no USB 
devices are detected, it's empty..

How can I solve this?

---

### Post by ^_Pepe_^ on 2010-07-07
Hi,

I've recently purchased a APC 550ES and I'm really surprised about how easy I could put it to work in 10.04.

1. Please, read [http://www.apcupsd.com/manual/manual.html#quick-start-for-beginners](http://www.apcupsd.com/manual/manual.html#quick-start-for-beginners)
2. Check my apcupsd.conf, attached to this post.
3. After this, my test was nok, but works.


```
pepe@HOMER:~$ apctest


2010-07-07 11:32:32 apctest 3.14.6 (16 May 2009) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
apctest error termination completed

```

4. You can see a battery on GNOME panel to check, and also, there's a easy GUI to manage apcupsd, called gapcmon, but please, use 0.8.6. version, because 0.8.9 has a bug with icons.

Best,
^_Pepe_^

---

### Post by ^_Pepe_^ on 2010-07-07
Hi again,

You can also check,

```
pepe@HOMER:~$ apcaccess status
APC      : 001,036,0942
DATE     : Wed Jul 07 11:48:52 CEST 2010
HOSTNAME : HOMER
VERSION  : 3.14.6 (16 May 2009) debian
UPSNAME  : HOMER
CABLE    : USB Cable
MODEL    : Back-UPS ES 700G 
UPSMODE  : Stand Alone
STARTTIME: Tue Jul 06 00:45:41 CEST 2010
STATUS   : ONLINE 
LINEV    : 230.0 Volts
LOADPCT  :  41.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  14.6 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 180.0 Volts
HITRANS  : 266.0 Volts
ALARMDEL : Always
BATTV    : 13.3 Volts
LASTXFER : Low line voltage
NUMXFERS : 1
XONBATT  : Tue Jul 06 18:01:25 CEST 2010
TONBATT  : 0 seconds
CUMONBATT: 109 seconds
XOFFBATT : Tue Jul 06 18:03:14 CEST 2010
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2010-01-20
SERIALNO : 3B1004X02003  
BATTDATE : 2000-00-00
NOMINV   : 230 Volts
NOMBATTV :  12.0 Volts
FIRMWARE : 871.O1 .I USB FW:O1
APCMODEL : Back-UPS ES 700G 
END APC  : Wed Jul 07 11:48:54 CEST 2010

```

To see if it works.

Sorry,

I have to stop apcupsd service and run test as sudo to put it to work.

```
pepe@HOMER:~$ sudo service apcupsd stop
Stopping UPS power management: apcupsd.
pepe@HOMER:~$ sudo apctest


2010-07-07 11:58:46 apctest 3.14.6 (16 May 2009) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
Hello, this is the apcupsd Cable Test program.
This part of apctest is for testing USB UPSes.

Getting UPS capabilities...SUCCESS

Please select the function you want to perform.

1)  Test kill UPS power
2)  Perform self-test
3)  Read last self-test result
4)  Change battery date
5)  View battery date
6)  View manufacturing date
7)  Set alarm behavior
8)  Set sensitivity
9)  Set low transfer voltage
10) Set high transfer voltage
11) Quit

Select function number: 

```

Are you using USB or RS-232?

Regards,
^_Pepe_ ^

---

### Post by kovacslajcsi on 2010-07-08
hi,

at my last reboot, a small icon next to the clock apperard for some seconds, but at the time, i clicked on it, it dissappeard..

Is this the bug, in 0.8.9?

if yes, how can I downgrade it to 0.8.6?

I try to use the USB port of the UPS..

---

### Post by ^_Pepe_^ on 2010-07-08
Hi,

Yes, sure! This is the buggy icon problem.

To downgrade to 0.8.6, download the .deb from here [http://packages.debian.org/es/lenny/admin/gapcmon](http://packages.debian.org/es/lenny/admin/gapcmon) and uninstall firstly 0.8.9 from Synaptic.

Hope it helps!
P.S.: You can follow the bug here [https://bugs.launchpad.net/ubuntu/+source/gapcmon/+bug/491773](https://bugs.launchpad.net/ubuntu/+source/gapcmon/+bug/491773)

^_Pepe_^

---

### Post by macmike on 2010-08-04
How do you reinstall gapcmon once you download the 8.6 version?

---

