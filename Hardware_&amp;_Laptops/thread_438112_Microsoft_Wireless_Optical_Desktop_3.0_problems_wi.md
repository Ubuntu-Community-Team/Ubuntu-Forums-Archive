---
title: "Microsoft Wireless Optical Desktop 3.0 problems with usbhid"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Kegetys on 2007-05-09
Hi,

For the last few days I have been trying to get the Microsoft Wireless Optical Desktop USB keyboard & mouse working in Ubuntu 7.04 without much success. When I use the default usbhid module the device disconnects and reconnects repeatedly all the time; the leds on the receiver blink, hald takes up 100% cpu time and this repeats over and over again in dmesg:


[ 3662.949884] usb 1-2.1: new low speed USB device using ohci_hcd and address 74
[ 3663.067877] usb 1-2.1: configuration #1 chosen from 1 choice
[ 3663.077900] input: Microsft Microsoft Wireless Optical Desktop? 2.10 as /class/input/input1398
[ 3663.077964] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop? 2.10] on usb-0000:00:02.0-2.1
[ 3663.102667] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.103662] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.104667] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.105659] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.106656] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.107660] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.108662] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.109652] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.109904] input: Microsft Microsoft Wireless Optical Desktop? 2.10 as /class/input/input1399
[ 3663.110017] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop? 2.10] on usb-0000:00:02.0-2.1
[ 3663.113688] usb 1-2.1: USB disconnect, address 74
[ 3663.433303] usb 1-2.1: new low speed USB device using ohci_hcd and address 75
[ 3663.551333] usb 1-2.1: configuration #1 chosen from 1 choice
[ 3663.561377] input: Microsft Microsoft Wireless Optical Desktop? 2.10 as /class/input/input1400
[ 3663.561455] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop? 2.10] on usb-0000:00:02.0-2.1
[ 3663.587082] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.588081] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.589080] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.590077] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.591076] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.592078] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.593074] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.594080] drivers/usb/input/hid-core.c: ctrl urb status -62 received
[ 3663.594332] input: Microsft Microsoft Wireless Optical Desktop? 2.10 as /class/input/input1401
[ 3663.594430] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop? 2.10] on usb-0000:00:02.0-2.1
[ 3663.598092] usb 1-2.1: USB disconnect, address 75


The only help I found by googling around was to remove the usbhid module and use usbkbd & usbmouse instead. This way the keyboard works, but the mouse doesn't. Also the extra "multimedia" keys on the keyboard do not work with usbkbd so using it is not an option... I have tried different BIOS settings for OS/BIOS kb/mouse support and different USB ports but nothing seems to help.

The device works fine when used in PS/2 port, in USB it also works in the BIOS but once Ubuntu loads the problem starts. I also tried it on a Windows XP system where it worked without problems. I need the ps2 port for another keyboard & mouse, so I'd need to get this device working in USB.

Any help on how to get usbhid working with this would be very much appreciated.

System specs:
AMD Athlon XP 1800+
MSI nForce2 motherboard
GeForce 4 Ti4200
Microsoft Wireless Optical Desktop 3.0 ([http://www.microsoft.com/hardware/oempartners/ProductDetails.aspx?pid=031](http://www.microsoft.com/hardware/oempartners/ProductDetails.aspx?pid=031))

---

### Post by Kegetys on 2007-05-10
Finally found a solution myself after some experimenting with the usbhid module source (I had no idea what I was doing ;). The device needed HID_QUIRK_NOGET for it in the kernel drivers/usb/input/usb-core.c hid_blacklist (Vendor id 0x045e, device id 0x009d). Both mouse and keyboard appear to work without problems now.

---

### Post by jake31789 on 2007-05-13
Kegetys, would you mind explaining in more detail what you did to get your keyboard and mouse to work? I have the same keyboard and mouse and I'm not sure how to fix the issue. It would be greatly appreciated. Thank you very much in advance, this is the only problem that is keeping me from using Ubuntu regularly on my desktop.

---

### Post by Him on 2007-11-06
I also suffer from this same problem and would love to have this fixed for my keyboard and mouse. Any further guidance would be appreciated.

---

### Post by mercurious on 2007-11-07
I have this same, problem, I think.  I can get the OS to boot, but I can't use the mouse, and when I type, it accepts input only in cycles.  I can type on several keys and it will get nothing, then, suddenly, it will render 3-4 keystrokes. 

Obviously, this is useless.  I managed to bring up gnome system monitor, and it says both my cpus are running at 30%, with nothing happening.

unfortunately, this is the only keyboard and mouse I have, and I really want to switch from Vista to this.

Thanks,
marc

---

### Post by zarvox on 2007-11-18
Indeed, this is a bug with the hardware.  It doesn't correctly report the mouse interface descriptor, so the kernel doesn't apply the mouse/keyboard workaround for the mouse (HID_QUIRK_NOGET).  I sumbitted a patch to the HID maintainer as well as Linus; we'll see if/when it gets committed.  If you're comfortable compiling your own kernel, try this patch:

```
diff --git a/drivers/hid/usbhid/hid-quirks.c b/drivers/hid/usbhid/hid-quirks.c
index a255285..d3bc7e1 100644
--- a/drivers/hid/usbhid/hid-quirks.c
+++ b/drivers/hid/usbhid/hid-quirks.c
@@ -296,6 +296,7 @@

 #define USB_VENDOR_ID_MICROSOFT                0x045e
 #define USB_DEVICE_ID_SIDEWINDER_GV    0x003b
+#define USB_DEVICE_ID_MICROSOFT_WIRELESS_OPTICAL_DESKTOP_3_0 0x009d

 #define USB_VENDOR_ID_NCR              0x0404
 #define USB_DEVICE_ID_NCR_FIRST                0x0300
@@ -532,6 +533,7 @@ static const struct hid_blacklist {
        { USB_VENDOR_ID_ATEN, USB_DEVICE_ID_ATEN_4PORTKVMC, HID_QUIRK_NOGET },
        { USB_VENDOR_ID_ELO, USB_DEVICE_ID_ELO_TS2700, HID_QUIRK_NOGET },
        { USB_VENDOR_ID_LOGITECH, USB_DEVICE_ID_LOGITECH_WHEEL, HID_QUIRK_NOGET },
+       { USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MICROSOFT_WIRELESS_OPTICAL_DESKTOP_3_0, HID_QUIRK_NOGET },
        { USB_VENDOR_ID_PETALYNX, USB_DEVICE_ID_PETALYNX_MAXTER_REMOTE, HID_QUIRK_NOGET },
        { USB_VENDOR_ID_SUN, USB_DEVICE_ID_RARITAN_KVM_DONGLE, HID_QUIRK_NOGET },
        { USB_VENDOR_ID_TURBOX, USB_DEVICE_ID_TURBOX_KEYBOARD, HID_QUIRK_NOGET },

```
The only module affected is usbhid.  If I some free time in the next week, I might make a modules package for it.  If not, hopefully Linus will commit the patch and it'll get in the next release/update.

---

### Post by xphelanx on 2007-12-30
I have to throw in my "Me too" on this one as well. I have the MS wireless optical desktop pro setup. Hoping there's an easy fix by now.

---

### Post by Golden Phoenix on 2008-01-14
Zarvox,

Your post on dealing with the Microsoft Wireless Desktop Receiver is the first post I've seen on this that addresses this issue the most completely.

Congrats!

I'm just wondering, did you ever go about making a module package?  I've personally mucked my way through a kernel or two in my day (I had to tweak Red Hat 3 like crazy a million years ago), but I think for some of the newer users, it may be more advantageous to work on a package to help meld that sucker in a little better.

I've got a couple of questions and comments:  From reading around many forums, it looks like there are at least four or five different versions of the receiver that have been released into the market.  I'm not sure, but with the different errors people are getting from the input devices, I think the issue may be in general that ALL versions may send out the wrong descriptor.  I'm wondering if each version sends out the same, though I think if you just "lsusb" each device, you may get a different product ID.  

Do you (or anybody else reading this thread) know of any thread on any forum or mailing list that addresses this issue?  

If not, maybe this should be discussed in other parts of the form or on Launchpad, where we could gather information and flesh out this patch to cover as much as possible.

---

### Post by xphelanx on 2008-01-15
I will do anything to help this issue along, here is the output from lsusb:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I have the MS Wireless Optical Desktop Pro that my sister got for me from Amazon:
[http://www.amazon.com/Microsoft-Wireless-Optical-Desktop-Pro/dp/B0000AOWVP/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1200407258&sr=8-1](http://www.amazon.com/Microsoft-Wireless-Optical-Desktop-Pro/dp/B0000AOWVP/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1200407258&sr=8-1)

I hope this helps out somehow, I'd really like to get this thing working.

Edit: Here is relevant output from dmesg:
[   35.826007] usb 2-2: configuration #1 chosen from 1 choice
[   35.829771] usbcore: registered new interface driver hiddev
[   35.840335] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /class/input/input2
[   35.840355] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:02.1-1
[   35.875047] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /class/input/input3
[   35.875182] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:02.1-1
[   35.885301] input: Microsoft Microsoft Wheel Mouse Optical® as /class/input/input4
[   35.885447] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:02.1-2
[   35.885464] usbcore: registered new interface driver usbhid
[   35.885468] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

---

### Post by zarvox on 2008-01-16
Good news: the patch for the Wireless Optical Desktop 3.0 got accepted into Linus's tree and will be a part of kernel 2.6.24.  Not sure if it'll get backported to Gutsy or not, but one can hope...

Golden Phoenix: I never did get around to building a modules package, partly because I'm not wildly familiar with apt, partly because of school, but mostly, because I simply forgot.  If you could point me toward a HOWTO or something on packaging this to make it easier for end-users, that'd be great.

xphelanx: can you post or send me the output of lsusb -vvv?  Glancing at your dmesg output, it looks like the devices get created correctly.  Describe the issue in a little more detail, if you can.  For instance, on the piece of hardware I had to work with, I was alerted to the rapid recreation of device nodes by the fact that the wireless receiver light kept flashing (along with a rapidly growing syslog).  Anything else out of place that you noticed?

---

### Post by xphelanx on 2008-01-17
Well, shoot. Suddenly everything works perfectly and I don't even know why. It could have been a recent update, but I have no idea. I am typing this from my recliner and I'm very happy.It would be nice if the multimedia keys would work, but that's probably for another thread...

Edit: I got my multimedia keys working with keyTouch:  [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/) (also available in repos)

---

### Post by Golden Phoenix on 2008-01-18
Congrats, zarvox.  

I think Release Candidate 8 got released for 2.6.24 a couple of days ago.  I wouldn't be surprised if it gets pushed out this weekend.  

As for making module packs, It's been forever and a day since I've even thought about doing one, but I know where some instructions are.  Feel free to look out for my posts, as I plan to pop up a couple of links on a seperate posts on where to get some hints.  I'm not sure if it'll be super-easy for the end-user, but I guess I can dust off my old tech writer skills and see what I can do, if all else fails.

xphelanx and others:  If you DO have your extraneous keyboard keys stop working (like sound control, email buttons, etc.) it's most likely because of this issue with the RF hub being unfriendly with usbhid.

---

### Post by TopherTheMighty on 2008-03-16
Hey all, this is my first foray into Linux, and so far it's gone well, getting past the initial humps of configuring sound and wireless card drivers.

However, now that I attempted to attach my keyboard/mouse set, I am having the same issue as Kegetys. The issue is almost identical; same model (Wireless Optical Desktop 2.10), same blinky light eating up resources, same dmesg output. The only difference is that I'm using 7.10 instead of 7.04. However, I am not exactly as Linux-savvy as I had hoped, and can't figure out exactly what he or she meant about the HID_QUIRK_NOGET device, or how to use zarvox's code.

If one of you two, or someone else, could help explain either how to install or work the HID driver, or the code snippet, I would appreciate it greatly. Thanks so much!

---

### Post by sodamnmad on 2008-04-02
> **zarvox said:**
> Good news: the patch for the Wireless Optical Desktop 3.0 got accepted into Linus's tree and will be a part of kernel 2.6.24.  Not sure if it'll get backported to Gutsy or not, but one can hope...
?

I'm not sure if I'm looking at it right, but here 2.6.24.4 didn't have that patch. I manually added the 2 lines to the file b/c I couldn't figure out how to use the patch :(. I'll post a followup to let you know if it worked for me.

:guitar:

---

### Post by Paulo Wageck on 2008-04-03
i have the wireless optical desktop 1.0a and it was corectly configured during setup.. but when i press alt-f2 to run a program, nothing happens.... this is really anoying.. how can i fix it?
thanks in advance.

---

