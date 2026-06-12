---
title: "Bug# Bluetooth on Toshiba / Phoenix | need assistance"
date: 2008-06-20
forum: Hardware
---

### Post by marcon00 on 2008-06-20
Finally i figured it out,but how it works, im not sure.
I Got Qosmion F40, with Bios version 1.50 .
My Laptop/Bluetooth is not supported by Omnibook.
What i once noticed that bluetooth icon appeared! And kept disappearing, i was not able to figure it out,untill now.

If in Ubuntu Bluetooth is not working,i turn the switch Off then restart to Vista, turn switch on , then enable it from task bar, restart Vista. At Bios boot,turn switch off  ,wait for Ubuntu to load,after login when everything started, turn the Switch ON , and Bluetooth automatically starts and the icon appears! I tried sending and receiving , works they way it supposed to.

this is what HWinfo got me for bluetooth device:

```

hwinfo --bluetooth
01: USB 00.2: 11500 Bluetooth Device                            
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_930_508_noserial_if2
  Unique ID: 4ajv.wI5dDb1qIN0
  Parent ID: k4bc.yv9QH_etN77
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.2
  SysFS BusID: 1-1:1.2
  Hardware Class: bluetooth
  Model: "Toshiba Bluetooth Device"
  Hotplug: USB
  Vendor: usb 0x0930 "Toshiba Corp."
  Device: usb 0x0508 
  Revision: "19.15"
  Speed: 12 Mbps
  Module Alias: "usb:v0930p0508d1915dcE0dsc01dp01icFEisc01ip00"
  Driver Info #0:
    Driver Status: hci_usb is active
    Driver Activation Cmd: "modprobe hci_usb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (Hub)

```

Any ideas ??

---

### Post by marcon00 on 2008-06-25
*bump*

---

### Post by marcon00 on 2008-07-06
*bump bump*

is like everyone summering ? :P

---

### Post by rplancius on 2008-07-07
How weird it may sound, It worked for me. Running a dual-boot Vista/Ubuntu 8.04 ( becoming an Ubuntu enthousiastic user) HP 8710W and activating the Bluetooth adapter in Vista, also activated it in Ubuntu. Before that there was no Bluetooth device visible. All I did was activating it in Vista (and therefore probably in the bios). I am now able to communicate with my phone. Great post, thanks a lot!

---

### Post by marcon00 on 2008-07-07
hehe :D Glad it worked for someone too !! :) i just wish there would be an easier way to enable bluetooth rather than booting into Vista and goin trough all this process,once u forgot to turn it off before login out from Ubuntu :)

---

### Post by amamdispencer on 2008-07-08
what a crazy solution! I had such a problem and followed your direction and it worked pronto! This is after so much time going from one forum to another and being bombarded with series of commands to type: sudo, apt,aptitude, apt-get... the list is endless.

THANKS MEN!!!

Now do you have an equally easy solution to how to get my ubuntu ready/mounting my empty rewritable cds? i keep getting some can't mount udf volume message

---

### Post by kmitnick on 2008-07-08
dude dual booting Vista with Ubuntu isn't a logical solution.... so anyone?

---

### Post by timrichardson on 2008-07-08
maybe this helps

[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374)

---

### Post by marcon00 on 2008-07-15
about mounting ? no idea :P anything that says I CANT mount, i just force mount it :P search :D and tell me how it went !! :)

sry for late reply, been busy :P

timrichardson, omnibook with my laptop just doesnt work, and i even upgraded my bios to 1.90 , still no changes.

---

### Post by joro on 2008-07-22
I have toshiba satelitte a135 and have no idea how to make my bluetooth work. hcitool dev gives Device: 

 help

---

### Post by marcon00 on 2008-09-03
so no one is willing to look into this ? :S

---

### Post by marcon00 on 2008-09-07
*bump*

---

### Post by marcon00 on 2008-09-07
*bump*

---

### Post by marcon00 on 2008-09-12
*bump*

---

### Post by marcon00 on 2008-09-14
******** BUUUUUUUUUUUUUUUUUUUUUMMMMMMMMMMMMMPPPPPPPPPPPPPPPPPPP *******

Im a chick with DD size....

does this get any attention ? 
:P

---

### Post by marcon00 on 2008-09-18
* bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump * * bump *

---

### Post by marcon00 on 2008-10-13
*bump*

---

### Post by marcon00 on 2008-12-26
**bump**


is it the hollydays now ? ehh

---

### Post by Valon Majere on 2009-04-24
bump

I too have a Qosmio F40 and would like to see some kind of solution that doesn't involve Vista or a windows os. I have had windows off my system for almost a year and dont really want to install just to use bluetooth. If anyone has any ideas they would be greatly appriciated.

---

### Post by marcon00 on 2009-04-25
i havent tried it yet .. but what if you could  try running virtualbox with XP and enabling bluetooth from there so then it can be seen in ubuntu ? give it a try and tell me how it went on.

---

