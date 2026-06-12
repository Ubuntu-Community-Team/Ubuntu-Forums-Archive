---
title: "USB IR receiver device appears and disappears"
date: 2010-04-06
forum: Hardware
---

### Post by christer_f on 2010-04-06
I'm running Ubuntu 9.10 (Linux ubuntu 2.6.31-20-generic #57) and I'm trying to get a new IR receiver to work with LIRC. My current receiver from IguanaWorks works fine.
The new receiver comes with an IR remote for the Sony PS3 DVD player.

When I plug in the receiver it TEMPORARILY shows up with lsusb and in the /proc/bus/input/devices, but after about 15 seconds it disappears from both and will not appear again until I unplug and plug it in again.

While it appears, this is what I see:

```

lsusb ->
Bus 003 Device 005: ID 1130:0202 Tenx Technology, Inc.
```


```

cat /proc/bus/input/devices ->

I: Bus=0003 Vendor=1130 Product=0202 Version=0110
N: Name="Compx Game Controller"
P: Phys=usb-0000:00:04.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.0/input/input11
U: Uniq=
H: Handlers=event9 js0 
B: EV=1b
B: KEY=fff00000000 0 0 0 0
B: ABS=3002f
B: MSC=10

```

dmesg returns the following information when I plug in the device. As can be seen from the last line, it gets disconnected.

```

dmesg ->

[ 5158.360043] usb 3-3: new low speed USB device using ohci_hcd and address 7
[ 5158.588319] usb 3-3: configuration #1 chosen from 1 choice
[ 5158.607394] input: Compx Game Controller as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.0/input/input15
[ 5158.607748] generic-usb 0003:1130:0202.000A: input,hidraw3: USB HID v1.10 Joystick [Compx Game Controller] on usb-0000:00:04.0-3/input0
[ 5164.630425] usb 3-3: USB disconnect, address 7

```

Any hints?

  -- christer

---

### Post by dino99 on 2010-04-06
i've no experience with this kind of hardware but i wonder how much power its need to work properly ( if it need more power than it receive it can be a problem)

---

### Post by christer_f on 2010-04-06
Thanks for this idea, Dino, I have now tried to connect through a powered USB hub, but the result is the same, so unfortunately lack of power is not the explanation..

---

### Post by linux-trap on 2010-04-15
Hello
You have to pair your remote to the receiver, hold your remote up to your receiver and keep one button down, do this just after you plug in the receiver.
It worked for me.

PS
It is also explained in the user manual for your remote......

---

### Post by christer_f on 2010-04-18
Thanks linux-trap for this suggestion. But I believe you are referring to a Bluetooth remote control. I'm trying to use the USB receiver for an infrared remote. The one that can be used to control the DVD in the PS3.

---

### Post by linux-trap on 2010-05-16
Looks like the latest updates for 10.04 have solved some of the problems.
Now when i press a button it show up in the "lsusb list". then as you say it disconnect after 10-15 sec but now it reconnect when i press a button. But, the USB ID is counting up every time you press a button, that can not be right.  

christer_f
I have been talking about the IR-remote all the time, I just refer to the manual that state the usb receiver will connect the first time when a button is pressed and then change the steady light to a blinking light, this to confirm that the receiver is ready for use.

Have any managed to used this IR remote receiver under Ubuntu 10.04?
[I]
Bus 002 Device 006: ID 1130:0202 Tenx Technology, Inc.  [/I]

---

### Post by boko-lnx on 2010-05-31
I have the same problem.
I bought &#8220;SPEEDLINK SL-4435-SBK&#8221; PS3 IR RemoteControl with USB receiver.
My intention was to use it with XBMC on Linux /Ubuntu/, but I get the same problem as described in previous post.
It's appear and disappear from dmesg and lsusb on every button press.

Can it be a normal behavior for devices dedicated to PS3 ?

Here is a detail info for my device:
 lsusb -v -d 1130:0202
```

Bus 005 Device 029: ID 1130:0202 Tenx Technology, Inc. 
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

```

---

### Post by boko-lnx on 2010-06-01
Hi again,
I succeed to read some scan codes with my RC

```

boris-lnx:~/RC-PS3 # ./readEvent /dev/input/event7
scancode BTN_BASE4 (0x129)
type 1 code 297 value 1

scancode BTN_BASE4 (0x129)
type 1 code 297 value 1

scancode BTN_BASE (0x126)
type 1 code 294 value 1

scancode BTN_BASE2 (0x127)
type 1 code 295 value 1

scancode BTN_BASE (0x126)
type 1 code 294 value 1

scancode BTN_BASE4 (0x129)
type 1 code 297 value 1

scancode BTN_THUMB2 (0x122)
type 1 code 290 value 1

scancode BTN_JOYSTICK (0x120)
type 1 code 288 value 1

scancode BTN_THUMB2 (0x122)
type 1 code 290 value 1

scancode BTN_THUMB (0x121)
type 1 code 289 value 1

scancode BTN_THUMB2 (0x122)
type 1 code 290 value 1


```

Can some body try to repeat my experiment?

Experiment:

1.Discover yours eventX identifier. - connect USB dongle and start pressing RC buttons , meanwhile execute command : ls -la  /dev/input/by-id
In my case there is :
```

... root root   9 2010-06-01 16:11 usb-Compx_Game_Controller-event-joystick -> ..[COLOR="Red"]/event7[/COLOR]
...

```
2.Download and compile experimental event reader from my WS.
```

	cd ~
  	mkdir RC-PS3
	cd RC-PS3/
 	wget [http://85.130.95.169/RC-PS3/rc_ps3-eventReader.tar.gz](http://85.130.95.169/RC-PS3/rc_ps3-eventReader.tar.gz)
 	tar -zxvf rc_ps3-eventReader.tar.gz 
 	gcc -c readEvent.c 
   [COLOR="Lime"]# in some cases you need to add -fPIC for 64bit OS[/COLOR]
 	gcc readEvent.o -o readEvent

```
3.Start pressing RC buttons and then execute: ./readEvent /dev/input/event7


  The reader is very simple program and can't harm your computer. It is fact I took it from here:
[http://stackoverflow.com/questions/2547616/how-can-i-translate-linux-keycodes-from-dev-input-event-to-ascii-in-perl](http://stackoverflow.com/questions/2547616/how-can-i-translate-linux-keycodes-from-dev-input-event-to-ascii-in-perl)


It  is my personal opinion this experiment proves that if we  keep device active it work perfect  and can be used for example with &#8220;lirc&#8221; and &#8220;xbmc&#8221;, the only thing we need to achieve is to keep it active.
 I am planing a small hardware invasion on my USB dongle.

---

### Post by markosjal on 2011-04-15
I picked up one of these cheap and hoped to get it working with XBMC and have now confirmed the same . The device just disappears. 

Any update? 

Seems to work in Windows 7 

Mark

---

### Post by schubert.simon on 2011-10-07
did you solve the problem ?

i think about buying the remote control SL-4435-SBK.:popcorn:


in combination with Logitech 915-000144 Harmony Link
[http://www.amazon.com/Logitech-915-000144-Harmony-Link-Black/dp/B005O81U8Y/ref=sr_1_1?ie=UTF8&qid=1318041703&sr=8-1](http://www.amazon.com/Logitech-915-000144-Harmony-Link-Black/dp/B005O81U8Y/ref=sr_1_1?ie=UTF8&qid=1318041703&sr=8-1)

---

### Post by woket on 2012-01-02
I have a similar device, [PS3 Remote from **** Smith ]("http://dicksmith.com.au/product/YG7381/ps3-remote-with-hdmi-1-8m-cable")(Aussie version of Radio Shack) the local wholesaler (Futuretronics had nothing at all support wise). 

cat /proc/bus/input/devices ->
I: Bus=0003 Vendor=1130 Product=0202 Version=0110
N: Name="YuanChen Game Controller"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5
U: Uniq=
H: Handlers=event5 js1 
B: EV=1b
B: KEY=fff 0 0 0 0 0 0 0 0 0
B: ABS=3002f
B: MSC=10 

I running it on a HP EVO USFF with XBMCLive Dharma ([FONT=Arial][SIZE=2]Ubuntu 10.04.2 LTS) and the device is working flawlessly (For a cheapie)[/SIZE][/FONT]. 
After creating:/usr/share/xbmc/system/keymapsYuanChen.Game.Controller.xml to map the key for XBMC (I'm assuming via LIRC)

The disapearing from the device list sound like a power saving issue eg:ACPI, I'm afraid I not much help on the Linux side of power management but I would check the BIOS setting. 


Searching the device ID, I found this thread plus a range of devices also using same USB Tenx interface chip.

[http://www.gadgets.co.uk/item/USBMISSILE/USB-Missile-Rocket-Launcher.html](http://www.gadgets.co.uk/item/USBMISSILE/USB-Missile-Rocket-Launcher.html)
[http://www.engadget.com/2006/10/04/the-usb-powered-hamster-wheel/](http://www.engadget.com/2006/10/04/the-usb-powered-hamster-wheel/)
[http://www.technoline.eu/details.php?id=1526&kat=5](http://www.technoline.eu/details.php?id=1526&kat=5)
[http://www.latestbuy.com.au/usb-panic-button.html](http://www.latestbuy.com.au/usb-panic-button.html)
[http://nyko.com/products/product-detail/?name=BluWave](http://nyko.com/products/product-detail/?name=BluWave)


Cheers Rod

---

