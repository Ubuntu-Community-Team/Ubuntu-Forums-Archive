---
title: "calibrate tablet Trust eBrush on Ubuntu 12.04 Precise  [SOLVED]"
date: 2013-05-10
forum: Hardware
---

### Post by enpipes on 2013-05-10
Hello
It's my first thread, so sorry for the posible errors.
I have now a graphic tablet Trust eBrush Widescreen 17939. It works with Wizardpen, but the pen work before touch the surface of the tablet (at 5 mm. approx.), and the 2 buttons are unables. I've tested several helps from other threads about Trust tablets, but I'm at the same point.
  Here is some requested info:

Bus 004 Device 002: ID 172f:0505 Waltop International Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x172f Waltop International Corp.
  idProduct          0x0505 
  bcdDevice            1.07
  iManufacturer           1          WALTOP   
  iProduct                2  Batteryless Tablet 
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
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     335
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
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               4
Device Status:     0x0000
  (Bus Powered)

May you help me, please?
Thanks!

---

### Post by yusuke494 on 2013-05-12
Hi enpipes,

I'm developing Linux kernel driver for Waltop graphic tablet. 
I hava just added Waltop Venus tablet (equal to Trust eBrush) support to my driver using information which you have provided.
But I can't tell if it works correctly or not because I don't have Trust eBrush tablet. 
If it's OK with you, Please try my driver.

How to use
1. Install build-essential package[INDENT]sudo apt-get install build-essential
[/INDENT]
 2. Download & build driver[INDENT]wget [http://yusuke494.web.fc2.com/waltop/files/waltop-0.0.6beta.tar.gz](http://yusuke494.web.fc2.com/waltop/files/waltop-0.0.6beta.tar.gz)
  tar zxvf waltop-0.0.6beta.tar.gz
  cd waltop-0.0.6beta
  make
[/INDENT]
 3. Install driver[INDENT]chmod +x waltop.sh
  sudo ./waltop.sh unbind
  sudo insmod waltop.ko
[/INDENT]
 
See also [http://yusuke494.web.fc2.com/waltop/english/install.html](http://yusuke494.web.fc2.com/waltop/english/install.html)

---

### Post by enpipes on 2013-05-12
Done, Yusuke424. I've uninstalled the previous driver and installed yours.
It works, but, well, I'm at the same point: I can't calibrate the touching of the pencil, than occours approx. at 5 mm. from the surface of the tablet.
 With other drivers I've tryed to change the value of Zmin & Zmax (in  Aiptek.conf and Wacom.conf respectively),
but don't improve that problem.
 Thanks a lot anyway. I'm sure I'll achieve this :)

---

### Post by yusuke494 on 2013-05-12
Thank you for your reply.

I have written a test tool for your tablet.
It retrieves the pen position, pressure data, etc. from the tablet directly and show these data.
(It works without any Xorg drivers e.g., Wizardpen, Wacom, Aiptek, ...)

Please check the pen pressure of your tablet with this tool.
If it dosen't change, probably, your tablet has broken down.

How to use
1. Install libusb package[INDENT]sudo apt-get install libusb-1.0-0-dev
[/INDENT]
2. Download & build[INDENT]wget [http://yusuke494.web.fc2.com/waltop/files/waltop0505.c](http://yusuke494.web.fc2.com/waltop/files/waltop0505.c)
[/INDENT]
[INDENT]gcc waltop0505.c `pkg-config --libs --cflags libusb-1.0` -O2 -o waltop0505
[/INDENT]
3. Run[INDENT]sudo ./waltop0505
(Please Maximize the console window to easily view)
[/INDENT]
4. Move the pen at random and check the pressure

---

### Post by enpipes on 2013-05-12
thanks for your work, yusuke494.
the presure without touching the surface (at 2 cm.) is 5. Upper this come back to 0. I must "to eat" that 5 of presure!
A part of this, the tablet works. When the pencil touch the surface the presure go up correctly. Also in Windows (with his driver, of course) runs OK.
Reading about I've seen a posible problem with the energy of the pencil (too high?), but was about a battery's pencil, is not my case.
Thanks again

---

### Post by yusuke494 on 2013-05-12
OK, enpipes.

I have understood your tablet hasn't broken down.
Please check pressure threshold with Wacom driver as follows.

1. Enable Wacom driver[INDENT]Remove or move **-wizardpen.conf and **-aiptek.conf in /usr/share/X11/xorg.conf.d if exist.
(Don't remove 50-wacom.conf.)
    Check for the presence of the following lines in 50-wacom.conf.

    # Waltop tablets
    Section "InputClass"
        Identifier "Waltop class"
        MatchProduct "WALTOP"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
    EndSection
[/INDENT]
 
2. Reboot your PC
3. Enable my kernel driver[INDENT]sudo ./waltop.sh unbind
    sudo insmod waltop.ko
[/INDENT]
 4. Run "xsetwacom --list devices"[INDENT]If Wacom driver and my driver are active, it outputs the following message.
    "WALTOP Venus Battery Free Tablet stylus   id: xx"
[/INDENT]
 5. Run "xsetwacom --get xx Threshold"[INDENT]The xx is above id and it returns current pressure threshold.
[/INDENT]
 
After that, calibrate threshold value with "xsetwacom --set xx Threshold yy".
(The xx is stylus id, The yy is new threshold value.)

If it still dosen't work correctly, I have no idea, sorry.

---

### Post by enpipes on 2013-05-12
Great!! You are great, man!! SOLVED !
The tablet works fine, with his correct pressure. The 2 buttons work right too.
I have the tablet from 3 weeks ago, but seems I've buyed today :)

An appointment for everybody in the same case: the thereshold of the tablet is 2048.
Was dificult to find that in the especifications of the product.

If you need any time any graphic, I'll do for you, yusuke494 (please)
You can see my humble (now upgraded:) skills in my web site:
[http://www.aldeaglobal.net/enpipes/index_en.html](http://www.aldeaglobal.net/enpipes/index_en.html)
I hope you use this service.
Thanks again

P.D.: well, now I don't find how to mark this thread SOLVED...

---

### Post by enpipes on 2013-05-13
Yep!
Not totally SOLVED (or info about not completed).
Your driver works OK, if I enable it.
May I make it works at startup of Ubuntu?
(I suppose the way is not to add waltop.ko at startup programs list)
May I fix it?
Thanks a lot

---

### Post by yusuke494 on 2013-05-14
I have written new waltop-0.0.6beta2 drvier.
This driver becomes active automatically when you plugged your tablet.  
So you need not "sudo ./waltop.sh unbind" and "sudo insmod waltop.ko".

How to install:
```

wget [http://yusuke494.web.fc2.com/waltop/files/waltop-0.0.6beta2.tar.gz](http://yusuke494.web.fc2.com/waltop/files/waltop-0.0.6beta2.tar.gz)
tar zxvf waltop-0.0.6beta2.tar.gz
cd waltop-0.0.6beta2
make
sudo make install
``` 

After that, edit "/usr/share/X11/xorg.conf.d/50-wacom.conf" as follows to assign threshold. (root access needed)
```

# Waltop tablets
Section "InputClass"
  Identifier "Waltop class"
  MatchProduct "WALTOP"
  MatchIsTablet "on"
  MatchDevicePath "/dev/input/event*"
  Driver "wacom"
  Option "Threshold" "xx"   <---- Add this line and replace xx with proper threshold 
EndSection
``` 

Finally, reboot your PC. You need not "xsetwacom --set id Threshold xx" too.

How to uninstall:
```
sudo make uninstall
```

!!! IMPORTANT !!!
* This beta2 driver works on Ubuntu 12.04, but on 13.04, has some problems (On 12.10, I don't know, I haven't tried it yet). 
* Please build & install again as follows when you updated Linux kernel.

```

cd waltop-0.0.6beta2
sudo make uninstall
make clean
make
sudo make install
```


Maybe, you can use your tablet by assigning proper threshold without my driver.
If you don't use my driver, "usbhid" driver is used automatically.
But the usbhid driver supports only low resolution mode (2000 lines/inch).
My driver supports high resolution mode (4000 lines/inch).
(Actually, I can't feel the difference between these drivers ...)

---

### Post by enpipes on 2013-05-15
Run fine, thanks very much, yusuke494
With your clear instructions was easy.
The tablet go on from the startup.
I think now this thread is solved.
Thanks again.

---

### Post by enpipes on 2013-07-31
Hi, yusuke494
I hope you find this reply, than I put here for the tablet specifications:

My tablet 'Trust e-Brush' (than was appearing with the name 'WALTOP     Batteryless Tablet') don't work, and don't appear with 'grep -i name /proc/bus/input/devices'. All from yesterday when the linux kernel was actualized.
 Thanks to you was working fine from when I bought it. So I hope you can help me again.

You advise me than if this happen, I only need to reload your driver writing:
sudo ./waltop.sh unbind
sudo insmod waltop.ko
When I enter the 1st line the output is:
sudo: ./waltop.sh: command not found

I'm sad:( by my wonderfull tablet, help, please
Thanks

---

### Post by enpipes on 2013-07-31
Hi, yusuke494
I hope you find this reply, than I put here for the tablet specifications:

My tablet 'Trust e-Brush' (than was appearing with the name 'WALTOP     Batteryless Tablet') don't work, and don't appear with 'grep -i name /proc/bus/input/devices'. All from yesterday when the linux kernel was actualized.
 Thanks to you was working fine from when I bought it. So I hope you can help me again.

You advise me than if this happen, I only need to reload your driver writing:
sudo ./waltop.sh unbind
sudo insmod waltop.ko
When I enter the 1st line the output is:
sudo: ./waltop.sh: command not found

I'm sad:( by my wonderfull tablet, help, please
Thanks

---

