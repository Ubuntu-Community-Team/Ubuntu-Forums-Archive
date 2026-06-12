---
title: "HP 5189urf Multimedia Keyboard: music player keys not working"
date: 2009-04-19
forum: Hardware
---

### Post by J@n on 2009-04-19
Hi all,

I know I am not the only one having trouble with multimedia keys. I have surfed the forum rather extensively but haven't found a thread that solved my problem. So here it is:

I have a HP multimedia keyboard model 5189urf (K).
[[IMG]http://img156.imageshack.us/img156/9223/typeandproductnumber.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=typeandproductnumber.jpg)

I would like all my keys to work under Ubuntu 8.10. I have been able to get the most obvious keys working by selecting a keyboard (Preferences>Keyboard) that matches the 5189. In this case I use a HP Internet Keyboard. This works fine for the "normal" keys (eg. WWW, e-mail etc) but the keys for multimedia (play/pause, next, previous etc) don't work.
[[IMG]http://img156.imageshack.us/img156/3959/keyboardwithkeysindicat.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=keyboardwithkeysindicat.jpg)

I used lsusb to identify the keyboard and by using ```
lsusb -v
``` as root I got this output:
```
Bus 002 Device 002: ID 03f0:0f0c Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x0f0c 
  bcdDevice            1.30
  iManufacturer           1 BTC
  iProduct                2 USB Multimedia Cordless Kit
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
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
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      67
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     209
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

```

Needless to say that changing to any BTC type keyboard hasn't solved my issue.:(

I have tried Keytouch and Lineak but they were both unable to intercept the key codes for the multimedia keys. I have tried to get the codes with *xev* and *dmesg* but there was no output. In other words nothing happened.

I read in a post about acpi-listen but I can't find it or install it. I am not sure if that would help at all since I don't believe it is ACPI related. Could be wrong though.

I have even used the live CD for 9.04 RC but I don't think there is an improvement in that department.

I would really like the multimedia keys to work. If I haven't surfed the forum enough and overlooked a solution, please post the link.

If there is any information you need to analyze my problem (TIA) please let me know.

Any help greatly appreciated.

Greetz,

J@n

---

### Post by fetuszero on 2009-05-20
I'm having the same issue but with different keys, and funny enough, my keyboard is the same as yours from the pictures but sports a different model number which is KB0911, probably because I am in Canada instead of the UK (or so I think from your model number).

The keys that do not work for me are:
On the left side: HP Club; Web Browser; Help
On the right side: Eject disc 1; Eject disc 2; Record

All the rest works accordingly. It would be nice getting the Eject Disc key and the Web Browser one to work.

My play/pause;stop;next/previous track keys didn't work in Amarok, but I got them working by downloading the "Gnome Multimedia Key's" script in Amarok, so if you use it, give it a try. Otherwise I don't know how to solve the problem for other apps.

Gotta keep in mind that I use Hardy though, but soon enough I'm upgrading to Jaunty, don't know if it makes a big difference concerning those key issues.

I'll stick around this thread as well to see if anyone comes up with a solution to getting every keys working, could be helpful for me as well since the ones I mentioned do not show any output in XEV.

---

