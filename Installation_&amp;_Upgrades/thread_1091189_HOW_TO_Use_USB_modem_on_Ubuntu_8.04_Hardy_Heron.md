---
title: "HOW TO: Use USB modem on Ubuntu 8.04 Hardy Heron"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by shailendra on 2009-03-09
Below are the steps to use any USB data card on Ubuntu 8.04 Hardy Heron. I have tried these steps with my Reliance NetConnect ZTE MG880 USB modem. But I think this will work on all the USB modems.

1) Mount the USB modem. In most cases we need to manually mount the device.

***COMMAND: "sudo mount -t usbfs usbdevfs /proc/bus/usb"***

[COLOR="Blue"]Note: we can also use "None" option instead of "usbdevfs"[/COLOR]

2) Check whether the card is recognized by the kernel

***COMMAND: "sudo cat /proc/bus/usb/devices"***

You will see bunch of messages. But we need only the data at the end. It looks something like this.

[COLOR="DarkRed"][...]
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 19 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  **Vendor=19d2 ProdID=fffd Rev= 0.00**
S:  Manufacturer=ZTE, Incorporated
S:  **Product=ZTE CDMA Tech**
[...][/COLOR]

Pen down the "Vendor" and "ProdID"

3) Now modprobe the driver

***COMMAND: "sudo modprobe usbserial vendor=0xXXXX product=0xXXXX"***

Values of "Vendor" and "Product" can be obtained from the response for the command in step 2. For ZTE MG880 "vendor= 0x19D2" and "product = 0xFFD".

4) Give the command "dmesg"

***COMMAND: "sudo dmesg"***

The response will look something like this;

[COLOR="DarkRed"][38360.764000] usbcore: registered new interface driver usbserial
[38360.764000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[38360.940000] usbserial_generic 2-1:1.0: generic converter detected
[38360.940000] usb 2-1: generic converter now attached to ttyUSB0
[38360.940000] usbserial_generic 2-1:1.1: generic converter detected
[38360.940000] usb 2-1: generic converter now attached to ttyUSB1
[38360.940000] usbserial_generic 2-1:1.2: generic converter detected
[38360.940000] usb 2-1: generic converter now attached to ttyUSB2
[38360.940000] usbcore: registered new interface driver usbserial_generic
[38360.940000] drivers/usb/serial/usb-serial.c: USB Serial Driver core[/COLOR]

5) Now edit the wvdial.conf file

***COMMAND: "sudo vi /etc/wvdial.conf"***

[COLOR="DarkRed"][Dialer zte]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = #777
Username = Your phone number
Password = Your phone number or password if any
ISDN = 0
SetVolume = 0
FlowControl = Hardware (CRTSCTS)
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 460800
Stupid Mode = 1[/COLOR]

[COLOR="Blue"]Note: You need to enter all the data as described above.[/COLOR]

6) Run the "wvdial"

***COMMAND: "sudo wvdial Zte"***

[COLOR="DarkRed"]--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sat Mar 3 22:55:20 2007
--> Pid of pppd: 24314
--> Using interface ppp0
--> local IP address 220.226.50.126
--> remote IP address 97.239.2.10
--> primary DNS address 202.138.103.100
--> secondary DNS address 202.138.96.2[/COLOR]

Now you are connected to internet.

7) To disconnect just press ***"Ctrl+c"*** key.

[COLOR="Blue"]***NOTE:** Once you are connected to the internet and if you launch Firefox, it may give offline error message. So, go to "File" menu and uncheck the "Work Offline" option in Firefox. Refresh the page again and it should display the desired webpage.*[/COLOR]

Also, check the internet traffic. This can be done by "System->Administration->Networking". The ethernet interface must be in Roaming mode.

After you have successfully configured the USB modem through steps 1 to 7, next time to connect to the internet you will have to just follow the steps indicated below:
1) Mount the USB modem device.
2) Modprobe the driver
3) Run the "wvdial" to connect to internet
4) Press ***"Ctrl+c"*** key to disconnect.

[COLOR="DarkOrange"]**_To execute the above 3 instructions you can use the attached shell script file._**[/COLOR]

---

### Post by GeorgeVita on 2009-03-09
Hi **shailendra**,

in addition to your very informative post, can you try if works the following "automatic usbserial" (works with my ZTE MF636 on Ubuntu 8.04):

From terminal run: **sudo gedit /etc/udev/rules.d/90-zte.rules**
copy paste the following lines (according to post#4 of [http://ubuntuforums.org/showthread.php?t=665332):](http://ubuntuforums.org/showthread.php?t=665332):)
[B]
ACTION!="add", GOTO="ZTE_End"
#
SUBSYSTEM=="usb", SYSFS{idProduct}=="fffd",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
#
LABEL="ZTE_Modem"
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0xfffd",
MODE="660", GROUP="dialout"
#
LABEL="ZTE_End"
[/B]
Save and Exit from gedit.
Above shown your product id **fffd** instead of **0031** (for my MF636).

After reboot, the modem will "usbserial"ed automatically.
You can check this by listing the new serial ports: **ls /dev/ttyUSB***

Regards,
George

---

### Post by Neo_The_User on 2009-03-09
shailendra, private message one of the forum staff to move this to "Tutorials & Tips" as this belongs there.

---

### Post by shailendra on 2009-03-10
Thanks George. I will surely try your suggestion.

---

### Post by shailendra on 2009-03-10
Hi Neo.

Thanks a lot for your suggestion. I was trying to move this thread to Tutorials but I coundn't find any option to change the category. Please let me know if there is any option to do so, without deleting the current thread.

---

### Post by CArrowsm on 2009-03-12
Hi there, 

I'm following the instructions to get a USB modem working and everything goes smoothly until I try to run wvdial.  

I get the following message:

~$ sudo wvdial Zte
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

I wasn't given a password for my modem just a phone number.  I assume you enter it into the *.conf file without hyphens?  And including the area code?  

Other than that I'm not sure what's missing.  My modem model is ZTE MF636.

Cheers
Cheyenne

---

### Post by shailendra on 2009-03-13
> **CArrowsm said:**
> Hi there, 

I'm following the instructions to get a USB modem working and everything goes smoothly until I try to run wvdial.  

I get the following message:

~$ sudo wvdial Zte
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

I wasn't given a password for my modem just a phone number.  I assume you enter it into the *.conf file without hyphens?  And including the area code?  

Other than that I'm not sure what's missing.  My modem model is ZTE MF636.

Cheers
Cheyenne

Hi Cheyenne,

It seems like, your modem is not detected. Please check if it is properly connected and the details in wvdial.conf file is correct.

Is your zte modem working on windows? In Linux, use the same userId and password, which you are using in windows. 

Also, send me the snapshot of your wvdial.conf file.

---

### Post by ddeepak on 2009-04-22
Hi Shailendra,

I have Reliance NetConnect ZTE AC871 USB Modem of model EC-121. I am trying to install it on Hardy. 
I have gone through the step 1 to 4 , but in step 4 I don't see any ttyUSB* entry.

Actually step 3 doesn't return any thing.
Can you guide me here to setup this USB Modem?

Thanks in Advance,
-deepak


> **shailendra said:**
> Below are the steps to use any USB data card on Ubuntu 8.04 Hardy Heron. I have tried these steps with my Reliance NetConnect ZTE MG880 USB modem. But I think this will work on all the USB modems.

1) Mount the USB modem. In most cases we need to manually mount the device.

***COMMAND: "sudo mount -t usbfs usbdevfs /proc/bus/usb"***

[COLOR="Blue"]Note: we can also use "None" option instead of "usbdevfs"[/COLOR]

2) Check whether the card is recognized by the kernel

***COMMAND: "sudo cat /proc/bus/usb/devices"***

You will see bunch of messages. But we need only the data at the end. It looks something like this.

[COLOR="DarkRed"][...]
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 19 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  **Vendor=19d2 ProdID=fffd Rev= 0.00**
S:  Manufacturer=ZTE, Incorporated
S:  **Product=ZTE CDMA Tech**
[...][/COLOR]

Pen down the "Vendor" and "ProdID"

3) Now modprobe the driver

***COMMAND: "sudo modprobe usbserial vendor=0xXXXX product=0xXXXX"***

Values of "Vendor" and "Product" can be obtained from the response for the command in step 2. For ZTE MG880 "vendor= 0x19D2" and "product = 0xFFD".

4) Give the command "dmesg"

***COMMAND: "sudo dmesg"***

The response will look something like this;

[COLOR="DarkRed"][38360.764000] usbcore: registered new interface driver usbserial
[38360.764000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[38360.940000] usbserial_generic 2-1:1.0: generic converter detected
[38360.940000] usb 2-1: generic converter now attached to ttyUSB0
[38360.940000] usbserial_generic 2-1:1.1: generic converter detected
[38360.940000] usb 2-1: generic converter now attached to ttyUSB1
[38360.940000] usbserial_generic 2-1:1.2: generic converter detected
[38360.940000] usb 2-1: generic converter now attached to ttyUSB2
[38360.940000] usbcore: registered new interface driver usbserial_generic
[38360.940000] drivers/usb/serial/usb-serial.c: USB Serial Driver core[/COLOR]

5) Now edit the wvdial.conf file

***COMMAND: "sudo vi /etc/wvdial.conf"***

[COLOR="DarkRed"][Dialer zte]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = #777
Username = Your phone number
Password = Your phone number or password if any
ISDN = 0
SetVolume = 0
FlowControl = Hardware (CRTSCTS)
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 460800
Stupid Mode = 1[/COLOR]

[COLOR="Blue"]Note: You need to enter all the data as described above.[/COLOR]

6) Run the "wvdial"

***COMMAND: "sudo wvdial Zte"***

[COLOR="DarkRed"]--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sat Mar 3 22:55:20 2007
--> Pid of pppd: 24314
--> Using interface ppp0
--> local IP address 220.226.50.126
--> remote IP address 97.239.2.10
--> primary DNS address 202.138.103.100
--> secondary DNS address 202.138.96.2[/COLOR]

Now you are connected to internet.

7) To disconnect just press ***"Ctrl+c"*** key.

[COLOR="Blue"]***NOTE:** Once you are connected to the internet and if you launch Firefox, it may give offline error message. So, go to "File" menu and uncheck the "Work Offline" option in Firefox. Refresh the page again and it should display the desired webpage.*[/COLOR]

Also, check the internet traffic. This can be done by "System->Administration->Networking". The ethernet interface must be in Roaming mode.

After you have successfully configured the USB modem through steps 1 to 7, next time to connect to the internet you will have to just follow the steps indicated below:
1) Mount the USB modem device.
2) Modprobe the driver
3) Run the "wvdial" to connect to internet
4) Press ***"Ctrl+c"*** key to disconnect.

[COLOR="DarkOrange"]**_To execute the above 3 instructions you can use the attached shell script file._**[/COLOR]

---

### Post by thomman on 2009-05-05
All the steps work fine. Except when i give wvdial I get modem not initialised. I tried wvdialconf but it says modem not found although everything else seems to show that the modem works perfectly.

---

### Post by hallenr on 2009-09-15
This does not work with Ubuntu 9.04, as the commands scanmodem and usbseial are ineffective.:(

---

### Post by Nole1 on 2009-09-16
I have the same problem and it's still actual. just can't find the solution. 

Here are the results of some command under Ubuntu 9.04 from my laptop:

cat /proc/bus/usb/devices

...
T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=**10c4** ProdID=**ea60** Rev= 1.00
S:  Manufacturer=Silicon Labs
S:  Product=CP2102 USB to UART Bridge Controller
S:  SerialNumber=0001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
... 


and here is the file cdma.conf what I made for this modem

#[Dialer Defaults]
# New PPPD=yes
[Modem0]
Modem Type = USB Modem
Modem = /dev/ttyUSB0
Baud = 230400
Setvolume = 0
Dial Command = ATDT
Init1 = ATZ
Flow control=Hardware(CRTSCTS)
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
[Dialer cdma]
Username = â€cdmaâ€
Password = â€cdmaâ€
Phone = #777
Stupid Mode = 1 
Inherits=Modem0
# Ask Password = on 

here is the result of command lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

Here is the result of command 
modprobe acm vendor-0x10c4 product=0xea60
FATAL: Module acm not found.

I do not have more ideas and it is still not working... Please help me somebody 

Tried almost everything up to changing some files in init.d or something from other forums...
Is there any easier way to connect this modems to net?
Forgot to mention modem is ZTE CDMA (Chinese) usb...

---

### Post by GeorgeVita on 2009-09-18
> **Nole1 said:**
> ...Here is the result of command 
modprobe acm vendor-0x10c4 product=0xea60
FATAL: Module acm not found.
...

I am not sure about the name of driver (and also it needs '=' and not '-').
Try listing all drivers including 'acm' in their name: ```
sudo modprobe -l | grep -i acm
```
Also read a similar thread about usbserial driver:
[http://ubuntuforums.org/showthread.php?t=1117781](http://ubuntuforums.org/showthread.php?t=1117781)

Regards,
George

---

