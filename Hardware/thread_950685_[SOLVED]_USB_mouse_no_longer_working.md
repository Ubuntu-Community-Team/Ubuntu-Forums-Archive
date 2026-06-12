---
title: "[SOLVED] USB mouse no longer working"
date: 2008-10-17
forum: Hardware
---

### Post by mgangav on 2008-10-17
Hello,

Till yesterday, I was using a Microsoft Basic Optical Mouse v2.0 without any problems. But, when I plugged in the mouse into the laptop today, the mouse didn't even light up. I tried restarting the laptop to no avail.

What could have changed? I am sure that there is nothing wrong with the USB ports because I can use flash drives and the such through it. I don't have a USB to PS/2 adaptor, so any help would be greatly appreciated.

I'm using Hardy Heron. I upgraded the kernel to 2.6.*. I'm using an Acer Aspire 5630.

The mouse worked absolutely fine till yesterday.

---

### Post by Milkium on 2008-10-17
Could it be that you accidentally deleted/disabled its driver or something?

Have you tried using it on a another computer?

---

### Post by mgangav on 2008-10-17
No, I haven't used the mouse on any other computer. And, I don't thin that I messed around with it's driver or anything because. It was working yesterday. And today it is not. The only substantial thing that happened is that I got a huge update today of about 35 MB...

---

### Post by mgangav on 2008-10-17
Anyway, I'm a new Linux user, so, please bear with me. After searching around for a bit more, I used dmesg. Here is the last part of what it printed out (atleast the part that has usb in it):

[ 1095.451685] usb 4-1: new low speed USB device using uhci_hcd and address 10
[ 1095.571477] usb 4-1: device descriptor read/64, error -71
[ 1095.795078] usb 4-1: device descriptor read/64, error -71
[ 1096.011769] usb 4-1: new low speed USB device using uhci_hcd and address 11
[ 1096.134595] usb 4-1: device descriptor read/64, error -71
[ 1096.358199] usb 4-1: device descriptor read/64, error -71
[ 1096.573870] usb 4-1: new low speed USB device using uhci_hcd and address 12
[ 1096.981239] usb 4-1: device not accepting address 12, error -71
[ 1097.093071] usb 4-1: new low speed USB device using uhci_hcd and address 13
[ 1097.507441] usb 4-1: device not accepting address 13, error -71

---

### Post by ajgreeny on 2008-10-17
I would bet that the updates yesterday were for the new kernel etc, which have caused some problems of many sorts to others, including usb upsets.  Try booting into the 2.6.24-19 kernel at the grub menu and you may get the mouse back.  If you don't get a grub menu at boot, hit *esc* when you see "starting grub" appear on screen, and you should see it.

---

### Post by mgangav on 2008-10-17
> **ajgreeny said:**
> I would bet that the updates yesterday were for the new kernel etc, which have caused some problems of many sorts to others, including usb upsets.  Try booting into the 2.6.24-19 kernel at the grub menu and you may get the mouse back.  If you don't get a grub menu at boot, hit *esc* when you see "starting grub" appear on screen, and you should see it.

Hello, I just tried booting from the 2.6.24-19 kernel. My mouse actually flashed twice during bootup. But still remains unresponsive. When I try dmesg. I get the following:

> 
[   43.248459] usb 4-1: device descriptor read/64, error -71
[   43.475196] usb 4-1: device descriptor read/64, error -71
[   43.690805] usb 4-1: new low speed USB device using uhci_hcd and address 7
[   43.814595] usb 4-1: device descriptor read/64, error -71
[   44.042231] usb 4-1: device descriptor read/64, error -71
[   44.257901] usb 4-1: new low speed USB device using uhci_hcd and address 8
[   44.669204] usb 4-1: device not accepting address 8, error -71
[   44.781057] usb 4-1: new low speed USB device using uhci_hcd and address 9
[   45.189365] usb 4-1: device not accepting address 9, error -71



---

### Post by ajgreeny on 2008-10-17
OK, it was worth a try.  Can't help any further I'm afraid.

---

### Post by mgangav on 2008-10-17
Well after more searching, I've realised that xorg.conf is something important. Here are its contents:

<quote>
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
<\quote>

---

### Post by mgangav on 2008-10-17
> **ajgreeny said:**
> OK, it was worth a try.  Can't help any further I'm afraid.

Thanks for your help anyway.

---

### Post by gfclement on 2008-10-17
Yes, booting back into the old kernel solves this issue.

---

### Post by mgangav on 2008-10-17
Ok, following the written advice of some of the people in the forum, I booted into the older version of the kernel (2.6.24-19). But, my mouse still remained in a catatonic state. Then, I was in the middle of following this tutorial [http://www.linuxforums.org/forum/debian-linux-help/46802-usb-mouse-not-working-udev-hotplug-problem.html]("http://www.linuxforums.org/forum/debian-linux-help/46802-usb-mouse-not-working-udev-hotplug-problem.html") when I realised that I ought to be using the 2.6.24-21 kernel. Then, during bootup, my mouse revived and is now working. (I'm in the 2.6.24-21 kernel).

The only significant thing that I did was to boot in to the 2.6.24-19 kernel, run "modprobe usbcore" on the terminal, and boot into the 2.6.24-21 kernel. Strange.

Well, my mouse is working now anyway. Thanks to everyone for all their help.

---

