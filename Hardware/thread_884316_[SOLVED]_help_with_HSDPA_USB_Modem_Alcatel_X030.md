---
title: "[SOLVED] help with HSDPA USB Modem Alcatel X030"
date: 2008-08-08
forum: Hardware
---

### Post by adamantivm on 2008-08-08
Could anybody please help me try to get this 3G modem working? 

I have seen some instructions on setting up similar modems like [this one]("http://www.inorp.com/blog/2007/03/13/ubuntu-guide-to-using-hsdpa-usb-modem-huawei-e220-with-the-tre-network/"), but in my case unfortunately I can't get the driver to load as a usb-serial device: it always gets created as a usb storage device.

Could anybody please give me any hint on how to get to the point where I can create the tty devices so that I can use '''wvdial'''? Any hint on how to do debugging or manipulate the usb drivers beyond modprobe would be greatly appreciated.

---

### Post by Nick Lake on 2008-08-08
Is it mounting as a flash disk or CD-ROM instead?

If so I've got a quick way (although not sustainable in the long run) to get it going.

1] Unmount the flash disk.
2] Pull out device from USB.
3] Disable HAL... sudo /etc/init.d/hal stop
4] Plug the modem back in.
5] use dmesg to see if the modem has been detected yet (you will need to give it some time).

The problem with this of course is that you have to disable your hardware abstraction layer just to use the modem... But its a quick way to check if it is working.

- Nick Lake

---

### Post by adamantivm on 2008-08-09
Thank you very much for that reply! It did get me one step further. I could load usbserial pointing it to the particular device ID that I find with lsusb:

> 
root@betun:/etc# lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 1c9e:1001  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000
root@betun:/etc# modprobe usbserial vendor=0x1c9e product=0x1001
[92591.191242] usbcore: registered new interface driver usbserial
[92591.191305] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[92591.191369] usbserial_generic 1-1:1.0: generic converter detected
[92591.191786] usb 1-1: generic converter now attached to ttyUSB0
[92591.191808] usbcore: registered new interface driver usbserial_generic
[92591.191813] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core


Unfortunately, serial device /dev/ttyUSB0 doesn't respond :-(

Digging further into the matter, I think what happens is that this is a "Flip-Flop" USB device, which starts as a USB-Storage device and then must be switched into the USB-Modem device. I'm trying to use tools and information about this kind of issue which are [found here]("http://www.draisberghof.de/usb_modeswitch/"). I got there by following [this thread]("http://translate.google.com.ar/translate?hl=en&sl=it&u=http://www.suseitalia.org/modules/newbb/viewtopic.php%3Ftopic_id%3D17723%26forum%3D6%26post_id%3D104680&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D1c9e%2B1001%2Busbserial%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26sa%3DG").

Unfortunately again, it seems that the Alcatel OT-X020 is not exactly like mine device, since the switch command that I rescued from there doesn't seem to do anything:

> usb_modeswitch -v 0x1c9e -p 0x1001 -V 0x1c9e -P 0x6061 -C 0xff -d 1

Perhaps the target device and string is not correct? I'm now trying to dig more into the matter to see if I can sniff on Windows somehow to figure out if the device is indeed a Flip-Flop and what would be the right way to get it switched.

Again, any futher hint really appreciated.

---

### Post by adamantivm on 2008-08-09
A small update: using vmware + drivers on Windows XP, I can see the device is indeed switched into ID 1c9e:6061 ... why doesn't it work using usb_modeswitch?

---

### Post by Nick Lake on 2008-08-10
Hmmm... what's a "flip flop" device?

As it seems to have registered to USB0 can you send AT commands to it? Try the following command...

echo “AT" > /dev/ttyUSB0

If the serial device returns "OK" then the modem should be communicating OK.

Silly question but did you set up the connection properly... try:
sudo pppconfig

- Nick

---

### Post by adamantivm on 2008-08-10
Hi Nick,

Note that I'm learning about this as I go, so I'm no expert.

A "flip flop" or "multiple device" USB device seems to be a device that can behave as a different USB device at different times, using the same USB connection. Citing from the USB_ModeSwitch web page:

> "Several new USB devices [...] act like a flash storage and start installing the driver from there. After that [...] switches the mode internally, the storage device vanishes [...], and a new device (like an USB modem) shows up

I can assert this is the case for me since, when I first plug the device, lsusb reports it as a **1c9e:1001**, which gets detected and works as a USB storage device, but after using VMWare with a Windoze XP image and the device drivers, it turns into a USB Modem which is reported by lsusb as a **1c9e:6061** device. 

The 6061 device then can be used by usbserial, which generates three ttyUSB* devices which do respond to AT* and other commands - the original 1001 device, when forced to usbserial, does NOT respond to these commands.

So, what I now need to do is to solve the following problems
1) Get the device to switch from storage to modem within Linux, using usb_modeswitch or an equivalent - though this is not as critical now since I have this clunky workaround to do it with VMWare
2) To properly configure the connection using wvdial, pppdial or something like that.

I have tried with pppconfig as you suggested as well as with wvdialconf, but to no avail. I'm not sure what the proper connection properties are or whether the type of connection this modem uses (3G) is supported at all by those dialers. Do you have any suggestion on how to go about finding this out? Any pointers about different connection types and how to configure them?

I'm right now finishing to trace the modem communication on Windows so that I can post it. Perhaps that will give an idea of what type of connection needs to happen.

Thanks,
Julian

---

### Post by adamantivm on 2008-08-10
Here is a first pass at the trace in Windows, not 10% sure it is complete or accurate:

> 
ATE
OK
ATE0
OK
AT+CPIN?
OK
+CPIN: SIM PIN
OK
AT+CPNNUM
PIN1=3; PUK1=10; PIN2=0; PUK2=10
OK
AT+CPIN="1234"
OK
AT+NWLCK?
+NWLCK: UNKNOWN LOCK STATUS
OK
AT+NWLCK?
+NWLCK: UNKNOWN LOCK STATUS
OK
AT+NWLCK?
+NWLCK: UNKNOWN LOCK STATUS
OK
AT+NWLCK?
+NWLCK: UNKNOWN LOCK STATUS
OK
AT+NWLCK?
+NWLCK: UNKNOWN LOCK STATUS
OK
AT+NWLCK?
+NWLCK: NETWORK UNLOCKED
OK
AT+CIMI
722341175366945
OK
AT+CGMR
LQA0007.1.2_D02B
OK
AT+CLCK="SC",2
+CLCK: 1
OK
AT+COPS=3,2
OK
AT+MODODR?
+MODODR: 2
OK
AT+BNDPRF?
+BNDPRF: 65535,16383
OK
AT+CSCA?
+CME ERROR: SIM busy
AT+CPMS="SM"
+CMS ERROR: 314
AT+CPMS="SM",,"SM"
+CMS ERROR: 314
AT+CPBS="SM"
+CME ERROR: SIM busy
AT+COPS?
+COPS: 0,2,"72234",2
OK
AT+CSQ
+CSQ: 11,92
OK
AT+PSRAT
+PSRAT: UMTS
OK
AT+PSRAT
+PSRAT: HSDPA
OK


Any idea which dialer I can configure to do this and how?
Thanks,
Julian

---

### Post by adamantivm on 2008-08-10
Here's a slightly better version, the "> " lines are the ones that were sent to the modem, the rest are replies:

> 
> ATE
OK
> ATE0
OK
> AT+CPIN?
+CPIN: SIM PIN
OK
> AT+CPNNUM
PIN1=3; PUK1=10; PIN2=0; PUK2=10
OK
> AT+CPIN="1234"
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: NETWORK UNLOCKED
OK
> AT+CIMI
722341175366945
OK
> AT+CGMR
LQA0007.1.2_D02B
OK
> AT+CLCK="SC",2
+CLCK: 1
OK
> AT+COPS=3,2
OK
> AT+MODODR?
+MODODR: 2
OK
> AT+BNDPRF?
+BNDPRF: 65535,16383
OK
> AT+CSCA?
+CME ERROR: SIM busy
> AT+CPMS="SM"
+CMS ERROR: 314
> AT+CPMS="SM",,"SM"
+CMS ERROR: 314
> AT+CPBS="SM"
+CME ERROR: SIM busy
> AT+COPS?
+COPS: 0,2,"72234",2
OK
> AT+CSQ
+CSQ: 11,92
OK
> AT+PSRAT
+PSRAT: UMTS
OK
> AT+PSRAT
+PSRAT: HSDPA
OK


---

### Post by adamantivm on 2008-08-10
Here's a slightly better version, the "> " lines are the ones that were sent to the modem, the rest are replies:

> 
> ATE
OK
> ATE0
OK
> AT+CPIN?
+CPIN: SIM PIN
OK
> AT+CPNNUM
PIN1=3; PUK1=10; PIN2=0; PUK2=10
OK
> AT+CPIN="1234"
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: UNKNOWN LOCK ST> ATUS
OK
> AT+NWLCK?
+NWLCK: NETWORK UNLOCKED
OK
> AT+CIMI
722341175366945
OK
> AT+CGMR
LQA0007.1.2_D02B
OK
> AT+CLCK="SC",2
+CLCK: 1
OK
> AT+COPS=3,2
OK
> AT+MODODR?
+MODODR: 2
OK
> AT+BNDPRF?
+BNDPRF: 65535,16383
OK
> AT+CSCA?
+CME ERROR: SIM busy
> AT+CPMS="SM"
+CMS ERROR: 314
> AT+CPMS="SM",,"SM"
+CMS ERROR: 314
> AT+CPBS="SM"
+CME ERROR: SIM busy
> AT+COPS?
+COPS: 0,2,"72234",2
OK
> AT+CSQ
+CSQ: 11,92
OK
> AT+PSRAT
+PSRAT: UMTS
OK
> AT+PSRAT
+PSRAT: HSDPA
OK


---

### Post by momosapiens on 2008-08-11
Hi there,
Having the same problem.
I'm a newby in all this linux world.

Could you guys already solved it ?

TIA

---

### Post by adamantivm on 2008-08-11
I don't have a full recipe, but I was able to make interesting considerable progress:

1) Finally found how to switch the device from USB Storage to USB Modem: the trick was right in from of my eyes:

> julian@betun:~$ sudo usb_modeswitch -v 0x1c9e -p 0x1001 -V 0x1c9e -P 0x6061 -m 0x05 -M "55534243123456780000000000000606f50402527000000000000000000000"

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.4 (C) Josua Dietze 2008
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
Looking for default devices
 Found default devices (1)
Prepare switching, accessing latest device
Looking for active default driver to detach it
 OK, driver found ("usb-storage")
 OK, Driver "usb-storage" successfully detached
Setting up communication with device
Trying to send the message
 OK, message successfully sent.
-> See /proc/bus/usb/devices (or call lsusb) for changes. Bye

2) Dialing worked, though not sure why!!? Here is the wvdial.conf configuration:

> [Dialer Defaults]
#Created by wvdialconf:
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init1 = ATE
Init2 = ATE0
#Init3 = AT+CPIN="1234"
#Init2 = AT+CGDCONT=1,"ip","medinet.ma"
Modem = /dev/ttyUSB0
Phone = *99#
Idle Seconds = 300
Modem Type = USB Modem
Stupid Mode = 1
Compuserve = 0
Baud = 460800
Auto DNS = 1
Dial Command = ATDT
Ask Password = 0
ISDN = 0
Username = gprs
Password = gprs


I have to play running 'wvdial' several times. Typically I have to uncomment 'Init3' for the first run but, if it fails, I can only retry after commenting 'Init3' again. Here goes an example run:

Try 1: Init3 NOT commented:

> julian@betun:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE
ATE
OK
--> Sending: ATE0
ATE0
OK
--> Sending: AT+CPIN="1234"
OK
--> Modem initialized.
--> Idle Seconds = 300, disabling automatic reconnect.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Aug 11 22:15:09 2008
--> Pid of pppd: 3057
--> Using interface ppp0
--> pppd: &#65533;o&#65533;&#65533;P&#65533;[06][08]@&#65533;[06][08]
--> pppd: &#65533;o&#65533;&#65533;P&#65533;[06][08]@&#65533;[06][08]
--> pppd: &#65533;o&#65533;&#65533;P&#65533;[06][08]@&#65533;[06][08]
--> pppd: &#65533;o&#65533;&#65533;P&#65533;[06][08]@&#65533;[06][08]
--> Disconnecting at Mon Aug 11 22:15:46 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


Try 2, 'Init3' is now commented out:


> julian@betun:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE
OK
--> Sending: ATE0
ATE0
OK
--> Modem initialized.
--> Idle Seconds = 300, disabling automatic reconnect.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Aug 11 22:16:14 2008
--> Pid of pppd: 3098
--> Using interface ppp0
--> Disconnecting at Mon Aug 11 22:17:03 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.



Third one is the charm, also with 'Init3' commented out:

> julian@betun:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE
OK
--> Sending: ATE0
ATE0
OK
--> Modem initialized.
--> Idle Seconds = 300, disabling automatic reconnect.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Aug 11 22:17:25 2008
--> Pid of pppd: 3143
--> Using interface ppp0
--> local  IP address 172.22.135.108
--> remote IP address 10.64.64.64
--> primary   DNS address 172.25.7.6
--> secondary DNS address 172.25.7.7


Now I just need to polish all this to make it intelligible and simpler. Any advice, of course, appreciated.

---

### Post by Nick Lake on 2008-08-12
Your way is probably better but I found another way of disabling the flash disk mounting (therefore allowing the USB modem to be detected. I've not tried it and I'm afraid I didn't keep the ref to the original web site but here is the text that I originally cut and paste:

-----------------------------------------------------------------------
There is apparently a way of keeping USB mounting but disabling it specifically for the BandLuxe USB Modem. I haven't however managed to get this to work. Here's an extract about how this would work for the BandLuxe C100 Modem:

Adding a file called /etc/hal/fdi/preprobe/10-bandrich-c100.fdi (I think you'll need to put it there with root privileges) with the following contents forces the dynamic device mounting software higher up the tree to ignore the fake CD-ROM on the modem, and the bus resets don't occur. Here's the file:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device> 
<match key="usb.vendor_id" int="6797">
<match key="usb.product_id" int="4096">
<merge key="info.ignore" type="bool">true</merge>
</match>
</match>
</device>
</deviceinfo>

This very simple code simply instructs HAL to tell other software to ignore a device with vendor id (integer) 6797 and product id (integer) 4096. To get it working immediately just reset the DBUS system via sudo /etc/init.d/dbus restart.
-----------------------------------------------------------------------

You will need to find the usb.vendor_id and usb.product_id for your specific device.

If anyone tries this out and gets it to work - let me know.

- Over

---

### Post by adamantivm on 2008-08-12
Hi Nick,

Thanks for that tip. I think I understand what it is supposed to do.

I'm curious, once you get the HAL to not use the device as a USB Storage, can you actually manage to get it loaded by usbserial and use it successfully as a modem?

In my case (Alcatel OneTouch X030) I found that I had to send a command to the device to get it to switch into a USB Modem, otherwise it never worked despite my efforts with HAL.

Regards,
Julian

---

### Post by Nick Lake on 2008-08-13
Yeah I'm not sure... I haven't tried this myself... I'll get around to it soon (hopefully). My last post on this thread was something I found on the web when I had a similar problem... According to the guy who originally posted it - it worked for him.

If you give it a go and it works let me know.

-Nick

---

### Post by gonkyouka on 2009-05-02
> **Nick Lake said:**
> Your way is probably better but I found another way of disabling the flash disk mounting (therefore allowing the USB modem to be detected. I've not tried it and I'm afraid I didn't keep the ref to the original web site but here is the text that I originally cut and paste:

-----------------------------------------------------------------------
There is apparently a way of keeping USB mounting but disabling it specifically for the BandLuxe USB Modem. I haven't however managed to get this to work. Here's an extract about how this would work for the BandLuxe C100 Modem:

Adding a file called /etc/hal/fdi/preprobe/10-bandrich-c100.fdi (I think you'll need to put it there with root privileges) with the following contents forces the dynamic device mounting software higher up the tree to ignore the fake CD-ROM on the modem, and the bus resets don't occur. Here's the file:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device> 
<match key="usb.vendor_id" int="6797">
<match key="usb.product_id" int="4096">
<merge key="info.ignore" type="bool">true</merge>
</match>
</match>
</device>
</deviceinfo>

This very simple code simply instructs HAL to tell other software to ignore a device with vendor id (integer) 6797 and product id (integer) 4096. To get it working immediately just reset the DBUS system via sudo /etc/init.d/dbus restart.
-----------------------------------------------------------------------

You will need to find the usb.vendor_id and usb.product_id for your specific device.

If anyone tries this out and gets it to work - let me know.

- Over

sorry about a noob question but where should i put that file?

ive been trying to solve thing in [this thread]("http://locoteam.ubuntuforums.org/showthread.php?t=976435") but still no luck atm..


-gon

---

### Post by lupa18 on 2009-11-16
Hi all... I have the same Modem in Karmic Koala... and I couldn't make it works.... 

Here is the messages: 


```
Nov 16 18:33:36 frida kernel: [  164.068035] usb 6-2: new full speed USB device using uhci_hcd and address 2
Nov 16 18:33:36 frida kernel: [  164.230183] usb 6-2: configuration #1 chosen from 1 choice
Nov 16 18:33:36 frida kernel: [  164.465819] Initializing USB Mass Storage driver...
Nov 16 18:33:36 frida kernel: [  164.466754] scsi5 : SCSI emulation for USB Mass Storage devices
Nov 16 18:33:36 frida kernel: [  164.466923] usbcore: registered new interface driver usb-storage
Nov 16 18:33:36 frida kernel: [  164.466926] USB Mass Storage support registered.
Nov 16 18:33:36 frida kernel: [  164.576115] usb 6-2: USB disconnect, address 2
Nov 16 18:33:38 frida kernel: [  166.056037] usb 6-2: new full speed USB device using uhci_hcd and address 3
Nov 16 18:33:38 frida kernel: [  166.214182] usb 6-2: configuration #1 chosen from 1 choice
```

at the beginning.. 

```
sudo usb_modeswitch -v 0x1c9e -p 0x1001 -V 0x1c9e -P 0x6061 -m 0x05 -M "55534243123456780000000000000606f50402527000000000000000000000"
```

 tell me: 

```
Looking for target devices ...
No devices in target mode or class found
Looking for default devices ...
Found default devices (1)
Accessing device 004 on bus 006 ...
Using endpoints 0x05 (out) and 0x84 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
OK, driver found ("usb-storage")
OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
Vendor String: USBModem
Product String: Disk           
Revision String: 1.00
-------------------------

Device description data (identification)
-------------------------
Manufacturer: USB Modem
Product: USB MMC Storage
Serial No.: 000000000002
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x05 ...
OK, message successfully sent
Device is gone, skipping further steps ...
-> Run lsusb to note any changes. Bye.
```


but now I get and error instead those messages. 

Finally: 

```
sudo wvdialconf create

Editing `create'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3  

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
```

Any idea?

---

