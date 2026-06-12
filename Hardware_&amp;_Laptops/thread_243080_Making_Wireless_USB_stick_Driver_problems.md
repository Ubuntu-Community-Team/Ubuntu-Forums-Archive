---
title: "Making Wireless USB stick Driver problems"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by Miles Lombardi on 2006-08-24
I've recently purchased a new computer, and decided to run Ubuntu, but unfortunately it doesn't recognise the (rather generic) wireless USB adapater (I think) when simply plugged in. With the CD that came with it I found that it actually contaned some Linux source but I'm not entirely sure how to use it (yey for windows users >_>).

These are the requirements that it says:
> 
2.1 Requirements:
1. Kernel 2.4.x. I am developing the driver on 2.4.24, but it reportedly also works
on .4.x. If your kernels version is less than 2.4.22 (for example Red Hat 9.0
is .4.20-8), suggest to upgrade kernel for better support on USB 2.0.
2. Kernel 2.6.x. This driver has been verify on 2.6.6 and 2.6.7.
3. To build zd1211 you will need: Configured kernel source code for the kernel you are
running. Ideally, Configured means that you have at least run 'make config', 'make
enuconfig', or 'make xconfig'. If your platform is not SMP system, please don't
config SMP supported, because when module loaded, this will make unresolved
symbol.
4. Make sure your kernel usb 2.0 support is running
- Use lsmod to check "ehci-hcd" module is loaded.
- If host is not support usb 2.0, zd1211 will run under pure-b mode.


I don't know if that even means it'll run on Ubuntu.

Secondly it asks me to make it, which I can't because I'm too stupid and don't know how. I tried navigating to the folder containing the makefile and typing "make" (using the Command Line), but that doesn't do anything.

Also, when I naviagated to the directory "user/src" I found it was empty even when the makefile is supposed to be finding the kernel there. So I'm really confused. Should it work by default? (everything else seems to).

---

### Post by Cynical on 2006-08-25
Oh yeah dude I have a wireless card based on that same chipset. Don't worry that particular one is well supported in linux. To enable it just do

> modprobe zd1211
then 
> lsmod
and look for this line
> usbcore  139076  5 **zd1211**,usbhid,ehci_hcd,uhci_hcd
If you see it do
> sudo ifconfig wlan0 up
Now install a program like wifi-radar and configure it

---

### Post by Miles Lombardi on 2006-08-26
I got stuck at the ifconfig line, I got an error stating that it cannot find the device, even though it *is* plugged in.
Also you must remember that I cannot install any software (easily) without wasting a single write CD (which I don't really want to do).

---

