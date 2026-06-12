---
title: "Wake from suspend with keyboard or mouse"
date: 2012-03-09
forum: Hardware
---

### Post by sparhawkthesecond on 2012-03-09
Hi, my laptop (running Ubuntu 11.10) will only wake from suspend with the power button. I would like to wake up using the keyboard, trackpad buttons, and/or my external keyboard/mouse. Originally, Windows (dual-booted) would not allow wake from keyboard/USB either, so I went into BIOS and enabled wake from USB, which solved the problem in Windows.

Back in Ubuntu, I tried
```
$ lspci|grep USB
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```Then, I tried```
$ cat /proc/acpi/wakeup
```
There were no items labelled USB, but it did include the lines ```

EHC1      S3    *disabled  pci:0000:00:1d.0
EHC2      S3    *disabled  pci:0000:00:1a.0
PXSX      S4    *disabled  pci:0000:04:00.0
```
Then, I tried
```
$ echo .... > /proc/acpi/wakeup
``` where .... was EHC1, EHC2, PXSX. The first two options toggled the items to enabled, but the latter did nothing. In any case, none of these options solved the problem for me.

Would anyone have any suggestions as to how to proceed from here?

Cheers.

---

### Post by sparhawkthesecond on 2012-03-18
Bump?

---

### Post by Andrew James Collett on 2012-05-15
I have exactly the same issue. well mostly. my usb devices, i.e. keyboard, and wireless mouse and keyboard, don't wake up the pc in suspend. 

Desktop pc. installed ubuntu 12.04, had XBMCbuntu on before that. Dual booted with Win 7.

Windows suspended and resumed perfectly, the mouse and keyboard woke it up.

In ubuntu and XBMC i had edit these:
$ cat /proc/acpi/wakeup 
to "enabled" for all the usb's in order to wake. All the usb's where set to enabled on ubuntu 12.04

My bios doesnt include options choose what wakes the pc. only what sleep state the pc can be in, which is on S3.

but still no luck. usb doesn't seem to have any power either. but the pc resumes perfectly if I use the power button. If this is going to serve as a decent media pc i need this function to work. besides, its annoying that something in windows 7 doesn't work with Ubuntu :-P i'd really appreciate any help.

thanks! 
Andrew

p.s. not sure if its important, but WOL doesn't work either, even though its enabled. but again, only when dealing with ubuntu.

---

### Post by Andrew James Collett on 2012-05-15
This link may help you, though i don't know how you'll get the vendor stuff.

[http://ubuntuforums.org/showthread.php?t=1968487](http://ubuntuforums.org/showthread.php?t=1968487)

It seems to have solved my problem though. So no worries. unless i appear here again, im solved     :-)

---

### Post by sparhawkthesecond on 2012-05-15
Great, that's fantastic! Thanks for taking the time to post in this thread too!

FWIW here is precisely what I did to fix it, in the case that it helps others. Firstly, I wanted to test that I *could* fix it, before creating the udev rule (since my "$ cat /proc/acpi/wakeup" was a bit different to yours). So, I ran ```
$ lsusb
``` which included the line "Bus 003 Device 007: ID 1532:0016 Razer USA, Ltd" (for my Razer mouse). Then, I ran ```
$ lsusb -t
1-1.4:1.2: No such file or directory
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    |__ Port 1: Dev 5, If 0, Class=hub, Driver=hub/3p, 480M
        |__ Port 2: Dev 6, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 2: Dev 6, If 1, Class=HID, Driver=usbhid, 1.5M
        |__ Port 3: Dev 7, If 0, Class=HID, Driver=usbhid, 12M
```Here, bus 3 and device 7 matches to bus 3, port 1, port 3. Hence, I did ```
$ sudo su
# echo enabled > /sys/bus/usb/devices/3-1.3/power/wakeup
``` After this, the mouse would wake up the computer! Then, I created a (slightly modified) udev rule and all was well.```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="1532", ATTRS{idProduct}=="0016" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```Oddly enough, the upgrade to Ubuntu 12.04 meant that my external keyboard could wake up the computer, but not the mouse. Indeed, when I checked the wakeup file associated with it, it was enabled. I'm not sure why the inconsistency...

I'm also having trouble getting my laptop's internal keyboard or trackpad to wake the computer, but I'll post in the other thread regarding that.

Thanks for your help!

---

### Post by abexman on 2013-05-15
Hello, my laptop seems to have the opposite problem. It  seems to wake when I just look at if  funny. How would I edit the wake file so it *only* wakes from the power button? Ubuntu 12.04 here.

---

### Post by sparhawkthesecond on 2013-05-15
I'm not sure, but perhaps by reverting the options? e.g. echo "disabled" instead of "enabled"? It really depends what the problem is precisely. If that doesn't work, I'd suggest starting another thread. You should get more responses by doing that. Feel free to post the link here.

---

