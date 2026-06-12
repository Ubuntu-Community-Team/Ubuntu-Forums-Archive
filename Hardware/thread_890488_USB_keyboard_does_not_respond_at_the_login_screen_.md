---
title: "USB keyboard does not respond at the login screen (hardy)"
date: 2008-08-15
forum: Hardware
---

### Post by woo_kash on 2008-08-15
I use Ubuntu Hardy Heron 8.04 x64 and have 106 -key Genius Slim Star keyboard. When I use PS/2 connector, the keyboard is presented in BIOS, GRUB, login screen and in ubuntu.

However, when I plug the keyboard using USB port, I still have it working in BIOS, GRUB but is stops responding on the login screen. To log in I need to use the PS/2 connector and after login I am able to plug the keyboard to the USB port again and it works. The funny thing is that when the keyboard is plugged again to the USB port I am able to reset the x server (alt+ctrl+backspace) and the keyboard works on the login screen!

To sum up - I am not able to use the USB keyboard on the first login to ubuntu.

Please, let me know if you need some detailed information.

---

### Post by prshah on 2008-08-15
> **woo_kash said:**
> 
To sum up - I am not able to use the USB keyboard on the first login to ubuntu.

Let's see what Ubuntu/Xorg makes of your keyboard. Open a terminal (Applications-Accessories-Terminal), then give the following commands and post back output:```
dmesg | grep -i keyboard
dmesg | grep -i kbd
cat /etc/X11/xorg.conf | grep -i -A 8 keyboard
cat /var/log/Xorg.0.log | grep -i keyboard
```

---

### Post by woo_kash on 2008-08-15
Hi PRShah,

Thanks for so prompt reply.

here's the output (I have used PS/2 to enter username and password and changed it to USB as soon as I logged in):

```
**dmesg | grep -i keyboard**
[   31.520166] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[  117.762284] input: ABBAHOME USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-9/1-9:1.0/input/input6
[  117.797962] input,hidraw0: USB HID v1.10 Keyboard [ABBAHOME USB Keyboard] on usb-0000:00:02.0-9

**dmesg | grep -i kbd**
[   31.486492] serio: i8042 KBD port at 0x60,0x64 irq 1

**cat /etc/X11/xorg.conf | grep -i -A 8 keyboard**
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
--
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbRules"   "xorg"
    #Option         "Device" "/dev/usbdev2.1_ep81"
    Option         "XkbModel"   "pc106"
    Option         "XkbLayout"  "pl"
EndSection

Section "Monitor"

**cat /var/log/Xorg.0.log | grep -i keyboard**
(**) |-->Input Device "Keyboard0"
(II) Initializing built-in extension XKEYBOARD
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Keyboard0: Protocol: standard
(**) Keyboard0: XkbRules: "xorg"
(**) Keyboard0: XkbModel: "pc106"
(**) Keyboard0: XkbLayout: "pl"
(**) Keyboard0: CustomKeycodes disabled
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
```

Let me know if you need more data.

EDIT:

I have used various settings in xorg.conf, including 102, 105-key options but none seemed to work.

---

### Post by prshah on 2008-08-15
> **woo_kash said:**
> 
[  117.762284] input: ABBAHOME USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-9/1-9:1.0/input/input6
...  
**cat /etc/X11/xorg.conf | grep -i -A 8 keyboard**
...
Section "Module"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbRules"   "xorg"
[color=red]    #Option         "Device" "/dev/usbdev2.1_ep81"[/color]
    Option         "XkbModel"   "pc106"
    Option         "XkbLayout"  "pl"
EndSection
...


This is just a guess, but I don't think it can find the keyboard device; why is the device line commented out? You can try two things; uncomment it, save, quit, logout and restart X with Ctrl+Alt+BkSpace. Check if the keyboard works; if it doesn't, replace the device information with that which you have got with the earlier "dmesg | grep keyboard" command, repeat the process, and check if it works.

---

### Post by woo_kash on 2008-08-15
Hi,

Nah, this is line that I have added and should not have anything to do with my problem. I tried to set up a driver manually but it did not work.

Thanks again.

---

### Post by woo_kash on 2008-08-20
Anyone?

---

### Post by woo_kash on 2008-08-29
Can anyone help..?

---

### Post by Crafty Kisses on 2008-08-29
> **woo_kash said:**
> Can anyone help..?

Post the results of > lsusb

---

### Post by woo_kash on 2008-08-30
Thanks for reply.

```
lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05d5:6782 Super Gate Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

Please, note that I am logging on using PS/2 keyboard switch and then plug in the keyboard to the USB port.

The USB is working fine on BIOS but does not work on login screen nor if I drop to shell (with no x started)..

Any help would be much appreciated..

I should add that I have problems with PS/2 too - I need to plug it and hold under certain angle to make it work, otherwise I cannot use the PS/2 connector either.

---

### Post by woo_kash on 2008-09-01
Hello?

---

### Post by woo_kash on 2008-09-09
Hello..?

---

### Post by Cocoyol on 2008-11-15
I had the same problem. When I turn on the computer USB keyboard does not work but when you press the ctrl + shift + Num Lock, the LED turns on and so, the keyboard is ready for use.

---

### Post by woo_kash on 2008-11-15
Hi,

Thanks, but I have not tried it. I have resolved this and now I am using Intrepid (although the issue was also presented in hardy).

I had to add some lines to rc.local, i.e. to reload the below modules at startup. Now the keyboard loads fine on the login screen and after. There is a short period where I have no keyboard when the system starts, but I don't know how to resole this.

```
rmmod usbhid
rmmod usbkbd
modprobe usbkbd
modprobe usbhid
```

---

