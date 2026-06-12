---
title: "Must be restart ubuntu for USB stuff. is that a bug on ubuntu hardy (hero)?"
date: 2008-08-09
forum: Hardware
---

### Post by Kelen.Chang on 2008-08-09
Sometimes USB could not work, must going to restart computer for this problem. is that a bug? if not, who could help me? pls~ ](*,)  :(

laptop: IBM T61

---

### Post by Stemp on 2008-08-10
[http://thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61](http://thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61)

No sign of problems with USB :(

---

### Post by Kelen.Chang on 2008-08-10
Hi, dude, there was no any solution with this problem on your link showed me.  any mistakes ?

---

### Post by Stemp on 2008-08-10
Nope, there is no solution because they have no problems with USB :D
Are you sure it's not an hardware problem ?

---

### Post by Kelen.Chang on 2008-08-10
Well, i sure there is no hardware problem with usb, because they worked fine in Windows, and under ubuntu, sometimes they worked fine also.. So, i thought the hardware have no problem. 
And, i fond out this problem since a few days ago, i force quited system.  i thought there must be a mistake somewhere by this.
if it's not work, i checked by $ dmesg | grep usb. 
[  262.081699] usb 3-2: USB disconnect, address 5
[  890.358366] usb 3-1: new full speed USB device using uhci_hcd and address 6
[  890.535097] usb 3-1: configuration #1 chosen from 1 choice
[  890.568762] usb-storage: device found at 6
[  890.568767] usb-storage: waiting for device to settle before scanning
[  895.565595] usb-storage: device scan complete
[  915.411673] usb 3-1: USB disconnect, address 6
[COLOR="Red"][ 1051.733388]  [<f8894bab>] usb_hcd_irq+0x2b/0x60 [usbcore]
[ 1051.733534] [<f8894b80>] (usb_hcd_irq+0x0/0x60 [usbcore])[/COLOR]

---

### Post by Stemp on 2008-08-11
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126369](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126369)

«Solved by a Lenovo BIOS upgrade which is now available for X61t machines as well. See here: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-68005](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-68005) »

---

### Post by Kelen.Chang on 2008-08-11
Stemp, really appreciate for your help.
I was tried this way on this Bug.  
But i still do not know how to add 'irqpoll' option in /boot/grub/menu.lst     
For that, did you have any suggestion?

---

### Post by Stemp on 2008-08-12
You have to edit your grub menu.lst :
```
sudo gedit /boot/grub/menu.lst
```

Scroll down to this line :
```
## ## End Default Options ##
```

Then you will find your menu items :
```
title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=907b6351-577f-4e81-8c33-4690cd2e781f ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet
```

Add the irqpoll option in the kernel line :
```
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=907b6351-577f-4e81-8c33-4690cd2e781f ro quiet splash **irqpoll**
```

And reboot.

---

### Post by Kelen.Chang on 2008-08-12
well, it's worked by this way, 
Stemp, appreciate much for your help again.

---

### Post by Stemp on 2008-08-12
You're welcome. Have fun ;)

---

