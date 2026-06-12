---
title: "Will Ubuntu work on the Surface Pro 2 like it did on the original?"
date: 2013-10-27
forum: Hardware
---

### Post by weeman7007 on 2013-10-27
Hi, I was wondering if anyone could answer this before I purchase one. I would have thought that it should work seeing as the Secure Boot feature can still be disabled, although I understand there were WiFi issues with the original Surface Pro so I would imagine that these may still be present in the Pro 2. I understand there is a fix for the original however and am hopeful.

Thanks in advance for your input

---

### Post by radu-banabic on 2013-10-27
Hi. I have the Surface Pro 2 and installed Ubuntu 13.10 on it. The wifi/bluetooth does not work by default. It's the same wifi hardware as before (Marvell 350N), so would I expect the solutions for Surface Pro 1 to work. I tried a few, but could not manage to get the wifi to work. I also manually installed the latest Saucy mainline kernel (v3.11.6), but wifi still does not work. I have some experience with Linux/Ubuntu. I'm currently using my Nexus 4 as a USB modem to access internet; this works out of the box.

---

### Post by gunskilldreams on 2013-10-29
Radu,

Are you using a type cover or a touch cover?  I tried dual booting with Ubuntu 13 and 14 and neither was able to recognize the type cover 2.  Got it to install fine, but it is not fun having to use the on screen keyboard for all the first install stuff.

---

### Post by raphe_g on 2013-11-01
hi radu,
which version of Ubuntu did you use ? (12.04 or 13.10) & ( amd64 OR X86 ).
thanks.

---

### Post by alicia4542 on 2013-11-05
@gubskilldreams: confirmed with Ubuntu 13.10 (standard release and even saucy daily), I am also unable to get my Surface Pro 2 with type cover 2 to work with Ubuntu.  (The keyboard & trackpad are dead, not even the caps lock lights up when pressed, indicating that it is not receiving interrupts and hence a lack of driver support.)  The strangest thing is that the Grub bootloader works properly with the keyboard in the type cover 2, even though it does not work in Ubuntu.

I am able to boot via USB drive the live Ubuntu distribution on my Surface Pro and the pen & touch inputs work great, especially with an external USB keyboard, but the bluetooth+WiFi networking does not work.

I cannot find any info on how to get the Type Cover 2 and networking to work under Ubuntu on my Surface Pro 2.

---

### Post by PointSource on 2013-11-05
I booted SystemRescueCd 3.8.1 off liveUSB, and the keyboard was working well in the console with the default kernel, version 3.4.<something>. I was also getting data out of the touchpad via some device files in /dev/input/, but wasn't able to load X. The input devices seemed to be coming from USB device 045e:07a9 -> manufacturer "MICROSOFT", product name "SAM".

However, the alternate 3.10.x kernel on the same liveUSB lost support for the keyboard and the mouse, but was able to boot to X. It could be a kernel regression.

---

### Post by radu-banabic on 2013-11-06
In installed Ubuntu 13.10 amd64. I get the same behavior as alicia4542 with the type keyboard 2: it works in grub but not in Ubuntu.

---

### Post by alicia4542 on 2013-11-06
> **PointSource said:**
> I booted SystemRescueCd 3.8.1 off liveUSB, and the keyboard was working well in the console with the default kernel, version 3.4.<something>. I was also getting data out of the touchpad via some device files in /dev/input/, but wasn't able to load X. The input devices seemed to be coming from USB device 045e:07a9 -> manufacturer "MICROSOFT", product name "SAM".
However, the alternate 3.10.x kernel on the same liveUSB lost support for the keyboard and the mouse, but was able to boot to X. It could be a kernel regression.
As previously mentioned with Ubuntu 13.10 ISO, with live USB, X windows works great for me with pen and touch inputs on the Surface Pro 2, even though the touch/type cover 2 is dead.

Your assumption of a kernel driver regression for the touch/type cover 2 may likely be true.  But I am not sure how to address this.  Does anyone have any suggestions on a fix for this, such as a different Ubuntu ISO image or a different kernel module for the cover 2 keyboard?

I really hope to be able to get Ubuntu to work with the touch/type cover 2 keyboard+trackpad, while running under a USB flash drive, before I would be confident in wiping out Windows 8.1 from the main internal drive.

Thank you in advance.

---

### Post by ubootfanat on 2013-11-07
Hi Guys, just received my Pro 2 yesterday and installed ubuntu today.

I can confirm that neither wifi nor my touch cover 2 work. Bluetooth seems fine.

For the keyboard

I fully aggree with PointSource.
> **PointSource said:**
>  -> manufacturer "MICROSOFT", product name "SAM"..

the Xorg log shows various entries for the keyboard. It seems that plug and play works. The keyboard is referred to as "MICROSOFT SAM" and is removed and added everytime I snap the keyboard on and off.

the Xorg.log show the following right after snapping the keyboard on:
```
[  1625.773] (II) config/udev: removing device MICROSOFT SAM
[  1625.804] (II) evdev: MICROSOFT SAM: Close
[  1625.804] (II) UnloadModule: "evdev"
[  1626.172] (II) config/udev: Adding input device MICROSOFT SAM (/dev/input/mouse0)
[  1626.172] (II) No input driver specified, ignoring this device.
[  1626.172] (II) This device may have been added with another device file.
[  1626.174] (II) config/udev: Adding input device MICROSOFT SAM (/dev/input/event3)
[  1626.174] (**) MICROSOFT SAM: Applying InputClass "evdev pointer catchall"
[  1626.174] (**) MICROSOFT SAM: Applying InputClass "evdev keyboard catchall"
[  1626.174] (**) MICROSOFT SAM: Applying InputClass "evdev tablet catchall"
[  1626.174] (II) Using input driver 'evdev' for 'MICROSOFT SAM'
[  1626.174] (**) MICROSOFT SAM: always reports core events
[  1626.174] (**) evdev: MICROSOFT SAM: Device: "/dev/input/event3"
[  1626.174] (--) evdev: MICROSOFT SAM: Vendor 0x45e Product 0x799
[  1626.174] (--) evdev: MICROSOFT SAM: Found 3 mouse buttons
[  1626.174] (--) evdev: MICROSOFT SAM: Found relative axes
[  1626.174] (--) evdev: MICROSOFT SAM: Found x and y relative axes
[  1626.174] (--) evdev: MICROSOFT SAM: Found absolute axes
[  1626.174] (--) evdev: MICROSOFT SAM: Found x and y absolute axes
[  1626.174] (--) evdev: MICROSOFT SAM: Found absolute tablet.
[  1626.174] (--) evdev: MICROSOFT SAM: Found keys
[  1626.174] (II) evdev: MICROSOFT SAM: Configuring as tablet
[  1626.174] (II) evdev: MICROSOFT SAM: Configuring as keyboard
[  1626.174] (**) evdev: MICROSOFT SAM: YAxisMapping: buttons 4 and 5
[  1626.174] (**) evdev: MICROSOFT SAM: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1626.174] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input17/event3"
[  1626.174] (II) XINPUT: Adding extended input device "MICROSOFT SAM" (type: KEYBOARD, id 9)
[  1626.174] (**) Option "xkb_rules" "evdev"
[  1626.174] (**) Option "xkb_model" "pc105"
[  1626.174] (**) Option "xkb_layout" "us"
[  1626.174] (WW) evdev: MICROSOFT SAM: touchpads, tablets and touchscreens ignore relative axes.
[  1626.174] (II) evdev: MICROSOFT SAM: initialized for absolute axes.
[  1626.174] (**) MICROSOFT SAM: (accel) keeping acceleration scheme 1
[  1626.174] (**) MICROSOFT SAM: (accel) acceleration profile 0
[  1626.174] (**) MICROSOFT SAM: (accel) acceleration factor: 2.000
[  1626.174] (**) MICROSOFT SAM: (accel) acceleration threshold: 4
```

that looks promising but the keyboard does not work. no input events are fired (tested with xev).

any idea where I can continue with my troubleshoot?

---

### Post by PointSource on 2013-11-07
> **alicia4542 said:**
> Your assumption of a kernel driver regression for the touch/type cover 2 may likely be true.  But I am not sure how to address this.  Does anyone have any suggestions on a fix for this, such as a different Ubuntu ISO image or a different kernel module for the cover 2 keyboard?

Here is the pertinent kernel log chunk from SysRescueCD's v3.4.66 kernel:
```

[   61.954231] usb 2-3: USB disconnect, device number 4
[   61.960162] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[   61.960182] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q41] (Node ffff880119a96438), AE_NOT_FOUND (20120320/psparse-536)
[   62.324511] usb 2-3: new full-speed USB device number 11 using xhci_hcd
[   62.337459] usb 2-3: New USB device found, idVendor=045e, idProduct=07a9
[   62.337469] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   62.337474] usb 2-3: Product: SAM
[   62.337478] usb 2-3: Manufacturer: MICROSOFT
[   62.337482] usb 2-3: SerialNumber: 0.1.0000
[   62.342602] generic-usb 0003:045E:07A9.000A: logical range invalid 0 -1
[   62.342630] generic-usb 0003:045E:07A9.000A: item 0 1 0 11 parsing failed
[   62.342660] generic-usb: probe of 0003:045E:07A9.000A failed with error -22
[   62.345318] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input9
[   62.345710] generic-usb 0003:045E:07A9.000B: input,hidraw0: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input1
[   62.349718] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.2/input/input10
[   62.350018] generic-usb 0003:045E:07A9.000C: input,hiddev0,hidraw7: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input2

```

And from ubuntu's v3.11.0 kernel:
```

[  124.249057] usb 2-3: USB disconnect, device number 5
[  124.259049] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[  124.259072] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q41] (Node ffff880119ab1438), AE_NOT_FOUND (20130517/psparse-536)
[  124.619306] usb 2-3: new full-speed USB device number 12 using xhci_hcd
[  124.637245] usb 2-3: New USB device found, idVendor=045e, idProduct=07a9
[  124.637255] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  124.637260] usb 2-3: Product: SAM
[  124.637264] usb 2-3: Manufacturer: MICROSOFT
[  124.637268] usb 2-3: SerialNumber: 0.1.0000
[  124.650270] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input18
[  124.650541] hid-generic 0003:045E:07A9.000B: input,hidraw1: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input1
[  124.654093] hid-multitouch 0003:045E:07A9.000C: HID_DG_INPUTMODE out of range
[  124.654151] hid-multitouch 0003:045E:07A9.000C: No inputs registered, leaving
[  124.654337] hid-multitouch 0003:045E:07A9.000C: hiddev0,hidraw8: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input2

```
You'll notice that for HID device "0003:045E:07A9.000C", the kernels are loading different hid sub-drivers; "generic-usb" (which I think is now called hid-generic?) vs "hid-multitouch". While multitouch support might be neccesary for the type cover's integrated touchpad, for the time being it'd be better to have the keyboard working. I still haven't figured out how to [unbind and re-bind]("http://lwn.net/Articles/143397/") the device to the other driver yet.

> **alicia4542 said:**
> I really hope to be able to get Ubuntu to work with the touch/type cover 2 keyboard+trackpad, while running under a USB flash drive, before I would be confident in wiping out Windows 8.1 from the main internal drive.

You can dual-boot the Surface, just resize Window's partition down a bit. Don't forget to [create a recovery drive]("http://www.techrepublic.com/blog/windows-and-office/create-a-recovery-drive-in-windows-8/7261/") before you do anything, so you can get back to a clean slate if things go wrong.

> **ubootfanat said:**
> the Xorg log shows various entries for the keyboard. It seems that plug and play works. The keyboard is referred to as "MICROSOFT SAM" and is removed and added everytime I snap the keyboard on and off.

that looks promising but the keyboard does not work. no input events are fired (tested with xev).

any idea where I can continue with my troubleshoot?

If you run: ```
# cat /dev/hidraw8
```
(or the hidraw number that comes from the "hid-multitouch 0003:045E:07A9.xxxx"... line in your kernel log, you'll see that the keyboard and mouse are spewing out data, linux just isn't interpreting it right. The input device that Xorg is registering is actually the windows key capacitive touch button under the screen, as far as I can tell.

As for wifi, this kernel bug: [Bug 64111 - mwifiex_usb USB8797 fails to start]("https://bugzilla.kernel.org/show_bug.cgi?id=64111") seems to indicate it might be a problem with the USB3 controller rather than the wireless card. I haven't tried the steps listed there yet, but I managed to get the device half-working with a firmware extracted from "C:\Windows\System32\drivers\mwlu97w8x64.sys" under Win8.1, but didn't keep it because I was worried messing around with the firmware would do permanent damage to the wireless chip.

---

### Post by ubootfanat on 2013-11-09
> **PointSource said:**
> I still haven't figured out how to [unbind and re-bind]("http://lwn.net/Articles/143397/") the device to the other driver yet.

I second that. I just managed to unbind the driver from the device but am not able to rebind the device.
```
@ echo -n "0003:045E:07A7.xxxx" > /sys/bus/hid/drivers/hid-multitouch/unbind
@ echo -n "0003:045E:07A7.xxxx" > /sys/bus/hid/drivers/hid-generic/bind
bash: echo: write error: No such device
```
Although the device is still listed in /sys/bus/hid/devices.

> **PointSource said:**
> As for wifi, this kernel bug: [Bug 64111 - mwifiex_usb USB8797 fails to start]("https://bugzilla.kernel.org/show_bug.cgi?id=64111") seems to indicate it might be a problem with the USB3 controller rather than the wireless card. I haven't tried the steps listed there yet, but I managed to get the device half-working with a firmware extracted from "C:\Windows\System32\drivers\mwlu97w8x64.sys" under Win8.1, but didn't keep it because I was worried messing around with the firmware would do permanent damage to the wireless chip.

During the udev adventure I saw a device (it seems like the usb3 pci bridge) listed to be operated by the xhci_hcd driver which seems to be the usb3 driver with causes our wifi issues.
```
@ ls /sys/bus/pci/drivers/xhci_hcd/
0000:00:14:0  bind  module  new_id   remove_id   uevent   unbind
```
So I tried unregistering the device from the driver and registering the device to the uhci_hcd driver. But again:
```
@ echo -n "0000:00:14:0" > /sys/bus/pci/drivers/xhci_hcd/unbind; echo -n "0000:00:14:0" > /sys/bus/pci/drivers/uhci_hcd/bind;
bash: echo: write error: No such device
```
Unfortunately, No such device. Any usb-device stopped working so the device and the driver are indeed the pci/usb bridge. Cold restart.

Anyhow, if I can get the rebind to work I may be able to solve both problems, wifi and keyboard, for the session. If they are solvable for the session, one might take a look at udev rules to maybe persist the changes.

Any ideas regarding driver rebind? Or can we intercept the initial driver selection directly via udev rules?

ubootfanat

---

### Post by PointSource on 2013-11-11
I've compiled a custom kernel from Saucy's linux-source-3.11, with:
[LIST]
[*]a disabled CONFIG_USB_XHCI_HCD so that wifi works. No USB 3.0 for you.
[*]and these patches to the HID drivers to make the type cover operational:
[/LIST]
```
diff --git a/drivers/hid/hid-core.c b/drivers/hid/hid-core.c
index e80da62..54f1cdb 100644
--- a/drivers/hid/hid-core.c
+++ b/drivers/hid/hid-core.c
@@ -1869,6 +1869,9 @@ static const struct hid_device_id hid_have_special_driver[] = {
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ZEROPLUS, 0x0030) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ZYDACRON, USB_DEVICE_ID_ZYDACRON_REMOTE_CONTROL) },
 
+/*TYPE COVER 2 INSERTION*/
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2) },
+
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_PRESENTER_8K_BT) },
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_NINTENDO, USB_DEVICE_ID_NINTENDO_WIIMOTE) },
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_NINTENDO2, USB_DEVICE_ID_NINTENDO_WIIMOTE) },
diff --git a/drivers/hid/hid-generic.c b/drivers/hid/hid-generic.c
index e288a4a..fd59518 100644
--- a/drivers/hid/hid-generic.c
+++ b/drivers/hid/hid-generic.c
@@ -24,8 +24,11 @@
 
 #include <linux/hid.h>
 
+#include "hid-ids.h"
+
 static const struct hid_device_id hid_table[] = {
 	{ HID_DEVICE(HID_BUS_ANY, HID_GROUP_GENERIC, HID_ANY_ID, HID_ANY_ID) },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2), .driver_data = 0 },
 	{ }
 };
 MODULE_DEVICE_TABLE(hid, hid_table);
diff --git a/drivers/hid/hid-ids.h b/drivers/hid/hid-ids.h
index f0296a5..34b45a5 100644
--- a/drivers/hid/hid-ids.h
+++ b/drivers/hid/hid-ids.h
@@ -603,6 +603,7 @@
 #define USB_DEVICE_ID_MS_PRESENTER_8K_USB	0x0713
 #define USB_DEVICE_ID_MS_DIGITAL_MEDIA_3K	0x0730
 #define USB_DEVICE_ID_MS_COMFORT_MOUSE_4500	0x076c
+#define USB_DEVICE_ID_MS_TYPE_COVER_2	0x07a9
 
 #define USB_VENDOR_ID_MOJO		0x8282
 #define USB_DEVICE_ID_RETRO_ADAPTER	0x3201

```

You can download the compiled image here: [https://owncloud.staers.homelinux.net/public.php?service=files&t=b5967d8e58e45d5397fe27b56116becf](https://owncloud.staers.homelinux.net/public.php?service=files&t=b5967d8e58e45d5397fe27b56116becf)
But this is my home server, bandwidth speed and capacity is limited, so if someone would be kind enough to re-upload it to a file-sharing site or something, I'd appreciate it.

The HID fix is a hack. Yes, it works (mostly), but I'll file a bug with the kernel developers and see if they can do a better job of it.

Also, [these issues still exist]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1165938/comments/47"):
> ...the wifi works fine until you change the power mode/use the surface without power.
I'm getting a kernel bug at that point which disables the wifi. plugging the power back i does notsolve the issue.
Also the system hangs on the login screen after booting on battery power.

---

### Post by radu-banabic on 2013-11-11
> **PointSource said:**
> I've compiled a custom kernel from Saucy's linux-source-3.11, with:
[LIST]
[*]a disabled CONFIG_USB_XHCI_HCD so that wifi works. No USB 3.0 for you.
[*]and these patches to the HID drivers to make the type cover operational:
[/LIST]


That's great, I can confirm this works. I can connect to wifi and use the Type 2 keyboard cover (not the touchpad on it, though). Please post a link to the bug report after you post it, I'd like to follow it.

---

### Post by PointSource on 2013-11-11
> **radu-banabic said:**
> I can connect to wifi and use the Type 2 keyboard cover (not the touchpad on it, though). Please post a link to the bug report after you post it, I'd like to follow it.

Bug filed at [https://bugzilla.kernel.org/show_bug.cgi?id=64811](https://bugzilla.kernel.org/show_bug.cgi?id=64811).

You can't use the type cover's touchpad? It works for me: single-tap click, two-finger-tap right-click, two-finger scroll, and right- and left-click push-button. Both push-buttons produce a strange "touchpad disabled" notification that does nothing.

edit: actually, both pushbuttons work.

---

### Post by adritoelagil on 2013-11-12
> **PointSource said:**
> I've compiled a custom kernel from Saucy's linux-source-3.11, with:
[LIST]
[*]a disabled CONFIG_USB_XHCI_HCD so that wifi works. No USB 3.0 for you. 
[*]and these patches to the HID drivers to make the type cover operational: 
[/LIST]


Hello,

I use the Surface Pro (1) with Type cover 2. Is that package suitable for me? I am asking because Wifi is working out of the box. It would be nice to know how I can enable just the Type Cover 2.

Thanks in advance

---

### Post by radu-banabic on 2013-11-13
> **PointSource said:**
> You can't use the type cover's touchpad? 

No, I cannot. I get the same touchpad disabled notification when I press the buttons, but I don't see the cursor moving and I don't see any effect of the buttons. It doesn't bother me much, though.

---

### Post by PointSource on 2013-11-13
> **adritoelagil said:**
> I use the Surface Pro (1) with Type cover 2. Is that package suitable for me? I am asking because Wifi is working out of the box. It would be nice to know how I can enable just the Type Cover 2.

If you're prepared to give up USB 3.0 (and that doesn't cause any flow-on problems), then yes, that package will work. Otherwise, you'll need to compile a kernel with the hid patches [specified in the previous post]("http://ubuntuforums.org/showthread.php?t=2183946&p=12844865#post12844865").

---

### Post by gunskilldreams on 2013-11-15
Thanks for the custom kernel.  If I can ever figure out a bootloader for this thing I may get to use it.  Most directions say to install boot-repair, but unless i'm missing something, they are assuming that one has an internet connection first.  Seeing as how there's no connectivity when "trying" the install on a live disk I can't use apt to install it.  I tried manually adding refind , which boots and gives me choices, but it seems the windows boot manager takes over after that and points to the wrong place.  I'm not a linux pro or anything, I'm used to working in it and very rarely have to do customized installs.  How exactly did you all get this to boot to your installation?

Thanks.

---

### Post by ubootfanat on 2013-11-15
> **PointSource said:**
> I've compiled a custom kernel from Saucy's linux-source-3.11, with:
[LIST]
[*]a disabled CONFIG_USB_XHCI_HCD so that wifi works. No USB 3.0 for you.
[/LIST]


well I tried that as well. But I do not seem to get rid of the xhci_hcd driver.
- i followed this simple guide to compile a custom kernel: [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
- in configs I navigated to the xhci_hcd driver and set it to "N"
- I saved the config as .config
- compiled the kernel
- installed the kernel
- rebooted

/boot/config... shows xhci_hcd as not set. the xhci driver is loaded nonetheless.
modprobe -r xhci_hcd reports that the driver is build-in.
Can you point me in the right direction?

and thanks for the kernel. just installed it and I can confirm that wifi works. I might be able to extend your patch to the hid driver to cover the touch cover 2 as well (as soon as I get the kernel compilation to work).

Thanks again!

---

### Post by PointSource on 2013-11-15
> **gunskilldreams said:**
> Thanks for the custom kernel.  If I can ever figure out a bootloader for this thing I may get to use it.  Most directions say to install boot-repair, but unless i'm missing something, they are assuming that one has an internet connection first.  Seeing as how there's no connectivity when "trying" the install on a live disk I can't use apt to install it.  I tried manually adding refind , which boots and gives me choices, but it seems the windows boot manager takes over after that and points to the wrong place.  I'm not a linux pro or anything, I'm used to working in it and very rarely have to do customized installs.  How exactly did you all get this to boot to your installation?

I found I didn't need to use boot-repair, 13.10 was able to install grub in EFI mode and provide an entry for windows just fine.

Yes, the windows boot manager did take over a couple times. When it did, I booted back through the liveUSB, and ran these commands:
```
**# efibootmgr**
...
BootOrder: _0001,0002,0000_
Boot_0000_* USB Drive
Boot_0001_* Windows Boot Manager
Boot_0002_* ubuntu
**# efibootmgr --bootorder _0002,0001,0000_**
...
```

Take note of the underlined bits: you can change the UEFI boot order by re-arranging the comma separated list of boot entry hex-codes.

Although on a fairly regular basis, the Surface will boot to GRUB and the keyboard won't work until ubuntu loads. I've found powering into the BIOS configuration and then restarting again restores keyboard operation.

---

### Post by PointSource on 2013-11-15
> **ubootfanat said:**
> [QUOTE=PointSource;12844865]I've compiled a custom kernel from Saucy's linux-source-3.11well I tried that as well. But I do not seem to get rid of the xhci_hcd driver.
...
Can you point me in the right direction?
[/QUOTE]

I first started compiling custom kernels while I was using debian, and so I've kept to that method. This webpage: [http://debian-handbook.info/browse/squeeze/sect.kernel-compilation.html](http://debian-handbook.info/browse/squeeze/sect.kernel-compilation.html) is a good guide to using the kernel-package program.

As per section 8.10.3, copy in the config from the vanilla saucy kernel, then run "make menuconfig" to go disable xhci. Also, it can be made faster on multicore systems by prepending "CONCURRENCY_LEVEL=<num>".

---

### Post by PointSource on 2013-11-16
Right-click with the Surface Pen can be enabled like this:
[LIST=1]
[*]Find the Pen input's X device:
```
**$ xinput list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
[highlight]&#9116;   &#8627; MICROSOFT SAM                           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; MICROSOFT SAM                           	id=10	[slave  pointer  (2)][/highlight]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer          	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Front LifeCam                           	id=12	[slave  keyboard (3)]
    &#8627; Rear LifeCam                            	id=13	[slave  keyboard (3)]
```
It's one of the "MICROSOFT SAM" devices, usually the first one, but...
[*]Verify you have the correct device:
```
**$ xinput watch-props 9**
Device 'MICROSOFT SAM':
	Device Enabled (134):	1
	Coordinate Transformation Matrix (136):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000
	Device Product ID (251):	1118, 1961
	Device Node (252):	"/dev/input/event6"
	Evdev Axis Inversion (263):	0, 0
	Evdev Axis Calibration (264):	<no items>
	Evdev Axes Swap (265):	0
[highlight]	Axis Labels (266):	"Abs X" (256), "Abs Y" (257), "Abs Pressure" (258)[/highlight]
	Button Labels (267):	"Button Left" (137), "Button Unknown" (254), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141)
	Evdev Middle Button Emulation (268):	0
	Evdev Middle Button Timeout (269):	50
	Evdev Third Button Emulation (270):	0
	Evdev Third Button Emulation Timeout (271):	1000
	Evdev Third Button Emulation Button (272):	3
	Evdev Third Button Emulation Threshold (273):	20
	Evdev Wheel Emulation (274):	0
	Evdev Wheel Emulation Axes (275):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (276):	10
	Evdev Wheel Emulation Timeout (277):	200
	Evdev Wheel Emulation Button (278):	4
	Evdev Drag Lock Buttons (279):	0
^C

```
It will be the only one with a "Pressure" axis
[*]Swap "middle-click" and "right-click" button mappings around:
```
**$ xinput get-button-map 9**
1 2 3 4 5 
**$ xinput set-button-map 9 1 3 2 4 5**
**$ xinput get-button-map 9**
1 3 2 4 5 

```
[/LIST]
The process will need to be repeated every X session.

---

### Post by ubootfanat on 2013-11-16
> **ubootfanat said:**
> I might be able to extend your patch to the hid driver to cover the touch cover 2 as well (as soon as I get the kernel compilation to work).

as promised. Got the kernel compiled. there was just some old stuff residing in the boot directory that prevented the kernel to be properly installed.

anyhow: the touchcover 2 works like a charme by slightly enhancing the changeset proposed by PointSource:
```
diff --git a/drivers/hid/hid-core.c b/drivers/hid/hid-core.c
index e80da62..54f1cdb 100644
--- a/drivers/hid/hid-core.c
+++ b/drivers/hid/hid-core.c
@@ -1869,6 +1869,9 @@ static const struct hid_device_id hid_have_special_driver[] = {
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ZEROPLUS, 0x0030) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ZYDACRON, USB_DEVICE_ID_ZYDACRON_REMOTE_CONTROL) },
 
+/* MS TYPE AND TOUCH COVER 2 INSERTIONS*/
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2) },
+ 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TOUCH_COVER_2) },
+
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_PRESENTER_8K_BT) },
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_NINTENDO, USB_DEVICE_ID_NINTENDO_WIIMOTE) },
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_NINTENDO2, USB_DEVICE_ID_NINTENDO_WIIMOTE) },
diff --git a/drivers/hid/hid-generic.c b/drivers/hid/hid-generic.c
index e288a4a..fd59518 100644
--- a/drivers/hid/hid-generic.c
+++ b/drivers/hid/hid-generic.c
@@ -24,8 +24,11 @@
 
 #include <linux/hid.h>
 
+#include "hid-ids.h"
+
 static const struct hid_device_id hid_table[] = {
 	{ HID_DEVICE(HID_BUS_ANY, HID_GROUP_GENERIC, HID_ANY_ID, HID_ANY_ID) },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2), .driver_data = 0 },
+ 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TOUCH_COVER_2), .driver_data = 0 },
 	{ }
 };
 MODULE_DEVICE_TABLE(hid, hid_table);
diff --git a/drivers/hid/hid-ids.h b/drivers/hid/hid-ids.h
index f0296a5..34b45a5 100644
--- a/drivers/hid/hid-ids.h
+++ b/drivers/hid/hid-ids.h
@@ -603,6 +603,7 @@
 #define USB_DEVICE_ID_MS_PRESENTER_8K_USB	0x0713
 #define USB_DEVICE_ID_MS_DIGITAL_MEDIA_3K	0x0730
 #define USB_DEVICE_ID_MS_COMFORT_MOUSE_4500	0x076c
+#define USB_DEVICE_ID_MS_TOUCH_COVER_2	0x07a7
+#define USB_DEVICE_ID_MS_TYPE_COVER_2	0x07a9
 
 #define USB_VENDOR_ID_MOJO		0x8282
 #define USB_DEVICE_ID_RETRO_ADAPTER	0x3201
```

thanks to PointSource again for working around the issues in the first place!


anyhow: I just am onto a palmblock feature. Created a script that disables the touch input as soon as an event is sent to the deamon. After a certain time, touch is enabled again. The problem is that I have to somehow extract an event which shows me that the stylus is brought to the surface. Has anyone of you an idea on how to trigger a script when there is a motion event coming from the stylus?
[LIST][*]motion event (via xbindkeys) alone will trigger with any mouse input (touchpad, touch and drag, stylus hovering, ...) so that does not work.
[*]Accessing the /dev/input/mouse0 needs root privileges.
[/LIST]
Any other ideas?

---

### Post by gunskilldreams on 2013-11-17
nice, using the efibootmgr worked.  I got into ubuntu, installed the custom kernel, rebooted, within 3 seconds of ubuntu coming up it freezes, every time.  I've wiped the partition, re-installed, went through it all again (strangely enough it worked this time without changing the boot order) and same thing, freezes the os when the new kernel is used , al though if i'm quick i can type and see the keyboard works.  I think it's when it loads the wifi drivers.  It pops up the wifi looking and freezes.

I was messing with this through the live usb before and mounted everything to incorporate the wifi to see if i could straight download before and the that always froze the live setup too.  it seems my surface does not like the ubuntu wifi set up. 


> **PointSource said:**
> I found I didn't need to use boot-repair, 13.10 was able to install grub in EFI mode and provide an entry for windows just fine.

Yes, the windows boot manager did take over a couple times. When it did, I booted back through the liveUSB, and ran these commands:
```
**# efibootmgr**
...
BootOrder: _0001,0002,0000_
Boot_0000_* USB Drive
Boot_0001_* Windows Boot Manager
Boot_0002_* ubuntu
**# efibootmgr --bootorder _0002,0001,0000_**
...
```

Take note of the underlined bits: you can change the UEFI boot order by re-arranging the comma separated list of boot entry hex-codes.

Although on a fairly regular basis, the Surface will boot to GRUB and the keyboard won't work until ubuntu loads. I've found powering into the BIOS configuration and then restarting again restores keyboard operation.

---

### Post by gunskilldreams on 2013-11-18
N/M  After 3 reboots or so it magically stopped freezing and now works fine. Thanks again for the help.

---

### Post by alicia4542 on 2013-11-18
> **PointSource said:**
> I've compiled a custom kernel from Saucy's linux-source-3.11, with:
[LIST]
[*]a disabled CONFIG_USB_XHCI_HCD so that wifi works. No USB 3.0 for you.
[*]and these patches to the HID drivers to make the type cover operational:
[/LIST]
You can download the compiled image here: [https://owncloud.staers.homelinux.net/public.php?service=files&t=b5967d8e58e45d5397fe27b56116becf](https://owncloud.staers.homelinux.net/public.php?service=files&t=b5967d8e58e45d5397fe27b56116becf)
But this is my home server, bandwidth speed and capacity is limited, so if someone would be kind enough to re-upload it to a file-sharing site or something, I'd appreciate it.

The HID fix is a hack. Yes, it works (mostly), but I'll file a bug with the kernel developers and see if they can do a better job of it.

Also, [these issues still exist]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1165938/comments/47"):
Dear PointSource:

Thank you very much for this.  I have wiped Windows 8.1 on my Surface Pro 2 and after installing ubuntu-13.10-desktop-amd64.iso, I then installed your custom kernel.

As mentioned by yourself and others, I confirm that Touch Cover 2 keyboard+touchpad (mouse), touch screen, and pen inputs all work.  As does the Wi-Fi.

However, when I put my Surface Pro 2 in hibernate mode, I cannot wake it up, and I am forced to power cycle (pressing power + volume buttons) it.

Is there a way to invoke sleep mode (not hibernate) which a low power mode that stops the CPU but keeps DRAM power?  I cannot find how to do this.

Also, since I have a VMware licence, I need a copy of the Kernel headers, so that VMware can built its required kernel modules.  I downloaded kernel headers for 3.11.3, these did not match.  Would it be possible for you to share your copy of these headers, since a perfect match is needed?  Thanks.

---

### Post by gunskilldreams on 2013-11-18
nevermind on my nevermind.  This thing has a personality disorder.  I've gotten it to load ubuntu fine maybe 3 times.  All others it freezes within 3 seconds of the gui coming up.  I checked the boot logs, syslogs, kernal logs.  Sometimes the logs just stop in the middle of what looks like specific memory checks, sometimes there are what look like bios warnings.  No one else has freezing issues?

---

### Post by PointSource on 2013-11-19
> **alicia4542 said:**
> I need a copy of the Kernel headers, so that VMware can built its required kernel modules.  I downloaded kernel headers for 3.11.3, these did not match.  Would it be possible for you to share your copy of these headers, since a perfect match is needed? Thanks.

The kernel was compiled from the ubuntu package "linux-source-3.11.0", version 3.11.0-13.20, so the package "linux-headers-3.11.0-13" is the right kernel headers. I'm not sure why when compiled the package produced labels itself 3.11.3.

---

### Post by PointSource on 2013-11-19
> **gunskilldreams said:**
> nevermind on my nevermind.  This thing has a personality disorder.  I've gotten it to load ubuntu fine maybe 3 times.  All others it freezes within 3 seconds of the gui coming up.  I checked the boot logs, syslogs, kernal logs.  Sometimes the logs just stop in the middle of what looks like specific memory checks, sometimes there are what look like bios warnings.  No one else has freezing issues?

Yes, it has a personality disorder. I'd put it down to culture shock, coming from born-and-bred windows to linux.

> **alicia4542 said:**
> However, when I put my Surface Pro 2 in hibernate mode, I cannot wake it up, and I am forced to power cycle (pressing power + volume buttons) it.

Is there a way to invoke sleep mode (not hibernate) which a low power mode that stops the CPU but keeps DRAM power?  I cannot find how to do this.

As far as I know, both of these issues are the wifi's fault.

@gunskilldreams; I've only ever managed to boot it while plugged into the power socket when wifi is enabled.

@alicia4542: blacklisting the mwifiex + mwifiex-usb modules allows the device to suspend correctly.

Hopefully, both of these issues will be sorted out [with a new firmware for the wifi device]("https://bugzilla.kernel.org/show_bug.cgi?id=64111#c8"). I have [had some success with a firmware hacked out of windows]("http://ubuntuforums.org/showthread.php?t=2183946&p=12841231#post12841231"), and can post the instructions to allow one to aquire it if you like, but YMMV and I take no responsibility for anything it might do to your Surface.

---

### Post by gunskilldreams on 2013-11-19
Ahh, it does work if you boot with it charging.  So ubuntu has a power routing issue then?  As if it determined that battery power is not enough to take care of everything AND the wifi card?  So if you don't boot with the charger connected or if you take the charger off while it's running it has no idea what to do and freezes

---

### Post by gunskilldreams on 2013-11-19
so maybe the problems other people have with ubuntu and power management would translate here to, these guys say that the new version of pm-utils caused their issues, and they downgraded to a slightly older version:

[http://ubuntuforums.org/showthread.php?t=1623983&page=2&p=10185265#post10185265](http://ubuntuforums.org/showthread.php?t=1623983&page=2&p=10185265#post10185265)

i'm not at my surface so i can't test it.  Another suggestion is to set acpi=vender in the grub config, again haven't tested it.

---

### Post by gunskilldreams on 2013-11-20
Downgraded the pm-utils on my surface 2.  Boots up without the power plugged in and doesn't freeze, wireless works fine.  Can plug it in or unplug it while running without it freezing.  Don't see any weird side affects from it either.  Seems to work.

---

### Post by alicia4542 on 2013-11-20
> **PointSource said:**
> The kernel was compiled from the ubuntu package "linux-source-3.11.0", version 3.11.0-13.20, so the package "linux-headers-3.11.0-13" is the right kernel headers. I'm not sure why when compiled the package produced labels itself 3.11.3.
Unfortunately after installing "linux-headers-3.11.0-13", VMware is still complaining with this error:
> C header files matching your running kernel were not found.
I am guessing that the kernel version mismatch is likely causing issues.

I will attempt to build a new Surface Pro2 Linux kernel from source with the patches included in this thread.  Has anyone been keeping track of all proposed changes, and seeing which work best?  Maybe this should be in a wiki?

> **gunskilldreams said:**
> Downgraded the pm-utils on my surface 2. Boots up without the power plugged in and doesn't freeze, wireless works fine. Can plug it in or unplug it while running without it freezing. Don't see any weird side affects from it either. Seems to work.
This sounds great.  My system is current configured with pm-utils version "1.4.1-12ubuntu1".  Which version were you able to use to get it to work properly on your surface?

Thanks again for everyone's help.

---

### Post by gunskilldreams on 2013-11-20
I used 1.3.0-1ubuntu1:

[http://packages.ubuntu.com/en/lucid/all/pm-utils/download](http://packages.ubuntu.com/en/lucid/all/pm-utils/download)

---

### Post by alicia4542 on 2013-11-20
I have removed my previous [COLOR=#000000]pm-utils version "1.4.1-12ubuntu1", and installed "[/COLOR][COLOR=#000000]1.3.0-1ubuntu1[/COLOR][COLOR=#000000]", and then rebooted.[/COLOR]

[COLOR=#000000]Unfortunately for me, when I go into sleep mode, my Surface Pro 2 does not wake up, and I need to do a hard reboot (hitting power+volume buttons) to get back into Linux.[/COLOR]

---

### Post by gunskilldreams on 2013-11-21
Oh, I haven't had problems with taking it out of sleep, only with it freezing on boot without the power plugged in or if you were to take the power out after it's booted.  All I could find on your issues were the following links:

[http://askubuntu.com/questions/150613/graphics-cards-not-waking-from-sleep](http://askubuntu.com/questions/150613/graphics-cards-not-waking-from-sleep)

[http://askubuntu.com/questions/207761/ubuntu-will-suspend-but-wont-wake-up](http://askubuntu.com/questions/207761/ubuntu-will-suspend-but-wont-wake-up)

---

### Post by perpe on 2013-11-28
Hello,

many thanks for your efforts. With  PointSource's patch I  got my TypeCover 2 working with my Surface Pro 2. Disabling XHCI got my  wifi working, but it was buggy, same bugs like you have. Disabled wifi  after removing the power supply, usb not working after suspend(if it  goes to suspend mode), hangs on shut down in battery mode.
I have fixed it a little bit with changes in the kernel souce. In drivers/net/wireless/mwifiex/usb.c 
line 518
```
usb_disable_autosuspend(card->udev);
```
to
```
//usb_disable_autosuspend(card->udev);
```
prevents the hang on shut down

line 579
```
    .supports_autosuspend = 1,
```
to 
```
    .supports_autosuspend = 0,
```
(removing that line should also work)
prevents wifi suspend if power supply is removed

afterwards suspend/resume problems still exist. They don't exist with the unmodified kernel, therefore I gave XHCI a second try. Build it as a module, solved my suspend/resume problems. (wifi still works)

---

### Post by jon-network-plumbers on 2013-12-01
perpe,
Just to clarify, using the saucy 3.11.0-13-generic source, you applied the hid patches for the keyboard and made the 2 autosuspend line changes to usb.c and were successful with xhci compiled as a module?  I've just done that with both the saucy 3.11.0-13 and a vanilla 3.12 and neither results in /dev/mlan0 creation.  Is there any other change you were making so that mlan0 would be created with xhci enabled?
(Of note, on a vanilla 3.12 kernel, HID is completely broken with the patches and with xhci compiled as a module, only works if xhci is compiled in)
I also downgraded pm-utils.

What did I miss?  Thanks, Jon

---

### Post by perpe on 2013-12-01
Hello,

Yes, I used the [COLOR=#000000]3.11.0-13-generic source.[/COLOR]
I tried to rebuild my kernel with xhci enabled and didn't succeed. This is a little bit strang, if I build my kernel with xhci enabled via the ncurses menu, then mlan0 isn't available. If I build my kernel with xhci disabled and afterward only xhci with "make CONFIG_USB_XHCI_HCD=m" then xhci works. Enabling xhci from the menu also enables CONFIG_USB_XHCI_PLATFORM, maybe this is the reason?
Don't forget to run depmod, if you build the xhci module this way. 

You should add another change to the usb.c. The mwifiex_usb module misses a rest_resume function and the phy device is recreated after every resume. Adding "[COLOR=#000000].reset_[/COLOR][COLOR=#000000]resume [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] mwifiex_usb_resume[/COLOR][COLOR=#000000]," into the usb_driver mwifiex_usb_driver structure fixes it. (there the support_autosuspend was)
These fixed aren't perfect, [/COLOR][COLOR=#000000]wpa_supplicant crashes after suspend, but is more usable than without[/COLOR][COLOR=#000000]. I'm not a kernel developer ;-)[/COLOR][COLOR=#000000]

[/COLOR]USB on the Surface Pro 2 is completely strange and buggy.

Edit: USB 3 still doesn't work with thiisn hack, but it fixes my shutn down and sleep/resume problems.

Edit 2: "only xhci with "make CONFIG_USB_XHCI_HCD=m" then **xhci works**" should be  "wifi works" ;-)

---

### Post by alfonso-martone on 2013-12-11
Yes, installation worked for my Pro 2 as well (creating recoverydisk, repartitioning, disabling secureboot, installing ubuntu, *"dpkg *.deb" [see below]*, and finally rebooting: type-cover-2 and wifi working, and dual-boot): just throw in a powered USB hub with an ethernet-to-USB adapter, an USB mouse+keyboard and the USB drive with Ubuntu 13.10, and you're a go.

I installed Ubuntu with all "non-free stuff" option and "install updates as well" option (installation with internet, a keyboard and a mouse is easier than doing "USB drive acrobatics").

The two **.deb* files mentioned are the patched kernel presented in this thread and pm-utils version 1.3.0-anything.

At the end of Ubuntu installation, instead of "reboot now" I chose to continue; opened a Terminal, mounted the Linux root on */mnt* and installed there the two files. The *dpkg* must know the root filesystem to be updated (*dpkg* will show a warning about "downgrading", but that's exactly what we want). Something like this *(change /dev/sda5 to your partition)*:
```
sudo mount /dev/sda5 /mnt
sudo dpkg --root=/mnt -i linux-image*.deb
sudo dpkg --root=/mnt -i pm-utils*.deb
sudo umount /mnt
```

After the first reboot, the external keyboard+mouse+ethernet+hub thing is not needed anymore.

I am still experimenting, but some things are indeed interesting:

- the microSD slot of the Surface Pro 2 is a regular "USB drive" that can be used to boot both the Win8.1 recovery "disk" and the Ubuntu installation (my actual "Windows 8.1 Recovery Disk" is an 8 Gb microSD)

- if you keep pressed the "Del" key of the touch/type cover at boot, you will enter the *-uh-oh!-* AMI BIOS where you will see a few options: disable TPM (and manage certificates), and disable SecureBoot. You only need to disable SecureBoot. The login screen will appear red at every boot

- after every manual update (root doing: *apt-get update && apt-get upgrade && apt-get dist-upgrade && apt-get autoremove*) I have to install *again* the two **.deb* files (the "--root" option is not needed; the installer of the kernel will require you to confirm that you *want* to update the kernel on the same-version, or something like that). Automatic updates should be disabled, because a kernel (or pm-utils) update could happen anytime...

- Ubuntu 13.10 boot (from "after Grub" to "desktop and icons") is a matter of some 7 seconds, while the shutdown is somewhat slower.

---

### Post by dnquark on 2013-12-13
So is there anything that's still broken or flaky after pm-utils downgrade and the installing the patched kernel?  Sleep mode, hibernation, etc?  I'd love to get a definitive answer before spending over a $1000 on a machine :)

---

### Post by goepfling on 2013-12-14
Hmm... what? Shelling out a grand for the latest Microsoft hardware (low  RAM and lowest repairability score) to use with a short-term-support  Ubuntu release? Sure?
Note that you are also paying for 200 Gb Microsoft cloud storage, Skype voip-to-home calls, and even a full Windows 8.1 license.

As for all new hardware, Linux support is incomplete.

While I am using the 3.11.3 kernel compiled by [PointSource]("http://ubuntuforums.org/member.php?u=230031") ):P, I cannot file bugs on Launchpad for an "unknown origin" Linux kernel.

Below, a partial list of what I've found.


Hardware/kernel related bugs, both in stock Ubuntu kernel (3.11.0-14) and in PointSource's kernel (3.11.3):

- suspend: hangs everything

- bluetooth: does not work
```
root@surface:~# hcitool inq
Inquiring ...
Inquiry failed.: No such device
root@surface:~# hcitool dev
Devices:
root@surface:~# hcitool scan
Device is not available: No such device
```

- acpi: system temperature is incorrectly read by the kernel ("-271°C", "-269.3°C"...); other values from lm-sensors are correct; for example, dmesg reports:
```
 [    0.722669] ACPI: Thermal Zone [TZ0] (-271 C)
```

- audio works but hdmi audio does not work (the "5+1" mode is mute, and the "stereo" mode stops the kernel audio from working). Using PointSource's kernel I get:
```
[ 1294.179242] Haswell HDMI audio: Mute after set on pin 0x6: [0x0 0x0]
[ 1395.126851] hda-intel 0000:00:1b.0: Unstable LPIB (14110 >= 1764); disabling LPIB delay counting
```

- stock Ubuntu kernel also reports something apparently related to HDMI audio output:```
[    6.493562] HDMI: Unknown ELD version 7
[    6.793389] HDMI: Unknown ELD version 7
[    6.827780] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

- type cover 2: only works with PointSource's kernel and, in that case, at boot time, only works if "cold boot" (i.e.: after a normal "reboot" you cannot do a selection in the grub boot menu)

- wifi does not work with stock Ubuntu kernel

- AMI BIOS of the Surface Pro 2 is broken: early boot messages (both in stock kernel and PointSource's  kernel) say:
```
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.11.0/drivers/iommu/dmar.c:488 warn_invalid_dmar+0x7e/0x90()
[    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.000000] BIOS vendor: American Megatrends Inc.; Ver: 2.03.0550; Product Version: 1
[    0.000000] Modules linked in:
[    0.000000] CPU: 0 PID: 0 Comm: swapper Not tainted 3.11.0-14-generic #21-Ubuntu
[    0.000000] Hardware name: Microsoft Corporation Surface Pro 2/Surface Pro 2, BIOS 2.03.0550 09/25/2013
[    0.000000]  000000000000000b ffffffff81c01de8 ffffffff816e593a ffffffff81c01e30
[    0.000000]  ffffffff81c01e20 ffffffff81061dbd ffffffff81fd001c ffffffff81fd005c
[    0.000000]  0000000000000000 ffff88021fdabbc0 ffffffff81e72000 ffffffff81c01e80
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff816e593a>] dump_stack+0x45/0x56
[    0.000000]  [<ffffffff81061dbd>] warn_slowpath_common+0x7d/0xa0
[    0.000000]  [<ffffffff81061e74>] warn_slowpath_fmt_taint+0x44/0x50
[    0.000000]  [<ffffffff81d401f3>] ? early_ioremap+0x13/0x15
[    0.000000]  [<ffffffff81d36d4e>] ? __acpi_map_table+0x13/0x18
[    0.000000]  [<ffffffff815c446e>] warn_invalid_dmar+0x7e/0x90
[    0.000000]  [<ffffffff81d7b0d4>] check_zero_address+0x68/0xf4
[    0.000000]  [<ffffffff81d7b175>] detect_intel_iommu+0x15/0xae
[    0.000000]  [<ffffffff81d30e24>] pci_iommu_alloc+0x4a/0x6c
[    0.000000]  [<ffffffff81d3fc2c>] mem_init+0x17/0x9c
[    0.000000]  [<ffffffff81d26ccb>] start_kernel+0x1de/0x416
[    0.000000]  [<ffffffff81d268f6>] ? repair_env_string+0x5c/0x5c
[    0.000000]  [<ffffffff81d26120>] ? early_idt_handlers+0x120/0x120
[    0.000000]  [<ffffffff81d265de>] x86_64_start_reservations+0x2a/0x2c
[    0.000000]  [<ffffffff81d266e8>] x86_64_start_kernel+0x108/0x117
[    0.000000] ---[ end trace de0668eb4418ce5b ]---
```


External display related bugs:

- power management: display is not switched off after blanking; note:  when using an external display, the built-in display is correctly  switched off when selecting "off" in System settings / Displays / Built-in;

- external display: when it reports the same resolution of the internal  display, it should default to "mirror displays" instead of "extended  desktop"

- pen input is not disabled when the built-in display is switched off (i.e. when using only an external display)

- pen: when attaching an external display, its work area gets   incorrectly recalculated/extended (correct behaviour: should always   depend on built-in display resolution: either 1920x1080 or "rotated to   1080x1920", not the 3840x1080 virtual desktop)


Software/settings related bugs:

- type cover 2 backlighting remains "on" when built-in display is "off" (expected behavior: kernel should handle its backlighting)

- pen: works but does not disable multitouch while in use (your hand cannot rest on the screen)

- power management utilities: pm-utils package has to be downgraded to  1.3.xx (every time you update packages,  remember to update "again"  PointSource's kernel and pm-utils; if you forget it, Ubuntu  will always hang when  loading the desktop)


Bugs related to PointSource's kernel:

- usb 3.0 support disabled

- wifi works but emits "-ENOSR" errors from time to time (should be corrected on next Marvell firmware update)
```
 [  654.426391] usb 1-1.2: data: -ENOSR is returned
```


Bugs not yet fully explored:

- built-in display brightness: sometimes it defaults to 100% at boot (apparently System Settings does not save the last state, but it seems due to external monitor plugging/unplugging)

- sometimes sound does not work after a reboot (apparently a consequence of trying the HDMI audio output)

- microSD slot: only works with stock Ubuntu kernel (thus it means it is connected to the internal USB3.0 hub)

- battery: sometimes the battery is incorrectly reported as "absent" (both on battery and on AC power), until next cold reboot (apparently something happened between upgrading to pm-utils 1.4 and downgrading to pm-utils 1.3)

- the vibration feedback of the hardware "Windows key" doesn't seem software-controllable.

---

### Post by PointSource on 2013-12-15
> **goepfling said:**
> Hardware/kernel related bugs, both in stock Ubuntu kernel (3.11.0-14) and in PointSource's kernel (3.11.3):
- suspend: hangs everything
- bluetooth: does not work
Yes, issues with the WiFi. I've taken to:[LIST]
[*]blacklisting the mwifiex and mwifiex-usb modules for now:
```
# echo "blacklist mwifiex" > /etc/modprobe.d/blacklist-mwifiex.conf
# echo "blacklist mwifiex-usb" >> /etc/modprobe.d/blacklist-mwifiex.conf
```
[*]carrying around a USB WiFi adapter,
[*]and "modprobe mwifiex-usb"-ing when that's more convenient, on the proviso that I have to shutdown instead of suspend the Surface after it's use.
[/LIST]

> **goepfling said:**
> - microSD slot: only works with stock Ubuntu kernel (thus it means it is connected to the internal USB3.0 hub)
I wondered why that wasn't working for me...

> **goepfling said:**
> - pen: when attaching an external display, its work area gets   incorrectly recalculated/extended (correct behaviour: should always   depend on built-in display resolution: either 1920x1080 or "rotated to   1080x1920", not the 3840x1080 virtual desktop)
If your set-up is: [built-in] LEFT-OF [external], and they're both 1080p, then manipulating the "Coordinate Transformation Matrix" for pen and touch input can fix the positioning mismatch:
```
xinput set-prop <ID> 136 0.5 0 0 0 1 0 0 0 1
```
where <ID> is the ID of the pen (one of "MICROSOFT SAM") or touch ("Atmel Atmel maXTouch Digitizer") device, according to [http://ubuntuforums.org/showthread.php?t=2183946&p=12849196#post12849196](http://ubuntuforums.org/showthread.php?t=2183946&p=12849196#post12849196). See [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation) and [https://wiki.archlinux.org/index.php/Calibrating_Touchscreen](https://wiki.archlinux.org/index.php/Calibrating_Touchscreen) for more info.

Many thanks to goepfling for the extensive buglist. :)

---

### Post by tlnlion on 2013-12-16
Thanks PointsSource for the patches!

Is it possible to fix the microSD card problem without disabling wifi? the onboard memory is too small to live with.

Also is there a way to get right click by long press on the touch screen?

---

### Post by goepfling on 2013-12-16
1)  Start Windows 8.1 to do some clean-up:
- erase the "shadow copy" file (will free some gigabytes on the Windows partition) using *wmic* in Administrator mode:
```
vssadmin list shadowstorage
wmic
    shadowcopy delete
    exit
```
- erase the hibernation file (you won't ever need to hibernate, won't you? and it will free some extra gigabytes on the Windows partition):
```
powercfg /hibernate off
```
- then create a Recovery disk (8Gb USB drive required: it will free the 6.9 gigabytes Recovery partition; then keep the 8Gb USB drive in your safest safe!)
- and finally (after *cleanmgr* and *dfrgui)* shrink the Windows partition to accomodate a Linux partition.


2) You don't need to place your multimedia files (videos, MP3s) on *both* partitions.

If you place them on Windows partition and want to access them from Ubuntu, you should add to your */etc/fstab* a line to mount the Windows partition on some local Linux directory:
```
/dev/sda4   /windows    ntfs-3g   defaults,user,ro   0  0
```
I suggest to not to use read-write mode with "user" (non-root) access.
Note: I cannot guarantee that Windows is "actually" unable to peek in ext4 filesystems and send to Microsoft NSA Cloud your secret directories (LOL).  :D

"Right-click" using pen long press:
- install *mousetweaks* package
- press the Windows *(uh-oh)* key (the Surface will vibrate for a moment) and search for Startup Applications
- add an entry:
name:     pen right click
command:  mousetweaks --ssc --ssc-time=0.7 --daemonize
comment:  emulate right click after 0.7 seconds of pen pressed

"Expose windows":
press the Windows *(erm...)* key and search for CompizConfig Settings (ouch! Ubuntu 13.10 still has Compiz?!?) and in the Window Management / Scale / Bindings section, select Initiate Window Picker For All Windows (the one with the display icon) and select the center top area (top left will only work with a mouse) and allow it to disable some useless "Flip" effect. Now, use the pen to move the cursor to the highest pixel of the center top area and... pronto! the window picker for all windows. Excellent when you use two or more browsers on the same web chat to impersonate two different people trolling and fighting each other (LOL) :D

---

### Post by goepfling on 2013-12-23
Bugs, bugs, bugs!!

Movies: *mplayer2* cannot show full-screen videos (hangs for some seconds every few frames):
```
[31814.040889] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[31814.040918] [drm:i915_hangcheck_elapsed] *ERROR* no progress on render ring
[31814.041037] [drm:i915_set_reset_status] *ERROR* render ring hung flushing bo (0x88d000 ctx 0) at 0xe03538
```

Switched to *mplayer* but it shows the same problem.

*VLC* works (because it doesn't require the "full screen": it just creates a... full-screen window), but after full-screen video playing, the pointer cursor does not appear again. As this happens also with *UrbanTerror,* I guess it is a Xorg problem. To get the cursor again without rebooting, just switch to a text-console (ctrl-alt-F2) and from there then get into Xorg again (alt-f7), or enter the "screenshot area select" and then press Esc.

The *xhci* (USB 3.0 support) is compiled in the kernel: you cannot disable it, neither from kernel command-line nor from kernel unloading, and the following command has no effect:
```
echo 'SUSPEND_MODULES="xhci"' >> /etc/pm/config.d/unload_module
```


Suggestions:

Skype text font in the chat is tiny: edit your *~/.config/Trolltech.conf* and use the *Ubuntu,14* font (or even bigger), then start Skype again.
```
[Qt]
font="Ubuntu,14,-1,5,50,0,0,0,0,0"[/nocode]
As usual, you can login with more than one account (multiple Skype instances):
[code]alias skype2='skype --dbpath=~/.Skype2'
```

VirtualBox: after installing both *virtualbox-qt* and *virtualbox-guest-additions-iso* packages, you still need Oracle's Extpack to access the USB 2.0 gadgets from virtual machines:
[oracle.com: download VirtualBox 4.2 extpack]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack")

The most ancient ethercard supported by VirtualBox is a PCnet PCI-based thing which was supported since Linux 2.0.7: I installed Slackware '96 virtual box (a 4Mb RAM Linux server on my ubuntified Surface!) but it came with Linux 2.0.0, so no networking out of the box.

Arrrgh, *pcsxr 1.9.92* does not work: "BadAlloc (insufficient resources for operation)... error_code 11 request_code 149 minor_code 19)". The latest release (1.9.93) has a fix but is not yet available in Ubuntu repositories. Thanks to this bug, I found that the Surface Pro 2 supports Unity 3D passing all tests:
```
/usr/lib/nux/unity_support_test -p
```

Character recognition: *cellwriter* does its job; install it, lock it to Launcher, and change its installation defaults to:
- interface: dimensions: cells 58 by 96 pixels, grid 16 by 4 cells, keyboard 1000 pixels wide
- recognition: 10 samples per character (and you may want to disable English word context)
Then train some characters and go on experimenting.
Note: it still has a bug (it assumes that its icon appears on the top bar, but it doesn't...).

Note-taking: *xournal* works great... except the eraser tip. Install *xournal* and configure it to:
- view: one page; zoom: normal size
- page: set page style to "ruled" (we should apply for a feature request: "larger ruled")
- page: set page size to "custom: pixels: 1850 x 945 pixels" and then "save as default"
- options: enable pressure sensitivity (and use the "thick" tip) and autosave
- you may want to enable "tools / shape recognizer" as well for drawing rectangles
It would be great to disable touch when *xournal* is the active window. I proudly remember ten years ago note-taking with a tablet PC and a pen, with my hand resting on the screen all the time...

I also loved that indicator-multiload applet to have CPU and network graphing on the top left of the screen: most of the time only a single core is working (this is why after a few minutes working on battery, I still see "battery: 100%, 6:56 remaining").

Firewall and services: just run *sudo gufw* and disable everything you don't need. I do not have printers and do not need them, so I uninstalled *cups* (I found *cups* only because *gufw* listed it in listening services).

Command-line stuff: I've been using a Mac for a few years, so I added to my .bash_aliases the pastebuffer copy (its standard input goes to the "copy/paste" buffer) and pastebuffer paste (puts on stdout the "copy/paste" buffer). Good when you work with your terminal:
```
alias pbcopy='xsel --clipboard --input'
alias pbpaste='xsel --clipboard --output'
```

I also happen to love some logging at boot, so I wiped the "splash" option in the */etc/default/grub* kernel args string (but -sigh!- grub themes do not work):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```
```
sudo update-grub
sudo grub-install
```

---

### Post by goepfling on 2013-12-23
The installed Linux kernel supports the SSD TRIM feature:
```
sudo hdparm -I /dev/sda | grep TRIM
  *  Data Set Management TRIM supported (limit 8 blocks)
```

I added a line in the root's *crontab* to perform the TRIM on the 35th minute of every hour (I read that a daily operation was sufficient, maybe I'm a bit too paranoid about it):
```
# m h  dom mon dow   command
35  *  *   *   *     /sbin/fstrim -v /
```

It's a Good Thing© to let the SSD know discarded bytes (sectors not accessed anymore after some disk write operation) for its "wearing" management. The first time *fstrim* will require a few seconds because we never executed it before.

---

### Post by goepfling on 2013-12-24
I tried Ubuntu 14.04 Alpha (20131222). It is a "development" release, "alpha" quality (i.e.: bugs and inconsistencies everywhere). I tried it to see if recent kernel and software releases would solve the most annoying problems found with Ubuntu 13.10, but it appears we're far from a decent Ubuntu installation.

To install without wiping out the partition of the previous 13.10 installation, the trick was to move all directories (except the *lost+found* one) in a temporary directory (so that my */dev/sda5* only showed "lost+found" and "mydata") and then installing on it without formatting. Same trick for restoring another installation (but if you forget something... prepare for apocalyptic crashes and data losses).

Booting and installing required an USB hub with an USB ethernet adapter and an USB keyboard+mouse (mouse is not necessary because touch and pen work out of the box), because wifi and touch cover do not work.

The *pm-utils* version is 1.4.1-13 (it did not require "downgrading" to 1.3.0, like previous Ubuntu 13.10 release). I guess the problem was not in *pm-utils* but in the kernel.

The *efibootmgr* after the installation (before rebooting) correctly shows "ubuntu" (that is: grub menu) as the first thing to start at boot (but it could be due to previous install).

The only **funny bug of the installer** is that if you select *Vatican (Holy See)* as your state, it switches to *Ivory Coast* for package mirror and GMT clock, as it did on Ubuntu 13.10.

This Ubuntu 14.04 Alpha ships kernel version 3.12.0: this kernel release only solves the HDMI stereo output bug and the *pm-utils* freeze.

The default installed user interface is not Unity3D (yep, this is a "development" release, "alpha" quality, not a production release; tomorrow's another day).

**Linux kernel warnings and errors:**

The 3.12.0 does not yet handle the broken AMI BIOS "DMAR" thing. I don't know if this has effects anywhere except the *dmesg* thing below:
```
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.12.0/drivers/iommu/dmar.c:488 warn_invalid_dmar+0x7e/0x90()
[    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.000000] BIOS vendor: American Megatrends Inc.; Ver: 2.03.0550; Product Version: 1
[    0.000000] Modules linked in:
[    0.000000] CPU: 0 PID: 0 Comm: swapper Not tainted 3.12.0-7-generic #15-Ubuntu
[    0.000000] Hardware name: Microsoft Corporation Surface Pro 2/Surface Pro 2, BIOS 2.03.0550 09/25/2013
[    0.000000]  000000000000000b ffffffff81c01de8 ffffffff81711aee ffffffff81c01e30
[    0.000000]  ffffffff81c01e20 ffffffff8106432d ffffffff81fd101c ffffffff81fd105c
[    0.000000]  0000000000000000 ffff88021fdabbc0 ffffffff81e74000 ffffffff81c01e80
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff81711aee>] dump_stack+0x45/0x56
[    0.000000]  [<ffffffff8106432d>] warn_slowpath_common+0x7d/0xa0
[    0.000000]  [<ffffffff810643e4>] warn_slowpath_fmt_taint+0x44/0x50
[    0.000000]  [<ffffffff81d4b99f>] ? early_ioremap+0x13/0x15
[    0.000000]  [<ffffffff81d41e1a>] ? __acpi_map_table+0x13/0x18
[    0.000000]  [<ffffffff815ec5ce>] warn_invalid_dmar+0x7e/0x90
[    0.000000]  [<ffffffff81d86ad8>] check_zero_address+0x68/0xf4
[    0.000000]  [<ffffffff81d86b79>] detect_intel_iommu+0x15/0xae
[    0.000000]  [<ffffffff81d3bead>] pci_iommu_alloc+0x4a/0x6c
[    0.000000]  [<ffffffff81d4b3d0>] mem_init+0x17/0x9c
[    0.000000]  [<ffffffff81d31ccb>] start_kernel+0x1de/0x41f
[    0.000000]  [<ffffffff81d318f6>] ? repair_env_string+0x5c/0x5c
[    0.000000]  [<ffffffff81d31120>] ? early_idt_handlers+0x120/0x120
[    0.000000]  [<ffffffff81d315de>] x86_64_start_reservations+0x2a/0x2c
[    0.000000]  [<ffffffff81d316e8>] x86_64_start_kernel+0x108/0x117
[    0.000000] ---[ end trace 6d9bbe62d12e6bb1 ]---
```

Thermal zone: still reports a funny near-zerokelvin temperature, like in 13.10:
```
[    0.870858] [Firmware Bug]: Invalid critical threshold (86)
[    0.872995] thermal LNXTHERM:00: registered as thermal_zone0
[    0.873000] ACPI: Thermal Zone [TZ0] (-269 C)
```

Another "exclamation marked" warning in the *dmesg:*
```
[    0.873057] GHES: HEST is not enabled!
```

Some ACPI warnings, don't know if related to other problems:
```
[    3.203612] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20130725/utaddress-251)
[    3.203620] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.203626] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20130725/utaddress-251)
[    3.203630] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20130725/utaddress-251)
[    3.203634] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.203635] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20130725/utaddress-251)
[    3.203639] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20130725/utaddress-251)
[    3.203642] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.203644] lpc_ich: Resource conflict(s) found affecting gpio_ich
```

TypeCover2: lights up but does not work, like in previous Ubuntu 13.10: maybe the issue is the HID_DG_INPUTMODE thing (using a kernel with *xhci* disabled makes it work flawless):
```
[    3.453994] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input3
[    3.454585] hid-generic 0003:045E:07A9.0002: input,hidraw0: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input1
[    3.455467] hid-multitouch 0003:045E:07A9.0003: HID_DG_INPUTMODE out of range
[    3.455511] hid-multitouch 0003:045E:07A9.0003: No inputs registered, leaving
```

Another Human Interface Device failed (orientation sensor):
```
[    3.472525] hid_sensor_magn_3d HID-SENSOR-200083.0: failed to setup attributes
[    3.472537] hid_sensor_magn_3d: probe of HID-SENSOR-200083.0 failed with error -1
```

Some extra mistery:
```
[    3.579254] init: failsafe main process (601) killed by TERM signal
```

Something in the *udevd* configuration is not tuned yet:
```
[    3.812478] systemd-udevd[360]: Error calling EVIOCSKEYCODE: Invalid argument
[    3.812483] systemd-udevd[360]: Error calling EVIOCSKEYCODE: Invalid argument
[    3.812490] systemd-udevd[360]: Error calling EVIOCSKEYCODE: Invalid argument
```

Wifi does not work, as already happened in Ubuntu 13.10:
```
[    4.597763] usb 2-2: USB disconnect, device number 3
[    4.597818] mwifiex_usb: mwifiex_usb_disconnect: card or card->adapter is NULL
[   10.408258] usb 2-2: WLAN FW is active
[   22.673947] usb 2-2: mwifiex_cmd_timeout_func: Timeout cmd id (1387740121.182604) = 0x3, act = 0x0
```

The audio section shows some warnings, but works and... **good!** HDMI stereo audio output now works:
```
[    5.770913] hda_codec: invalid CONNECT_LIST verb 5[1]:0
[    5.771031] hda_codec: invalid CONNECT_LIST verb 7[1]:0
[    5.774234] HDMI: Unknown ELD version 7
[    5.777779] HDMI: Unknown ELD version 7
[    5.779579] HDMI: Unknown ELD version 7
```

Bluetooth does not work, like in previous Ubuntu 13.10; funny thing, the internal bluetooth adapter was seen as *hc1* (host controller 1 instead of 0), gave a warning, but actually worked for device scanning:
```
[   12.418712] Bluetooth: hci1 command 0x0c14 tx timeout
```


**First installation: update packages...**

Installation went flawless. I also checked that the partitioning had correctly aligned offset (all zeros), using this command:
```
blockdev --getalignoff /dev/sda?
```

The installation of this release of Ubuntu 14.04 Alpha required some 80 megs updates at boot (because I selected the "non-free stuff").

Hmm... not all packages are actually ready (and you may wonder why some *systemd* stuff is in Ubuntu 13.10 and 14.04):
```
[  214.430642] systemd-hostnamed[2109]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

I installed my usual stuff, including *LyX* and *TeX* and, after that, more than 500 Mb could be freed removing its... documentation!
```
sudo apt-get remove texlive-latex-extra-doc texlive-latex-recommended-doc texlive-latex-base-doc texlive-pictures-doc
```

Ach! Ubuntu 14.04 still ships Xorg, Gnome-control-center and usual stuff. I regret that Mir is not yet here.

System Settings (aka: gnome-control-center): I wonder why the "Wacom tablet" menu is not a submenu of a (needed!) "Pen and touch" menu.
It would be **Very Good®** to have there an option to disable "touch" and only leave "pen" enabled.

I also wonder why the Landscape Service is there in every Ubuntu install, even if 99.9% of Ubuntu users won't ever choose it.

Alas, *mplayer2* still has issues playing in full-screen a less-than-fullHD video, because some direct rendering manager thing still has its "ring stuck"...
```

[ 5007.575725] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5011.573505] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5015.547270] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5019.545038] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5023.542790] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5037.523017] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5041.532759] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5045.530527] [drm:ring_stuck] *ERROR* Kicking stuck wait on render ring
[ 5045.530543] [drm] no progress on render ring
[ 5045.530546] [drm] capturing error event; look for more information in /sys/class/drm/card0/error
[ 5045.557215] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x1864000 ctx 0) at 0x186402c
```
UPDATE: reverting to the old *mplayer* fixes the problem (but only in 14.04, not in Ubuntu 13.10).

Hmm... time to build a wiki "Ubuntu on Surface Pro 2" ?

---

### Post by PointSource on 2014-01-09
Good news, everybody! The [bug affecting the wifi in the Surface Pro 2]("https://bugzilla.kernel.org/show_bug.cgi?id=64111") has been solved. Bing Zhao, a kernel dev from Marvell, [has released a new firmware image]("http://git.marvell.com/?p=mwifiex-firmware.git;a=commit;h=20e4d14b2c4f19afd766109621414781fc3ac050"), which you can download from here:

[http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin;h=196379881310cba56e4fc5482d82e73008226cde;hb=73217084ea2a3b1eaa505ad87fb4771009860293](http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin;h=196379881310cba56e4fc5482d82e73008226cde;hb=73217084ea2a3b1eaa505ad87fb4771009860293)

This fix will probably be integrated into the mainline linux-firmware in the near future, but for now you need to add it to /lib/firmware/mrvl/ manually.

However, the new firmware needs USB 3.0 to operate correctly, so I've rolled a new, up-to-date 3.11.0-15 kernel with the type2/touch2 cover hackfixes and included USB 3.0:
linux-image: [https://owncloud.staers.homelinux.net/public.php?service=files&t=9b4b7ebd62fc34200463a948d0a15e3f](https://owncloud.staers.homelinux.net/public.php?service=files&t=9b4b7ebd62fc34200463a948d0a15e3f)
linux-headers: [https://owncloud.staers.homelinux.net/public.php?service=files&t=5526b0037f21dab6462fa5250d5e466f](https://owncloud.staers.homelinux.net/public.php?service=files&t=5526b0037f21dab6462fa5250d5e466f)

Once again, if someone wouldn't mind mirroring these to a filesharing service, it'd be greatly appreciated.

---

### Post by easyxtarget on 2014-01-10
So how do we get the fixes for the Type Cover 2 added into the kernel by the time 14.04 ships?

---

### Post by goepfling on 2014-01-15
> **PointSource said:**
> Good news, everybody!

Yes: using PointSource's kernel, I see wifi, typecover2, bluetooth (see below), microSD slot, typecover2 working.
VirtualBox stuff gets correctly re-compiled by DKMS.

And I just found that the current kernel/pm_utils release does not freeze anymore (no need to downgrade to *pm_utils 1.3),* after both warm and cold reboots.

Note 1: remember to rename the firmware blob file to: */lib/firmware/mrvl/usb8797_uapsta.bin*

Note 2: remember to delete the */etc/modprobe.d/blacklist-mwifiex.conf* if you had one (following the old guidelines in late 2013).


Bluetooth problems:

- I tried to pair a Logitech M555b bluetooth mouse: Ubuntu reports "paired OK" but the mouse still flashes the "pairing" LED; any "PIN options" gives the same result, not even an event is transmitted. The same mouse works flawless on an Ubuntu 12.04 box with a cheap USB bluetooth dongle

- I tried to pair a Nokia N900 phone: file browsing works, PAN works (requires some scripts on the phone and command-line activation), DUN is not enabled (only gets a "timeout"). Everything including DUN works flawless on an Ubuntu 12.04 box with a cheap USB bluetooth dongle

- same results after rebooting, same results after purging the /var/lib/bluetooth/28:18:78* directory (to reset bluetooth to fresh install state), same results after cold reboot.

- I also tried an USB bluetooth dongle on the Surface with stock Ubuntu kernel and got the same problems.

---

### Post by goepfling on 2014-01-16
"Wifi works", yes, but after some hours (and lots of "ENOSR"), a kernel "oops" happens and wifi stops working until next reboot. This means that the Surface has to be rebooted at least every day. How do I send this *dmesg* to Zhao?

```
[85989.067422] usb 2-2: data: -ENOSR is returned
[86183.259202] usb 2-2: data: -ENOSR is returned
[86414.827719] usb 2-2: data: -ENOSR is returned
[86987.593510] usb 2-2: mwifiex_cmd_timeout_func: Timeout cmd id (1389898325.385738) = 0xa4, act = 0x0
[86987.593524] usb 2-2: num_data_h2c_failure = 0
[86987.593527] usb 2-2: num_cmd_h2c_failure = 0
[86987.593528] usb 2-2: num_cmd_timeout = 1
[86987.593530] usb 2-2: num_tx_timeout = 0
[86987.593532] usb 2-2: last_cmd_index = 1
[86987.593534] usb 2-2: last_cmd_id: 16 00 a4 00 16 00 a4 00 7f 00
[86987.593536] usb 2-2: last_cmd_act: 00 00 00 00 00 00 00 00 00 00
[86987.593537] usb 2-2: last_cmd_resp_index = 0
[86987.593539] usb 2-2: last_cmd_resp_id: 16 80 7f 80 16 80 a4 80 7f 80
[86987.593541] usb 2-2: last_event_index = 3
[86987.593543] usb 2-2: last_event: 17 00 2b 00 17 00 2b 00 03 00
[86987.593544] usb 2-2: data_sent=0 cmd_sent=0
[86987.593546] usb 2-2: ps_mode=1 ps_state=0
[86987.593552] usb 2-2: cmd timeout
[86987.593577] usb 2-2: failed to get signal information
[86997.604016] usb 2-2: mwifiex_cmd_timeout_func: Timeout cmd id (1389898335.401800) = 0xa4, act = 0x0
[86997.604021] usb 2-2: num_data_h2c_failure = 0
[86997.604023] usb 2-2: num_cmd_h2c_failure = 0
[86997.604024] usb 2-2: num_cmd_timeout = 2
[86997.604026] usb 2-2: num_tx_timeout = 0
[86997.604027] usb 2-2: last_cmd_index = 2
[86997.604029] usb 2-2: last_cmd_id: 16 00 a4 00 a4 00 a4 00 7f 00
[86997.604031] usb 2-2: last_cmd_act: 00 00 00 00 00 00 00 00 00 00
[86997.604032] usb 2-2: last_cmd_resp_index = 0
[86997.604033] usb 2-2: last_cmd_resp_id: 16 80 7f 80 16 80 a4 80 7f 80
[86997.604035] usb 2-2: last_event_index = 3
[86997.604036] usb 2-2: last_event: 17 00 2b 00 17 00 2b 00 03 00
[86997.604038] usb 2-2: data_sent=0 cmd_sent=1
[86997.604039] usb 2-2: ps_mode=1 ps_state=0
[86997.604060] usb 2-2: cmd timeout
[86997.604070] usb 2-2: failed to get signal information
[86997.604333] ------------[ cut here ]------------
[86997.604343] WARNING: CPU: 0 PID: 13228 at drivers/usb/core/urb.c:327 usb_submit_urb+0x3be/0x3d0()
[86997.604346] URB ffff88021202f840 submitted while active
[86997.604348] Modules linked in: snd_seq_dummy(F) pci_stub(F) vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) btusb(F) snd_hda_codec_hdmi(F) snd_hda_codec_realtek(F) hid_logitech(F) ff_memless(F) usb_storage(F) xt_hl(F) ip6t_rt(F) nf_conntrack_ipv6(F) nf_defrag_ipv6(F) ip6t_REJECT(F) xt_LOG(F) xt_limit(F) xt_tcpudp(F) xt_addrtype(F) nf_conntrack_ipv4(F) nf_defrag_ipv4(F) xt_conntrack(F) joydev(F) mwifiex_usb(F) mwifiex(F) ipt_REJECT(F) hid_multitouch(F) hid_generic(F) uvcvideo(F) videobuf2_vmalloc(F) ip6table_filter(F) videobuf2_memops(F) cfg80211(F) videobuf2_core(F) ip6_tables(F) videodev(F) nf_conntrack_netbios_ns(F) nf_conntrack_broadcast(F) nf_nat_ftp(F) usbhid(F) nf_nat(F) hid(F) nf_conntrack_ftp(F) nf_conntrack(F) iptable_filter(F) ip_tables(F) x_tables(F) tpm_infineon(F) x86_pkg_temp_thermal(F) kvm_intel(F) kvm(F) crct10dif_pclmul(F) crc32_pclmul(F) ghash_clmulni_intel(F) aesni_intel(F) aes_x86_64(F) lrw(F) gf128mul(F) glue_helper(F) ablk_helper(F) cryptd(F) rfcomm(F) bnep(F) bluetooth(F) microcode(F) snd_hda_intel(F) snd_hda_codec(F) snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) binfmt_misc(F) snd_seq(F) snd_seq_device(F) snd_timer(F) i915(F) snd(F) lpc_ich(F) tpm_tis(F) drm_kms_helper(F) video(F) mac_hid(F) drm(F) i2c_algo_bit(F) soundcore(F) mei_me(F) mei(F) nls_iso8859_1(F) coretemp(F) lp(F) parport(F) ahci(F) libahci(F)
[86997.604444] CPU: 0 PID: 13228 Comm: kworker/0:0 Tainted: GF         IO 3.11.10 #2
[86997.604447] Hardware name: Microsoft Corporation Surface Pro 2/Surface Pro 2, BIOS 2.03.0550 09/25/2013
[86997.604459] Workqueue: MWIFIEX_WORK_QUEUE mwifiex_main_work_queue [mwifiex]
[86997.604461]  0000000000000009 ffff880075159c78 ffffffff816e6492 ffff880075159cc0
[86997.604465]  ffff880075159cb0 ffffffff81061d1d ffff880213d7bc00 ffff880210a5a000
[86997.604468]  0000000000000001 ffff8802120e263c 0000000000008000 ffff880075159d10
[86997.604471] Call Trace:
[86997.604478]  [<ffffffff816e6492>] dump_stack+0x45/0x56
[86997.604483]  [<ffffffff81061d1d>] warn_slowpath_common+0x7d/0xa0
[86997.604486]  [<ffffffff81061d8c>] warn_slowpath_fmt+0x4c/0x50
[86997.604491]  [<ffffffff8109b42c>] ? update_curr+0xec/0x180
[86997.604494]  [<ffffffff81521a5e>] usb_submit_urb+0x3be/0x3d0
[86997.604499]  [<ffffffffa040441c>] mwifiex_usb_host_to_card+0x10c/0x280 [mwifiex_usb]
[86997.604504]  [<ffffffff810b766e>] ? getnstimeofday+0xe/0x30
[86997.604511]  [<ffffffffa05c5d93>] mwifiex_exec_next_cmd+0x3d3/0x530 [mwifiex]
[86997.604517]  [<ffffffffa05c1ac2>] mwifiex_main_process+0x4e2/0x520 [mwifiex]
[86997.604523]  [<ffffffffa05c1b20>] mwifiex_main_work_queue+0x20/0x30 [mwifiex]
[86997.604526]  [<ffffffff8107ce9c>] process_one_work+0x17c/0x430
[86997.604530]  [<ffffffff8107de6c>] worker_thread+0x11c/0x3c0
[86997.604533]  [<ffffffff8107dd50>] ? manage_workers.isra.25+0x2b0/0x2b0
[86997.604537]  [<ffffffff81084600>] kthread+0xc0/0xd0
[86997.604540]  [<ffffffff816eb769>] ? schedule+0x29/0x70
[86997.604544]  [<ffffffff81084540>] ? kthread_create_on_node+0x120/0x120
[86997.604548]  [<ffffffff816f632c>] ret_from_fork+0x7c/0xb0
[86997.604551]  [<ffffffff81084540>] ? kthread_create_on_node+0x120/0x120
[86997.604554] ---[ end trace f2c6580532d9396a ]---
[86997.604556] usb 2-2: mwifiex_usb_host_to_card: usb_submit_urb failed
[86997.604559] usb 2-2: DNLD_CMD: host to card failed
[86997.604616] usb 2-2: failed to get signal information
[86997.604680] usb 2-2: mwifiex_usb_host_to_card: usb_submit_urb failed
[86997.604683] usb 2-2: DNLD_CMD: host to card failed
[86997.604726] usb 2-2: failed to get signal information
[86998.883351] usb 2-2: data: -ENOSR is returned
```

---

### Post by mack5 on 2014-01-21
Hi,

I am a brand new Ubuntu user, and having just got a Surface Pro 2 from my job, but needing to do a lot of work through a terminal on it, I just want to thank you guys for being so helpful. Particularly PointSource for the fixes for the keyboard/mouse, and for wifi, and then geopfling for pointing out the missing bit (changing the name) to get the wifi driver going.

I'm still having some issues with the wifi network at the school where I work, where it works briefly but then stops, but this might be a result of the network security features rather than the driver. I am going to try it at home and see if I have the same problems, but regardless since I connect via a usb to ethernet adapter at the school anyway, this is all pretty great.

Thanks for all the great work, and it'd be awesome if people could keep updating this page as more fixes become available, since it is one of the top results on Google at the moment still for this kind of thing, and Im sure others would like to gain the same kind of arcane knowledge I feel like I've been privy to... ha ha ha! At this point I actaully like Ubuntu more than Windows 8 on this thing (presuming the wifi works flawlessly at home) since the mouse seems to act much nicer... Too much weird **** still with windows 8. lol

Cheers everyone.
M

EDIT - So WIFI isn't working as I thought it was. It seems the driver is recognized now, but the only network it has been able to connect to at all is my secure work internet - and only briefly, before it disconnects and stays that way, whereas my home wifi (that has basic router encryption), and wifi from my phone are both unable to connect at all.

Does anyone have a workaround for this, or can maybe explain what my problem is?

---

### Post by PointSource on 2014-01-21
> **mack5 said:**
> EDIT - So WIFI isn't working as I thought it was. It seems the driver is recognized now, but the only network it has been able to connect to at all is my secure work internet - and only briefly, before it disconnects and stays that way, whereas my home wifi (that has basic router encryption), and wifi from my phone are both unable to connect at all.

Does anyone have a workaround for this, or can maybe explain what my problem is?

Seems I spoke too soon regarding the wifi. One problem got fixed, only for two more to crop up in it's place.

[Following the kernel bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=64111"), disabling autosuspend in the wifi driver makes it more stable, but others have reported driver hangs for separate reasons.

So; updated kernel packages:
linux-image: [https://owncloud.staers.homelinux.net/public.php?service=files&t=9b4b7ebd62fc34200463a948d0a15e3f](https://owncloud.staers.homelinux.net/public.php?service=files&t=9b4b7ebd62fc34200463a948d0a15e3f)
linux-headers: [https://owncloud.staers.homelinux.net/public.php?service=files&t=5526b0037f21dab6462fa5250d5e466f](https://owncloud.staers.homelinux.net/public.php?service=files&t=5526b0037f21dab6462fa5250d5e466f)

I will endeavour to keep updating, editing and/or invalidating previous kernel links as more fixes become available.

---

### Post by mack5 on 2014-01-22
Thanks PointSource, you are totally awesome!

Internet at home randomly was working tonight when I tried, but I installed the updated kernel and that will hopefully make things a bit more silky smooth elsewhere.

Thanks again! Im pretty stoked to have Ubuntu and Windows 8 dual booting properly on this machine now. :-)

---

### Post by tlnlion on 2014-01-26
Thank you PointSource, your packages are very helpful!
Keep up the good work!

---

### Post by prcdslnc13 on 2014-02-08
Hey guys. I'm trying to get 13.10 on my surface 2 pro. I had a surface pro and using point sources kernel everything was working perfect. But I exchanged it for the 2 yesterday and now I'm having WiFi issues. 

The type cover and touch pad are working fine but no networking. It doesn't even list the wireless card in networking. 

I also added the .bin file posted a few back on the last posting of the kernel. After I modprobed it I can't even use a wireless USB adapter. 

Any help?

---

### Post by PointSource on 2014-02-11
> **prcdslnc13 said:**
> Hey guys. I'm trying to get 13.10 on my surface 2 pro. I had a surface pro and using point sources kernel everything was working perfect. But I exchanged it for the 2 yesterday and now I'm having WiFi issues. 

The type cover and touch pad are working fine but no networking. It doesn't even list the wireless card in networking. 

I also added the .bin file posted a few back on the last posting of the kernel. After I modprobed it I can't even use a wireless USB adapter. 

Any help?

if you link a [pastebin]("http://pastebin.com/") to this thread of your [FONT=Courier New]/var/log/syslog[/FONT] from just after the problem occurs, someone might be able to provide some troubleshooting.

Also, with the updated wireless firmware, did you:
> **goepfling said:**
> Note 1: remember to rename the firmware blob file to: */lib/firmware/mrvl/usb8797_uapsta.bin*

---

### Post by DeastinY on 2014-02-11
[SIZE=2]Hi,[/SIZE]
First of all I'd like to thank the all of you for the great work you've done here.
Secondly I'd like to say that I do not have that much of experience working with kernels etc, yet.

So I carefully read through the thread and decided to give it a try (deleting my windows while being careless, but never mind..).
I can't get this to run properly, so if someone could check what I did up to now, I'd really appreciate it:


[LIST=1]
[*]Grab PointSource Kernel-fix 
[*]Install Ubuntu 13.10 (No working Typecover/Wifi/BT afterwards, as expected) 
[*]Install the Kernel-fix (I simply used the ubuntu-install-center0-thing, then update-grub) 
[/LIST]

Reboot - choose the new kernel in grub - nothing changed.
Did I miss something ?

I do not really understand what I am supposed to do with the firmware-blob-rename (this file does exist, so I assume the fix includes it)
and I did a fresh install after messing around with the pre-PointSource-fixes, so I do not have the blacklist-file to take care of.

Sorry for any inconveniences and thanks again to all of you.

Cheers, DeastinY

---

### Post by PointSource on 2014-02-11
If you've installed and booted the fixed kernel correctly, the type cover should be working.

For the firmware, maybe a short command-line script would make it easier to apply:
```
$ wget --content-disposition "http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin"
$ sudo mv usb8797_uapsta.bin /lib/firmware/mrvl/usb8797_uapsta.bin
```

---

### Post by patrick.broetto on 2014-02-13
Hi,

i think there is an interesting news about secure boot that refers to surface pro and surface pro 2 that you should know: [http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro](http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro)

I have tested it and it is functioning properly on a surface pro 2 with dual boot Windows 8.1 Pro + Ubuntu 13.10 with secure boot ENABLED :)

Cheers,
Patrick

---

### Post by PointSource on 2014-02-13
> **DeastinY said:**
> ...
Reboot - choose the new kernel in grub - nothing changed.
Did I miss something ?

...And now my keyboard won't work either.

The [Surface Pro 2's update history for February]("http://www.microsoft.com/surface/en-us/support/install-update-activate/pro-2-update-history") refers to various device firmware updates, including the Touch Cover 2 and the Type Cover 2. My syslog shows a different device setup procedure, back to:
```
hid-multitouch 0003:045E:07A9.0014: HID_DG_INPUTMODE out of range
hid-multitouch 0003:045E:07A9.0014: No inputs registered, leaving
```

The only thing I did was windows update. A word to everyone else, if you can avoid it, I'd caution against updating for the moment.

---

### Post by mack5 on 2014-02-13
I'm also unable to get the type 2 mouse/keyboard cover working now also... This isn't just a problem with my newbieness then?

I guess I should just use a virtualbox for now to do my work, then?

This is a bummer. :-(

---

### Post by PointSource on 2014-02-15
OK. Managed to find a patchset that restores functionality. I don't know why I didn't pick up on it before...

New kernel packages:
linux-image: [https://owncloud.staers.homelinux.net/public.php?service=files&t=5e59389bb350f141f39524d78c597a79](https://owncloud.staers.homelinux.net/public.php?service=files&t=5e59389bb350f141f39524d78c597a79)
linux-headers: [https://owncloud.staers.homelinux.net/public.php?service=files&t=6f4b413803b6ed5ac4f108db7fdcbd40](https://owncloud.staers.homelinux.net/public.php?service=files&t=6f4b413803b6ed5ac4f108db7fdcbd40)

If anyone's interested, these are the patches I applied to the kernel source:
```
diff --git a/drivers/hid/hid-ids.h b/drivers/hid/hid-ids.h
--- a/drivers/hid/hid-ids.h
+++ b/drivers/hid/hid-ids.h
@@ -611,6 +611,8 @@
 #define USB_DEVICE_ID_MS_PRESENTER_8K_USB	0x0713
 #define USB_DEVICE_ID_MS_DIGITAL_MEDIA_3K	0x0730
 #define USB_DEVICE_ID_MS_COMFORT_MOUSE_4500	0x076c
+#define USB_DEVICE_ID_MS_TOUCH_COVER_2	0x07a7
+#define USB_DEVICE_ID_MS_TYPE_COVER_2	0x07a9
 
 #define USB_VENDOR_ID_MOJO		0x8282
 #define USB_DEVICE_ID_RETRO_ADAPTER	0x3201
diff --git a/drivers/hid/hid-core.c b/drivers/hid/hid-core.c
--- a/drivers/hid/hid-core.c
+++ b/drivers/hid/hid-core.c
@@ -1878,6 +1878,10 @@ static const struct hid_device_id hid_have_special_driver[] = {
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ZEROPLUS, 0x0030) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ZYDACRON, USB_DEVICE_ID_ZYDACRON_REMOTE_CONTROL) },
 
+	/* MS TYPE AND TOUCH COVER 2 INSERTIONS*/
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2) },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TOUCH_COVER_2) },
+
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_PRESENTER_8K_BT) },
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_NINTENDO, USB_DEVICE_ID_NINTENDO_WIIMOTE) },
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_NINTENDO, USB_DEVICE_ID_NINTENDO_WIIMOTE2) },
diff --git a/drivers/hid/hid-microsoft.c b/drivers/hid/hid-microsoft.c
--- a/drivers/hid/hid-microsoft.c
+++ b/drivers/hid/hid-microsoft.c
@@ -207,6 +207,10 @@ static const struct hid_device_id ms_devices[] = {
 		.driver_data = MS_NOGET },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_COMFORT_MOUSE_4500),
 		.driver_data = MS_DUPLICATE_USAGES },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2),
+		.driver_data = 0 },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TOUCH_COVER_2),
+		.driver_data = 0 },
 
 	{ HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_PRESENTER_8K_BT),
 		.driver_data = MS_PRESENTER },
diff --git a/drivers/net/wireless/mwifiex/usb.c b/drivers/net/wireless/mwifiex/usb.c
--- a/drivers/net/wireless/mwifiex/usb.c
+++ b/drivers/net/wireless/mwifiex/usb.c
@@ -557,7 +557,7 @@ static struct usb_driver mwifiex_usb_driver = {
 	.id_table = mwifiex_usb_table,
 	.suspend = mwifiex_usb_suspend,
 	.resume = mwifiex_usb_resume,
-	.supports_autosuspend = 1,
+	//~ .supports_autosuspend = 1,
 };
 
 static int mwifiex_usb_tx_init(struct mwifiex_adapter *adapter)

```

---

### Post by mack5 on 2014-02-17
Thanks PointSource! This Kernel seems to get the bare necessities working again... The keyboard works, and the touchpad, but it seems the left and right physical buttons on the touchpad do not? Right clicking can still be accomplished by tapping with two fingers, and dragging and such can either be done through rightclicking the top of the bar or using my finger or the stylus...

Regardless, thanks very much! This is definitely sufficient to allow me to continue working. :-D

---

### Post by Nickolai_Leschov on 2014-03-04
Could you please share your experience and advice on using Ubuntu on Surface Pro 2? [Not to hijack this thread, I've created a separate one for this]("http://ubuntuforums.org/showthread.php?t=2209247").

Is any of the work done by users in this thread being merged into 14.04?

---

### Post by mack5 on 2014-03-04
It seems the WI FI has stopped working, where the system doesn't even register the hardware exists... Does anyone else have this problem? It used to be working, but then one day the wifi just... vanished.

---

### Post by goepfling on 2014-03-07
Mack5, any "linux-firmware" package update (automatic or manual) could probably destroy the *usb8797_uapsta.bin* needed to make wifi and bluetooth somewhat working. Just download it again and install in the */lib/firmware/mrvl* directory and reboot (I often find useless rmmod'ing and modprob'ing again *mwifiex_usb* and *mwifiex* modules).

Note that the best combination (pointsource's kernel and latest *usb8797_uapsta.bin*) still shows some problems:
- wifi randomly crashes (sometimes after more than 24 hours of intense traffic, sometimes after less than 2 minutes after booting)
- bluetooth does not pair with a mouse and only pairs in "PAN" mode with my phone (apparently bluetooth stack has problems with HID and serialport profiles)

---

### Post by mack5 on 2014-03-09
Thanks goeofling! I didnt realize that updating could bugger up the .bin file... I re-downloaded and copied it and it works again. :-) Thanks for the help!

---

### Post by sblake on 2014-03-09
Just wanted to say a massive thanks to all involved here, especially PointSource for all your help. It's been a massive help!Where I'm at at the moment is I have Ubuntu 13.10 working fairly well, with the touch cover working perfectly. However, WiFi is still an issue.I simply can't get it to stay connected to a network for more than 5 minutes. And when it drops off (which it always does), it requires a reboot to get it to connect again (otherwise it simply hangs while trying to reconnect again and again).Is this a known bug that is being worked on by someone? Or is it USB network dongles all the way? :P

---

### Post by drmclaser on 2014-03-13
> Once again, if someone wouldn't mind mirroring these to a filesharing service, it'd be greatly appreciated.
 
As I have been using this download a couple of times now, I figured it would only be fair if I provided with alternative download links:


[SIZE=4]linux-image-3.11.10_20140215-surfacepro2_amd64.deb:[/SIZE]

[http://ubuntuone.com/074dmRVoVqJlxPrDz6c7iW](http://ubuntuone.com/074dmRVoVqJlxPrDz6c7iW)

[SIZE=4]linux-headers-3.11.10_20140215-surfacepro2_amd64.deb:[/SIZE]

[http://ubuntuone.com/2DioyChO246QzDw70brlWH](http://ubuntuone.com/2DioyChO246QzDw70brlWH)

And just to keep things together, I will a link to the mrvl driver:

[SIZE=4]mrvl-usb8797_uapsta:[/SIZE]

[http://ubuntuone.com/2HfEvFO3aT1f2Auun6AWnM](http://ubuntuone.com/2HfEvFO3aT1f2Auun6AWnM)

Thanks to everybody who have made this possible ! :)

---

### Post by PointSource on 2014-03-13
> **drmclaser said:**
> As I have been using this download a couple of times now, I figured it would only be fair if I provided with alternative download links:
[http://ubuntuone.com/](http://ubuntuone.com/)...
Thank you so much @drmclaser! I forgot ubuntu one provided 5GB free storage.

I have revised the patches a little based on some new and/or pending kernel commits, these patches are at the end of this post. Based on these, here are some new kernel packages, downloadable from ubuntu one:
[linux-image-3.11.10.4_20140314_amd64.deb: http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm]("http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm")
[linux-headers-3.11.10.4_20140314_amd64.deb: http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK]("http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK")

Thanks again to drmclaser, whose valuable contribution has enabled everyone faster download speeds.

> **goepfling said:**
> Note that the best combination (pointsource's kernel and latest *usb8797_uapsta.bin*) still shows some problems:
- wifi randomly crashes (sometimes after more than 24 hours of intense traffic, sometimes after less than 2 minutes after booting)
- bluetooth does not pair with a mouse and only pairs in "PAN" mode with my phone (apparently bluetooth stack has problems with HID and serialport profiles)
Bluetooth may be a little more stable this time around after disabling autosuspend on btusb. The issue with the wifi crash has still not been resolved upstream.

> **sblake said:**
> WiFi is still an issue.I simply can't get it to stay connected to a network for more than 5 minutes. And when it drops off (which it always does), it requires a reboot to get it to connect again (otherwise it simply hangs while trying to reconnect again and again).Is this a known bug that is being worked on by someone? Or is it USB network dongles all the way? :P
It's being worked on, see [https://bugzilla.kernel.org/show_bug.cgi?id=69661](https://bugzilla.kernel.org/show_bug.cgi?id=69661). For now, a USB wireless adapter is the best option if your network crashes too often to be usable.

Patches:```

--- ./drivers/net/wireless/mwifiex/usb.c.orig	2014-02-19 05:13:05.000000000 +0800
+++ ./drivers/net/wireless/mwifiex/usb.c	2014-03-13 08:14:41.877822883 +0800
@@ -511,13 +511,6 @@
 						   MWIFIEX_BSS_ROLE_ANY),
 				  MWIFIEX_ASYNC_CMD);
 
-#ifdef CONFIG_PM
-	/* Resume handler may be called due to remote wakeup,
-	 * force to exit suspend anyway
-	 */
-	usb_disable_autosuspend(card->udev);
-#endif /* CONFIG_PM */
-
 	return 0;
 }
 
@@ -576,7 +569,6 @@
 	.id_table = mwifiex_usb_table,
 	.suspend = mwifiex_usb_suspend,
 	.resume = mwifiex_usb_resume,
-	.supports_autosuspend = 1,
 };
 
 static int mwifiex_usb_tx_init(struct mwifiex_adapter *adapter)
--- drivers/bluetooth/btusb.c.orig	2014-02-19 05:13:05.000000000 +0800
+++ drivers/bluetooth/btusb.c	2014-03-14 21:40:14.904609775 +0800
@@ -50,6 +50,7 @@
 #define BTUSB_WRONG_SCO_MTU	0x40
 #define BTUSB_ATH3012		0x80
 #define BTUSB_INTEL		0x100
+#define BTUSB_MWIFIEX		0x200
 #define BTUSB_BCM_PATCHRAM	0x800
 
 static struct usb_device_id btusb_table[] = {
@@ -230,6 +231,9 @@
 	/* Intel Bluetooth device */
 	{ USB_DEVICE(0x8087, 0x07dc), .driver_info = BTUSB_INTEL },
 
+	/* Marvell 8797 - mwifiex-usb composite wifi+bt device */
+	{ USB_DEVICE(0x1286, 0x2044), .driver_info = BTUSB_MWIFIEX },
+
 	{ }	/* Terminating entry */
 };
 
@@ -1511,6 +1515,11 @@
 	if (id->driver_info & BTUSB_BCM_PATCHRAM)
 		hdev->setup = btusb_setup_patchram;
 
+	if (id->driver_info & BTUSB_MWIFIEX) {
+		printk(KERN_INFO KBUILD_MODNAME ": mwifiex bt detected, disabling usb autosuspend\n");
+		usb_disable_autosuspend(data->udev);
+	}
+
 	/* Interface numbers are hardcoded in the specification */
 	data->isoc = usb_ifnum_to_if(data->udev, 1);
 
--- ./drivers/hid/usbhid/hid-quirks.c.orig	2014-02-19 05:13:05.000000000 +0800
+++ ./drivers/hid/usbhid/hid-quirks.c	2014-03-13 08:46:37.785748753 +0800
@@ -73,6 +73,9 @@
 	{ USB_VENDOR_ID_FORMOSA, USB_DEVICE_ID_FORMOSA_IR_RECEIVER, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_FREESCALE, USB_DEVICE_ID_FREESCALE_MX28, HID_QUIRK_NOGET },
 	{ USB_VENDOR_ID_MGE, USB_DEVICE_ID_MGE_UPS, HID_QUIRK_NOGET },
+	{ USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_SURFACE_PRO_2, HID_QUIRK_NO_INIT_REPORTS },
+	{ USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2, HID_QUIRK_NO_INIT_REPORTS },
+	{ USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TOUCH_COVER_2, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_MSI, USB_DEVICE_ID_MSI_GX680R_LED_PANEL, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_NOVATEK, USB_DEVICE_ID_NOVATEK_MOUSE, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_PIXART, USB_DEVICE_ID_PIXART_OPTICAL_TOUCH_SCREEN, HID_QUIRK_NO_INIT_REPORTS },
--- ./drivers/hid/hid-core.c.orig	2014-03-13 08:16:08.013819550 +0800
+++ ./drivers/hid/hid-core.c	2014-03-13 08:18:37.721813758 +0800
@@ -733,6 +733,14 @@
 			(item_udata(&item) & 0xff) == HID_COLLECTION_PHYSICAL)
 			hid->group = HID_GROUP_SENSOR_HUB;
 	}
+	/*
+	 * Handle vendor specific handlings
+	 */
+	if ((hid->vendor == USB_VENDOR_ID_MICROSOFT) &&
+	    (hid->product == USB_DEVICE_ID_MS_TYPE_COVER_2 ||
+	     hid->product == USB_DEVICE_ID_MS_TOUCH_COVER_2)
+	    && (hid->group == HID_GROUP_MULTITOUCH))
+		hid->group = HID_GROUP_GENERIC;
 
 	return 0;
 }
--- ./drivers/hid/hid-ids.h.orig	2014-02-19 05:13:05.000000000 +0800
+++ ./drivers/hid/hid-ids.h	2014-03-13 08:16:08.025819550 +0800
@@ -611,6 +611,9 @@
 #define USB_DEVICE_ID_MS_PRESENTER_8K_USB	0x0713
 #define USB_DEVICE_ID_MS_DIGITAL_MEDIA_3K	0x0730
 #define USB_DEVICE_ID_MS_COMFORT_MOUSE_4500	0x076c
+#define USB_DEVICE_ID_MS_SURFACE_PRO_2	0x0799
+#define USB_DEVICE_ID_MS_TOUCH_COVER_2	0x07a7
+#define USB_DEVICE_ID_MS_TYPE_COVER_2	0x07a9
 
 #define USB_VENDOR_ID_MOJO		0x8282
 #define USB_DEVICE_ID_RETRO_ADAPTER	0x3201
--- drivers/hid/hid-sensor-hub.c.orig	2014-03-14 00:45:20.759523066 +0800
+++ drivers/hid/hid-sensor-hub.c	2014-03-14 00:45:50.307521923 +0800
@@ -607,6 +607,15 @@
 }
 
 static const struct hid_device_id sensor_hub_devices[] = {
+	{ HID_DEVICE(HID_BUS_ANY, HID_GROUP_SENSOR_HUB, USB_VENDOR_ID_MICROSOFT,
+			USB_DEVICE_ID_MS_TOUCH_COVER_2),
+			.driver_data = HID_SENSOR_HUB_ENUM_QUIRK},
+	{ HID_DEVICE(HID_BUS_ANY, HID_GROUP_SENSOR_HUB, USB_VENDOR_ID_MICROSOFT,
+			USB_DEVICE_ID_MS_TYPE_COVER_2),
+			.driver_data = HID_SENSOR_HUB_ENUM_QUIRK},
+	{ HID_DEVICE(HID_BUS_ANY, HID_GROUP_SENSOR_HUB, USB_VENDOR_ID_MICROSOFT,
+			USB_DEVICE_ID_MS_SURFACE_PRO_2),
+			.driver_data = HID_SENSOR_HUB_ENUM_QUIRK},
 	{ HID_DEVICE(HID_BUS_ANY, HID_GROUP_SENSOR_HUB, HID_ANY_ID,
 		     HID_ANY_ID) },
 	{ }

```

---

### Post by drmclaser on 2014-03-14
Excellent!

What will happen if I installed Ubuntu 14.04? will I be able to apply the same fixes ? 
I have tried booting 14.04 and everything seems to be the same as 13.10, hardware support wise.

**#Update**
I have now installed Ubuntu 14.04, and after applying the marvell fix, I now have working wifi. it seems pretty stable, although I have only used it for ~4 hours.
Type cover 2 doesn't work.

---

### Post by hoganaj on 2014-03-14
This is awesome, thanks PointSource et al for the amazing work.  I'm excited to try this out on my Surface.  

Can I ask though whether these brilliant kernel changes are being incorporated into the 14.04 release?  That would really be fantastic if the Marvel driver, keyboard driver, touch screen stuff worked on installation.

---

### Post by javispedro2 on 2014-03-15
A warning: there's a [kernel regression]("https://lkml.org/lkml/2014/3/6/5") on 3.13.5 and higher versions that can corrupt SD card contents if using the card reader in USB 3.0 speeds. The SFPro's internal card reader **is** connected by USB3!

I got bit by this bug and lost a few songs from my SD card :)

Fortunately just reverting that commit seems enough to fix the problem. Remember this if you're trying new kernel versions!

---

### Post by matt49 on 2014-03-24
hi folks. I'll preface with: i'm relatively new to linux as i've usually been tied to cad software running on windows.

I've followed much of the previous thread and used the patches above. everything is/was working great.  however, now the touchpad on the Type 2 Keyboard does not work in ubuntu.

Here's what happened.  Everything was workign flawlessly using the above patches, except the keyboard was not working in GRUB2 after using boot-repair as suggested by the "ask" tutorial.  I then held down the vol-up button during restart and booted into windows.  Then grub was getting missed and booting straight into windows.  I fixed that by forcing a restart into "ubuntu boot" from the windows boot loader.  Now GRUB2 loads and the keyboard works and i can choose between windows/ubuntu at start.  Starting up ubuntu everything seems to work (including wifi) fine except for the touchpad.  I tried re-running the most updated patches however it does not seem to make a difference.  

I assume this is a relatively straightforward fix? perhaps there's a line earlier in this thread that describes what i'm missing and just not understanding? thanks
edit: i should add, i appreciate the work everyone is doing here turning a useful device even more useful.

---

### Post by PointSource on 2014-03-24
> **matt49 said:**
> I've followed much of the previous thread and used the patches above. everything is/was working great.  however, now the touchpad on the Type 2 Keyboard does not work in ubuntu.
Hi matt49,
post the kernel log messages for when you unplug and replug the type cover 2. ie, in a terminal, run this:
```
$ sudo tail -n0 -f /var/log/kern.log
```
unplug, replug, CTRL-C to kill program.

---

### Post by matt49 on 2014-03-25
> **PointSource said:**
> Hi matt49,
post the kernel log messages for when you unplug and replug the type cover 2. ie, in a terminal, run this:
```
$ sudo tail -n0 -f /var/log/kern.log
```
unplug, replug, CTRL-C to kill program.

Okay, I am a little surprised with the following.  I had the system off for a while, turned it on again and the keyboard stopped working during Grub2 boot loader, but the touchpad returned to working in ubuntu. It seems that I get to have one working but not the other (I tihnk the surface really just wants me to only use ubuntu!).

Below is the kernel log during removal and replacement of the type 2 cover:
```
$ sudo tail -n0 -f /var/log/kern.log
Mar 25 18:06:51 carbonix kernel: [ 2773.809138] usb 2-2: data: -ENOSR is returned
Mar 25 18:08:30 carbonix kernel: [ 2872.212997] usb 2-3: USB disconnect, device number 10
Mar 25 18:08:30 carbonix kernel: [ 2872.221562] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
Mar 25 18:08:30 carbonix kernel: [ 2872.221571] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q42] (Node ffff880119ab23e8), AE_NOT_FOUND (20130517/psparse-536)
Mar 25 18:08:30 carbonix kernel: [ 2872.588942] usb 2-3: new full-speed USB device number 11 using xhci_hcd
Mar 25 18:08:30 carbonix kernel: [ 2872.606923] usb 2-3: New USB device found, idVendor=045e, idProduct=0799
Mar 25 18:08:30 carbonix kernel: [ 2872.606933] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 25 18:08:30 carbonix kernel: [ 2872.606938] usb 2-3: Product: SAM
Mar 25 18:08:30 carbonix kernel: [ 2872.606942] usb 2-3: Manufacturer: MICROSOFT
Mar 25 18:08:30 carbonix kernel: [ 2872.606945] usb 2-3: SerialNumber: 0.1.0000
Mar 25 18:08:30 carbonix kernel: [ 2872.621695] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input18
Mar 25 18:08:30 carbonix kernel: [ 2872.622011] hid-generic 0003:045E:0799.000E: input,hidraw0: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input1
Mar 25 18:08:35 carbonix kernel: [ 2877.048737] usb 2-3: USB disconnect, device number 11
Mar 25 18:08:35 carbonix kernel: [ 2877.061496] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
Mar 25 18:08:35 carbonix kernel: [ 2877.061520] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q41] (Node ffff880119ab23c0), AE_NOT_FOUND (20130517/psparse-536)
Mar 25 18:08:35 carbonix kernel: [ 2877.422294] usb 2-3: new full-speed USB device number 12 using xhci_hcd
Mar 25 18:08:35 carbonix kernel: [ 2877.440172] usb 2-3: New USB device found, idVendor=045e, idProduct=07a9
Mar 25 18:08:35 carbonix kernel: [ 2877.440181] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 25 18:08:35 carbonix kernel: [ 2877.440186] usb 2-3: Product: SAM
Mar 25 18:08:35 carbonix kernel: [ 2877.440190] usb 2-3: Manufacturer: MICROSOFT
Mar 25 18:08:35 carbonix kernel: [ 2877.440195] usb 2-3: SerialNumber: 0.1.0000
Mar 25 18:08:35 carbonix kernel: [ 2877.450282] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input19
Mar 25 18:08:35 carbonix kernel: [ 2877.450709] hid-generic 0003:045E:07A9.0010: input,hidraw0: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input1
Mar 25 18:08:35 carbonix kernel: [ 2877.453147] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.2/input/input20
Mar 25 18:08:35 carbonix kernel: [ 2877.453534] hid-generic 0003:045E:07A9.0011: input,hiddev0,hidraw3: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input2

```

---

### Post by culion1987 on 2014-03-27
Hi!

I'm an original Surface Pro user with a Type Cover 2. I downloaded the packages+installed the latest packages on this thread, but I still can't get the Type Cover 2 to work at all. As others have mentioned, the keyboard works will in the GRUB menu. 

Here's my output from /var/log/kern.log after reconnecting the cover. 

Mar 27 22:46:08 archer kernel: [  237.306316] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
Mar 27 22:46:08 archer kernel: [  237.306337] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q42] (Node ffff8801192a9dc0), AE_NOT_FOUND (20130517/psparse-536)
Mar 27 22:46:08 archer kernel: [  237.325101] usb 2-1.5: USB disconnect, device number 3
Mar 27 22:46:08 archer kernel: [  237.650257] usb 2-1.5: new full-speed USB device number 6 using ehci-pci
Mar 27 22:46:08 archer kernel: [  237.744753] usb 2-1.5: New USB device found, idVendor=045e, idProduct=0799
Mar 27 22:46:08 archer kernel: [  237.744767] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 27 22:46:08 archer kernel: [  237.744774] usb 2-1.5: Product: SAM
Mar 27 22:46:08 archer kernel: [  237.744781] usb 2-1.5: Manufacturer: MICROSOFT
Mar 27 22:46:08 archer kernel: [  237.744787] usb 2-1.5: SerialNumber: 0.1.0000
Mar 27 22:46:08 archer kernel: [  237.760644] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input11
Mar 27 22:46:08 archer kernel: [  237.761025] hid-generic 0003:045E:0799.0007: input,hidraw4: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:1d.0-1.5/input1
Mar 27 22:46:10 archer kernel: [  239.500330] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
Mar 27 22:46:10 archer kernel: [  239.500352] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q41] (Node ffff8801192a9d98), AE_NOT_FOUND (20130517/psparse-536)
Mar 27 22:46:10 archer kernel: [  239.630245] usb 2-1.5: USB disconnect, device number 6
Mar 27 22:46:10 archer kernel: [  239.918170] usb 2-1.5: new full-speed USB device number 7 using ehci-pci
Mar 27 22:46:10 archer kernel: [  240.013422] usb 2-1.5: New USB device found, idVendor=045e, idProduct=07a9
Mar 27 22:46:10 archer kernel: [  240.013438] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 27 22:46:10 archer kernel: [  240.013444] usb 2-1.5: Product: SAM
Mar 27 22:46:10 archer kernel: [  240.013449] usb 2-1.5: Manufacturer: MICROSOFT
Mar 27 22:46:10 archer kernel: [  240.013453] usb 2-1.5: SerialNumber: 0.1.0000
Mar 27 22:46:20 archer kernel: [  250.021997] microsoft 0003:045E:07A9.0008: usb_submit_urb(ctrl) failed: -1
Mar 27 22:46:20 archer kernel: [  250.022036] microsoft 0003:045E:07A9.0008: timeout initializing reports
Mar 27 22:46:20 archer kernel: [  250.022404] microsoft 0003:045E:07A9.0008: hiddev0,hidraw4: USB HID v1.11 Device [MICROSOFT SAM] on usb-0000:00:1d.0-1.5/input0
Mar 27 22:46:20 archer kernel: [  250.028869] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input12
Mar 27 22:46:20 archer kernel: [  250.029262] microsoft 0003:045E:07A9.0009: input,hidraw5: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:1d.0-1.5/input1
Mar 27 22:46:20 archer kernel: [  250.038311] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2/input/input13
Mar 27 22:46:20 archer kernel: [  250.038478] microsoft 0003:045E:07A9.000A: input,hiddev0,hidraw6: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:1d.0-1.5/input2


Any thoughts?

---

### Post by javispedro2 on 2014-03-28
> **culion1987 said:**
> Mar 27 22:46:20 archer kernel: [  250.021997] microsoft 0003:045E:07A9.0008: usb_submit_urb(ctrl) failed: -1
Mar 27 22:46:20 archer kernel: [  250.022036] microsoft 0003:045E:07A9.0008: timeout initializing reports

PointSource's kernel is missing the "skip initializing reports" quirk, so you get that error message. This patch should fix that: [https://www.mail-archive.com/linux-input@vger.kernel.org/msg08881.html](https://www.mail-archive.com/linux-input@vger.kernel.org/msg08881.html)
EDIT: Actually, look at his last message before this one and you will see a more recent binary that includes that patch.

---

### Post by PointSource on 2014-03-28
> **culion1987 said:**
> ```
Mar 27 22:46:20 archer kernel: [  250.021997] microsoft 0003:045E:07A9.0008: usb_submit_urb(ctrl) failed: -1
Mar 27 22:46:20 archer kernel: [  250.022036] microsoft 0003:045E:07A9.0008: timeout initializing reports
```

Like javispedro2 said, update to the newest kernel binary [from this post]("http://ubuntuforums.org/showthread.php?t=2183946&p=12956261#post12956261"). Also see note below.

> **matt49 said:**
> Okay, I am a little surprised with the following.  I had the system off for a while, turned it on again and the keyboard stopped working during Grub2 boot loader, but the touchpad returned to working in ubuntu. It seems that I get to have one working but not the other (I tihnk the surface really just wants me to only use ubuntu!).

The March 2014 system updates (as listed on [Microsoft's Surface Pro 2 update history page]("http://www.microsoft.com/surface/en-us/support/install-update-activate/pro-2-update-history")), specifically "System Firmware Update - 3/11/2014" **significantly** improved keyboard reliability for me, so that the keyboard works 100% of the time at GRUB bootloader.

---

### Post by javispedro2 on 2014-03-31
Has anyone tried the eraser end of the wacom? 

I have managed to get it to work, but I noticed after using the eraser end that it gets "stuck" in eraser mode until I restart the machine (even if I use the pencil end of the stylus again).
I think I've found the cause of the problem deep in the Xorg wacom driver, but since I am yet to heard anyone complain about this problem, I'm starting to believe "it's just me"...

---

### Post by drmclaser on 2014-04-01
I think people are more focused on getting their keyboards and wifi to work properly 
I at least am really fustated by not having a reliable internet connection. If it wasn't for that, I would only have to go into windows for OneNote. 
How is that working for you ? 

Anyway, I would love to have the eraser working. If you have the time and knowledge please do investigate the problem !

---

### Post by mack5 on 2014-04-07
Hello,

So, for newbs who don't want to go through everything on this forum so far, a quick summary is as follows (as I just performed on a replacement SP2 from the shop... accidentally broke the audio jack oops).

To begin, repartition your harddrive to make space for your ubuntu install from within windows. Further, install all updates (at least up to the date this post was made). 

After this, follow the instructions linked to earlier by patrick.broetto, [here.]("http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro") (make sure you use a command prompt with admin privileges, eg by right clicking it in the start menu and hitting "run as admin"). If you ran this properly, you should be able to boot to your ubuntu install usb driver WITHOUT turning off Secure Boot.

After this, boot to USB, and install ubuntu as normal. When you get to the point where it asks you for your "installation type" click "do something else." Create swap space, and a new partition as described [in this guide.]("http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu")

Finish your install, and then in your initial boot of ubuntu I advise (solely to avoid complications) making sure you run the updater, and installing anything recommended (or don't, that's your prerogative). Reboot to make sure it all goes smooth. 

Once this is done, if you are connected to the internet (if you are unable to do this, there is a longer method I will explain below - this script will just do it all for you, painlessly) open a terminal window and paste this:
> mkdir Desktop/kernel; cd Desktop/kernel; wget -O image.deb [http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm;](http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm;) wget -O headers.deb [http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK;](http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK;) sudo dpkg -i image.deb; sudo dpkg -i headers.deb; wget --content-disposition "http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin"; sudo mv usb8797_uapsta.bin /lib/firmware/mrvl/usb8797_uapsta.bin

The first portion of this downloads the required image and header files, the second portion installs them, and the last portion downloads the required wifi driver (at least I think its a driver, Im still new at this myself lol) and copies it to the desired directory.

If you don't have some other source of internet, you can instead:
Double click the image file that you can get from [here]("http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm") then install the headers file that you can get from [here.]("http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK") Note that for me there is a LONG delay sometimes between when I click "install" and when it asks for my sudo password... And often the "install" button becomes available again. I find that spamming the button is not kosher, just click it once and be very patient... lol
(The kernel is as provided by PointSource - thank you once again!)

Lastly, download the wifi driver [here]("http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin"), then rename and copy it to /lib/firmware/mrvl/usb8797_uapsta.bin

Upon rebooting, you should have completely functioning wifi, keyboard and mouse. (though, the mouse still has peculiarities... like being unable to click and drag, but only at certain times? does anyone else have this issue? also by chance does anyone know how to setup tap then tap and hold to drag? its really annoying that this doesn't work at all on the Surface :-( oh well)

Also, it is worth mentioning that sometimes the mouse on my keyboard doesn't work on a fresh boot into ubuntu. Disconnecting and reconnecting the keyboard seems to solve this, however.

Lastly, I will do my best to edit this post as updated kernels and patches become available.

(edited to include secure boot UEFI CA tool)

---

### Post by javispedro2 on 2014-04-07
> **drmclaser said:**
> I think people are more focused on getting their keyboards and wifi to work properly 
I at least am really fustated by not having a reliable internet connection. If it wasn't for that, I would only have to go into windows for OneNote. 
How is that working for you ? 

Anyway, I would love to have the eraser working. If you have the time and knowledge please do investigate the problem !
I do not currently have any problems whatsoever with WI-Fi.

Also, what's your current problem with the eraser? Does it match my description?

> **mack5 said:**
> 
I am wondering if anyone could explain to me how get GRUB loading with Secure Boot enabled, as here:


 Its not a big deal, since selecting "Windows Boot Manager" in the grub menu just boots to Windows, but it would be cool to have a nicer menu.

Just follow the instructions on that link. Note that enabling Secure Boot will not give you a "nicer menu". It will however disable the "scary red" boot screen.

---

### Post by mack5 on 2014-04-07
Thanks javispedro2 - the instructions worked perfectly, but only when performed before the ubuntu install (of course...). I am a dolt for not trying that before.

I havent used the pen much at all so far in ubuntu unfortunately, so I have no idea if my issues match yours on the eraser-end. What program do you use to try it?

---

### Post by Adam_Ayd on 2014-04-08
Coming to the party late here, but I just purchased a Surface Pro on Saturday with the direct notion of putting linux on it. So far mostly everything works out of the box and following the detailed instructions from mack5 except for my keyboard.  I have a power cover keyboard and it's dead to the world.  Oddly enough it actually reports the second battery in the Power Statistics.  Other than that I've been pretty impressed with the work everyone has done and especially PointSource.  Oh and my Arc Mouse won't recognize either.  Courtesy of my Apple bluetooth keyboard, I'm making due.  Does anyone else have a power cover keyboard or the arc mouse working?

---

### Post by javispedro2 on 2014-04-08
> **mack5 said:**
> I havent used the pen much at all so far in ubuntu unfortunately, so I have no idea if my issues match yours on the eraser-end. What program do you use to try it?
( I was not specifically asking you :) , just people interested in pen). I use GIMP, though.


> **Adam_Ayd said:**
> Coming to the party late here, but I just purchased a Surface Pro on Saturday with the direct notion of putting linux on it. So far mostly everything works out of the box and following the detailed instructions from mack5 except for my keyboard.  I have a power cover keyboard and it's dead to the world.  Oddly enough it actually reports the second battery in the Power Statistics.  Other than that I've been pretty impressed with the work everyone has done and especially PointSource.  Oh and my Arc Mouse won't recognize either.  Courtesy of my Apple bluetooth keyboard, I'm making due.  Does anyone else have a power cover keyboard or the arc mouse working?

For the power cover, it is probably being recognized as a multitouch device too so it's missing a specific patch. I suggest you run "lsusb" on your surface while the power cover is connected (you might need root), post the results here, and someone is certainly going to build a new kernel image for you.

As for the arc mouse (Surface Edition?), I'm going to get one soon so I'll be able to test it. As far as I know so far, it is a Bluetooth Low Energy device (BLE) using HID over GATT profile (HoG). This means it requires recent Bluez5, and I'm not sure which one Ubuntu is using at the moment.

---

### Post by Adam_Ayd on 2014-04-08
Thanks javispedro2.  Bellow is my lsusb printout with the power cover connected:```
Bus 002 Device 005: ID 045e:0794 Microsoft Corp. 
Bus 002 Device 004: ID 03eb:8209 Atmel Corp. 
Bus 002 Device 003: ID 045e:07da Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:0795 Microsoft Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:0307 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1286:2044 Marvell Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

Yes the arc mouse is the surface edition.  I forgot to mention that.  I also forgot to mention that like most others, the keyboard does work in GRUB. Also the arc mouse shows up in my bluetooth manager, but is listed as unknown and won't let me add the device.  The continue button is greyed out.

---

### Post by javispedro2 on 2014-04-09
Ok, I am the moment using the Arc Mouse from Gentoo. I needed to upgrade to the very latest Bluez 5.17 but I'm not entirely sure why -- should work in earlier versions. Also, you need CONFIG_UHID enabled in kernel configuration.

Since I'm on Mate desktop I can't really talk about neither Unity's nor Gnome's bluetooth config. For command line configuration, these instructions are OK:
[https://wiki.archlinux.org/index.php/Bluetooth_Mouse#Bluez5_instructions](https://wiki.archlinux.org/index.php/Bluetooth_Mouse#Bluez5_instructions)

---

### Post by Adam_Ayd on 2014-04-09
Javispedro, 

I was thinking about bluez5 but moved on for the time being. I wanted to get the OS's installed and come back to issues. Unfortunately OSX killed me. I messed something up with clover and wound up bricking the surface. Thanks to my restore USB, I'm back to windows 8.1 with all windows updates installed (for the second time). I'm thinking of trying to go in a different order of OS install tomorrow. Triple boot is fun :)

---

### Post by mack5 on 2014-04-10
It looks like windows has finally given the touchpad the "tap then tap and hold to drag" feature (as it should have had from the very beginning). What are the chances we can get the same thing going in ubuntu? (not that I have any experience with this)

Also, I am curious why I cant even click and drag (like press the left mouse button and move my finger on the trackpad) to move some things (most notably my terminal window) around, but I seem to have no problem with other things like chrome using the same technique.

Anyone else have this issue? Also often an image of a trackpad appears in the top right corner of my screen with an X over one of the buttons...? (the right click seems to not work properly either, but tapping with two fingers registers as a right click anyway so I can make due)

For the record, these issues have always been present for me. (the windows update allowing double tap and hold to drag hasn't affected my ubuntu experience at all.)

---

### Post by Adam_Ayd on 2014-04-11
So far so good.  I'm back together for the most part.  Oddly enough though I didn't install the PointSource image and headers this time around.  13.10 that I downloaded the other day today for some reason decided to have wifi work out of the box.  Bluetooth, wifi, and everything except for my power keyboard and Arc Mouse (I still have messed with Bluez 5.17 yet).  The Arc Mouse is seen when I go into pairing mode, but it just says unknown next to it in the Add A Device screen.  It will even pair the mouse, but it doesn't work.  OS X is running great as new trial drivers are out for the touch pen.  I was actually completely opposite between the two OS's.  OS X had keyboard but not pointer/touch/mouse and Ubuntu has not Keyboard but touch and pen work for the most part.  And well of course Windows is still Windows.  Anyway I didn't know if anyone else has a power cover and was able to get it working.  Please post up if you have a solution.  Thanks.

---

### Post by javispedro2 on 2014-04-11
> **mack5 said:**
> It looks like windows has finally given the touchpad the "tap then tap and hold to drag" feature (as it should have had from the very beginning). What are the chances we can get the same thing going in ubuntu? (not that I have any experience with this)

On Linux we are currently limited to using precision touchpads in "mouse emulation mode", so if the firmware doesn't recognize tap and drag by itself (it doesn't in Type/Touch Cover v2, supposedly because they wanted to "align" with the stupid behavior of Win8.1).

It is possible to setup the touchpad in multitouch mode so that then we can use e.g. xf86-input-synaptics , but it has a few gotchas so far: you need to set a specific HID feature and you need to separate the keyboard and touchpad HID devices (otherwise synaptics will eat keyboard events). If no one else does this I plan to take on this task at some point but it may be a while given my schedule (e.g. years)

---

### Post by microuav on 2014-04-13
Hi all,
I'm installing Ubuntu 12.04 on my surface pro 2 in dual boot configuration.
Thanks to all your hard work I'm pretty far. only the WiFi will not work for now.

It works when I install Ubuntu (I use a USB slitter with /USB WiFi dongle, Key board and Ubuntu boot USB)

From the moment I install the linux-image-3.11.10.4_20140314_amd64.deb my WiFi dongle stops working. 

then I do the flowing step:


download the wifi driver mrvl-usb8797_uapsta.bin here [http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin](http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin) , then rename and copy it to /lib/firmware/mrvl/usb8797_uapsta.bin
cd Desktop
cp mrvl-usb8797_uapsta.bin /lib/firmware/mrvl/usb8797_uapsta.bin

The WiFi of the surface pro2 is lighting up. I can see all the WiFi spots and when Klicken on them I can give the WEP key, but the surface pro2 will never connect.
(the same happens when i use my WiFi USB dongle who first was working perfect)

If someone have an idea how to solve this please let me know.

Kind Regards Microuav.



This are all the steps I did also to give an overview for newbies.

PARTITION


To begin, repartition your harddrive to make space for your ubuntu install from within windows. 
first step on this site
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
Create a partitioned drive.
-Press search button on your keyboard type 'boot'.
-Select 'settings >> Create and format disk partitions'
-Select C drive, right click and select 'shrink volume'.
-This is your choice but I use appox. 29.3 Gigs(30,000 MB): Shrink respectively.


Further, install all updates of windows (at least up to the date this post was made). 




USING THE MICROSOFT UEFI CA TOOL FOR SURFACE PRO


After this, follow the instructions linked to earlier by patrick.broetto, here.
[http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro](http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro)


[http://www.microsoft.com/en-us/download/details.aspx?id=41666](http://www.microsoft.com/en-us/download/details.aspx?id=41666)
link to dounload Microsoft Surface Pro UEFI CA OEM PK Tool
unzip 
 OEM_PK_Surface


1)  Save the platform key by running the SavePlatformKey.cmd script. 
make sure you use a command prompt with admin privileges, eg by right clicking it in the wondows 8.1 start menu and hitting "run as admin". If you ran this properly, you should be able to boot to your ubuntu install usb driver WITHOUT turning off Secure Boot.
cd ..\..
cd Users\bartremes\Downloads\ubuntu\OEM_PK_Surface
SavePlatformKey.cmd


2)Boot to the UEFI menu using the Power/Volume+ button combination at power on - See more at: [http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro#sthash.X1ZGV836.dpuf](http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro#sthash.X1ZGV836.dpuf)


3)Use the UEFI menu entry to ‘Delete all Secure Boot keys’, then save and reset.


4)Boot back into Windows and run the InstallSecureBootWithMsftUefiCertAuthToDB.cmd script.
cd ..\..
cd Users\bartremes\Downloads\ubuntu\OEM_PK_Surface
InstallSecureBootWithMsftUefiCertAuthToDB.cmd


After this, boot to USB, and install ubuntu as normal. 




MAKE UBUNTU USB BOOT DRIVE


download ubuntu desktop
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)


to make a ubuntu usb boot drive use Universal-USB-Installer-1.9.5.2
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)




INSTALL UBUNTU


Put your Ubuntu Live USB disk and USB keyboard and USB wifi dongle in a USB hub and in the USB 3 port on the Surface Pro, and head back to the Settings menu on the Charm Bar. Navigate back to the General PC settings update and recovery then recovery and boot into Advanced Startup. Tap the icon with the USB stick and the DVD labeled Use a Device one the Surface has booted into the Advanced settings (if you come back in windows you need to do it ones more).


When you get to the point where it asks you for your "installation type" click "do something else." Create swap space, and a new partition as described in this guide.


[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)


-It will ask if you want to unmount your installation device. Select 'No'.
-Now select the new free space and press the '+' button under the partitions.
-Select from the drop list 'swap' and select the 'logical' radio button and 'insert at beginning' and finish. Select anywhere from 400 to 600 MB to be safe at least.


-Now select the new free space and press the 'change' button - again.
-Select from the drop list 'Ext4' and select the 'primary' radio button, 'insert at beginning', 'format' button checked and '/' as root and finish. Use the remaining space you have reserved.
-Finish your install, and then in your initial boot of ubuntu I advise (solely to avoid complications) making sure you run the updater, and installing anything recommended (or don't, that's your prerogative). Reboot to make sure it all goes smooth. 
-Finish install process on the Ext4 partition you created.
!!!Do not restart, click the Continue Testing button.!!!




DUAL BOOT MENU


Make sure Grub2 was installed without problem.


sudo apt-get install grub2-common
sudo update-grub2


Setup Grub2 boot repair and run.


sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
sudo boot-repair


Select 'Recommended Repair'.
Restart to make sure you see the boot loader. If you wish to make the 10 second count shorter or longer, go back to boot-repair and select 'Advanced'.


Now you can restart.




MAKE THE SURFACE PRO 2 KEYBOARD AND MOUSE WORK


If you don't have some other source of internet, you can instead:
Double click the image file linux-image-3.11.10.4_20140314_amd64.deb that you can get from here [http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm](http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm) then install the headers file linux-headers-3.11.10.4_20140314_amd64.deb that you can get from here [http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK](http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK) . Note that for me there is a LONG delay sometimes between when I click "install" and when it asks for my sudo password... And often the "install" button becomes available again. I find that spamming the button is not kosher, just click it once and be very patient... lol
(The kernel is as provided by PointSource - thank you once again!)



WIFI


download the wifi driver mrvl-usb8797_uapsta.bin here [http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin](http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin) , then rename and copy it to /lib/firmware/mrvl/usb8797_uapsta.bin
cd Desktop
cp mrvl-usb8797_uapsta.bin /lib/firmware/mrvl/usb8797_uapsta.bin

---

### Post by javispedro2 on 2014-04-13
On the topic of the precision touchpad, you may have noticed if you dual boot Windows that if you reboot from Windows into Linux (ie no poweroff) sometimes the touchpad will stop working but the keyboard itself will still work.

That's because Windows left the touchpad in "precision touchpad" mode, so it's now sending multitouch events. But since the patch moves the touchpad to the hid-generic driver, the multitouch events are being eaten by the hid-generic driver...

(For the time being, just disconnect / reconnect the cover, that will put it back into mouse mode).

---

### Post by porear on 2014-04-15
Thanks to all for the work in this thread.  Just to add my two cents, I ran a 13.10 Live USB, and on the first run the type cover 2 worked fine.  After that - never again, like others.  At that point I had not set up Wifi so not sure what is getting modified.  

At any rate, after trying the deb packages here, I still do not have a working type cover.  I've tried both 12.04 and 13.10, both on Live USBs with persistence.  Should the Live experience perform any differently from an install?

I did update the wifi, and it does work for short periods, as expected.

Thanks!

EDIT:  Works after install

---

### Post by alicia4542 on 2014-04-20
This Easter weekend, I did a clean install of the new Ubuntu Trusty Tahr LTS (14.04 AMDx64) release onto my Surface Pro2, using a USB hub, usb flash drive, USB Ethernet adapter, and USB keyboard.

Unfortunately, I am said to report that my Type Cover2, Wi-Fi, and Bluetooth are not working with this release.  Looks like the Ubuntu maintainers decided to ignore us Surface Pro users.  :(
 
Rather than downgrade Ubuntu, with the previous custom kernels, any suggestions on step-by-step instructions on how to get all of the surface pro2 devices to work with Trusty Tahr?

On a side note, since I have full disk encryption turned on in Ubuntu.  Is there any way for me to enter my disk passcode during boot with the type cover2, and avoid using a separate USB keyboard?

Thank you in advance.

---

### Post by drmclaser on 2014-04-20
I have a very similar experence.  Wifi and type cover 2 doesn't work. However the touch cover 1 does work, and after applying the Marvell firmware, as described ealier in this thread, the wifi starts working.

---

### Post by Jerry_Drake on 2014-04-20
> **mack5 said:**
> Hello,

So, for newbs who don't want to go through everything on this forum so far, a quick summary is as follows (as I just performed on a replacement SP2 from the shop... accidentally broke the audio jack oops).

  - this script will just do it all for you, painlessly) open a terminal window and paste this:


The first portion of this downloads the required image and header files, the second portion installs them, and the last portion downloads the required wifi driver (at least I think its a driver, Im still new at this myself lol) and copies it to the desired directory.


Lastly, I will do my best to edit this post as updated kernels and patches become available.

(edited to include secure boot UEFI CA tool)


Thank you, thank you and thank you again: very useful post especially for a newbie; it saved me a lot of time the copying and pasting of the script;
I installed the new 14.04 on my surface pro2 and after following the different posts I was able to make almost everything work; I had a usb to ethernet adapter to have internet to update right away ; grub2 was updated and worked right away after rebooting (no need to use boot repair); then I was able to copy and paste the script provided here that solved the problems with wifi and bluetooth; I already had a generic bluetooth mouse and bluetooth keyboard that worked perfectly. So, now, the only thing (important) that does not work is the brand new power keyboard (like someone else posted too); if someone would come up with a patch for that it would be greatly appreciated as well; the power keyboard works when you power up to select and choose the operating system, once it boots up it does not work anymore.

---

### Post by alicia4542 on 2014-04-20
> **microuav said:**
> Make sure Grub2 was installed without problem.
sudo apt-get install grub2-common
sudo update-grub2
Setup Grub2 boot repair and run.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
sudo boot-repair

Select 'Recommended Repair'.
Restart to make sure you see the boot loader. If you wish to make the 10 second count shorter or longer, go back to boot-repair and select 'Advanced'.

Now you can restart.

MAKE THE SURFACE PRO 2 KEYBOARD AND MOUSE WORK


If you don't have some other source of internet, you can instead:
Double click the image file linux-image-3.11.10.4_20140314_amd64.deb that you can get from here [http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm](http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm) then install the headers file linux-headers-3.11.10.4_20140314_amd64.deb that you can get from here [http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK](http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK) . Note that for me there is a LONG delay sometimes between when I click "install" and when it asks for my sudo password... And often the "install" button becomes available again. I find that spamming the button is not kosher, just click it once and be very patient... lol
(The kernel is as provided by PointSource - thank you once again!)

WIFI

download the wifi driver mrvl-usb8797_uapsta.bin here [http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin](http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin) , then rename and copy it to /lib/firmware/mrvl/usb8797_uapsta.bin
cd Desktop
cp mrvl-usb8797_uapsta.bin /lib/firmware/mrvl/usb8797_uapsta.bin
Thank you microuav for the helpful tips.

Under Trusty Tahr (14.04), copying the mrvl firware works great.  My Wi-Fi and bluetooth now work!  (My bluetooth Microsoft surface wedge mouse also works.)

Installing and configuring grub2 does not allow me to use my type cover2 to specify my disk encryption PassCode.  (I have to use my USB keyboard instead.)

Trusty Tahr comes with 3.13.0.24-generic.  If I download the kernel sources, any suggestions on what I need to modify/patch, in order to get my type cover2 to work.  I don't want to install the older 3.11.10.4 kernel, and would prefer to make this work with this 3.13.0.24 kernel.

Thanks.

---

### Post by alicia4542 on 2014-04-21
Since I was desparate to get my Surface Pro2 to work with Ubuntu Trusty Tahr, I managed to modify the previous surface pro patch posted on this discussion thread, to get it to successfully build for the newer  linux-3.13.0-24.46_amd64.  (Although it was a challenge, since as a former Mac user, it was my first time ever building a Linux kernel.)

Note that the previous patch posted required a few changes for the newer HID files in the kernel source, in order to build.

So far for me, everything seems to be working, including my type cover2 (keyboard + trackpad), even during boot for my disk decyption passcode.

If anyone else is interested in trying it, you can download it here:

[http://www.mediafire.com/download/zxu6a00mh8r0uuq/surface_pro-linux-3.13.0-24-variante_3.13.0-24.46_amd64.zip](http://www.mediafire.com/download/zxu6a00mh8r0uuq/surface_pro-linux-3.13.0-24-variante_3.13.0-24.46_amd64.zip)

If you do try it, please let me know.  (So that I can see if it was worth wasting my entire Sunday evening on it.)

---

### Post by drmclaser on 2014-04-21
Thank you very much ! Everything works great, I now have a 14.04 with the same hardware support as I had with 13.10.

---

### Post by sq2-yful-nat on 2014-04-22
Works great for me too. Got the type cover 2 working out great.

---

### Post by alicia4542 on 2014-04-23
I seem to be having issues with suspend.  When I suspend to take my Surface Pro2 between home and work, I notice that it is still running and in the case it gets hot and the fan goes nuts.  And when I try to wake it up, it either crashes the OS, or wireless is completely dead.

Anyone else having these issues?  Is there a work-around or fix?

The biggest motivator in getting the Surface Pro2 instead of Pro1 was the battery life.  But without support for proper suspend and other power management, it won't make it through the day.

---

### Post by xylog on 2014-04-23
Was able to get wifi working with firmware file, but it will stop working after a few minutes and there is no way to revive except for rebooting. Power management seems to be broken - cannot suspend/resume without rebooting. Type cover Keyboard does not work.

---

### Post by alicia4542 on 2014-04-23
> **xylog said:**
> Was able to get wifi working with firmware file, but it will stop working after a few minutes and there is no way to revive except for rebooting. Power management seems to be broken - cannot suspend/resume without rebooting. Type cover Keyboard does not work.
Was this with my linux 3.13.0 kernel build, that I had previous posted on Easter?

As mentioned, power management is also broken for me, but at least my type cover2 and bluetooth works reliably.  However although WiFi works most of the time, it is not reliable and occasionally requires a reboot.

So much work and effort to replace Windows with Linux, and now there are still critical issues that make me consider switching back, since I was previously able to run my Surface Pro2 using Windows 8.1 for weeks without any rebooting or loss of device/interface support.

---

### Post by Jerry_Drake on 2014-04-24
> **alicia4542 said:**
> .....
So far for me, everything seems to be working, including my type cover2 (keyboard + trackpad), even during boot for my disk decyption passcode.

If anyone else is interested in trying it, you can download it here:

[http://www.mediafire.com/download/zxu6a00mh8r0uuq/surface_pro-linux-3.13.0-24-variante_3.13.0-24.46_amd64.zip](http://www.mediafire.com/download/zxu6a00mh8r0uuq/surface_pro-linux-3.13.0-24-variante_3.13.0-24.46_amd64.zip)

If you do try it, please let me know.  (So that I can see if it was worth wasting my entire Sunday evening on it.)


It did not work for me : actually that file messed up my system, the software center got stuck and I had to manually reinstall some missing files.
anyone here had luck with the power cover ? 
any solutions/patch for it ?
Thank you

---

### Post by javispedro2 on 2014-04-24
Suspend works for me very well on Gentoo / kernel 3.13.9, so it's either Ubuntu or something about your kernel. I have repeteadly suspended / resumed it like 10 times in a row to no problem, and it succesfully recovered the Wi-Fi connection every time.

Wi-Fi sometimes gets randomly stuck (spamming dmesg in the process) but it happens very infrequently, and if it happens it often happens right after a poweron. Removing/reinserting mwifiex may either fix it or oops the kernel.

Something to check: because of some problems with the firmware, Surface Pro will NOT get woken up by pressing keys on the keyboard. If yours wakes up, it is most probably not sleeping (and thus burning CPU). Otherwise I want to hear about your setup :) Also read dmesg often.

---

### Post by Frobozz on 2014-04-27
First of all, thanks to everyone in this thread. It's given me an Ubuntu tablet/laptop that I just love.

Is there a way to upgrade the firmware on the Surface Pro 1/2 without having to use Windows 8? My Pro is single-boot, Ubuntu only and firmware updates are about the only thing that make me consider going back to a dual-boot setup (but I'd lose so much space for an OS I never use!). I'm curious if anyone has solved this problem.

Thanks a lot!

---

### Post by yoshanuikabundi2 on 2014-04-27
Hi all,

With the help of this thread, I've (finally) got Ubuntu 12.04.4 dual-booting with Win 8.1 on my Surface Pro 2. I picked 12.04.4 because I figured it would be less bleeding edge, but I'm having troubles regardless. I've installed linux-image-3.11.10.4_20140314_amd64.deb and linux-headers-3.11.10.4_20140314_amd64.deb linked to by mack5, and I've copied the Marvell drivers over as instructed. My Type Cover 2 works and my Bluetooth mouse works, but my WiFi doesn't - I can select a network and enter my WPA key, but then it just gets stuck on "Connecting..." until it gives up.

I've tried two other wireless USB dongles but neither of them work. I've tried USB and Bluetooth tethering my phone, and they fail, though I can FTP into my phone over Bluetooth so I know it is pairing. I don't have access to a USB ethernet adapter.

I've also tried a few of the different drivers linked to in this thread but I can't get anything to work. Any hints?

---

### Post by microuav on 2014-05-02
> **yoshanuikabundi2 said:**
> Hi all,

With the help of this thread, I've (finally) got Ubuntu 12.04.4 dual-booting with Win 8.1 on my Surface Pro 2. I picked 12.04.4 because I figured it would be less bleeding edge, but I'm having troubles regardless. I've installed linux-image-3.11.10.4_20140314_amd64.deb and linux-headers-3.11.10.4_20140314_amd64.deb linked to by mack5, and I've copied the Marvell drivers over as instructed. My Type Cover 2 works and my Bluetooth mouse works, but my WiFi doesn't - I can select a network and enter my WPA key, but then it just gets stuck on "Connecting..." until it gives up.

I've tried two other wireless USB dongles but neither of them work. I've tried USB and Bluetooth tethering my phone, and they fail, though I can FTP into my phone over Bluetooth so I know it is pairing. I don't have access to a USB ethernet adapter.

I've also tried a few of the different drivers linked to in this thread but I can't get anything to work. Any hints?


I have exactly the same problem. Solutions are welcome so we can test them on our setup.
thanks in advanced.

---

### Post by zezrum on 2014-05-09
> **alicia4542 said:**
> Since I was desparate to get my Surface Pro2 to work with Ubuntu Trusty Tahr, I managed to modify the previous surface pro patch posted on this discussion thread, to get it to successfully build for the newer  linux-3.13.0-24.46_amd64.  (Although it was a challenge, since as a former Mac user, it was my first time ever building a Linux kernel.)

Note that the previous patch posted required a few changes for the newer HID files in the kernel source, in order to build.

So far for me, everything seems to be working, including my type cover2 (keyboard + trackpad), even during boot for my disk decyption passcode.

If anyone else is interested in trying it, you can download it here:

[http://www.mediafire.com/download/zxu6a00mh8r0uuq/surface_pro-linux-3.13.0-24-variante_3.13.0-24.46_amd64.zip](http://www.mediafire.com/download/zxu6a00mh8r0uuq/surface_pro-linux-3.13.0-24-variante_3.13.0-24.46_amd64.zip)

If you do try it, please let me know.  (So that I can see if it was worth wasting my entire Sunday evening on it.)

THANK YOU.  I really appreciate this - your update has made my Type Cover 2 working great on 14.04, as well as wifi.  I can finally enjoy Ubuntu on my Surface Pro 2.  I haven't tried to suspend yet so not sure how it behaves. I am dual booting with Win8.1, and kind of wish I went with the 512 vs. 265gb. :)

Thanks again.

---

### Post by edsena on 2014-05-11
> **Frobozz said:**
> First of all, thanks to everyone in this thread. It's given me an Ubuntu tablet/laptop that I just love.

Is there a way to upgrade the firmware on the Surface Pro 1/2 without having to use Windows 8? My Pro is single-boot, Ubuntu only and firmware updates are about the only thing that make me consider going back to a dual-boot setup (but I'd lose so much space for an OS I never use!). I'm curious if anyone has solved this problem.

Thanks a lot!

I wouldn't do that. Just bought a surface pro (1), a couple of weeks ago @ Amazon, and ubuntu 14.04 was running beautifully on it: type2, wifi, bluetooh, no issues at all (in fact, I decided to go with the first version exactly for compatibility reasons). 

But, instead of wiping at once the virus called windows from it, i let it there. After a few days, out of curiosity, I booted the windows partition and it showed me that I could upgrade my windows to 8.1. Innocently, I allowed the upgrade to go thru, to then realize that in the middle it also pushed some firmware upgrade. After that, my type2 cover isn't working anymore and, if I try to use the kernel (s) provided in this trhead, the type2 issue is solved but my wifi adapter can't connect to my WPA2 home network.  

So, in a nutshell: If ain't broke, don't fix it :-P

---

### Post by Frobozz on 2014-05-19
> **edsena said:**
> I wouldn't do that. Just bought a surface pro (1), a couple of weeks ago @ Amazon, and ubuntu 14.04 was running beautifully on it: type2, wifi, bluetooh, no issues at all (in fact, I decided to go with the first version exactly for compatibility reasons). 

But, instead of wiping at once the virus called windows from it, i let it there. After a few days, out of curiosity, I booted the windows partition and it showed me that I could upgrade my windows to 8.1. Innocently, I allowed the upgrade to go thru, to then realize that in the middle it also pushed some firmware upgrade. After that, my type2 cover isn't working anymore and, if I try to use the kernel (s) provided in this trhead, the type2 issue is solved but my wifi adapter can't connect to my WPA2 home network.  

So, in a nutshell: If ain't broke, don't fix it :-P

   That's actually a very good point. Right now the Pro is working out great as a linux machine. I'd really rather not mess that up if at all possible. Thanks!

--
Chris

---

### Post by alicia4542 on 2014-05-29
FYI, for those that are interested, I recently build a new Surface Pro kernel, upgraded to Linux (amd64) 3.13.0-27.50, using Generic with Surface Pro patch, to enable the covers.

You can download it here:

[http://www.mediafire.com/download/41670zslebf1jlj/linux-3.13.0-27.50-surfacepro.zip](http://www.mediafire.com/download/41670zslebf1jlj/linux-3.13.0-27.50-surfacepro.zip)

Furthermore if you are interested in building your own kernel, you can apply this Surface Pro fix to the kernel source tree:

[http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

With regard to my previously reported suspend/hibernate issues, it was due to an unrelated cause.  Specifically I carry my surface pro 2 around in my purse, and for some reason the power button gets accidentally pressed.  I will need to see if there is some type of physical protection for that button to prevent it from being pressed.  I have no difficulties with suspend & hiberate when the surface pro is on my desk.

This was not an issue with Windows 8.1u1 and my same purse, since as long as the cover is closed, Windows won't turn on.  But with Ubuntu, when I hibernate, it remains in the LUKS boot password prompt indefinitely without sleeping or turning off, even when there is no password.  And with suspend, when it turns on, it remains in the user login prompt to resume, without going to back to sleep when the cover is closed and there is no input.

With regard to WiFi, it is very flaky.  Even with the current firmware, often just visiting a large webpage is enough to kill both WiFi (mlan) and BlueTooth.  When this happens, [COLOR=#0000ff]**does anyone know if there is a way to reset the wireless driver without having to reboot?**[/COLOR]

And my last issue.  [COLOR=#0000ff]**Is there anyway to force Ubuntu to recognise the pen input as a proper Watcom device?**[/COLOR] The control panel for Watcom is expecting some type of USB device.

Cheers and thanks in advance.

---

### Post by tobyw01 on 2014-06-04
This thread is great.  I'm able to get ubuntu gnome on my Surface Pro 1. Is anyone else using gnome OSK is a little flaky but everything else works well.

---

### Post by john235 on 2014-06-05
> **alicia4542 said:**
> FYI, for those that are interested, I recently build a new Surface Pro kernel, upgraded to Linux (amd64) 3.13.0-27.50, using Generic with Surface Pro patch, to enable the covers.

You can download it here:

[http://www.mediafire.com/download/41670zslebf1jlj/linux-3.13.0-27.50-surfacepro.zip](http://www.mediafire.com/download/41670zslebf1jlj/linux-3.13.0-27.50-surfacepro.zip)




Hi, 

Thank you so much for really working on making this work and I apologize for my ignorance - as I'm new to all of this. It would be great if you could help me out with installation problems I'm having. I have Surface Pro2 and Ubuntu 14.04 on a separate partition. I have only the keyboard of the Type Cover 2 working and I currently don't have Wifi, Touchpad, or Bluetooth.

I downloaded your file package and tried to install it. There are 4 files in it and whenever I try Cloud tools, Headers and the Tools files, i get something similar to the following:

Dependency is not satisfiable: (then the file name and description)

I did manage to get the Image one to install. Any ideas?? 
Thanks in advance!

---

### Post by NoLongerHere on 2014-06-06
Nevermind.

I normally use archlinux, and I was going the roundabout way installing Ubuntu in order to use a signed-boot to bypass the ugly red screen.
Read a bit on shim and decided to just make and sign things to make things easier. 

For anyone interested. Just follow: [http://www.rodsbooks.com/efi-bootloaders/secureboot.html](http://www.rodsbooks.com/efi-bootloaders/secureboot.html)

It's pretty straightforward and simple.

---

### Post by alicia4542 on 2014-06-07
> **john235 said:**
> Hi, 
Thank you so much for really working on making this work and I apologize for my ignorance - as I'm new to all of this. It would be great if you could help me out with installation problems I'm having. I have Surface Pro2 and Ubuntu 14.04 on a separate partition. I have only the keyboard of the Type Cover 2 working and I currently don't have Wifi, Touchpad, or Bluetooth.
I downloaded your file package and tried to install it. There are 4 files in it and whenever I try Cloud tools, Headers and the Tools files, i get something similar to the following:
Dependency is not satisfiable: (then the file name and description)
did manage to get the Image one to install. Any ideas?? 
Thanks in advance!
It sounds like you are missing some important dependencies
Before installing my kernel, first install the base kernel tools, cloud, and header files of the same version.

**I have just released a new updated version for Linux kernel 3.13.0-29.53 for Surface Pro:**[INDENT][http://www.mediafire.com/download/ja5jdfv25szj5tu/linux-3.13.0-29.53-surfacepro.tgz](http://www.mediafire.com/download/ja5jdfv25szj5tu/linux-3.13.0-29.53-surfacepro.tgz)[/INDENT]

So make sure that you first install: linux-headers-3.13.0-29, linux-tools-3.13.0-29, & linux-cloud-tools-3.13.0-29, before installing my Surface Pro Linux Kernel packages.

Note my my trackpad on my Type Cover 2 is working okay with this and the previous kernel.

With regard to your wireless (WiFi & BlueTooth), you need to replace the firmware binary as follows:
        
[LIST]
[*]wget 'http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin' -O usb8797_uapsta.bin
[*]cp usb8797_uapsta.bin  /lib/firmware/mrvl/usb8797_uapsta.bin
[/LIST]
And then reboot.

---

### Post by bowmessage on 2014-06-09
> **alicia4542 said:**
> It sounds like you are missing some important dependencies
Before installing my kernel, first install the base kernel tools, cloud, and header files of the same version.

**I have just released a new updated version for Linux kernel 3.13.0-29.53 for Surface Pro:**[INDENT][http://www.mediafire.com/download/ja5jdfv25szj5tu/linux-3.13.0-29.53-surfacepro.tgz](http://www.mediafire.com/download/ja5jdfv25szj5tu/linux-3.13.0-29.53-surfacepro.tgz)[/INDENT]

So make sure that you first install: linux-headers-3.13.0-29, linux-tools-3.13.0-29, & linux-cloud-tools-3.13.0-29, before installing my Surface Pro Linux Kernel packages.

Note my my trackpad on my Type Cover 2 is working okay with this and the previous kernel.

With regard to your wireless (WiFi & BlueTooth), you need to replace the firmware binary as follows:
        
[LIST]
[*]wget 'http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin' -O usb8797_uapsta.bin
[*]cp usb8797_uapsta.bin  /lib/firmware/mrvl/usb8797_uapsta.bin
[/LIST]
And then reboot.

Thanks! Your new kernel worked really well on my Surface Pro 1. How much code did you have to write? Would it be possible to release a diff file? Thanks so much!

EDIT: Just wanted to drop an edit here and help some of the people with spotty WiFi connections. I find that when I stream media (usually music using Spotify) that I get a much better connection quality. It seems that by keeping the connection alive more often I get interrupted less often. Just wanted to share that.

---

### Post by john235 on 2014-06-10
Thank you so much for the information. As I'm going through these things, I'm starting to understand little by little...

I managed to get everything working (Type Cover 2, internet, etc...) then, the Software Center installed a bunch of updates. Now I can't use Type Cover 2 again...
Did you guys run into the same issue?

---

### Post by tobyw01 on 2014-06-11
> **john235 said:**
> Thank you so much for the information. As I'm going through these things, I'm starting to understand little by little...

I managed to get everything working (Type Cover 2, internet, etc...) then, the Software Center installed a bunch of updates. Now I can't use Type Cover 2 again...
Did you guys run into the same issue?

You probably got the kernel update that was released and its using the new one at boot time.  Use the modified one on the thread posted by alicia4542 in the Grub menu if loaded it.

---

### Post by rodolforoblesss on 2014-06-12
Hello, I have the first surface, could anyone tell me the average battery time you get with yours?

I only get about 2 hours or less...

---

### Post by john235 on 2014-06-14
Hey guys,

Thanks so much for helping out. I got one more challenge. Now I have the Ubuntu running on my SurfacePro2 and everything seems to be working great - except Wifi will slack sometimes, I have to reboot. I don't have Windows 8.1 anymore and I would like to put it back. I think my steps are:

1. Boot with Gparted Live to make a new partition for Windows.
2. Make a bootable USB with the Windows 8.1 iso

Unfortunately, after I create the bootable Gparted Live, I can't seem to boot from the USB. On the Grub2 menu, all I see is UBuntu, Advanced Options and Settings. Any ideas how to boot with USB on SurfacePro that has only Ubuntu on it?

Thanks!

---

### Post by jtensuan on 2014-06-18
> **alicia4542 said:**
> It sounds like you are missing some important dependencies
Before installing my kernel, first install the base kernel tools, cloud, and header files of the same version.

**I have just released a new updated version for Linux kernel 3.13.0-29.53 for Surface Pro:**[INDENT][http://www.mediafire.com/download/ja5jdfv25szj5tu/linux-3.13.0-29.53-surfacepro.tgz](http://www.mediafire.com/download/ja5jdfv25szj5tu/linux-3.13.0-29.53-surfacepro.tgz)[/INDENT]

So make sure that you first install: linux-headers-3.13.0-29, linux-tools-3.13.0-29, & linux-cloud-tools-3.13.0-29, before installing my Surface Pro Linux Kernel packages.

Note my my trackpad on my Type Cover 2 is working okay with this and the previous kernel.

With regard to your wireless (WiFi & BlueTooth), you need to replace the firmware binary as follows:
        
[LIST]
[*]wget 'http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin' -O usb8797_uapsta.bin 
[*]cp usb8797_uapsta.bin  /lib/firmware/mrvl/usb8797_uapsta.bin 
[/LIST]
And then reboot.

thanks for this, the kernel fixes my type cover 2 on my surface pro 1; the drivers also seem to make my wifi a bit more stable.  :cool: 

I do seem to have an issue with suspend though.  I didn't see it mentioned in this thread (different issue than the 'suspend and won't wake' issue).  When I try to suspend, my system appears to enter suspend, but then it turns right back on after a few seconds.

Anyone else see this?

TIA!

---

### Post by microuav on 2014-06-19
Thanks again for the hard work in this treat.

As a thank you I will describe what steps I did to make my surface pro 2 dual boot on Linux 14.04 and windows 8 also whit a theme boot loader!!
WiFi, touch pad, type cover 2, touch screen all works
only thing is the WiFi will not work after suspend. If a new kernel is released where this problem is solved you defiantly find it in this great threat later on.

What do you need:
-A surface pro
-USB dongle with 4 ports
-Wireless USB dongle
-USB mouse
-USB keyboard
-empty USB stick >=3GB


The beginning make a partition:

To begin, repartition your harddrive to make space for your ubuntu install from within windows. 
first step on this site
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
Create a partitioned drive.
-Press search button on your keyboard type 'boot'.
-Select 'settings >> Create and format disk partitions'
-Select C drive, right click and select 'shrink volume'.
-This is your choice but I use appox. 29.3 Gigs(30,000 MB): Shrink respectively.


Further, install all updates of windows (at least up to the date this post was made). 


USING THE MICROSOFT UEFI CA TOOL FOR SURFACE PRO


follow the instructions linked to earlier by patrick.broetto, here.
[http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro](http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro)

in short:
[http://www.microsoft.com/en-us/download/details.aspx?id=41666](http://www.microsoft.com/en-us/download/details.aspx?id=41666)
link to dounload Microsoft Surface Pro UEFI CA OEM PK Tool
unzip 
 OEM_PK_Surface


1)  Save the platform key by running the SavePlatformKey.cmd script. 
make sure you use a command prompt with admin privileges, eg by right clicking it in the wondows 8.1 start menu and hitting "run as admin". or go to the C map in windows explorer and click "file" then "open command prompt" then "run command prompt as admin".
 If you ran this properly, you should be able to boot to your ubuntu install usb driver WITHOUT turning off Secure Boot.
cd ..\..
cd Users\microuav\Downloads\ubuntu\OEM_PK_Surface
SavePlatformKey.cmd


2)Boot to the UEFI menu using the Power/Volume+ button combination at power on - See more at: [http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro#sthash.X1ZGV836.dpuf](http://uefidk.intel.com/blog/using-microsoft-uefi-ca-tool-surface-pro#sthash.X1ZGV836.dpuf)


3)Use the UEFI menu entry to &#8216;Delete all Secure Boot keys&#8217;, then save and reset.


4)Boot back into Windows and run the InstallSecureBootWithMsftUefiCertAuthToDB.cmd script.
cd ..\..
cd Users\microuav\Downloads\ubuntu\OEM_PK_Surface
InstallSecureBootWithMsftUefiCertAuthToDB.cmd


MAKE UBUNTU USB BOOT DRIVE


take your empty USB drive


download ubuntu desktop
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)


to make a ubuntu usb boot drive use Universal-USB-Installer-1.9.5.2
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


INSTALL UBUNTU


Put your Ubuntu Live USB disk and USB keyboard, USB mouse and USB wifi dongle in a USB hub and in the USB 3 port on the Surface Pro, and head back to the Settings menu on the Charm Bar of windows 8.1. Navigate to settings, General PC settings, update and recovery then recovery and boot into Advanced Startup. Tap the icon with the USB stick and the DVD labeled Use a Device one the Surface has booted into the Advanced settings (if you come back in windows you need to do it ones more).


When you get to the point where it asks you for your "installation type" click "do something else." Create swap space, and a new partition as described in this guide.


[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)


-It will ask if you want to unmount your installation device. Select 'No'.
-Now select the new free space and press the '+' button under the partitions.
-Select from the drop list 'swap' and select the 'logical' radio button and 'insert at beginning' and finish. Select anywhere from 400 to 600 MB to be safe at least.


-Now select the new free space and press the 'change' button - again.
-Select from the drop list 'Ext4' and select the 'primary' radio button, 'insert at beginning', 'format' button checked and '/' as root and finish. Use the remaining space you have reserved.
-Finish your install, and then in your initial boot of ubuntu I advise (solely to avoid complications) making sure you run the updater, and installing anything recommended (or don't, that's your prerogative). Reboot to make sure it all goes smooth. 
-Finish install process on the Ext4 partition you created.
!!!Do not restart, click the Continue Testing button.!!!

connect the USB WiFi dongle to the your WiFi network


DUAL BOOT MENU


Make sure Grub2 was installed without problem.


sudo apt-get install grub2-common
sudo update-grub2


Setup Grub2 boot repair and run.


sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
sudo boot-repair


Select 'Recommended Repair'.
Restart to make sure you see the boot loader. If you wish to make the 10 second count shorter or longer, go back to boot-repair and select 'Advanced'.


Now you can reboot.








MAKE THE SURFACE PRO 2 KEYBOARD AND MOUSE WORK


old version before 17/06/2014


If you don't have some other source of internet, you can instead:
Double click the image file linux-image-3.11.10.4_20140314_amd64.deb that you can get from here [http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm](http://ubuntuone.com/6yG9RLMEBmpUGVvL25qvBm) then install the headers file linux-headers-3.11.10.4_20140314_amd64.deb that you can get from here [http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK](http://ubuntuone.com/1BGEYJsffNAGDhI7CA3PCK) . Note that for me there is a LONG delay sometimes between when I click "install" and when it asks for my sudo password... And often the "install" button becomes available again. I find that spamming the button is not kosher, just click it once and be very patient... lol
(The kernel is as provided by PointSource - thank you once again!)


version on 17/06/2014

[http://ubuntuforums.org/showthread.php?t=2183946&page=12&p=13043433#post13043433](http://ubuntuforums.org/showthread.php?t=2183946&page=12&p=13043433#post13043433)


it sounds like you are missing some important dependencies
Before installing my kernel, first install the base kernel tools, cloud, and header files of the same version.


I have just released a new updated version for Linux kernel 3.13.0-29.53 for Surface Pro:
[http://www.mediafire.com/download/ja...surfacepro.tgz](http://www.mediafire.com/download/ja...surfacepro.tgz)


So make sure that you first install: linux-headers-3.13.0-29, linux-tools-3.13.0-29, & linux-cloud-tools-3.13.0-29, before installing my Surface Pro Linux Kernel packages. 

sudo apt-get install linux-headers-3.13.0-29-generic  linux-tools-3.13.0-29-generic linux-cloud-tools-3.13.0-29-generic  linux-image-3.13.0-29-generic

or can be done by following those steps (it takes a wile):
 make 14.04 update and install usfull software
[http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr))


_** version on 28/06/2014**_

[http://ubuntuforums.org/showthread.php?t=2183946&page=13&p=13060893#post13060893](http://ubuntuforums.org/showthread.php?t=2183946&page=13&p=13060893#post13060893)

**first Do:**
sudo apt-get install linux-headers-3.13.0-30-generic  linux-tools-3.13.0-30-generic linux-cloud-tools-3.13.0-30-generic  linux-image-3.13.0-30-generic

** Please download here:**
[http://www.mediafire.com/download/v3...surfacepro.tgz]("http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz")
[B]Double click the image file linux-image
then install the headers file linux-headers[/B]


Note my my trackpad on my Type Cover 2 is working okay with this and the previous kernel.

new kernel image:
[http://ubuntuforums.org/showthread.php?t=2183946&page=15&p=13100140#post13100140](http://ubuntuforums.org/showthread.php?t=2183946&page=15&p=13100140#post13100140)
progress towards making the Surface Pro 2 hardware more stable. I've  compiled a kernel image from mainline, it is available here: [https://drive.google.com/open?id=0Bz...F9QcFVEdjMtUnM]("https://drive.google.com/open?id=0Bzl2mZ4p-k_DZF9QcFVEdjMtUnM")
I've also stumbled across a set of programs at [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop)  that can dynamically re-orient the screen based on accelerometer data,  and change the backlight brightness according to ambient light. They  were written for the Lenovo Ideapad Yoga, but work just as well on the  SP2. You have to change the touchscreen device though:      Code:
      $ sudo ./orientation --touchscreen="Atmel Atmel maXTouch Digitizer" 


_** With regard to your wireless (WiFi & BlueTooth), you need to replace the firmware binary as follows:**_


    wget 'http://git.marvell.com/?p=mwifiex-firmware.git;a=blob;f=mrvl/usb8797_uapsta.bin' -O usb8797_uapsta.bin
    sudo cp usb8797_uapsta.bin /lib/firmware/mrvl/usb8797_uapsta.bin




And then reboot!!
when rebooting remove the WiFi USB dongle from the USB hub


THEMED BOOT-LOADER FOR UBUNTU 14.04 (looks very nice [http://youtu.be/ZygXCR6qqGs](http://youtu.be/ZygXCR6qqGs) )


[https://github.com/webbrandon/Surface-Boot-Themes](https://github.com/webbrandon/Surface-Boot-Themes)


#INSTALL INSTRUCTIONS
extract Surface-Boot-Themes-master.zip
to desktop


1) sudo mkdir /usr/share/grub/themes (IF DONE SKIP TO TWO.)


   cd Desktop/Surface-Boot-Themes-master/


2) sudo cp --recursive ./surface /usr/share/grub/themes


3) Add the following line below to 
   sudo gedit /etc/default/grub
   GRUB_THEME=/usr/share/grub/themes/surface/theme.txt


4) Make the repair title and icon for kernel repair.


   sudo gedit /etc/grub.d/10_linux 
   and search for(towards bottom) for:
   echo "submenu '$(gettext_printf "Advanced options for %s" "${OS}" | grub_quote)'
   Insert the following immediatly after:
   --class recovery --class repair
   (note: edit "Advanced options for %s" to "Repair")


5) Make the Secure Boot title and icon.


   sudo gedit /etc/grub.d/30_uefi-firmware
   and search for(towards bottom) :
   menuentry '$LABEL'
   Insert the following immediatly after:
   --class secure --class recovery
   (note: edit '$Label' to "Secure Boot")


6) NOT NEEDED FOR 14.04
   
7) sudo update-grub


8) Reboot


NOW YOU ARE DONE







AFTER WINDOWS UPDATE
your dual boot is not working any more. you are straight booting up in windows.
grub menu is not showing up when booting
to solve install graphical interface boot repair:


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


- from an USB Ubuntu live-session (boot your computer on a Ubuntu live-USB then choose "Try Ubuntu") 
- connect to the Internet with wifi dongle via usb hub
- connect mouse and keyboard to usb dongel.
- open a new Terminal, then type the following commands (press Enter after each line): 


sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)


Use Recomended Repair.
follow the instruktions on the screen.


spotted in the comments of this site
[http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

if it is still not working you can try it from within Windows
install this program in windows

[http://www.easyuefi.com/index-us.html](http://www.easyuefi.com/index-us.html)

found in this description last box bothem of the page: [COLOR=#3A5FAD][FONT=abelregular]If your computer is NOT booting into the Grub Bootloader &#8230;[/FONT][/COLOR]
[http://www.tweaking4all.com/os-tips-and-tricks/uefi-dual-boot-windows81-ubuntu/](http://www.tweaking4all.com/os-tips-and-tricks/uefi-dual-boot-windows81-ubuntu/)


If you want to use the same data disk in windows and Linux you have to disable fast startup option in windows:
[http://itsfoss.com/solve-ntfs-mount-problem-ubuntu-windows-8-dual-boot/](http://itsfoss.com/solve-ntfs-mount-problem-ubuntu-windows-8-dual-boot/)




Make windows boot first:

[http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/step7/Boot-Manager-Customization-optional/](http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/step7/Boot-Manager-Customization-optional/)

In order to simplify the available options you can also install the &#8220;Grub Customizer&#8221;.


Among other things, this applications allows you to:


- Set the default operating system;
- Set the boot manager timeout;
- Hide/Show boot options;


To install this tool you can just open a console and insert the following commands;


sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
sudo grub-customizer


Then you can open the program and start customizing.


In the first tab you can eliminate/hide non desired options, so that the menu will only show the options you want. In our case, we only left one option for Ubuntu and one for Windows. With a right click you can also rename the entries, which in this case we did for &#8220;Windows Boot UEFI loader&#8221; to just &#8220;Windows 8&#8221;.


Deleted entries go to the trash bin but they can be restored at any moment...



[B]Disable fast startup in windows
[/B]this make you able to get to your windows data when in Linux
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

[B]Virualbox your linux partiton in windows 
[COLOR=#ff0000]NOT WORKING YET (all substaps are working but VirtualBox error: no bootable medium found)
[/COLOR][/B][http://lifehacker.com/how-to-dual-boot-and-virtualize-the-same-partition-on-y-493223329](http://lifehacker.com/how-to-dual-boot-and-virtualize-the-same-partition-on-y-493223329)
[https://www.youtube.com/watch?v=D9TePODkYME](https://www.youtube.com/watch?v=D9TePODkYME)

**Step One: Create Your New Virtual Machine**

[FONT=Georgia]Assuming you already have both partitions set up, boot into Windows and perform the following steps:[/FONT]

[LIST=1]
[*]Back up everything before you begin. No, I'm serious. Don't skip this step. Don't! 
[*]Open up a Command Prompt as an administrator and run the following command: wmic diskdrive list brief /format:list Find the drive on which your Linux partition resides and note its number (in my case, it was Disk 0) 
[*]Use the CD command to change to the directory in which VirtualBox is installed. For me, this was: CD "C:\Program Files\Oracle\VirtualBox" 
[*]Run this next command, replcaing the variables with the correct ones for your system: VBoxManage internalcommands createrawvmdk -filename "C:\Users\Bart\Desktop\Ubuntu.vmdk" -rawdisk \\.\PhysicalDrive0 Replace the file path with wherever you want to put your VMDK file. Replace the 0 in \\.\PhysicalDrive0 with your disk number. 
[*]You should get a message saying the VMDK was created successfully. If not, make sure you followed these steps *exactly*, and if you're still having problems [read through that manual chapter]("http://www.virtualbox.org/manual/ch09.html#rawdisk"). You may have special needs that we didn't discuss here. 
[/LIST]
**Step Two: Create a GRUB ISO**

[FONT=Georgia]Now, boot into Linux. We're going to use Ubuntu for this example. Before we set up our virtual machine, we'll need to put the GRUB bootloader on an ISO, since not all computers will load your existing version of GRUB properly. Once you're inside Linux, perform the following steps:[/FONT]

[LIST=1]
[*]Create a new folder on your desktop and call it "iso." Inside that folder, create one called "boot," and inside the boot folder, create a folder called "grub." 
[*]Open a terminal and run the following command: cp /usr/lib/grub/x86_64-efi/* /home/microuav/Desktop/iso/boot/grub Obviously, replace "microuav" with your user name. 
[*]Next, run:   cp /boot/grub/grub.cfg /home/microuav/Desktop/iso/boot/grub 
[*]Run the following command: sudo nano /home/microuav/Desktop/iso/boot/grub/grub.cfg Scroll down to the section that says "menuentry 'Windows'" or something similar, and delete everything from "menuentry" to the "}" at the end of that section. 
[*]Lastly, run: grub-mkrescue -o boot.iso /home/microuav/Desktop/iso/ install the **xorriso** package **first** with: sudo apt-get install xorriso When you're done, you should have a file called boot.iso in your home directory. Copy this to a flash drive or to your Windows partition. 
[/LIST]

**Step Three: Boot Into Your New Virtual Machine**

[FONT=Georgia]Now, it's time to boot back into Windows and get this sucker up and running. Once you've returned to Windows:[/FONT]

[LIST=1]
[*]Run VirtualBox as an administrator. Click the New button and name your virtual machine. Choose the amount of RAM to allocate to the virtual machine as normal. 
[*]At the next step, choose "Use an existing virtual hard drive file." Click the browse button on the right, and browse to the VMDK file we made earlier. Click the Create button. If all goes well, you should see it show up in VirtualBox's sidebar. 
[*]Select your new virtual machine in the sidebar and click the Settings button. Under Storage, select "Controller: IDE" and click the plus sign next to it. Press "Choose Disk" and navigate to the boot.iso file we created earlier. Click OK and return to the main VirtualBox screen. 
[*]Select your new virtual machine and click the Start button. Choose Linux from the GRUB menu that pops up. 
[*]If all goes well, you should see your Linux installation's login screen. You can log in, [install VirtualBox's Guest Additions]("http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox"), and use your Linux partition without shutting down Windows! 
[/LIST]
[FONT=Georgia]*IMPORTANT NOTE*: Never try to mount or read from your Windows partition while you're running Linux in VirtualBox. This is where the danger of this method comes in. If you try to read your Windows partition, your machine will crash and you could cause data corruption (since your host OS is already using that partition). In fact, I recommend [removing it from your fstab file]("http://www.tuxfiles.org/linuxhelp/fstab.html") so it never pops up in Linux, thus keeping you much safer.[/FONT]


[http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/)

Surface pro3 dual boot

[http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/](http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/)

 Hopes it helps
Microuav

---

### Post by Jerry_Drake on 2014-06-27
Thanks for all the efforts and the explanations; still my power keyboard does not work. 
Anyone here has the power keyboard working ? Ubuntu just sees it a second battery.
Thanks

---

### Post by alicia4542 on 2014-06-28
A newly updated Linux kernel for Surface Pro, version 3.13.0-30.54, tested and working on my Surface Pro 2 with Type Cover 2.

Please download here:
[http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz](http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz)

It was built using mostly generic kernel config using these same patches for the Surface Pro as the previous version:
[http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

Note that from now on, to save space, I will only keep the the last two kernel versions in my shared folder, which now includes just this 3.13.0-30.54 and the previous 3.13.0-29.53 kernels.  Older versions have been deleted.

I would appreciate knowing if it works on the power cover, since I don't have one.  If not, I will see if there is a patch for it, that I could apply to the kernel.

To Surface Pro 3 owners, whom I am very envious of, I would also appreciate knowing if this kernel works or not, and if there is any other patches I should add.

It would be best to have a single kernel patch for all Surface Pro versions and covers.

---

### Post by Jerry_Drake on 2014-06-30
Still the power cover does not work even with the last update....

---

### Post by jtensuan on 2014-06-30
> **alicia4542 said:**
> A newly updated Linux kernel for Surface Pro, version 3.13.0-30.54, tested and working on my Surface Pro 2 with Type Cover 2.

Please download here:
[http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz](http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz)

It was built using mostly generic kernel config using these same patches for the Surface Pro as the previous version:
[http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

Note that from now on, to save space, I will only keep the the last two kernel versions in my shared folder, which now includes just this 3.13.0-30.54 and the previous 3.13.0-29.53 kernels.  Older versions have been deleted.

I would appreciate knowing if it works on the power cover, since I don't have one.  If not, I will see if there is a patch for it, that I could apply to the kernel.

To Surface Pro 3 owners, whom I am very envious of, I would also appreciate knowing if this kernel works or not, and if there is any other patches I should add.

It would be best to have a single kernel patch for all Surface Pro versions and covers.

Thanks again for your work on the kernel, this most recent one and the previous work great on my surfacepro1 with type cover2.

noob question- I am using the above referenced kernel; if I do a software update, it looks like it will update to the generic kernel.  I know I can just choose the proper (custom) kernel when booting up in grub, but is there (an easy) way to either disable the kernel update, or keep the custom kernel as default when booting?  

Hope that makes sense, thx!

---

### Post by bowmessage on 2014-07-01
> **jtensuan said:**
> Thanks again for your work on the kernel, this most recent one and the previous work great on my surfacepro1 with type cover2.

noob question- I am using the above referenced kernel; if I do a software update, it looks like it will update to the generic kernel.  I know I can just choose the proper (custom) kernel when booting up in grub, but is there (an easy) way to either disable the kernel update, or keep the custom kernel as default when booting?  

Hope that makes sense, thx!

I may be wrong, but in my experience this means that my generic kernel is at a newer version than my surfacepro kernel, and its time to update with a version provided by one of the awesome folks here on the forums!

If that's not the case for you, it looks like this askubuntu question might help you out: [http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry](http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry)

---

### Post by javispedro2 on 2014-07-01
hello, I've found that we can use the firmware file for the Avastar/Wi-Fi card from the Windows drivers and use it on the opensource driver seemingly without problems. While this is probably useless for most people, it may be useful for 'developers'/tinkerers who are trying to diagnose problems with the mwifiex_usb driver, to remove that persistent doubt that the issues might be caused by differences in the public  firmwares :)

Again: *this does nothing to help with your Wi-Fi problems*. Don't do this. And even if you consider yourself 'developer' don't blame me if you do this and your card explodes, cause I only tried it for a few minutes.

To extract the firmware file from Windows drivers:

1. Download Surface Pro 2 driver pack from [http://www.microsoft.com/en-us/download/details.aspx?id=38826](http://www.microsoft.com/en-us/download/details.aspx?id=38826)

2. Extract file mwlu97w8x64.sys . It can be found in Surface Pro 2 - June 2014.zip/Marvell/wlan . Its md5sum is
```
59debcf12e8b5ab0b14cc8b8d3c2bc66  mwlu97w8x64.sys
```

3. Extract the firmware file from the driver .sys file:
```
dd ibs=1 count=492788 skip=$((0x102150)) if=mwlu97w8x64.sys of=usb8797_uapsta.bin
```
The md5sum of resulting usb8797_uapsta.bin should be
```
075cd2de8537348c3efc194896bd18f6  usb8797_uapsta.bin
```

Note that the Windows firmware is sligthly more recent that the latest available public firmware (jan2014 vs dec2013), but is also significantly smaller for some reason.

---

### Post by zer0fun on 2014-07-08
> **alicia4542 said:**
> A newly updated Linux kernel for Surface Pro, version 3.13.0-30.54, tested and working on my Surface Pro 2 with Type Cover 2.

Please download here:
[http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz](http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz)

It was built using mostly generic kernel config using these same patches for the Surface Pro as the previous version:
[http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

Note that from now on, to save space, I will only keep the the last two kernel versions in my shared folder, which now includes just this 3.13.0-30.54 and the previous 3.13.0-29.53 kernels.  Older versions have been deleted.

I would appreciate knowing if it works on the power cover, since I don't have one.  If not, I will see if there is a patch for it, that I could apply to the kernel.

To Surface Pro 3 owners, whom I am very envious of, I would also appreciate knowing if this kernel works or not, and if there is any other patches I should add.

It would be best to have a single kernel patch for all Surface Pro versions and covers.


ya the power cover only shows up as a battery.  Thanks so much for the work on this.

---

### Post by tobyw01 on 2014-07-15
All,  I rebooted into my windows partition to find a windows firmware update available dated 7/8/2014. Has anyone tried to install it yet.  I don't want it to break things for my Ubuntu install.  If anyone has tried it can you please post results.

Thanks,

---

### Post by javispedro2 on 2014-07-17
The new update only seems to install a new Wi-Fi driver on the windows side, so it should be safe. It is a "windows hardware update" and not a firmware update.

See official changelog for more info: [http://www.microsoft.com/surface/en-us/support/install-update-activate/pro-2-update-history](http://www.microsoft.com/surface/en-us/support/install-update-activate/pro-2-update-history)

Note however that if you've been skipping other updates this one may install them.

---

### Post by tobyw01 on 2014-07-20
> **javispedro2 said:**
> The new update only seems to install a new Wi-Fi driver on the windows side, so it should be safe. It is a "windows hardware update" and not a firmware update.

See official changelog for more info: [http://www.microsoft.com/surface/en-us/support/install-update-activate/pro-2-update-history](http://www.microsoft.com/surface/en-us/support/install-update-activate/pro-2-update-history)

Note however that if you've been skipping other updates this one may install them.

Thanks,:KS

---

### Post by GusBricker on 2014-08-03
> **alicia4542 said:**
> A newly updated Linux kernel for Surface Pro, version 3.13.0-30.54, tested and working on my Surface Pro 2 with Type Cover 2.

Please download here:
[http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz](http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz)

It was built using mostly generic kernel config using these same patches for the Surface Pro as the previous version:
[http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

Note that from now on, to save space, I will only keep the the last two kernel versions in my shared folder, which now includes just this 3.13.0-30.54 and the previous 3.13.0-29.53 kernels.  Older versions have been deleted.

I would appreciate knowing if it works on the power cover, since I don't have one.  If not, I will see if there is a patch for it, that I could apply to the kernel.

To Surface Pro 3 owners, whom I am very envious of, I would also appreciate knowing if this kernel works or not, and if there is any other patches I should add.

It would be best to have a single kernel patch for all Surface Pro versions and covers.
Hi

I have just tried to install your kernel in Ubuntu 14.04.01 LTS on my SP2, i have managed to get the wifi working but the type cover seems intermittant. It sometimes works when my sp wakes from sleep.
Specifically I ran these commands:
1) sudo apt-get install linux-headers-3.13.0-30-generic linux-tools-3.13.0-30-generic linux-cloud-tools-3.13.0-30-generic linux-image-3.13.0-30-generic
2)  sudo dpkg -i linux-headers-3.13.0-30-surfacepro_3.13.0-30.54_amd64.deb linux-tools-3.13.0-30-surfacepro_3.13.0-30.54_amd64.deb linux-cloud-tools-3.13.0-30-surfacepro_3.13.0-30.54_amd64.deb linux-image-3.13.0-30-surfacepro_3.13.0-30.54_amd64.deb
If I run uname -a after a reboot I can see the kernel update doesnt seem to have been applied?

dmesg shows this when i unplug and plug in the type cover:
```
[  881.387102] usb 2-3: USB disconnect, device number 15
[  881.387836] ACPI Error: [\SB__.IADP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[  881.387857] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q41] (Node ffff880119ac6b90), AE_NOT_FOUND (20131115/psparse-536)
[  881.765428] usb 2-3: new full-speed USB device number 16 using xhci_hcd
[  881.783825] usb 2-3: New USB device found, idVendor=045e, idProduct=07a9
[  881.783834] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  881.783839] usb 2-3: Product: SAM
[  881.783843] usb 2-3: Manufacturer: MICROSOFT
[  881.783847] usb 2-3: SerialNumber: 0.1.0000
[  891.791944] hid-sensor-hub 0003:045E:07A9.0015: usb_submit_urb(ctrl) failed: -1
[  891.791996] hid-sensor-hub 0003:045E:07A9.0015: timeout initializing reports
[  891.792979] hid_sensor_magn_3d HID-SENSOR-200083.2.auto: failed to setup attributes
[  891.793000] hid_sensor_magn_3d: probe of HID-SENSOR-200083.2.auto failed with error -1
[  891.796633] input: MICROSOFT SAM as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.1/input/input20
[  891.796821] hid-generic 0003:045E:07A9.0016: input,hidraw0: USB HID v1.11 Keyboard [MICROSOFT SAM] on usb-0000:00:14.0-3/input1
[  891.799468] hid-generic 0003:045E:07A9.0017: item fetching failed at offset -1409853854
[  891.799488] hid-generic: probe of 0003:045E:07A9.0017 failed with error -22

```

Any ideas?
Thanks!

---

### Post by GusBricker on 2014-08-03
Doh, im an idiot. Knew it was something dumb! I needed to change which kernel boots by default in grub.

---

### Post by GusBricker on 2014-08-04
> **alicia4542 said:**
> A newly updated Linux kernel for Surface Pro, version 3.13.0-30.54, tested and working on my Surface Pro 2 with Type Cover 2.

Please download here:
[http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz](http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz)

It was built using mostly generic kernel config using these same patches for the Surface Pro as the previous version:
[http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

Note that from now on, to save space, I will only keep the the last two kernel versions in my shared folder, which now includes just this 3.13.0-30.54 and the previous 3.13.0-29.53 kernels.  Older versions have been deleted.

I would appreciate knowing if it works on the power cover, since I don't have one.  If not, I will see if there is a patch for it, that I could apply to the kernel.

To Surface Pro 3 owners, whom I am very envious of, I would also appreciate knowing if this kernel works or not, and if there is any other patches I should add.

It would be best to have a single kernel patch for all Surface Pro versions and covers.
I've got your kernel working, seems pretty stable. The only problem I'm having is, the surface pro 2 never wakes correctly from sleep.
It just turns on, the fan spins up really fast, then it shuts down. Is this expected with your kernel?

---

### Post by goepfling on 2014-08-07
Did the patch make in Ubuntu stock kernel 3.13.0-32?

---

### Post by javispedro2 on 2014-08-15
Hello, I've extracted the "typing sounds" that Windows makes when typing  on the _Touch_ cover in the Surface Pro and used them to build a small  program that reproduces such typing feedback on Linux. 

Source is available on [https://gitorious.org/javispedro-desktop-misc/coveraudiod/](https://gitorious.org/javispedro-desktop-misc/coveraudiod/) To build it just "make" and "sudo make install", then run "coveraudiod". Keep installing -dev packages until it builds [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

It should automatically detect whether you have a touch or a type cover  plugged in and only enable the sounds when using a touch cover.  

License of the program is GPLv3 albeit license of the sound files is  more... complicated. I guess it should be OK to distribute between  Surface users (the sound files are part of the drivers).

---

### Post by PointSource on 2014-08-16
Hi all. Sorry for the long silence.

Recently released kernels have made progress towards making the Surface Pro 2 hardware more stable. I've compiled a kernel image from mainline, it is available here: [https://drive.google.com/open?id=0Bzl2mZ4p-k_DZF9QcFVEdjMtUnM](https://drive.google.com/open?id=0Bzl2mZ4p-k_DZF9QcFVEdjMtUnM)
Specifically:[LIST]
[*]a number of patches have been published for wifi (see [kernel bug 69661 - mwifiex_usb on MS Surface Pro 1 is unstable]("https://bugzilla.kernel.org/show_bug.cgi?id=69661")).
[*]Graphics are a little better (IMO), though the backlight still won't turn off at screensaver for me.
[*]keyboard re-plugging works better, as well as the sensor hub, see [https://bugzilla.kernel.org/show_bug.cgi?id=73321#c11](https://bugzilla.kernel.org/show_bug.cgi?id=73321#c11) (comment 12's patch has been included).
[*]I've tried to include power cover USB IDs according to [https://bbs.archlinux.org/viewtopic.php?pid=1405831#p1405831](https://bbs.archlinux.org/viewtopic.php?pid=1405831#p1405831)
[/LIST]
This is the bleeding-edge of versions, though, so Your Mileage May Vary. For example, an API change probably caused my DKMS virtualbox modules to fail to compile.

I've also stumbled across a set of programs at [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop) that can dynamically re-orient the screen based on accelerometer data, and change the backlight brightness according to ambient light. They were written for the Lenovo Ideapad Yoga, but work just as well on the SP2. You have to change the touchscreen device though: ```
$ sudo ./orientation --touchscreen="Atmel Atmel maXTouch Digitizer"
```

---

### Post by Jerry_Drake on 2014-08-19
Hi there,
Thanks for your efforts.
I have been trying to install the header & the linux image but the software center keeps me giving this warning that the packages are of bad quality and they can cause serious problems on the computer, so I should contact the provider of the package and let them know these details (ths is just for the linux image) : Lintian check results ...... linux-image-3.16.0-20140816+maybepowercover_3.16.0-20140816+maybepowercover-65_amd64.deb:
E: linux-image-3.16.0-20140816+maybepowercover: maintainer-address-malformed Anonymous <root@mnemeframe> 
Any help ?
Thanks

---

### Post by Yobibyte on 2014-08-20
I was frustrated by the lack of an actual .patch file here, so I have created one. It is attached. 
[Edit: lol, didn't realize it was already on comment 12 in patch form]

I've also compiled the most recent official kernel used by Ubuntu. 

The packages for it can be found [here]("https://mega.co.nz/#!ZckngYjJ!v0cs7ciqCjOF7fkCYit6gGUCYE7n5ZkII1bsJpkC6jM").

I recommend installing these using the following steps:
[LIST=1]
[*]Install gdebi, if you don't have it (installs package dependancies along with the packages)
[LIST]
[*]```
sudo apt-get install gdebi
``` 
[/LIST]
  
[*]Extract compressed archive:
[LIST]
[*]```
tar xzvf linux-3.13.0-34.trusty.surface2.tar.gz
``` 
[/LIST]
  
[*]Change into new directory:
[LIST]
[*]```
cd linux-3.13.0-34.trusty.surface2
``` 
[/LIST]
  
[*]Install packaged with gdebi:
[LIST]
[*]```
sudo gdebi linux*3.13.0-34*.deb
``` 
[/LIST]
    
[/LIST]

---

### Post by Jerry_Drake on 2014-08-27
I am not able to install those packages; I get these errors :
" This package is uninstallable
Dependency is not satisfiable: linux-cloud-tools-3.13.0-34 "
Any suggestions ?
Thanks

---

### Post by ROVguy on 2014-09-07
Any chance there is a newer version of the kernel? I recently purchased  the SurfPro 3 and want to spend more time learning Ubuntu 14.04LTS and all that  it has to offer but at the moment I need to connect a mouse and keyboard  through a USBhub which is annoying and defeats the purpose of the tablet. I  tried the updates currently posted but it had no effect on my system.

Greatly apreciate any help you guys can give.

---

### Post by goepfling on 2014-09-26
Since kernel 3.13.0-32 (early August 2014) I did not need a patched kernel for Wifi/bluetooth and TypeCover. I bet some patches made it in the kernel (in fact the USB port still appears as an USB 2.0; I hope they will soon fix the 3.0 issue because the 3.0 standard allows more current).

I safely went out for a week with only a Surface Pro2 and a Nokia N900 (nice thing navigating internet via bluetooth at more than 200 kbytes/sec while the train ran at some 140 mph). The only issue left with the TypeCover is the unplugging/replugging one.

After latest Ubuntu Linux kernel update (3.13.0-36-generic) external displayport monitor correctly goes in standby after a few minutes of inactivity of the "enter password" lock screen.

---

### Post by advent.children91 on 2014-10-05
> **goepfling said:**
> Since kernel 3.13.0-32 (early August 2014) I did not need a patched kernel for Wifi/bluetooth and TypeCover. I bet some patches made it in the kernel (in fact the USB port still appears as an USB 2.0; I hope they will soon fix the 3.0 issue because the 3.0 standard allows more current).

I safely went out for a week with only a Surface Pro2 and a Nokia N900 (nice thing navigating internet via bluetooth at more than 200 kbytes/sec while the train ran at some 140 mph). The only issue left with the TypeCover is the unplugging/replugging one.

After latest Ubuntu Linux kernel update (3.13.0-36-generic) external displayport monitor correctly goes in standby after a few minutes of inactivity of the "enter password" lock screen.

Are you saying your WIFI works out of the box with kernel 3.13.0-32? 
I have the same installed without any patch and it doesn't work, neither the Bluetooth.
Did you do something to make it work?

---

### Post by Yobibyte on 2014-10-10
I have compiled the latest kernel updates again. They are available for download [here]("https://mega.co.nz/#%21JF13XRYA%21lt1LqRMLCWTm53B9-CXNPqlytVwkcEhMXId2ypsIrU8").


I have included a working copy of the wifi firmware this time. 

I recommend installing these using the following steps:



[LIST=1]
[*]Extract compressed archive:
[LIST]
[*]```
tar xzvf linux-3.13.0-37.trusty.surface2.tar.gz
```
[/LIST]

[*]Change into new directory:
[LIST]
[*] ```
cd linux-3.13.0-37.trusty.surface2
```
[/LIST]

[*]Install wifi firmware. Network Access is required for gdebi to install dependancies.
[LIST]
[*]```
sudo cp Wifi\ Firmware/usb8797_uapsta.bin /lib/firmware/mrvl/
```
[/LIST]

[*]REBOOT
[*]Connect to Wifi
[*]Install gdebi, if you don't have it (installs package dependancies along with the packages)
[LIST]
[*]```
sudo apt-get install gdebi
```
[/LIST]

[*]Install packaged with gdebi:
[LIST]
[*]```
sudo gdebi linux*3.13.0-37*.deb
```
[/LIST]

[*]If you are having trouble  with your wifi adaptor not being detected after installing the new  kernel, reinstall the wifi firmware.
[/LIST]

---

### Post by mongr31 on 2014-10-21
I've got 14.04 installed on my SP1. I've updated to kernel version 3.17.1 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.1-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.1-utopic/) and most everything works. But I have a few problems...

[LIST]
[*]When I am brought the the login screen, if I accidentally hit the screen before I move the mouse, the Type Cover will stop working and I'll have to shut down and start back up again.
[*]I can use the buttons on the mouse, only tapping is allowed. It doesn't appear to show up as a trackpad but a regular mouse so I can't change scrolling direction. This also makes it hard to select text or drag/resize a window.
[*]The WiFi is spotty at best. I've downloaded the lastest drivers from Marvell's Github, but 9/10 when it goes to sleep the wireless won't come back up, and it'll just die over sometimes for the heck of it.
[/LIST]

Has anyone else come across these problems and knows what to do?

---

### Post by cheshirekow2 on 2014-10-24
Hi PointSource, 
Does that yoga-laptop orientation program actually work for you? The sensors don't seem to be working for me on my SP1. I've tried kernels 3.13 (latest 14.04 release), 3.14, and 3.17. Did you have to do anything special to get the accelerometer, gyro, ambient light, etc. sensors to enumerate?


> **PointSource said:**
> 
I've also stumbled across a set of programs at [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop) that can dynamically re-orient the screen based on accelerometer data, and change the backlight brightness according to ambient light. They were written for the Lenovo Ideapad Yoga, but work just as well on the SP2. You have to change the touchscreen device though: ```
$ sudo ./orientation --touchscreen="Atmel Atmel maXTouch Digitizer"
```

---

### Post by PointSource on 2014-10-27
> **cheshirekow2 said:**
> Hi PointSource, 
Does that yoga-laptop orientation program actually work for you? The sensors don't seem to be working for me on my SP1. I've tried kernels 3.13 (latest 14.04 release), 3.14, and 3.17. Did you have to do anything special to get the accelerometer, gyro, ambient light, etc. sensors to enumerate?

It could be one of two patches:
[LIST]
[*][http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=00478ee8984a80e531ed491eede0459eae07396d](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=00478ee8984a80e531ed491eede0459eae07396d)
[*]or this one:
```
--- a/drivers/hid/usbhid/hid-quirks.c
+++ b/drivers/hid/usbhid/hid-quirks.c
@@ -74,6 +74,9 @@ static const struct hid_blacklist {
 	{ USB_VENDOR_ID_FORMOSA, USB_DEVICE_ID_FORMOSA_IR_RECEIVER, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_FREESCALE, USB_DEVICE_ID_FREESCALE_MX28, HID_QUIRK_NOGET },
 	{ USB_VENDOR_ID_MGE, USB_DEVICE_ID_MGE_UPS, HID_QUIRK_NOGET },
+	{ USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_SURFACE_PRO_2, HID_QUIRK_NO_INIT_REPORTS },
+	{ USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_2, HID_QUIRK_NO_INIT_REPORTS },
+	{ USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TOUCH_COVER_2, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_MSI, USB_DEVICE_ID_MSI_GX680R_LED_PANEL, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_NEXIO, USB_DEVICE_ID_NEXIO_MULTITOUCH_PTI0750, HID_QUIRK_NO_INIT_REPORTS },
 	{ USB_VENDOR_ID_NOVATEK, USB_DEVICE_ID_NOVATEK_MOUSE, HID_QUIRK_NO_INIT_REPORTS },


```
[/LIST]
I think the first is already integrated into the 3.17 kernel, but IIRC the second just improves the keyboard's hotplug stabiility.

Hope this helps.

I've also found another program that links the IIO sensors into the orientation framework that GNOME already supports through udev:
[https://github.com/hadess/iio-sensor-proxy/](https://github.com/hadess/iio-sensor-proxy/)
I haven't tested it at all though.

---

### Post by dnquark on 2014-12-10
I just installed 14.10 with the 3.16.0-25 kernel, on Surface Pro 1 and I am seeing what others are reporting in this thread -- wifi dies after the device goes into suspend, also, sometimes wifi just dies in the course of normal operation (I got a traceback from dmesg when it did that).  It appears that when wifi goes, it's impossible to fix without a reboot -- unloading and reloading the kernel module doesn't do anything.  

Latest firmware from Marvell's github didn't fix the problem (in fact, it seems to have made it worse, I had a much more difficult time connecting to wifi).  If anyone knows workarounds for these issues, or how to get traction with Marvell's firmware devs in terms of fixing these problems, please speak up :)

---

### Post by Knightwise on 2015-02-15
Does this also work for the Surface pro 1 ? (14.04, latest kernell)

---

### Post by cnnr-dhrty on 2015-04-14
On my SP1 w/14.10, wifi problems go away when I disable bluetooth. However I have never gotten it to broadcast an ad-hoc or AP network, that doesn't seem to work.

---

### Post by kaierlong on 2015-08-06
I wonder if you keep the files below:linux-image-3.11.10.4_20140314_amd64.deb,linux-headers-3.11.10.4_20140314_amd64.deb.I can't get them from ubuntuone since it's already closed.can you mail them to me <snip> . That will be great thanks!

---

### Post by jeff-fire on 2015-11-16
Dual booting 15.10 on my Surface Pro 2, installed on a partition. Works a treat out of the box except that it locks up whenever I use the internet over wifi. If I use bluetooth for internet it works fine - crashes on firefox and downloading new software through application centre or in terminal. Connects to a network via wifi fine, freezes when I actaully try and use the connection for something.

Havent used Ubuntu for about 5 years - can't believe how close it is to working out of the box. I have tried to replace to wifi driver but i'm not sure I did it right as without being able to install gksu it was not simple for a rusty user like myself.

---

### Post by tlf30 on 2016-10-18
Has anyone got Ubuntu 16.10 working on SP2? 
I have not been able to get it to even boot...

~Trevor

---

### Post by Bucky Ball on 2016-10-18
> **tlf30 said:**
> Has anyone got Ubuntu 16.10 working on SP2? 
I have not been able to get it to even boot...

~Trevor

Not sure how much support you're expecting posting sixteen pages deep on a thread that was started three years ago, hasn't seen action for almost a year and is about a different release altogether.

You greatly improve your chances of support by starting new threads rather than tagging on to someone else's, especially when that thread is a year old dead one.

Good luck solving your issue with a new thread. Perhaps try installing then make your first post on the new thread about what problems you get and what you attempt to try and fix it. 

*Thread closed.*

---

