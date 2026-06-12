---
title: "Nuscan 1000U USB Barcode scanner"
date: 2009-03-31
forum: Hardware
---

### Post by keithclark on 2009-03-31
I'm trying to get my Nuscan 100U USB Barcode scanner to work under 8.10 or 9.04.  It currently works under neither.

I plug it in, it chimes that it is connected.  When I depress the scan button in open air (away from a readable code) the LEDs come on and I can do that repeatedly and the LEDs will come on and off with the hand trigger.

When I try to scan a barcode, the light will come on, the scanner beeps that it has read a valid bar code and that is all that happens.  The application never receives the read code, and the scanner no longer functions.  The LEDs will no longer work when the trigger is pressed.  The only solution is to unplug/plug the scanner and then it will only do the same thing again without working.

I have no idea where to begin to troubleshoot this problem.  The manufacturer has no Linux driver and is unwilling to in the future.

Any help would be appreciated.

Thanks,

Keith

---

### Post by JanMalte on 2009-05-03
[B]//edit:
Take a look at [http://ubuntuforums.org/showpost.php?p=776752&postcount=2](http://ubuntuforums.org/showpost.php?p=776752&postcount=2)
Worked well for me[/B]

Hello, i have a similar problem. I use an usb Barcode scanner at my desktop computer. Under Hardy it worked well, but now with Jaunty it doesn't work anymore.

USB keyboard seems to wrk, but USB mouse seems not.
PS2 works fine with mouse and keyboard. Badly i have only the USB Barcode scanner and not an PS2 one.

Is there any solution to fix this problem. Discovered it have to work till monday :( Hope i don't have to by a PS2 one monday morning :(

```
janmalte@leseanreiz:~$ dmesg | tail
[112311.129377] usb 6-2: configuration #1 chosen from 1 choice
[112344.416125] usb 6-2: USB disconnect, address 2
[113039.312123] usb 5-2: USB disconnect, address 3
[115252.020999] usb 5-2: new low speed USB device using uhci_hcd and address 4
[115252.186552] usb 5-2: configuration #1 chosen from 1 choice
[115252.218650] input: USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input13
[115252.243974] generic-usb 0003:15D9:0A33.0003: input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.0-2/input0
[117059.880136] usb 6-2: new low speed USB device using uhci_hcd and address 3
[117060.046554] usb 6-2: configuration #1 chosen from 1 choice
[117083.944150] usb 5-2: USB disconnect, address 4

``````
janmalte@leseanreiz:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 1130:0001 Tenx Technology, Inc.
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
Bus 006 Device 003: ID 1130:0001 Tenx Technology, Inc. 
Device Descriptor:                                     
  bLength                18                            
  bDescriptorType         1                            
  bcdUSB               1.10                            
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0         8                             
  idVendor           0x1130 Tenx Technology, Inc.       
  idProduct          0x0001                             
  bcdDevice            1.00                             
  iManufacturer           0                             
  iProduct                2                             
  iSerial                 0                             
  bNumConfigurations      1                             
  Configuration Descriptor:                             
    bLength                 9                           
    bDescriptorType         2                           
    wTotalLength           34                           
    bNumInterfaces          1                           
    bConfigurationValue     1                           
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
      bNumEndpoints           1                         
      bInterfaceClass         3 Human Interface Device  
      bInterfaceSubClass      1 Boot Interface Subclass 
      bInterfaceProtocol      1 Keyboard                
      iInterface              0                         
        HID Device Descriptor:                          
          bLength                 9                     
          bDescriptorType        33                     
          bcdHID               1.10                     
          bCountryCode            0 Not supported       
          bNumDescriptors         1                     
          bDescriptorType        34 Report              
          wDescriptorLength      78                     
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
        wMaxPacketSize     0x0008  1x 8 bytes           
        bInterval              10                       
cannot read device status, Operation not permitted (1) 
```Seems like it is related to:
[http://ubuntuforums.org/showthread.php?t=126341](http://ubuntuforums.org/showthread.php?t=126341)
[http://ubuntuforums.org/showthread.php?t=137287](http://ubuntuforums.org/showthread.php?t=137287)

---

### Post by feistybird on 2009-05-12
> **JanMalte said:**
> [B]//edit:
Take a look at [http://ubuntuforums.org/showpost.php?p=776752&postcount=2](http://ubuntuforums.org/showpost.php?p=776752&postcount=2)
Worked well for me[/B]

I tried 

$ sudo modprobe usbkbd

But it says:

$ FATAL: Module usbkbd not found.


My kernel version: 2.6.30-020630rc4-generic

Any ideas?

Thanks!

---

### Post by keithclark on 2009-06-09
I found the following information on Ubuntu Community site:

---------------------------------------------------------------

ADESSO CCD Contact Barcode USB Scanner

    *

      Only works on systems without USB keyboard and mouse
    * 7.10 sees it as a USB HID v1.00 Keyboard, powers it up, but when you scan a valid barcode, it shuts off and doesn't output the barcode.
    * usbkbd.ko was loaded but still didn't work. 

Fix

The trick is to make it be handled by the usbkbd driver which isn't as picky about HID compliance. Inserting the usbkbd module isn't enough to fix it though -- the usbhid driver still grabs it first if you check dmesg.

However if you edit the modprobe blacklist file (/etc/modprobe.d/blacklist) and change the USB-input driver lines to look like this:

#blacklist usbmouse #blacklist usbkbd blacklist usbhid

It works just fine! 

--------------------------------------------------------------
But, my problem is that I'm not sure about the fix.  I tried to edit /etc/modprobe.d/blacklist, but there was no such file.  I created one and now when I do a modprobe usbkbd, I get the following output:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Not sure how to go any further with this solution.  I don't think I'm following the files correctly.

Keith

---

### Post by keithclark on 2009-06-09
> **keithclark said:**
> I found the following information on Ubuntu Community site:

---------------------------------------------------------------

ADESSO CCD Contact Barcode USB Scanner

    *

      Only works on systems without USB keyboard and mouse
    * 7.10 sees it as a USB HID v1.00 Keyboard, powers it up, but when you scan a valid barcode, it shuts off and doesn't output the barcode.
    * usbkbd.ko was loaded but still didn't work. 

Fix

The trick is to make it be handled by the usbkbd driver which isn't as picky about HID compliance. Inserting the usbkbd module isn't enough to fix it though -- the usbhid driver still grabs it first if you check dmesg.

However if you edit the modprobe blacklist file (/etc/modprobe.d/blacklist) and change the USB-input driver lines to look like this:

#blacklist usbmouse #blacklist usbkbd blacklist usbhid

It works just fine! 

--------------------------------------------------------------
But, my problem is that I'm not sure about the fix.  I tried to edit /etc/modprobe.d/blacklist, but there was no such file.  I created one and now when I do a modprobe usbkbd, I get the following output:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Not sure how to go any further with this solution.  I don't think I'm following the files correctly.

Keith

Ok, the trick is to modify /etc/modprobe.d/blacklist.conf as follows:

Change
blacklist usbmouse
to
# blacklist usbmouse

Change
blacklist usbkbd
to 
# blacklist usbkbd

Add
blacklist usbhid

Then, logoff and back on again.

All is well and works perfectly!

Keith

---

### Post by ssokolow on 2009-10-15
I have a variety of USB HID devices so I couldn't use that solution. As a result, I ended up finding a better solution.

The following udev config line let me force the usbkbd driver on my Acan FG-8100 without having to dump all my other USB HID devices.

```

# Force the messy USB CCD barcode reader to use the more lenient usbkbd driver
KERNEL=="event[0-9]*", SYSFS{idVendor}=="04b4", SYSFS{idProduct}=="bca1", ACTION=="add", RUN+="/lib/udev/check_driver usbkbd $devpath $env{ID_BUS}"

```

To use it on your system, adjust the USB vendor and product ID checks as appropriate and then add it to your udev rules. (/etc/udev/rules.d/10-local.rules on my Gentoo box)

Don't worry about incompatibility. /lib/udev/check_driver actually originated on Debian, so if Gentoo has it, everyone probably does.

---

### Post by Stanislas on 2009-12-02
A far better solution for the Acan FG-8100 barcode scanner is to change 

#define USB_DEVICE_ID_CYPRESS_BARCODE_1 0xde61 to 
#define USB_DEVICE_ID_CYPRESS_BARCODE_1 0xbca1 

in linux-source-2.6.xx/drivers/hid/hid-ids.h  
and recompile the usbhid driver and use the new usbhid module. 

Maybe somewhat more difficult, but then it works in Karmic Koala! 

It should be added to the mainstream kernel in my opinion. Any suggestions how to get this scanner added?

---

### Post by Stanislas on 2009-12-03
Good news for those that have the Acan FG-8100 scanner a patch is in the patchqueue for the next kernel update based in the info I passed to the maintainer of the HID drivers.

---

### Post by elzein on 2009-12-04
@Stanislas: It would be nice if you could post instructions on how to rebuild the kernel module without rebuilding the whole kernel.

Thanks

---

### Post by keithclark on 2009-12-07
> **keithclark said:**
> Ok, the trick is to modify /etc/modprobe.d/blacklist.conf as follows:

Change
blacklist usbmouse
to
# blacklist usbmouse

Change
blacklist usbkbd
to 
# blacklist usbkbd

Add
blacklist usbhid

Then, logoff and back on again.

All is well and works perfectly!

Keith

Now in 9.10, you have to reverse all of this back in order for the scanner to work!

Keith

---

### Post by smurfix on 2010-01-16
*Sigh*. Why can't these guys create standards-conforming hardware? It can't be **that** difficult.

(*) the usbkbd driver was removed from the kernel in 2007.

(*) Blacklisting anything is no longer necessary. You can manually bind a device to a driver without affecting the rest of the system. See [http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/) for details.

(*) All of these scanners are not created equal. They all use vendor:product of 1130:0001, but mine only shows as a control endpoint on USB.  No interrupt EP. Therefore no usbhid. :-/ Time to trace whatever Windows is doing with the thing; it does work out of the box there. :(

(*) My scanner is supposed to talk via Bluetooth; their USB adapter is included. I have no idea how to convince the thing to associate with some other adapter, which would probably be the easiest way to connect to it. Oh well.

---

