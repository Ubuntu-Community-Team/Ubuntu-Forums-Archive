---
title: "USB Nyko IR Remote"
date: 2009-02-11
forum: Hardware
---

### Post by ihumanable on 2009-02-11
I've recently got my hands on a Nyko PS3 IR Remote (This is it [http://www.nyko.com/nyko/products/?i=113]("http://www.nyko.com/nyko/products/?i=113"))

It works great with my PS3, I thought it might be possible to use it to control XBMC or Boxee on my Ubuntu-box (Not the PS3, just a vanilla PC running 8.10 64-bit).  I've looked at the lirc project but this doesn't appear to be a supported remote.  I tried anyhow hoping that I could figure out how to configure it.  Suffice it to say, I'm not having much luck, lirc can't see my IR receiver or any of the input from it.

If anyone could point me in the right direction I'd be extremely grateful.

---

### Post by ardinmcallister on 2009-02-13
*bump* 

i'm wondering the same thing.

when i plug mine in, i get this from the Nyko Bluray Remote, in dmesg

[980986.436197] input: Compx Game Controller as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input25
[980986.476167] input,hidraw1: USB HID v1.10 Joystick [Compx Game Controller] on usb-0000:00:13.0-1
[980992.443898] usb 1-1: USB disconnect, address 20

lsusb -v shows it as this:

Bus 001 Device 025: ID 1130:0202 Tenx Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1130 Tenx Technology, Inc.
  idProduct          0x0202 
  bcdDevice            1.00
  iManufacturer           1 Compx
  iProduct                2 Game Controller
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              2 Game Controller
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     101
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
        bInterval              32
Device Status:     0x0000
  (Bus Powered)

seems like it disconnects right away, which is unfortunate. I'm trying to type fast enough to send it the "on" command to the usb channel, but it doesnt look like i can catch it.


any ideas guys? if anyone could help, or even point me in the right direction, that'd be great.

---

### Post by MaximillionSterling on 2009-03-04
From what I can tell testing with Ubuntu and Windows 7, the device unmounts when the light goes out. Windows 7 sees it a game controller as of yet I have nothing installed to test functionality though.

---

### Post by doobiest on 2010-02-02
Did anyone figure this out?  I bought one today thinking it would work with little effort.  I can't find anything online about it.

Mine is actually a intec ps3 remote but the specs come up the same as yours with lsusb, messages etc.

---

### Post by linux-trap on 2010-04-15
Any news about this ps3 ir remote? I open mine to see what IC they have used but its all "home" made so no information to get from the PCB or the IC. Its posible it could work with one of the lirc drivers already out there, but thats a lot of work to find out.

---

### Post by markosjal on 2011-04-16
I wanted to add to this thread as I am trying to get this working with XBMC.

Here is what I have found so far. 

First I posted this:
[http://forum.xbmc.org/showthread.php?t=99415](http://forum.xbmc.org/showthread.php?t=99415)


then I came across this
[http://forum.xbmc.org/showthread.php?p=776903#post776903](http://forum.xbmc.org/showthread.php?p=776903#post776903)

What this second thread enlightened me to was that I had previously observed that the USB dongle seems to unmount from linux when no keys are pressed, but mounts again on the next key press. XBMC does not detect new devices once running but WILL detect a disconnect. This means that once the device unmounts its done.



In conclusion we need to see if there is a way to force this driver to remain active so that it conceals any disconnects from XBMC and always shows the hardware device as connected.

Is there any way to force a joystick driver to load (regardless of device status)  and ignore when the device is disconnected, meanwhile telling all software that the device is there?

---

### Post by markosjal on 2011-10-29
A friend brought me a "Score" branded PS3 remote control today and it behaves exactly like the Blue Wave remote. It Identifies itself as "Compx Game Controller" as I believe the blu wave did too. It says on Back [www.pdp.com](www.pdp.com) S-6350 EU Mini-remote for PS3. It has that same tacky looking metalic strip down one side that the Blue Wave had

Funny thing is  that I have some that look Identical to this one my friend brought me (without the tacky looking metalic strip) and are branded "Perfect Game" by "Perfect Choice", as this is what I can get in Mexico. These perfect choice units do NOT disconnect.

I have also come to find out that the two are not IR compatible with each other.

---

