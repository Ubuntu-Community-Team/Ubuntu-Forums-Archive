---
title: "IOGear GUWH104 wireless usb hub and adaptor"
date: 2010-11-06
forum: Hardware
---

### Post by Mr.Transistor on 2010-11-06
i bought this system for the ability to use a really expensive wired mouse and keyboard from a good distance away and it works as a kvm switch aswell allowing the use of said peripherals on up to 3 machines.

i decided i want to use it so i can oporate my ubuntu server aswell... alas they only implemented drivers for win: xp/vista/7
no linux support.... has anyone used this hub?
does anyone know a way to make it work on ubuntu?

---

### Post by Mr.Transistor on 2010-11-07
Bump

---

### Post by Mr.Transistor on 2010-11-09
Bump

---

### Post by Mr.Transistor on 2010-11-12
Bump

---

### Post by Mr.Transistor on 2010-11-22
could it be possable to decompile the drivers and recompile them as whatever linux likes? is there a way to make this work?

---

### Post by Fafler on 2010-11-22
So you brought one of these too? [http://www.iogear.com/product/GUWA100U/](http://www.iogear.com/product/GUWA100U/)

Open a console and type
```

tail -f /var/log/messages
```

Then insert the device and post the output it gives. Also do a

```
lsusb -t 
```

with the transmitter connected to the PC and another device connected to the hub.
That should get us started.
Altering the Windows driver is not really possible or feasible.

---

### Post by Mr.Transistor on 2010-11-23
> **Fafler said:**
> So you brought one of these too? [http://www.iogear.com/product/GUWA100U/](http://www.iogear.com/product/GUWA100U/)

Open a console and type
```

tail -f /var/log/messages
```Then insert the device and post the output it gives. Also do a

```
lsusb -t 
```with the transmitter connected to the PC and another device connected to the hub.
That should get us started.
Altering the Windows driver is not really possible or feasible.
why you also bought one?
```
Nov 23 01:35:18 matrix kernel: [86694.861425] usb 1-2: configuration #1 chosen from 1 choice
Nov 23 01:35:18 matrix kernel: [86694.861734] i1480-dfu-usb 1-2:1.0: firmware: requesting i1480-pre-phy-0.0.bin
Nov 23 01:35:18 matrix kernel: [86694.875688] i1480-dfu-usb 1-2:1.0: firmware: requesting i1480-usb-0.0.bin
Nov 23 01:35:18 matrix kernel: [86694.884043] i1480-dfu-usb 1-2:1.0: firmware: requesting ptc-0.0.bin
Nov 23 01:35:18 matrix kernel: [86694.891556] i1480-dfu-usb: probe of 1-2:1.0 failed with error -2

```for the lsusb -t:
```

~$ lsusb -t
1-2:1.0: No such file or directory
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 2: Dev 5, If 0, Class=vend., Driver=, 480M

```
what can we do with this data bro?

---

### Post by Fafler on 2010-11-23
No, i just looked at their website.

The /var/log/messages part tells us it's looking for a firmware file. This is very common, as some USB devices comes without a "real" ROM and depends on a bootloader that receives the firmware from the host each time the device is powered up. First of all, it tells us that the driver is there and it is able to communicate with the device.

There's a firmare file here: [http://www.linuxuwb.org/thewiki/Firmware_for_the_Intel%28r%29_Wireless_UWB_Link_1480](http://www.linuxuwb.org/thewiki/Firmware_for_the_Intel%28r%29_Wireless_UWB_Link_1480)
You should extract the files to /lib/firmware and reconnect the device. If you still have trouble with it, you know what to do.

---

### Post by Mr.Transistor on 2010-11-23
> **Fafler said:**
> No, i just looked at their website.

The /var/log/messages part tells us it's looking for a firmware file. This is very common, as some USB devices comes without a "real" ROM and depends on a bootloader that receives the firmware from the host each time the device is powered up. First of all, it tells us that the driver is there and it is able to communicate with the device.

There's a firmare file here: [http://www.linuxuwb.org/thewiki/Firmware_for_the_Intel%28r%29_Wireless_UWB_Link_1480](http://www.linuxuwb.org/thewiki/Firmware_for_the_Intel%28r%29_Wireless_UWB_Link_1480)
You should extract the files to /lib/firmware and reconnect the device. If you still have trouble with it, you know what to do.
thx alot bro. i'll see if this works. i was almost about to give up on it.

---

### Post by Mr.Transistor on 2010-11-24
ok so i have done what you said then i attempted everything that i could to try to make it work, and no such luck. shall i run through the log procedure again and find out whats not talking to what again? also it it helps to know, the hub works in wired mode.

---

### Post by Fafler on 2010-11-25
Yes. It would be nice to see if the firmware file loads. Apart from that, the firmware file seems to be quite old. Maybe you can extract a more recent version from the windows driver package. You should look for three files similar to those you already got, name the exactly the same and put them in /lib/firmware

---

### Post by Mr.Transistor on 2010-11-25
so they might exist on the windows driver disk

---

### Post by Fafler on 2010-11-26
Yes, but probably inside a cab file and they could be names differently. They good thing is that you are unlikely to break things by trying the wrong firmware.

---

### Post by Mr.Transistor on 2010-12-15
> **Fafler said:**
> Yes, but probably inside a cab file and they could be names differently. They good thing is that you are unlikely to break things by trying the wrong firmware.

sorry for going so long with out asking for help again.. lol i have been busy and just put my learning to a halt. so i can pretty much just grab all the firmware files the i can find on this disk and put them in that linux dir. and it will only work if something asks for it rught there shouldnt be any conflicts?

---

### Post by Fafler on 2010-12-16
Yes. You should rename them to match and replace the old files.

Post a ls -la of the contents of both .zip (or .cab) files if you need help.

---

### Post by Mr.Transistor on 2010-12-18
so it turns out there are no compessed files on the disk nor in the running directory on my win machine. it's creepy how bare it is... i am starting to think that it is not going to happen.. and me with only 2 months untill i go to basic training... i guess i might as well give up on this and move into other linux stuff! =] mqaybe get back to teaching myself web lang, like php and java cloud code lol

---

