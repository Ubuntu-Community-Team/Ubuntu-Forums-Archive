---
title: "My mouse seems to be  recognized as a keyboard"
date: 2017-07-23
forum: Hardware
---

### Post by edenw on 2017-07-23
my mouse doesn't work and it seems to be  recognized as a keyboard when I use ```
xinput --list
``` to check

what should I do to make my mouse work?

```

$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard     id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB2.0 Camera                       id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard     id=10    [slave  keyboard (3)]
    &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard     id=11    [slave  keyboard (3)]
    &#8627; USB Optical Mouse                           id=15    [slave  keyboard (3)]


```

---

### Post by Autodave on 2017-07-23
Is this a problem that just started? Did it work OK before? When did it stop working correctly?

Laptop or desktop? If laptop, do you have a USB keyboard or mouse connected?

---

### Post by efflandt on 2017-07-23
Is the mouse wired or wireless (connected to USB 2.0 or 3.0?) and what brand/model mouse? What do you get for each of following related to the mouse:```
lsusb
sudo lsusb -v
xinput --list --long 15
```I have seen keyboards with no mousepad show up under both pointer and keyboard. My Logitech MX Master which has 6 buttons (5 mouse buttons + 1 hidden in foot under my thumb that sends Ctrl+Alt+Tab keycode), only shows up in xinput as pointer. Normally mousepad and mouse (or multiple keyboards) should be able to work simultaneously in Linux (unlike Windows which sometimes deactivates mousepad when mouse is connected).

Also see what **dmesg** shows when you plug in the mouse (run dmesg from a terminal and see what shows at end of that after connecting the mouse).

It is possible that you might need to add a udev rule for an unknown device. At one time Ubuntu lumped all Logitech keyboard and mouse devices into hiddev* and I had to add something to instead use hidraw* for USB ID of my diNovo Edge keyboard (which did not need any drivers). That has since been incorporated into udev rules to set the diNovo Edge different. But other than coming up with a temporary fix for that, I am no expert on udev rules.

---

### Post by edenw on 2017-07-24
I installed xubuntu only about two or three days.When I have already installed first time, my mouse already doesn't work.But sometimes it works such as I updated the kernel(because the system stucked on the boot screen with 10.0.0.28 kernel) or when i reinstall the system several times(Most time it doesn't work when i reboot). I use a laptop, and a usb keyboard connected.

---

### Post by edenw on 2017-07-24
> **Autodave said:**
> Is this a problem that just started? Did it work OK before? When did it stop working correctly?

Laptop or desktop? If laptop, do you have a USB keyboard or mouse connected?

Today I reinstall the system again, my mouse works again, but I donn't know when it may doesn't again.

---

### Post by edenw on 2017-07-24
> **efflandt said:**
> Is the mouse wired or wireless (connected to USB 2.0 or 3.0?) and what brand/model mouse? What do you get for each of following related to the mouse:```
lsusb
sudo lsusb -v
xinput --list --long 15
```I have seen keyboards with no mousepad show up under both pointer and keyboard. My Logitech MX Master which has 6 buttons (5 mouse buttons + 1 hidden in foot under my thumb that sends Ctrl+Alt+Tab keycode), only shows up in xinput as pointer. Normally mousepad and mouse (or multiple keyboards) should be able to work simultaneously in Linux (unlike Windows which sometimes deactivates mousepad when mouse is connected).

Also see what **dmesg** shows when you plug in the mouse (run dmesg from a terminal and see what shows at end of that after connecting the mouse).

It is possible that you might need to add a udev rule for an unknown device. At one time Ubuntu lumped all Logitech keyboard and mouse devices into hiddev* and I had to add something to instead use hidraw* for USB ID of my diNovo Edge keyboard (which did not need any drivers). That has since been incorporated into udev rules to set the diNovo Edge different. But other than coming up with a temporary fix for that, I am no expert on udev rules.

The mouse is wired and connected to USB2.0(I tried 3.0, it not works).I don't know the brand, it's just a common gaming mouse, maybe a small factory produce it.Today I reinstall the system again, my mouse works again.And just now, I pull out it and plug in it, it doesn't work again.I don't know why my keyboard showed up both pointer and keyboard(by the way, my mouse also showed up both pointer and keyboard when it works normally).
```
$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard     id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard     id=9    [slave  keyboard (3)]
    &#8627; Chicony USB2.0 Camera                       id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard     id=16    [slave  keyboard (3)]
    &#8627; USB Optical Mouse                           id=11    [slave  keyboard (3)]


```

```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 04f2:b59e Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 1bcf:0823 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 1b1c:1b33 Corsair 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
xinput --list --long 11
USB Optical Mouse                           id=11    [slave  keyboard (3)]
    Reporting 1 classes:
        Class originated from: 11. Type: XIKeyClass
        Keycodes supported: 248
```

```
dmesg when plug in
[ 2801.837343] usb 1-11: USB disconnect, device number 6
[ 2815.584776] usb 1-11: new full-speed USB device number 7 using xhci_hcd
[ 2815.727118] usb 1-11: New USB device found, idVendor=1bcf, idProduct=0823
[ 2815.727122] usb 1-11: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 2815.727124] usb 1-11: Product: USB Optical Mouse
[ 2815.730094] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11:1.0/0003:1BCF:0823.0006/input/input22
[ 2815.789041] hid-generic 0003:1BCF:0823.0006: input,hidraw2: USB HID v1.00 Keyboard [USB Optical Mouse] on usb-0000:00:14.0-11/input0
[ 2841.489827] usbhid 1-11:1.1: can't add hid device: -110
[ 2841.489849] usbhid: probe of 1-11:1.1 failed with error -110

```

the lsusb -v is too long that I output to a txt file.[ATTACH]276118[/ATTACH]

---

### Post by efflandt on 2017-07-25
It is not strange that your keyboard is also listed under **pointer**, but it is strange that your keyboard is listed twice under **keyboard**.

Apparently that has been a problem with other mice too, although in this case it may have been when they plugged in another mouse while a Sunplus mouse or other device was working:
[https://askubuntu.com/questions/768455/usb-mouse-suddenly-stopped-working-16-04](https://askubuntu.com/questions/768455/usb-mouse-suddenly-stopped-working-16-04)

Something quick to try, but all on one line in case it would temporarily disrupt your USB keyboard as separate lines, would be:```
sudo rmmod usbhid && sudo modprobe usbhid
```One reply was that **fwupd** was interfering and could be removed. That is apparently for updating UEFI firmware, but I am not familiar with that or how frequently that might be used. I only have 1 low end Win10/Ubuntu 16.04 laptop that even has UEFI, and wireless Logitech mouse or keyboard have not had any issues.

---

### Post by edenw on 2017-07-29
> **efflandt said:**
> It is not strange that your keyboard is also listed under **pointer**, but it is strange that your keyboard is listed twice under **keyboard**.

Apparently that has been a problem with other mice too, although in this case it may have been when they plugged in another mouse while a Sunplus mouse or other device was working:
[https://askubuntu.com/questions/768455/usb-mouse-suddenly-stopped-working-16-04](https://askubuntu.com/questions/768455/usb-mouse-suddenly-stopped-working-16-04)

Something quick to try, but all on one line in case it would temporarily disrupt your USB keyboard as separate lines, would be:```
sudo rmmod usbhid && sudo modprobe usbhid
```One reply was that **fwupd** was interfering and could be removed. That is apparently for updating UEFI firmware, but I am not familiar with that or how frequently that might be used. I only have 1 low end Win10/Ubuntu 16.04 laptop that even has UEFI, and wireless Logitech mouse or keyboard have not had any issues.

I think my keyboard is listed twice probably because it used two usb...one for itself and one for the usb on keyboard body.Now I make my mouse work by setting udev rules.Hope it can work longer this time.Thank you for your help!

---

