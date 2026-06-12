---
title: "USB Keyboard uses Cntl and Alt equal Shift"
date: 2014-08-16
forum: Hardware
---

### Post by Everton_Nagel on 2014-08-16
Hi, I bought a USB Keyboard (Genius K5 model) to use with my notebook as a extended keyboard (is the same layout), but on Linux the keys Control and Alt operate equal the Shift key.
When I press Control or Alt, the Shift function works, and the Shift key still with the Shift functions.
I try on windows and all keys are working.
The notebook keyboard works perfectly too.

Is this a driver problem? because if, I can put in the blacklist, right?

$ demsg

[ 1919.567840] usb 3-4: USB disconnect, device number 4
[ 1921.141181] usb 3-4: new low-speed USB device number 5 using xhci_hcd
[ 1921.162759] usb 3-4: New USB device found, idVendor=0c45, idProduct=7603
[ 1921.162767] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1921.162771] usb 3-4: Product: USB Keyboard
[ 1921.162774] usb 3-4: Manufacturer: SONiX
[ 1921.163039] usb 3-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 1921.163051] usb 3-4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 1921.166189] input: SONiX USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input24
[ 1921.166541] hid-generic 0003:0C45:7603.000A: input,hidraw0: USB HID v1.11 Keyboard [SONiX USB Keyboard] on usb-0000:00:14.0-4/input0
[ 1921.173285] input: SONiX USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/input/input25
[ 1921.173947] hid-generic 0003:0C45:7603.000B: input,hiddev0,hidraw1: USB HID v1.11 Keyboard [SONiX USB Keyboard] on usb-0000:00:14.0-4/input1

Thanks for your attention.

att. Éverton Nagel

---

### Post by marinedtm on 2014-08-25
I am having same issue and all the problem buttons have same "USB code"  0x700e1 hence there is no way to fix this (driver/hardware problem?). It is detected as SONiX usb keyboard and works fine in Windows. I found one other post in Croatian that seemed to be about the same keyboard (it has got a choice of three backlit led colours but no Ctrl Key!). EasyAcc Gaming Keyboard - not Linux compatible.

---

### Post by swoogan on 2015-04-21
Hello,

I have an Azio keyboard that reports as a SONiX USB Keyboard as well. I wrote a Linux driver for it that you can find at [https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)

I wrote a series of blog posts about the work that went into creating it: [http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html](http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html)

I would appreciate any feedback you have if you are able to give it a try.


Colin

---

### Post by mariuscristianc+launchpad on 2015-04-29
> **swoogan said:**
> Hello,I have an Azio keyboard that reports as a SONiX USB Keyboard as well. I wrote a Linux driver for it that you can find at [https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)I wrote a series of blog posts about the work that went into creating it: [http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html](http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html)I would appreciate any feedback you have if you are able to give it a try.ColinHi Colin,It works like a charm with Cougar 200K based on same microdia 0c45:7603 chipset.Thanks for your effort (I've spent a lot of time looking in the wrong direction as the keyboard was working fully on my Lenovo laptop with Ubuntu 14.04, but not on my desktop).

---

### Post by gluonman on 2015-09-03
> **swoogan said:**
> Hello,

I have an Azio keyboard that reports as a SONiX USB Keyboard as well. I wrote a Linux driver for it that you can find at [https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)

I wrote a series of blog posts about the work that went into creating it: [http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html](http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html)

I would appreciate any feedback you have if you are able to give it a try.


Colin

OMG thank you so much!!

I spent between 08/2014 and 10/2014 trying to find a way to get around the fact that the scancodes and keycodes were all identical for the shift, ctrl, and alt keys, making it impossible to create my own assignments with autokey or xbindkeys.  After almost a couple months of dicking around with this keyboard, I just gave up.  I just started trying to figure it out again a few weeks ago, and finally I came upon this forum and your aziokbd driver.  I installed the driver, restarted my machine, and this thank you note is the very first thing I am doing with my now WORKING gaming keyboard (that's right, I was actually able to use my Ctrl key to skip back to the word 'working,' highlight it, and then make it all-caps).

I paid probably more money for this keyboard than I should have, but it is a beautiful, multi-coloured, backlit keyboard, and I'm very happy to be able to get full use out of it now.  Thank you so much, swoogan!  :D

---

### Post by gluonman on 2015-11-03
> **swoogan said:**
> Hello,

I have an Azio keyboard that reports as a SONiX USB Keyboard as well. I wrote a Linux driver for it that you can find at [https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)

I wrote a series of blog posts about the work that went into creating it: [http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html](http://swoogan.blogspot.com/2014/09/azio-l70-keyboard-linux-driver.html)

I would appreciate any feedback you have if you are able to give it a try.


Colin

Hi Colin,

While this solution was working for me before, it seems to no longer be working when I download and rebuild the module.  I am using Sabayon Linux 15.11 and kernel 4.2.0-sabayon, and I get the following warning when trying to build it that didn't occur before when it was working:

> ## Making package ##
make -C /lib/modules/4.2.0-sabayon/build M=/root/aziokbd modules
make[1]: Entering directory '/usr/src/linux-4.2.0-sabayon'
  CC [M]  /root/aziokbd/aziokbd.o
/root/aziokbd/aziokbd.c: In function ‘usb_kbd_irq’:
/root/aziokbd/aziokbd.c:114:7: warning: unused variable ‘keys’ [-Wunus
ed-variable]
  char keys[9];
       ^
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/aziokbd/aziokbd.mod.o
  LD [M]  /root/aziokbd/aziokbd.ko
make[1]: Leaving directory '/usr/src/linux-4.2.0-sabayon'
## Installing package ##
install -p -m 644 aziokbd.ko  /lib/modules/4.2.0-sabayon/kernel/driver
s/input/keyboard
/sbin/depmod -a 4.2.0-sabayon
## usbhid is compiled into kernel ##
usbhid.quirks=0x0c45:0x7603:0x0007
NOTICE - grub config file has already been updated
## You must reboot to load the module ##

Is this something you might be able to help me figure out?

---

