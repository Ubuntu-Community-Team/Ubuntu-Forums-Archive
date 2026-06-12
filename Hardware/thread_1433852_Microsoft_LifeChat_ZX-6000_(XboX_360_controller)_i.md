---
title: "Microsoft LifeChat ZX-6000 (XboX 360 controller) in Ubuntu 9.10 Karmic Koala"
date: 2010-03-19
forum: Hardware
---

### Post by Realnot on 2010-03-19
Hi, I found problems installing the headset Microsoft LifeChat ZX-6000 on Ubuntu 9.10. I followed the manual step by step, but nothing to do ... sorry for my bad English:

[http://ubuntuforums.org/showthread.php?t=404577&page=21](http://ubuntuforums.org/showthread.php?t=404577&page=21)
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy)


[B]Error:
[/B]
[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ cd /home/mauro/.xpad360
[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ sudo make
make modules -C /lib/modules/2.6.31-19-generic/build SUBDIRS=/home/mauro/.xpad360
make[1]: ingresso nella directory «/usr/src/linux-headers-2.6.31-19-generic»
  CC [M]  /home/mauro/.xpad360/xpad.o
/home/mauro/.xpad360/xpad.c: In function ‘xpad_open’:
/home/mauro/.xpad360/xpad.c:339: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/.xpad360/xpad.c: In function ‘xpad_close’:
/home/mauro/.xpad360/xpad.c:350: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/mauro/.xpad360/xpad.c:440: error: ‘struct input_dev’ has no member named ‘cdev’
/home/mauro/.xpad360/xpad.c:441: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/.xpad360/xpad.c: In function ‘usb_xpad_init’:
/home/mauro/.xpad360/xpad.c:519: error: implicit declaration of function ‘info’
make[2]: *** [/home/mauro/.xpad360/xpad.o] Errore 1
make[1]: *** [_module_/home/mauro/.xpad360] Errore 2
make[1]: uscita dalla directory «/usr/src/linux-headers-2.6.31-19-generic»
make: *** [all] Errore 2

**lsusb:**

[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ lsusb
Bus 002 Device 007: ID 045e:0719 Microsoft Corp. 
Bus 002 Device 005: ID 045e:0714 Microsoft Corp. 
Bus 002 Device 004: ID 045e:0717 Microsoft Corp. 
Bus 002 Device 003: ID 045e:0707 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 045e:075d Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg | tail -n20**

[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ dmesg | tail -n20
[ 7501.533367] 8:3:1: usb_set_interface failed
[ 7501.837047] usb 1-1: new high speed USB device using ehci_hcd and address 9
[ 7501.985340] usb 1-1: configuration #1 chosen from 1 choice
[ 7501.988133] uvcvideo: Found UVC 1.00 device Microsoft® LifeCam Cinema(TM) (045e:075d)
[ 7501.996870] input: Microsoft® LifeCam Cinema(TM) as /devices/pci0000:00/0000:00:02.1/usb1/1-1/1-1:1.0/input/input17
[ 7503.117114] 9:3:1: cannot get freq at ep 0x82
[ 7504.241805] usb 2-2: USB disconnect, address 6
[ 7504.244080] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[ 7504.316121] 9:3:1: cannot get freq at ep 0x82
[ 7505.449116] 9:3:1: cannot get freq at ep 0x82
[ 7507.469032] usb 2-2: new full speed USB device using ohci_hcd and address 7
[ 7507.694216] usb 2-2: configuration #1 chosen from 1 choice
[ 7507.697664] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input18
[ 7507.697921] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.2/input/input19
[ 7507.698139] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.4/input/input20
[ 7507.698340] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.6/input/input21
[ 8837.311908] padlock: VIA PadLock not detected.
[ 8837.411250] alg: No test for xts(twofish) (xts(twofish-generic))
[ 8837.472897] alg: No test for xts(serpent) (xts(serpent-generic))
[ 8837.503701] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended.

Thank's for support!

---

### Post by Chr0mis on 2010-05-01
Has anybody found a way to fix this and get the headset working? I am also running Karmic Koala. 


**Error:**

[email]katja@Holland:~/.xpad[/email]360$ sudo make
make modules -C /usr/src/linux-headers-2.6.31-14-generic SUBDIRS=/home/katja/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/katja/.xpad360/xpad.o
/home/katja/.xpad360/xpad.c: In function ‘xpad_wireless_connect’:
/home/katja/.xpad360/xpad.c:291: error: implicit declaration of function ‘info’
/home/katja/.xpad360/xpad.c: In function ‘xpad_open’:
/home/katja/.xpad360/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/katja/.xpad360/xpad.c: In function ‘xpad_close’:
/home/katja/.xpad360/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/katja/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/katja/.xpad360/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/katja/.xpad360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/katja/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/katja/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2


**lsusb**
[email]katja@Holland:~/.xpad[/email]360$ lsusb
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:5800 Broadcom Corp. 
Bus 001 Device 003: ID 05ca:1815 Ricoh Co., Ltd 
Bus 001 Device 005: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 010: ID 045e:0719 Microsoft Corp. 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


All help is greatly appreciated!

---

### Post by Realnot on 2010-05-02
Hi, I  found this howto for the headset, much more recent past, although the  results are the same ... some output

howto: [https://help.ubuntu.com/community/Xbox360Controller#Compile](https://help.ubuntu.com/community/Xbox360Controller#Compile)

```
mauro@workstation:~$ cd xpad
mauro@workstation:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.32-22-generic SUBDIRS=/home/mauro/xpad
make[1]: ingresso nella directory «/usr/src/linux-headers-2.6.32-22-generic»
  CC [M]  /home/mauro/xpad/xpad.o
/home/mauro/xpad/xpad.c: In function ‘xpad_wireless_connect’:
/home/mauro/xpad/xpad.c:291: error: implicit declaration of function ‘info’
/home/mauro/xpad/xpad.c: In function ‘xpad_open’:
/home/mauro/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/xpad/xpad.c: In function ‘xpad_close’:
/home/mauro/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/xpad/xpad.c: In function ‘xpad_probe’:
/home/mauro/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/mauro/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/mauro/xpad/xpad.o] Errore 1
make[1]: *** [_module_/home/mauro/xpad] Errore 2
make[1]: uscita dalla directory «/usr/src/linux-headers-2.6.32-22-generic»
make: *** [all] Errore 2
mauro@workstation:~/xpad$ 
```:confused::confused::confused:

---

