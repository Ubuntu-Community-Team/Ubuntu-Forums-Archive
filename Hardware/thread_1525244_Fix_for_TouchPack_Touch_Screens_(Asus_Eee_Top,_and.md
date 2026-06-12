---
title: "Fix for TouchPack Touch Screens (Asus Eee Top, and others)"
date: 2010-07-06
forum: Hardware
---

### Post by guywithcable on 2010-07-06
[SIZE=4]Introduction[/SIZE]

After researching this problem for days, I finally found a usable fix  for TouchPack screens in Ubuntu 10.04.

Before you begin, does your touch screen move the cursor to the top left  corner of the screen no matter where you click? If not, then this  method might not work for you. If so, then this method should fix it!

The problem is that the screen reports its coordinates using the Z and  RX axes, instead of the X and Y axes, which the USB HID driver used by  Linux expects. There is a fix already in the driver, but unfortunately  it didn't make it into the kernel used by Ubuntu Lucid Lynx. The fix  flags the device to use a "multi input quirk" mode. (source: [https://patchwork.kernel.org/patch/77055/](https://patchwork.kernel.org/patch/77055/)  )

So, in order to flag the device, we must add an option to the USB HID  driver. (source: [https://bugzilla.redhat.com/show_bug.cgi?id=473144](https://bugzilla.redhat.com/show_bug.cgi?id=473144) )

And we can easily do this using a modprobe script. (source: [http://ubuntuforums.org/showthread.php?t=1175001](http://ubuntuforums.org/showthread.php?t=1175001)  )

[SIZE=4]Instructions[/SIZE]

Open up a terminal and follow these steps:
```
lsusb
```You should see a line similar to this:
> Bus 001 Device 006: ID **1bfd**:**1688** TouchPack  Resistive Touch ScreenThe two numbers in bold after "ID" need to  go into the following command:
```
echo "options usbhid quirks=0x**1bfd**:0x**1688**:0x40" | sudo tee /etc/modprobe.d/usbhid.conf
```When that command runs, you  will be asked for your password, then you should see the options line  repeated back to you.

Now reboot, and your touch screen should work!

[SIZE=4]Supported Devices[/SIZE]

This method was tested on an Asus Eee Top ET1602C, and should work on  ET1602, and any other computer with a TouchPack screen.

---

### Post by WeaponX on 2010-08-17
Not work for me :(


(ASUS ET1602)

---

### Post by drdialtone on 2010-08-21
> **guywithcable said:**
> [SIZE=4]Introduction[/SIZE]

After researching this problem for days, I finally found a usable fix  for TouchPack screens in Ubuntu 10.04.

Before you begin, does your touch screen move the cursor to the top left  corner of the screen no matter where you click? If not, then this  method might not work for you. If so, then this method should fix it!

The problem is that the screen reports its coordinates using the Z and  RX axes, instead of the X and Y axes, which the USB HID driver used by  Linux expects. There is a fix already in the driver, but unfortunately  it didn't make it into the kernel used by Ubuntu Lucid Lynx. The fix  flags the device to use a "multi input quirk" mode. (source: [https://patchwork.kernel.org/patch/77055/](https://patchwork.kernel.org/patch/77055/)  )

So, in order to flag the device, we must add an option to the USB HID  driver. (source: [https://bugzilla.redhat.com/show_bug.cgi?id=473144](https://bugzilla.redhat.com/show_bug.cgi?id=473144) )

And we can easily do this using a modprobe script. (source: [http://ubuntuforums.org/showthread.php?t=1175001](http://ubuntuforums.org/showthread.php?t=1175001)  )

[SIZE=4]Instructions[/SIZE]

Open up a terminal and follow these steps:
```
lsusb
```You should see a line similar to this:
The two numbers in bold after "ID" need to  go into the following command:
```
echo "options usbhid quirks=0x**1bfd**:0x**1688**:0x40" | sudo tee /etc/modprobe.d/usbhid.conf
```When that command runs, you  will be asked for your password, then you should see the options line  repeated back to you.

Now reboot, and your touch screen should work!

[SIZE=4]Supported Devices[/SIZE]

This method was tested on an Asus Eee Top ET1602C, and should work on  ET1602, and any other computer with a TouchPack screen.
Works well for me (and thank you for the info)
The question is how to calibrate????  The left side of the screen is aligned perfectly but the further right I go, the more the cursor drifts left.  Ultimately, a full inch off when the stylus or finger reaches the lower right corner.  I was under the impression that /etc/X11/xorg.conf is not used in 10.04 (even though i can generate it from the shell).
I greatly apreciate any help!!

---

### Post by Harry2o on 2010-09-14
Hi,

unfortunately it doesn't work for me (on 10.04).
I'm using ET1602 (and my lsusb ID is the same), and the fix is without effect. The cursor is still placed at the top left corner.

Any recommendation how to get to the bottom of this?

EDIT:
Interestingly it works, if I unload and reload the module (sudo modprobe -r usbhid; sudo modprobe usbhid).
As a workaround, I implemented this in a init.d-Script (b/c it didn't work in /etc/profile), but this is a lousy hack.

---

### Post by ebbe on 2010-09-17
It worked for me. Ubuntu 10.04 on a ET1610PT.

Btw, on 10.10 beta it works out of the box :)

---

### Post by naugtur on 2010-09-24
I have used this method and it worked at first, but after another reboot (conf file still present) the screen stops working again.

I haven't yet found any pattern in it working or not.

---

### Post by HugoSerrano on 2010-12-10
Hi.
I had the same problem with ET1610PT.

I solved based on Harry2o sugestion.

added to /etc/rc.local (before exit0)

modprobe -r usbhid
modprobe usbhid

---

### Post by ben72 on 2010-12-11
Thanks guywithcable!

This worked for me on a ET1602. I didn't have to modprobe etc..

I upgraded 9.10 -> 10.04 when it stopped working. It worked on another ET1602 when installing 10.04 from scratch.

---

