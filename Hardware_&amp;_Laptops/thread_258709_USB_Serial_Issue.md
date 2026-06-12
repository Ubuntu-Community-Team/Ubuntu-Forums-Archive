---
title: "USB Serial Issue"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by kaushal on 2006-09-16
Hi, need some help loading the driver for Texas Instruments USB -> Serial cable. I have tried this with Ubuntu 6.06, Fedora 4 and 5, but end up with the same error. I use this cable to connect to my CDMA phone, which acts as my modem, it works perfectly in Windows and I was able to get it to work in Fedora 3 (2.6.9 kernel) after downloading and installing the driver from [http://gate.brimson.com/downloads](http://gate.brimson.com/downloads). However, since Linux kernel 2.6.11, this driver is included in the Linux kernel, however, it does not seem to be working properly. When loaded correctly, it should create a device node as /dev/ttyUSBx where x could be 0,1,2 etc. The dmesg output when the cable is plugged is given below;

Sep 16 20:05:35 localhost kernel: [   83.667829] ohci_hcd 0000:00:02.1: wakeup
Sep 16 20:05:35 localhost kernel: [   83.793676] usb 2-1: new full speed USB device using ohci_hcd and address 2
Sep 16 20:05:35 localhost kernel: [   83.930814] usbcore: registered new driver usbserial
Sep 16 20:05:35 localhost kernel: [   83.931121] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Sep 16 20:05:35 localhost kernel: [   83.931474] usbcore: registered new driver usbserial_generic
Sep 16 20:05:35 localhost kernel: [   83.931542] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Sep 16 20:05:35 localhost kernel: [   83.936232] drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 3410 1 port adapter
Sep 16 20:05:35 localhost kernel: [   83.936589] drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 5052 2 port adapter
Sep 16 20:05:35 localhost kernel: [   83.936948] ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected
Sep 16 20:05:36 localhost kernel: [   84.410689] usb 2-1: reset full speed USB device using ohci_hcd and address 2
Sep 16 20:05:37 localhost kernel: [   84.476585] usb 2-1: device firmware changed
Sep 16 20:05:37 localhost kernel: [   84.476595] ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5
Sep 16 20:05:37 localhost kernel: [   84.476604] usb 2-1: USB disconnect, address 2
Sep 16 20:05:37 localhost kernel: [   84.476607] usbcore: registered new driver ti_usb_3410_5052
Sep 16 20:05:37 localhost kernel: [   84.476609] drivers/usb/serial/ti_usb_3410_5052.c: TI USB 3410/5052 Serial Driver v0.9
Sep 16 20:05:37 localhost kernel: [   84.528825] usb 2-1: new full speed USB device using ohci_hcd and address 3
Sep 16 20:05:37 localhost kernel: [   84.618361] usb 2-1: configuration #1 chosen from 2 choices
Sep 16 20:05:37 localhost kernel: [   84.620186] ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected
Sep 16 20:05:37 localhost kernel: [   84.620193] ti_usb_3410_5052: probe of 2-1:1.0 failed 


device info via lsusb -v is also given below; any help in resolving this issue is appreciated, until then I am unable to connect to the net from Ubuntu :( 

$lsusb -v

Bus 002 Device 006: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x3410 TUSB3410 Microcontroller
  bcdDevice            1.00
  iManufacturer           1 Texas Instruments
  iProduct                2 TUSB3410 Boot Device
  iSerial                 3 TUSB3410
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     2
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered

---

### Post by maduranga on 2006-09-23
hey... me too having the same prob. I'm using the HUAWEI ETS2288 modem and it gives the following error when i give the command "dmesg"

 [COLOR="Black"]ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5[/COLOR]


what is this error? is there any solution for this?

---

### Post by kaushal on 2006-09-23
well....I have not found a solution as yet, but there is a way to get around the USB probing error by using the following command before plugging in the cable which will load generic usb serial driver instead of the TI usb driver
# modprobe usbserial vendor=0x0451 product=0x3410

However, our problem is not solved by this since the Huawei ETS2288 modem does not seem to work when it is attached to /dev/ttyUSB0 via the generic usb serial driver

---

### Post by kaushal on 2006-10-01
Finally, I found a solution to this issue

1. Create the folllowing file 
[INDENT][FONT="Courier New"]/etc/udev/rules.d/026_ti_usb_3410.rules[/FONT][/INDENT]

2. Add the following lines to this file
[INDENT][FONT="Courier New"]#TI USB 3410
SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \
SYSFS{bNumConfigurations}=="2" \
 SYSFS{bConfigurationValue}=="1" \
 RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"
[/FONT]
[/INDENT]

3. Plug in your USB Serial cable and it should create a device node as /dev/ttyUSB0

4. Configure the modem using wvdial and specify the modem as /dev/ttyUSB0

---

### Post by jprupp on 2006-11-18
It seems that the previous line to be added to the UDEV rules is wrong. It doesn't have commas separating the different sections of the rule.

I think it should be something more like this:

If there are not commas separating everything, my computer runs the mini-shell-script everytime I plug any USB device, no matter which vendor it comes from. I don't know why, but UDEV behaves erratically.

#TI USB 3410
SUBSYSTEM=="usb_device", ACTION=="add", \
SYSFS{idVendor}=="0451", SYSFS{idProduct}=="3410", \
SYSFS{bNumConfigurations}=="2", \
SYSFS{bConfigurationValue}=="1", \
RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"

By the way, this UDEV rule is supposed to run this instruction when you plug the USB cable:

/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'

This instruction writes the number "2" to the bConfigurationValue file that belongs to the USB cable in the /sys directory, that seems to change the behavior of the device in some way, and makes it activate a ttyUSB? device, then usbserial instructs UDEV to create a /dev/ttyUSB? device node.

I must mention that I have a generic DKU-5 USB cable and a Nokia 2112 phone. I haven't been able to talk to this phone through this cable, even when I have access to the /dev/ttyUSB? node for it. I am actually talking to the cable because if I power off the phone and then on again, I see some garbage on my minicom terminal when the phone is connected, though it doesn't answer to AT commands, it doesn't even echo them.

---

### Post by ramnarayan on 2006-11-29
would appreciate if you post your wvdial.conf file

and also a brief on the other steps.

Did you have to make a new file in /etc/peers
did you have to edit pap-secrets and chap-secrets
did you have to uninstall any other modems , or references to them and if yes how ?

am really struggling with this and if it works then for the first time I will be able to access the internet, from home,  using linux instead windows

thanks
ram

---

### Post by vsukthankar on 2006-12-05
I have tried this on Ubuntu 6.06 and some other distros.. I suggest that you try this....

1) Without inserting the DKU-5 Cable...
   #modprobe usbserial vendor=0x451 product=0x3410
2) Then insert the cable, you should not get the error..

I think this issue is due to udev, which is not loading the usbserial.. I have not tried with the new udev, which could have fixxed the issue...

Rgds
Vijay

---

### Post by gippie on 2006-12-13
Ok just a quick post as only the wvdial.conf is asked for to get a huawei cdma modem to connect here in Uganda to MTN and perhaps UTL's wireless network.

I used Ubuntu 6.10, compiled the ti_usb_3410_5052, put in a rules file and a script file and used the following wvdial.conf to make the connection.

/etc/wvdial.conf

[Dialer Defaults]

Modem = /dev/modem  # <= or /dev/ttyUSB0
Baud = 230400  # <= important
Dial Command = ATDT
Initzl = ATZ
Phone = #555
Username = [email]0312xxxxxx@yelloaccess.co.ug[/email]
Password = 0312xxxxxx
Stupid Mode 1
#New PPPD = yes


Rest is already explained in the posts.

---

### Post by gippie on 2006-12-14
CDMA data phone under Linux. Ubuntu 6.10 in this case.

After reading so many requests from the web to get this cdma modem and cable to work I decided to give it a go because I have this modem unused on the shelf.

The procedure as I remember to get all running:

I did a standard install of a Ubuntu 6.10 distribution cd and include some gcc compile options and the kernel source and it's requirements. You can always use apt-get as needed in a later stage if anything is missing during a compile.

The driver we need to compile as a module is the ti_usb_3410_5052 and the usbserial that you eventually modprobe. It comes standard in this Ubuntu Distribution as I found out later but it needs some tweaking.

I downloaded the module source ti_usb_2.6-1.1.tar.gz as I did not know Ubuntu kernel already had it. The download came from:  [http://gate.brimson.com/downloads/](http://gate.brimson.com/downloads/)

I untarred ti_usb_2.6-1.1.tar.gz  in a separate folder and copied the ti_usb_3410_5052.c and .h from the Linux kernel source for Ubuntu into the untarred src folder after which I did the configure, make and make install.

P.s. When I did configure and make with the original tar file I ended up with a wrong module.

The make install puts the module in the correct place (lib/modules/2.6.17-18-generic/kernel/drivers/usb/serial/) but not the hotplug script as it puts it in /etc/hotplug/usb/ (for older Linux distributions. This script needs to be in /etc/udev/scripts/ under Ubuntu 6.10 as 6.10 uses udev and hal with the name as ti_usb_3410_5052 and it should contain:

#-------------------------------------------------------------------------------------------------------------------
#!/bin/bash

BOOT_CONFIG=1
ACTIVE_CONFIG=2

if [[ "$ACTION" != "add" ]]
then
        exit
fi

CONFIG_PATH=/sys${DEVPATH%/?*}/bConfigurationValue

if [[ 0`cat $CONFIG_PATH` -ne $BOOT_CONFIG ]]
then
        exit
fi

PRODUCT=${PRODUCT%/?*}          # delete version
VENDOR_ID=`printf "%d" 0x${PRODUCT%/?*}`
PRODUCT_ID=`printf "%d" 0x${PRODUCT#*?/}`

PARAM_PATH=/sys/module/ti_usb_3410_5052/parameters
function scan() {
        s=$1
        shift
        for i
        do
                if [[ $s -eq $i ]]
                then
                        return 0
                fi
        done
        return 1
}

IFS=$IFS,

if (scan $VENDOR_ID 1105 `cat $PARAM_PATH/vendor_3410` &&
scan $PRODUCT_ID 13328 `cat $PARAM_PATH/product_3410`) ||
(scan $VENDOR_ID 1105 `cat $PARAM_PATH/vendor_5052` &&
scan $PRODUCT_ID 20562 20818 20570 20575 `cat $PARAM_PATH/product_5052`)
then
        echo $ACTIVE_CONFIG > $CONFIG_PATH
fi
/
#-------------------------------------------------------------------------------------------------------------------

Also give the file +x so it can be executed when the cable is inserted.

p.s. this script you find in the ti_usb_3410_5052.c files. Copy it into a separate file.

Once this was done I created a rules script for /etc/udev/rules.d/. I named it 26_ti_usb_3410.rules as I got this from some forum page I don't remember. Thanks to the individual! Anyway it should contain:

#-------------------------------------------------------------------------------------------------------------------
#TI USB 3410
SUBSYSTEM=="usb_device", ACTION=="add", \
SYSFS{idVendor}=="0451", SYSFS{idProduct}=="3410", \
SYSFS{bNumConfigurations}=="2", \
SYSFS{bConfigurationValue}=="1", \
RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"
SYSMLINK=”modem”
#-------------------------------------------------------------------------------------------------------------------

This will create the /dev/ttyUSB0 and a link to /dev/modem for you once it is all on place.

P.s. Thanks Andrew? For the rules addition!

I use wvdial to connect to MTN's Internet in Uganda with the following /etc/wvdial.conf 

#-------------------------------------------------------------------------------------------------------------------
[Dialer Defaults]

Modem = /dev/modem
Baud = 230400
Dial Command = ATDT
Initl = ATZ
Phone = #555 
Username = [email]0312xxxxxx@yelloaccess.co.ug[/email] 
Password = 0312xxxxx 
Stupid Mode = 1
# New PPPD = yes
#-------------------------------------------------------------------------------------------------------------------

Note the Baud = 230400. Without it this line it simply will not dial.

I found out whilst playing with minicom and changing settings!

So I have to say thanks for those that pointed me through the different forums to create the /dev/ttyUSB0 interface so my playing around with my modem experience solved it.

P.s. cant remember what I did to fix ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5 but will put this error in my txt for others to find it.

When wvdial starts I get:

root@gippie-dd:/etc/udev# wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT#555
--> Waiting for carrier.
ATDT#555
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Dec 13 13:25:48 2006
--> Pid of pppd: 19667
--> Using interface ppp0
--> local  IP address 10.0.0.85
--> remote IP address 2.2.2.2
--> primary   DNS address 212.88.97.20
--> secondary DNS address 193.108.214.50

root@gippie-dd:/etc/udev# ping 212.88.97.67
PING 212.88.97.67 (212.88.97.67) 56(84) bytes of data.
64 bytes from 212.88.97.67: icmp_seq=1 ttl=60 time=331 ms
64 bytes from 212.88.97.67: icmp_seq=2 ttl=60 time=328 ms

--- 212.88.97.67 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 328.026/329.801/331.576/1.775 ms

We are connected :)

Some times it takes a few attempts to connect when the net is busy!

Quiting wvdial shows:

Crtl-C

Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> Connect time 7.7 minutes.
--> Disconnecting at Wed Dec 13 13:33:33 2006

We are disconnected :_)

Rest is a dump of what the box logs:

lsusb

Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 011: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 004 Device 001: ID 0000:0000 

lsmod
...
snd_mixer_oss	19584  1 snd_pcm_oss
ti_usb_3410_5052	57288  0 
usbserial              	34152  1 ti_usb_3410_5052
...
ieee1394              	306104  2 sbp2,ohci1394
uhci_hcd               	24968  0 
usbcore               	134912  8 cdc_acm,ti_usb_3410_5052,usbserial,usb_storage,
libusual,ehci_hcd,uhci_hcd
ide_generic             	2432  0 

dmesg of insertion:

[17194581.184000] usb 4-1: new full speed USB device using uhci_hcd and address 12
[17194581.372000] usb 4-1: configuration #1 chosen from 1 choice
[17194581.376000] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[17194582.016000] usb 4-1: reset full speed USB device using uhci_hcd and address 12
[17194582.156000] usb 4-1: device firmware changed
[17194582.156000] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
[17194582.156000] usb 4-1: USB disconnect, address 12
[17194582.272000] usb 4-1: new full speed USB device using uhci_hcd and address 13
[17194582.492000] usb 4-1: configuration #1 chosen from 2 choices
[17194582.496000] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[17194582.496000] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
[17194582.612000] ti_usb_3410_5052 4-1:2.0: TI USB 3410 1 port adapter converter detected
[17194582.612000] usb 4-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

Similar in /var/log/messages:

Dec 13 13:22:09 gippie-dd kernel: [17194582.016000] usb 4-1: reset full speed USB device using uhci_hcd and address 12
Dec 13 13:22:10 gippie-dd kernel: [17194582.156000] usb 4-1: device firmware changed
Dec 13 13:22:10 gippie-dd kernel: [17194582.156000] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
Dec 13 13:22:10 gippie-dd kernel: [17194582.156000] usb 4-1: USB disconnect, address 12
Dec 13 13:22:10 gippie-dd kernel: [17194582.272000] usb 4-1: new full speed USB device using uhci_hcd and address 13
Dec 13 13:22:10 gippie-dd kernel: [17194582.492000] usb 4-1: configuration #1 chosen from 2 choices
Dec 13 13:22:10 gippie-dd kernel: [17194582.496000] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
Dec 13 13:22:10 gippie-dd kernel: [17194582.496000] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
Dec 13 13:22:10 gippie-dd kernel: [17194582.612000] ti_usb_3410_5052 4-1:2.0: TI USB 3410 1 port adapter converter detected
Dec 13 13:22:10 gippie-dd kernel: [17194582.612000] usb 4-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

If I skipped a step please let me know.

---

### Post by olivierCLEODE on 2007-03-21
Hello,

I try to install the TUSB3410 converter usb serial on Linux 2.6.11.7 and Linux recognize the device but don't attach it to ttyUSB0.

I put the firmware in the path : /etc/hotplug/usb/ti_usb_3410_5052 because we use hotplug.

When i connect it, i have this result:

hub 1-0:1.0: state 5 ports 2 chg 0000 evt 0002
ocp-ohci 02: GetStatus roothub.portstatus [0] = 0x00010101 CSC PPS CCS
hub 1-0:1.0: port 1, status 0101, change 0001, 12 Mb/s
hub 1-0:1.0: debounce: port 1: total 100ms stable 100ms status 0x101
ocp-ohci 02: GetStatus roothub.portstatus [0] = 0x00100103 PRSC PPS PES CCS
usb 1-1: new full speed USB device using ocp-ohci and address 5
ocp-ohci 02: GetStatus roothub.portstatus [0] = 0x00100103 PRSC PPS PES CCS
usb 1-1: ep0 maxpacket = 8
usb 1-1: new device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-1: default language 0x0409
usb 1-1: Product: TUSB3410UART EVM
usb 1-1: Manufacturer: Texas Instruments
usb 1-1: SerialNumber: 00000231
usb 1-1: hotplug
usb 1-1: adding 1-1:1.0 (config #1, interface 0)
usb 1-1:1.0: hotplug
hub 1-0:1.0: state 5 ports 2 chg 0000 evt 0002


I test an other device, the Prolific PL2103 and Linux recognize and attach it to ttyUSB0.


usb 1-1: Product: USB-Serial Controller
usb 1-1: Manufacturer: Prolific Technology Inc.
usb 1-1: hotplug
usb 1-1: adding 1-1:1.0 (config #1, interface 0)
usb 1-1:1.0: hotplug
pl2303 1-1:1.0: usb_probe_interface
usb_probe_interface
pl2303 1-1:1.0: usb_probe_interface - got id
drivers/usb/serial/usb-serial.c: 1) usb_serial_probe
drivers/usb/serial/usb-serial.c: descriptor matches
drivers/usb/serial/usb-serial.c: found interrupt in on endpoint 0
drivers/usb/serial/usb-serial.c: found bulk out on endpoint 1
drivers/usb/serial/usb-serial.c: found bulk in on endpoint 2
pl2303 1-1:1.0: PL-2303 converter detected
drivers/usb/serial/usb-serial.c: get_free_serial 1
drivers/usb/serial/usb-serial.c: get_free_serial - minor base = 0
drivers/usb/serial/usb-serial.c: usb_serial_probe - setting up 1 port structures
 for this device
drivers/usb/serial/pl2303.c: device type: 2
drivers/usb/serial/usb-serial.c: usb_serial_probe - registering ttyUSB0
usb 1-1: PL-2303 converter now attached to ttyUSB0
hub 1-0:1.0: state 5 ports 2 chg 0000 evt 0002

I think i have a problem with hotplug.

Can you help me.

Thanks.

---

### Post by olivierCLEODE on 2007-04-02
I've found a solution, just change the ProductID in the ti_usb_3410_5052.h.

Put 0x341A.

Bye

---

### Post by TabletGuy on 2007-05-21
Hi

Just a quick note to say thanks to gippie for this.

I got this working in Feisty using the scripts gippie posted (without having to compile the driver).

---

### Post by newpants2003 on 2007-07-25
nice to see the tips, going to try that tomorrow.
thanks.

---

### Post by bobby261 on 2007-09-01
i want connect cdma nokia 6585 to display led microcontroler.
who can help my problem.
where i can download AT command nokia 6585?
my email   [email]bobby_bobby261@yahoo.com[/email]
thank you

regard

bobby261

---

