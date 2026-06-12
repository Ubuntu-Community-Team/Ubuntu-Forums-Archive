---
title: "SixAxis not working in Intrepid"
date: 2008-11-01
forum: Hardware
---

### Post by falkTX on 2008-11-01
My PS3 controller no longer works in Ubuntu...
In Hardy was ok, now...

Even when using the USB cable it doesn't work.
It registers fine (dmesg log) but when i run "jstest /dev/input/js0" it is detected but no button works

---

### Post by falkTX on 2008-11-01
I think I found what the problem is:
The sixaxis is (right now) working as a pointing device (mouse)

How do I disable it?
"Blacklisting"?

---

### Post by falkTX on 2008-11-01
Not sixaxis prob, seems like no joystick is working at all..

---

### Post by falkTX on 2008-11-01
NO!!!! I wanted to play tomorrow! (I told my friends about my PS3 wireless and I need to show them..

I just read this:

"Stating with Ubuntu 8.10 Intrepid Ibex and due to changes in Xorg, each 
model of joystick needs a special file to be used properly."

Grr...

---

### Post by falkTX on 2008-11-01
Finally!

Got it working again!

Follow the link:
[https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done)


I managed to get in bluetooth mode as well, using (my own patched) Hardy deb files.

---

### Post by Leno. on 2008-11-02
> **falkTX said:**
> Finally!
I managed to get in bluetooth mode as well, using (my own patched) Hardy deb files.Can you upload them?

---

### Post by falkTX on 2008-11-02
Here's the patch (64-bit only)

Before installing the patch please remove (completely/purge) all bluez stuff and libbluetooth

install bluez-audio and libbluetooth (Hardy versions, download them at packages.ubuntu.com)

install pack with patch

install bluez-gnome (Hardy version) if you want to manage BT devices.

Reboot (important).


Don't forget to copy the DualShock3 fdi file in the page on previous posts.
And DO NOT UPDATE bluez* packages, or it will stop working

---

### Post by Kiek on 2008-11-04
Regressing bluez with a major number does not count as *solved* but *hacked* in my opinion :S

I am currently playing over USB with the DualShock3.fdi file
did anybody find a fix for bluetooth?

```
yannick@yannick-ubuntu810:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 054c:0268 Sony Corp. Batoh Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by falkTX on 2008-11-06
Do you understand patching files? I don't...

All I know is that "bluez" deb has included *-utils/audio/network, so the solution is to find the "main.c" file of *-utils and patch it manually.

I have no idea on how to patch manually

(And remember that new bluez doesn't have the command "hidd" (bug), so it will be necessary to include one from a previous version)

---

### Post by falkTX on 2008-11-06
I really wanted to get this fixed, but it's harder than it looks.

Having downgraded Hardy debs on Intrepid it's not recommended, so I started making one. It is bluez-4.12, with hidd and sixpair and a modified /etc/init.d/bluetooth to enable hidd - 
 - The reason "hidd" is not anymore on bluez package is because it was replaced by bluetoothd, the new BT daemon. But it don't seem to work with sixaxis yet.

I actually got the joystick to be recognized using "hidd" (yes, with bluez-4.12), but I still don't see any results on "jstest /dev/input/js0" although in usb mode it works fine.

Maybe you can help - download the deb file attached.

To run:
1. install the package
2. turn off bluetooth
#sudo /etc/init.d/bluetooth stop
3. start BT with sixaxis patch (for loading hidd modules)
#sudo /etc/init.d/bluetooth_six start
4. stop BT-six
#sudo /etc/init.d/bluetooth_six stop
5. start hidd mode
#sudo hidd --server --nocheck -n
6. press the ps3 key on the joystick
(you should see something in the terminal)
7. Press Ctrl+C
8. run "jstest /dev/input/js0"

The joystick is registered, but I see no input on jstest

Please Help

---

### Post by falkTX on 2008-11-06
I have completed my task - making sixaxis to work without messing around with Ubuntu

check this how-to:
[http://ubuntuforums.org/showthread.php?t=973112](http://ubuntuforums.org/showthread.php?t=973112)

---

