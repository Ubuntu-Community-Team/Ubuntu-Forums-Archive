---
title: "xbox controller + ubuntu 8.08 64bit"
date: 2008-05-22
forum: Hardware
---

### Post by squirrelplayingtag on 2008-05-22
I just installed hardy 64bit. I plugged in my xbox controller and the first player position lights up and it is recognized by both the system settings manager and my mupen64 but when I press a button nothing happens. "cat /dev/input/js0" also yields no results. I'm wondering if it's a problem because it's the 64bit version?

---

### Post by MaindotC on 2008-05-22
Why would the 64-bit version of Ubuntu be the problem?  All that means is it utilizes 64-bit registers to transfer data and in out of the CPU (which is supposed to be faster).

---

### Post by squirrelplayingtag on 2008-05-23
I'm just throwing my thoughts out there. If there are other programs that don't work as expected on 64bit systems why wouldn't something that depends on a kernel module to not behave as expected?

---

### Post by MaindotC on 2008-05-23
I just don't understand why you thought that was the problem.  I would think this is a driver issue not moving 64-bits of data instead of 32-bits.  Do you see the controller recognized in lspci or lsusb?

---

### Post by squirrelplayingtag on 2008-05-23
Yes

$ lsusb
Bus 001 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller

---

### Post by MaindotC on 2008-05-23
Well Ubuntu seems to recognize it from an electrical standpoint.  My guess is that now it just needs the proper code to communicate with the controller (a driver).  As if you haven't done this already, you'll have to search for a driver.  I'm going to bed :(  GL - I'll check this thread tomorrow.

---

### Post by squirrelplayingtag on 2008-05-23
Is the driver just the xpad module? That's all I've been able to find.

---

### Post by MaindotC on 2008-05-23
I'm not familiar with connecting this controller, but I searched for your suggestion and that seems to be a good bet.  I'm still a little puzzled that you plug it in and it's recognized and lights up but is still inoperable.  The thread to install the driver, which you probably found already, is a [Gentoo wiki]("http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux") but it's a start.  Do you have a test environment to try conducting this procedure?

---

### Post by squirrelplayingtag on 2008-05-23
Well one of the reasons I decided to upgrade to hardy was the inclusion of the xpad module by default. 

```

dave@dave-laptop:~$ locate xpad
/lib/modules/2.6.24-16-generic/kernel/drivers/input/joystick/xpad.ko
/usr/share/app-install/desktop/xpad.desktop
/usr/share/app-install/icons/xpad.png
/usr/src/linux-headers-2.6.24-16-generic/include/config/joystick/xpad
/usr/src/linux-headers-2.6.24-16-generic/include/config/joystick/xpad.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/joystick/xpad/ff.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/joystick/xpad/leds.h

```

Here are the modules that get loaded when I plug it in:
```

dave@dave-laptop:~$ lsmod | grep xpad
dave@dave-laptop:~$ lsmod | grep xpad
xpad                   13704  0
led_class               7176  1 xpad
ff_memless              7688  1 xpad
usbcore               169904  5 xpad,usbhid,ehci_hcd,uhci_hcd

```

```

dave@dave-laptop:~$ sudo tail -f /var/log/messages
May 23 16:29:31 dave-laptop kernel: [  385.352193] usb 1-1: new full speed USB device using uhci_hcd and address 2
May 23 16:29:31 dave-laptop kernel: [  385.562102] usb 1-1: configuration #1 chosen from 1 choice
May 23 16:29:31 dave-laptop kernel: [  385.705222] Registered led device: xpad0
May 23 16:29:31 dave-laptop kernel: [  385.705275] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
May 23 16:29:31 dave-laptop kernel: [  385.727584] usbcore: registered new interface driver xpad
May 23 16:29:31 dave-laptop kernel: [  385.727592] /build/buildd/linux-2.6.24/drivers/input/joystick/xpad.c: X-Box pad driver:v0.0.6

```


I actually have followed the gentoo howto but had no success. With gutsy the "cat /dev/input/js0" command showed input but under hardy it didn't even recognize the controller anymore.

---

### Post by MaindotC on 2008-05-23
I'm not sure how to help you any further from here.  I wish someone else who uses this controller could contribute!  It seems to me that everything is being properly recognized.  Is there any chance you can re-install the application that interacts with the controller - what appears to be the mupen64?  I see that it's a 64-bit emulator.  Can you try different emulators?  Sorry I'm not of much more technical help - just trying to give you some ideas :(

---

### Post by squirrelplayingtag on 2008-05-23
It's not just mupen that doesn't recognize it. There's also no response from the joystick configuration under system configuration and from jscalibrator even though it shows /dev/input/js0 as an xbox controller.

Thanks for trying to help though!

---

### Post by MaindotC on 2008-05-24
At least I'm learning for when I get a controller :)

---

### Post by squirrelplayingtag on 2008-05-24
I finally got it working!

First I used this file ([http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=49555&d=1194551405](http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=49555&d=1194551405)) instead of the ones from the xpad website and then followed these directions ([http://ohioloco.ubuntuforums.org/showpost.php?p=3752962&postcount=7](http://ohioloco.ubuntuforums.org/showpost.php?p=3752962&postcount=7)). I'm not really sure what is different from what I did before but it works.

---

### Post by MaindotC on 2008-05-24
Wow awesome!  Sorry I didn't help you more but I hope it feels good to star yourself :)  I'll never forget this though so if anyone else has a question in the future I know where to direct them.

---

### Post by Falcorian on 2008-06-02
> **squirrelplayingtag said:**
> I finally got it working!

First I used this file ([http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=49555&d=1194551405](http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=49555&d=1194551405)) instead of the ones from the xpad website and then followed these directions ([http://ohioloco.ubuntuforums.org/showpost.php?p=3752962&postcount=7](http://ohioloco.ubuntuforums.org/showpost.php?p=3752962&postcount=7)). I'm not really sure what is different from what I did before but it works.
I had the exact same symptoms on Hardy. lsusb shows it, lsmod shows xpad loaded, but no input from the controller was recognized.

Your fix worked after a reboot, thanks!

---

### Post by Falcorian on 2008-06-06
Bug report up at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/237170](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/237170)

Hopefully they'll update the xpad module in the Kernel soon.

---

### Post by wootah on 2008-06-16
There is also the userspace driver alternative to xpad. This one also allows for wireless controllers, 360 xbox-guitar, regular xbox controllers and additional types.

Please see this [guide for more details]("http://ubuntuforums.org/showthread.php?t=825464") :)

---

