---
title: "Prolific Technology, Inc. PL2303 Serial Port"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by mkosmo on 2006-12-20
I am running Ubuntu Edgy on a Dell E1705.  I have been banging my head on this for a week now, and have finally thrown in the towel and ego to post on the forum. ](*,) 
So, heres my problem.  I got an Airlink101 AC-USBS, which uses a Prolific PL-2303X chip.  I have this connected to a Sun Ultra 2.  I set up minicom at 9800-8-N-1.  I even ran minicom as root to prevent permissions from being the issue.  No traffic seems to be passed.  I know this machine has worked before, since I used minicom with the same settings on my other machine (which had a serial port) when it was here.  Here is a bunch of diagnostics... any ideas?

One thing I notice, is I think its loading the driver for the PL-2303 and not the PL-2303X.  Could this be the problem?  If so, how do I fix it?

Thanks a bunch!


kosmo@blade:~$ dmesg
...
[17282362.036000] usb 3-1: new full speed USB device using uhci_hcd and address 5
[17282362.196000] usb 3-1: configuration #1 chosen from 1 choice
[17282362.196000] pl2303 3-1:1.0: pl2303 converter detected
[17282362.196000] usb 3-1: pl2303 converter now attached to ttyUSB0

kosmo@blade:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  


kosmo@blade:~$ lsusb -v -d 067b:2303

Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
  bcdDevice            3.00
  iManufacturer           1 Prolific Technology Inc.
  iProduct                2 USB-Serial Controller
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

kosmo@blade:~$ cat /proc/bus/usb/devices 
...
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=067b ProdID=2303 Rev= 3.00
S:  Manufacturer=Prolific Technology Inc.
S:  Product=USB-Serial Controller
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=pl2303
E:  Ad=81(I) Atr=03(Int.) MxPS=  10 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
...

---

### Post by lubod on 2006-12-22
I think I have the regular PL-2303 in a standalone Serial-USB converter, rather than the 2303-X, but I am having some similar problems seeing any communication.

I got a little further than you, by trying other terminal programs besides minicom. Not to say it is bad, I have very little opinion of it, good or bad, I just thought something was going flaky on the software, rather than driver level for me, and I did make some progress.

I installed GTKTerm (from the Dapper Universe repository in my case), and am now getting some primitive input/output going.

At this stage, having turned on local echo, auto CR/LF and the port settings similar to what you used (9600,8N1) I can see stuff coming from my device (a managed switch with serial console) and I can type commands. It takes the commands ok, but does not echo back the result, so if I type exit, I have to force the connection to toggle on/off in some fashion, like changing flow control from RTS/CTS to Xon/Xoff, to see the result.

My problem is I need it to work completely, so I have to figure out what besides flow control might give me results when I type a command without any monkey business.

HTH

---

### Post by mkosmo on 2006-12-22
Nope... That didn't do it.
Airlink101 offers a driver for this device... for 2.4.x.  Too bad it doesn't compile for 2.6.

---

### Post by lubod on 2006-12-22
Sorry to hear that, I guess you really do have driver issues, which I seem to have side-stepped.

When confronted with that sort of problem, I sometimes simply forget the offending device (especially if it's a cheap one) and simply look for one that is known to work in Linux (or Mac OS X, basically anything other than windows). 

Sad that sometimes you have to give up, but maybe one day the hardware manufacturers of the world will wake up to the fact that Microsoft!=IT. Until then you can 'vote with your wallet' as they say by buying only (or at least mostly)  from vendors friendly to the idea that it should work with non-Microsoft products.

For reference, this is the vendor/product ID of my adapter:
Manufacturer:	Prolific Technology Inc.
  Product ID:	0x2303
  Serial Number:	Prolific Technology Inc.
  Vendor ID:	0x067b

---

### Post by mkosmo on 2006-12-22
> **lubod said:**
> 
For reference, this is the vendor/product ID of my adapter:
Manufacturer:	Prolific Technology Inc.
  Product ID:	0x2303
  Serial Number:	Prolific Technology Inc.
  Vendor ID:	0x067b

From reading, even the 2303X will read that if its misidentified.  The 2303X can be seen by looking at this:

kosmo@blade:~$ lsusb -v -d 067b:2303
...
bMaxPacketSize0 64


If its 64, I believe its the X, if not, its not.  Mine shows as a 2303 when its recognized, but from that bMaxPacketSize0, I think its a 2303X (also the product documentation says it is).  I tried to forcefully load the 2303X driver, Ubuntu reloads the usbserial module with the 2303 product.

---

### Post by lubod on 2006-12-22
Well mine says bMaxPacketsize0  = 8 so if your information is correct, I apparently do have the plain 2303, or at least another variant, not the 2303X.

Whatever it is, it certainly is acting flaky, now with 3 different drivers for OS X and the Linux built in one, it has gotten no further than before, at most it let me type commands, but not see the result.

Rather frustrating not knowing if it's a software or hardware or driver problem, even when it seems to be the first, not the other two.

---

### Post by mkosmo on 2006-12-24
Emailed Airlink101 a coupl days ago... still no response from their support.

---

### Post by ubmac on 2006-12-31
Hi,
I installed ubuntu to use a tool not included in windows, and linux is much better the last time I installed linux.
I'm trying to work with a PL-2303X serial adaptar too, and came to this thread.
Found this link [http://koti.mbnet.fi/lonnberg/pl2303x.html](http://koti.mbnet.fi/lonnberg/pl2303x.html) ,
but my problem was not to link to /dev/ttyS0 with the command **ln -sf /dev/ttyUSB0 /dev/ttyS0** :D > The following patch modifies the driver for the Prolific PL-2303 USB-serial adapter to add support for the highly similar but incompatible PL-2303X adapter. The PL-2303X has the same vendor ID and product ID as the older PL-2303, which means that it will be incorrectly detected as a PL-2303 by the driver currently in the Linux kernel. Attempting to use a PL-2303X as a PL-2303 simply results in an inability to transfer data through the serial port. In other words, nothing happens. This patch autodetects whether a PL-2303 or a PL-2303X is used and changes the initialisation sequence accordingly.

The PL-2303X can be distinguished from a PL-2303 by checking bMaxPacketSize0 for the device using lsusb -v -d 067b:2303 (as root). If bMaxPacketSize0 is 64, you probably have a PL-2303X and need this patch.> The main kernel tree includes PL-2303X support starting from 2.6.8 (I can confirm that PL-2303X works on 2.6.11rc2 without my patch), making this patch unnecessary.

Happy new year.

---

### Post by mkosmo on 2006-12-31
> **ubmac said:**
> Hi,
I installed ubuntu to use a tool not included in windows, and linux is much better the last time I installed linux.
I'm trying to work with a PL-2303X serial adaptar too, and came to this thread.
Found this link [http://koti.mbnet.fi/lonnberg/pl2303x.html](http://koti.mbnet.fi/lonnberg/pl2303x.html) ,
but my problem was not to link to /dev/ttyS0 with the command **ln -b /dev/ttyUSB0 /dev/ttyS0** :D 

Happy new year.

I am not currently near my serial adapter, so I will try it when I get back... but you're saying all I need to do is create that backup link and life will work for the PL2303X?

---

### Post by ubmac on 2006-12-31
> **mkosmo said:**
> I am not currently near my serial adapter, so I will try it when I get back... but you're saying all I need to do is create that backup link and life will work for the PL2303X?
It worked for me. :)

---

### Post by mkosmo on 2007-01-06
> **ubmac said:**
> It worked for me. :)

Sadly, this did not work for me :(

---

### Post by aka_bigred on 2007-02-26
Has anyone gotten the PL-2303X working under ubuntu?  I just ordered one off ebay, and it is in fact the X version (the bMaxPacketSize0 =64)

I went to the patch page, but am a little worried of messing things up since I'm newer to linux.  Wanted to see if anyone else had success with it.

Thanks!

---

### Post by mkosmo on 2007-02-26
My friend had it work on his Ubuntu box with no problem.  I couldn't get it working though.  Ignore the patch... its for an older kernel.

---

### Post by edgimar on 2007-03-23
I have one of the PL-2303X devices, and thought it was broken for a while because my Palm Vx could not sync to various software at 115200, 57600, 38400, and 9600 baud.  It turns out, however, that it does work at certain baud rates (i.e. 1200, 4800, and 19200).  So, perhaps one could say that the device or driver is "partly" broken, but does work under certain conditions.

---

### Post by JackRazz on 2007-04-07
mkosmo,
I also have a prolific serial to USB adapter and set this up a few months ago using Edgy and minicom to comminicate with my Tivo.  It worked just fine, good connection, file transfers and all.  

I recently did a clean install of feisty and just got it working with minicom talking to the Tivo.  However, in Feisty, the Devices Manager doesn't recognize the Prolific device by name like it did in Edgy.  I'm currently using a beta of Feisty, so this may change.  Below is a screenshot I took of the Device Manager showing my prolific device in *Edgy*.

[ [IMG]http://www.imagehosting.com/out.php/i441682_ScreenshotDeviceManagerShowingSerialDevice.png[/IMG]](http://www.imagehosting.com)

Here is the screenshot of the minicom settings I used to talk to my Tivo.

[ [IMG]http://www.imagehosting.com/out.php/i441735_SerialPortSettings.png[/IMG]](http://www.imagehosting.com)

In there you can see the tty device name I used.  So, if the device manager is showing a different name for the Prolific (includes the X) at the level I took that screenshot, then its probably recognizing it wrong.

I don't think it will help you, but I'm still a bit new to linux, and thus decided  to post it anyway.

I'm going to try and get mine working again under feisty, and I'll let you know.

JackRazz

---

### Post by dptxp on 2007-10-04
Anyone tried Silabs CP-2101 or CP-2102 ?

---

### Post by MrMasterplan on 2007-10-07
Hi there,
I think I have definitely come to the right thread. I have bought one of those PL-2303 Usb to serial adapters on ebay. It works fine on windows, and I was hoping to get it to run on Ubuntu. I tried to simply run the 'make inst' on one of the Redhat drivers, but unsurprisingly all I get is a very long list of errors. Since my knowledge of linux is quite limited, my progress ends here.
I have read that some of you have got this device to work with Ubuntu. I would be _really_ grateful if one of you could step me thorough the installation, or even just nudge me in the right direction to get started.  
Thanks a lot guys.
Simon :)

---

### Post by littlemaple on 2007-11-14
Hi, I have the same problem. Is there a way how to install drivers on debian-like systems? Prolific provides only something for red hat...

---

### Post by cogvos on 2007-11-26
Hi all,

I have no idea if this helps anyone, it doesn't me...

I have the PL2302 version on which I have hung a 56k modem (as my pc does not have a serial port). This works fine in Windowz and also OpenSuse 10.3, though it is very slow connecting to the internet via this. I am guessing that the reason it works is because suse and redhat are RPM based and Ubuntu is not (?) Is there not an RMP->APT converter somewhere? I'm sure I saw one.

Oddly lsusb lists the Prolific as follows

BUS01 DEV 04 Prolific Technology inc PL230 ....

So Ubuntu can see it, but for whatever reason not beyond it (to the modem)

Has anyone any ideas how to progress?

J.

---

### Post by Keith_Beef on 2007-12-28
Well, I have an Optimus Mini 3 (OM3) that uses a Prolific PL2303 but I don't know which variant...

And I have a USB to Serial adapter on the way to me, too... so I have two good reasons for being interested in this thread.

Please tell me, how to find out which variant of the PL2303 I have...

The lsusb command sees it like this:

```
$ uname -a
Linux Saturn 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
$ lsusb 
Bus 002 Device 002: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:2111 Broadcom Corp. 
Bus 001 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. 
Bus 004 Device 001: ID 0000:0000  

```

I know that the OM3 device is OK; I've used it on a Windows XP box at work, and I even had the keys display an image using the OpenOptimus configurator.

But development on that project seems to have fizzled out some time ago, and the program is practically useless other than as a demonstration that it is possible to get the OM3 to work.

Being hopeless at programming in C, I was hoping to get somewhere with the python-serial package that I installed tonight. 

Beef.

---

### Post by zivleyes on 2008-02-14
> **cogvos said:**
> Hi all,

I have no idea if this helps anyone, it doesn't me...

I have the PL2302 version on which I have hung a 56k modem (as my pc does not have a serial port). This works fine in Windowz and also OpenSuse 10.3, though it is very slow connecting to the internet via this. I am guessing that the reason it works is because suse and redhat are RPM based and Ubuntu is not (?) Is there not an RMP->APT converter somewhere? I'm sure I saw one.

Oddly lsusb lists the Prolific as follows

BUS01 DEV 04 Prolific Technology inc PL230 ....

So Ubuntu can see it, but for whatever reason not beyond it (to the modem)

Has anyone any ideas how to progress?

J.


to use RPMs within debian-based distros you need to install a program called alien
```

$ sudo apt-get install alien
```


I've just finished installing Ubuntu Ultimate Edition 1.7 (Gutsy based) on my new Lenovo X61 laptop and I've received from the IT department a "Aten" USB2Serial cable adaptor (prolific chipset)
All I did to get it working on minicom was 
```
sudo tail -f /var/log/messages
```
then plugged the cable in and waited... after a couple of secs this popped up:
```

Feb 14 17:27:55 X61-zivl kernel: [ 3720.244000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Feb 14 17:27:55 X61-zivl kernel: [ 3720.404000] usb 2-1: configuration #1 chosen from 1 choice
Feb 14 17:27:55 X61-zivl kernel: [ 3720.532000] usbcore: registered new interface driver usbserial
Feb 14 17:27:55 X61-zivl kernel: [ 3720.532000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Feb 14 17:27:55 X61-zivl kernel: [ 3720.532000] usbcore: registered new interface driver usbserial_generic
Feb 14 17:27:55 X61-zivl kernel: [ 3720.532000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Feb 14 17:27:55 X61-zivl kernel: [ 3720.544000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
Feb 14 17:27:55 X61-zivl kernel: [ 3720.544000] pl2303 2-1:1.0: pl2303 converter detected
Feb 14 17:27:55 X61-zivl kernel: [ 3720.544000] usb 2-1: pl2303 converter now attached to ttyUSB0
Feb 14 17:27:55 X61-zivl kernel: [ 3720.544000] usbcore: registered new interface driver pl2303
Feb 14 17:27:55 X61-zivl kernel: [ 3720.544000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver

```
Pay attention to the line that says "pl2303 converter now attached to ttyUSB0" that's the device name you need, then I went into minicom setup and changed the serial port settings to be /dev/ttysUSB0, saved and exited.
If you don't have a device to test it, open the minicom using the new settings, take the 9pin end of the cable and short circuit between pins 2 and 3, if you can see what you type, means you closed circuit and you're getting local echo.
Works like charm!
Hope this helps someone.
Ziv

---

### Post by TuxProbe on 2008-03-06
[quote=" zivleyes"]Pay attention to the line that says "pl2303 converter now attached to ttyUSB0" that's the device name you need, then I went into minicom setup and changed the serial port settings to be /dev/ttysUSB0, saved and exited.[/quote]

I'd just want to add, the device mentioned here, might not be what the pl2303.c module states; On my openwrt box its 'hidden' within /dev/usb/tty/X (where x = 0).
 If you're still having problems with newer kernels (should'nt be with Ubuntu though), you might be needing the module itself. The attached file (.ko files) is a tarball of my i686 2.6.23 should work on most architechtures. Do this:
```

sudo -s
cd /lib/modules/`uname -r`/kernel/drivers/usb
tar xfvz <PathToTarBall>serial-usb-drivers-2.6.23.tar.gz
modprobe usbserial
modprobe pl2303

```
NB: You might experience  that the module fails to load and the kernel complains that the module disagrees about a version of some interface - or simply that version magic doesnt match, do:
```

modprobe -f pl2303

```
Now pump minicom up, pipe a divx into it and watch it on your serial modem lcd-display *gG* :popcorn:

---

### Post by tormod on 2008-03-07
The pl2303 module is included in all Ubuntu kernels. Note that any module has to fit exactly to the kernel version.

Another tip for those with applications that don't easily find the port: Add a udev rule that makes a /dev/ttyS4 (~COM5) alias to the USB serial port.

```
$ cat /etc/udev/rules.d/91-usb-serial.rules
ACTION=="add",KERNEL=="ttyUSB*", SYMLINK+="ttyS4"

```

This will generate a /dev/ttyS4 link when you plug in the dongle.

If you use several dongles, you should change the above ttyUSB* to ttyUSB0 and add extra rules for ttyUSB1 -> ttyS5 and so on. If you have only one dongle, the above rule has the advantage that if you replug the dongle quickly and the same dongle now ends up at ttyUSB1, the link is still ttyS4.

Tormod

---

### Post by ThomasNovin on 2008-05-06
My ATEN International Co., Ltd UC-232A Serial Port [pl2303] works out of the box in Ubuntu Hardy/2.6.24-16-generic. Thanks for the tip about udev, works nicely.

---

### Post by shakaran on 2008-06-04
Hi, I have a USB SIM card reader ([http://www.dealextreme.com/details.dx/sku.6641](http://www.dealextreme.com/details.dx/sku.6641)) with PL2303 but it not working.

```
sudo tail -f /var/log/messages

Jun  4 15:45:43 otorion kernel: [ 1707.221771] usb 3-1: new full speed USB device using uhci_hcd and address 5
Jun  4 15:45:44 otorion kernel: [ 1707.256577] usb 3-1: configuration #1 chosen from 1 choice
Jun  4 15:45:44 otorion kernel: [ 1707.266090] pl2303 3-1:1.0: pl2303 converter detected
Jun  4 15:45:44 otorion kernel: [ 1707.266260] usb 3-1: pl2303 converter now attached to ttyUSB0
Jun  4 15:45:45 otorion pcscd: hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 003:005
Jun  4 15:45:45 otorion pcscd: readerfactory.c:1116:RFInitializeReader() Attempting startup of Towitoko Chipdrive USB 00 00 using /usr/lib/pcsc/drivers/towitoko.bundle/Contents/Linux/libtowitoko.so.2.0.0
Jun  4 15:45:45 otorion pcscd: readerfactory.c:949:RFBindFunctions() Loading IFD Handler 2.0
```

```
$ lsusb
Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
```

```
$ sudo lsusb -v -d 067b:2303

Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
  bcdDevice            3.00
  iManufacturer           1 Prolific Technology Inc.
  iProduct                2 USB-Serial Controller
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

Any idea to make it work?

---

### Post by tormod on 2008-06-05
> **shakaran said:**
> Any idea to make it work?
From what you have posted it seems to work, so you have to explain better what there is that doesn't work.

---

### Post by svenbertil on 2008-06-29
Digging up this thread,

I have a GPS that includes a pl2303. It works fine on my old laptop running 2.6.22-14 but on my new shiny X61s running the latest and greatest Hardy with 2.6.24-19 it does not work. I have also tried the -16 kernel with same results.

gpsd is very quiet, xgps show nothing at all. After a while a message shows up in dmesg stating that it was disconnected and then reconnected.

I have a USB key with some older kernel on so I'll try that later today to completely rule out hardware troubles, now however, I need food :)

Addition:
Turns out problem was not with the usb-serial thingy, but rather the gpsd in the repos. Downloaded and built same version running on my old laptop (2.33), and now it works just fine! btw, could not get the svn version of gpsd to compile..

---

