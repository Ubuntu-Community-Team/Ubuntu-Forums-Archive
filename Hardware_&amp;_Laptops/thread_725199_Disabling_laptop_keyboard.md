---
title: "Disabling laptop keyboard"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by cb951303 on 2008-03-15
Hello,

I have a laptop with a faulty keyboard. I plugged in an usb keybaord but occasionally the faulty one presses random keys. I want to disable it. I looked at bios settings but there is nothing there. Anyone knows how to disable it?

thanks very much

---

### Post by cb951303 on 2008-03-16
I hate to do it but: BUMP :)

---

### Post by cb951303 on 2008-03-16
Okay maybe a little change can get me some resolution. Since I don't use both integrated touchpad and keyboard I might just disable all PS/2 ports and use external usb keyboard and mice.

any ideas on howto disable PS/2 ports in linux?

thanks

---

### Post by cevans on 2008-03-24
I actually had this problem today as well. While it isn't a simple task, it does appear that it is possible to disable the keyboard in a number of cases.

Unfortunately, the process really depends on the type of keyboard and the choices of the laptop manufacturer, so I can only give you vague directions. The /sys/ directory is very useful for dealing with devices in odd ways, but is very complex and is poorly documented. Searching through dmesg ( eg, dmesg | grep -i keyb ) can provide enough information about the keyboard to find it in /sys/, and then one can play around with the controls in there (as root, use cat to get information and echo [something] > [file] to set things).

For example, on my laptop, the keyboard is connected via an internal usb connection. Searching through dmesg, I found that it was at "/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.2/input/input2", which is a subdirectory in /sys/. There are controls there in various levels, and one of them is "authorized" (in 1-2), which was set to 1. I set that to 0, and it disabled the keyboard and touchpad, which are both connected as the same device. In this case, the 0000:00:1d.0 directory corresponded to the UHCI bus driver, and usb1 corresponded to the first usb bus.

On another one of my laptops, searching through grep pointed me to /sys/devices/platform/i8042/serio0, but I haven't figured out how to disable it yet. Searching through the kernel documentation might be helpful.

Of course, all of this is rather dangerous if one doesn't know what one is doing, and I wouldn't recommend playing with /sys/ unless one is confident in one's grasp of the operating system. Doing the wrong things in /sys/ can cause all sorts of havoc.

---

### Post by cb951303 on 2008-04-02
that was exactly what I wanted
thanks very much

---

### Post by cb951303 on 2008-04-02
> /sys/devices/platform/i8042/serio0

thats exactly where my laptop points :)
if you find out howto disable pls let me know

thanks

---

### Post by cb951303 on 2008-05-07
ok, gentoo forums helped about this issue

adding "i8042.nokbd" to the kernel boot line works :guitar:

---

