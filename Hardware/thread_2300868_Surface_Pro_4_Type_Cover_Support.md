---
title: "Surface Pro 4 Type Cover Support"
date: 2015-10-29
forum: Hardware
---

### Post by savage_moogle on 2015-10-29
Hey guys,

I've been dual-booting Ubuntu 15.04 on my Surface Pro 3 for the past 3-4 months or so and things were working swimmingly.  It pretty much worked out of the box except I had to add support for the TypeCover by adding 

[COLOR=#000000][FONT=inherit]Section "InputClass"  
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07dc"
        Option "IgnoreAbsoluteAxes" "True"
EndSection[/FONT][/COLOR]
to the file [COLOR=#666666][FONT=Courier 10 Pitch]/usr/share/X11/xorg.conf.d/10-evdev.conf[/FONT][/COLOR]
That worked perfectly and I was able to use the keyboard and touch pad without any problems (no multi-touch but no big deal).

I got the new Surface Pro 4 Type Cover and the keyboard is awesome but it doesn't work in Ubuntu 15.10 (recently upgraded).

Does anybody know if there's a similar line of code I can add to that file to support the Surface Pro 4 TypeCover?  Or is it not baked into Ubuntu 15.10 yet?

Any help would be awesome for those out there who use a Surface Pro 3 =)

Thanks!

---

### Post by Ken_Rimple on 2015-10-29
Not 100% sure about what your device ID is - mine is the one with the palm reader.  You can attach the keyboard (while having a regular usb one attached and mouse with a usb hub). Then do a 'dmesg' and write down the numbers of the unrecognized device - it should be 045e:07xx (mine is 07e4).

Here is my cover. Try it and see if it helps. You can add it alongside the surface pro 3 cover in 10-evdev.conf

```

Section "InputClass"
     Identifier "Surface Pro 4 cover"
     MatchIsPointer "on"
     MatchDevicePath "/dev/input/event*"
     Driver "evdev"
     Option "vendor" "045e"
     Option "product" "07e4"
     Option "IgnoreAbsoluteAxes" "True"
 EndSection




```

So that SHOULD make the pointer work.

The kernel is another story.  I had to patch mine to recognize the keyboard. It took me two days to hack it through, but I did figure it out in the end.

The patch file is below so you  can see what I did, but I did this to rc7 of Kernel 4.3.0 after following the initial patch  from [https://github.com/neoreeps/surface-pro-3](https://github.com/neoreeps/surface-pro-3) (I used the patch for 4.2.0 kernel against the 4.3.0-rc7 source. Living on the edge).  

```


diff --git a/drivers/hid/hid-core.c b/drivers/hid/hid-core.c
index 70a11ac..3a801a9 100644
--- a/drivers/hid/hid-core.c
+++ b/drivers/hid/hid-core.c
@@ -725,6 +725,7 @@ static void hid_scan_collection(struct hid_parser *parser, unsigned type)
 
 	if (hid->vendor == USB_VENDOR_ID_MICROSOFT &&
 	    (hid->product == USB_DEVICE_ID_MS_TYPE_COVER_PRO_3 ||
+	     hid->product == USB_DEVICE_ID_MS_TYPE_COVER_PRO_4 ||
 	     hid->product == USB_DEVICE_ID_MS_TYPE_COVER_PRO_3_JP ||
 	     hid->product == USB_DEVICE_ID_MS_TYPE_COVER_3 ||
 	     hid->product == USB_DEVICE_ID_MS_POWER_COVER) &&
@@ -1928,6 +1929,7 @@ static const struct hid_device_id hid_have_special_driver[] = {
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_WIRELESS_OPTICAL_DESKTOP_3_0) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_OFFICE_KB) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_PRO_3) },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_PRO_4) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_PRO_3_JP) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_3) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_POWER_COVER) },
diff --git a/drivers/hid/hid-ids.h b/drivers/hid/hid-ids.h
index f769208..60b6b33 100644
--- a/drivers/hid/hid-ids.h
+++ b/drivers/hid/hid-ids.h
@@ -679,6 +679,7 @@
 #define USB_DEVICE_ID_MS_TOUCH_COVER_2   0x07a7
 #define USB_DEVICE_ID_MS_TYPE_COVER_2    0x07a9
 #define USB_DEVICE_ID_MS_TYPE_COVER_PRO_3    0x07dc
+#define USB_DEVICE_ID_MS_TYPE_COVER_PRO_4    0x07e4
 #define USB_DEVICE_ID_MS_TYPE_COVER_PRO_3_JP 0x07dd
 #define USB_DEVICE_ID_MS_TYPE_COVER_3    0x07de
 #define USB_DEVICE_ID_MS_POWER_COVER     0x07da
diff --git a/drivers/hid/hid-microsoft.c b/drivers/hid/hid-microsoft.c
index 9aa3515..de2a1c9 100644
--- a/drivers/hid/hid-microsoft.c
+++ b/drivers/hid/hid-microsoft.c
@@ -278,6 +278,8 @@ static const struct hid_device_id ms_devices[] = {
 		.driver_data = MS_DUPLICATE_USAGES },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_PRO_3),
 		.driver_data = MS_HIDINPUT },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_PRO_4),
+		.driver_data = MS_HIDINPUT },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_PRO_3_JP),
 		.driver_data = MS_HIDINPUT },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_3),


```

---

### Post by savage_moogle on 2015-10-29
Thanks for the help!  I tried the above first half (didn't change the kernel) but still didn't work.

I typed dmesg and ended up with: 

[   33.544348] usb 1-3: reset full-speed USB device number 13 using xhci_hcd
[   48.861599] usb 1-3: USB disconnect, device number 13
[   51.036848] usb 1-3: new full-speed USB device number 14 using xhci_hcd
[   51.166145] usb 1-3: New USB device found, idVendor=045e, idProduct=07e8
[   51.166149] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   51.166152] usb 1-3: Product: Surface Type Cover
[   51.166153] usb 1-3: Manufacturer: Microsoft

I subsequently changed the product to 07e8 and saved the 10-evdev.conf file.  When I restarted, however, neither the pointer nor the keyboard worked.  I tried the "IDentifier" both as Surface Pro 4 cover (as in your example) and "Surface Type Cover" (as in the dmesg), however, neither worked.  I attached my old Surface Pro 3 Type Cover and that worked without any problems.  

Do I have to update the kernel to get it to work?  What will updating the kernel do?  Or is it just that the current kernel I have doesn't work with the newer type cover?

Thanks!

---

### Post by Ken_Rimple on 2015-10-29
Yes, the Kernel has to recognize the device as a hid device I believe.

That's what the patches do, they add the various type cover devices to the kernel so that when they are attached the OS knows that they are keyboards and mice. That plus the trackpad settings in 10-evdev.conf will give you the support you need.

I would NOT suggest building your own Kernel if you don't have the experience unless you're OK risking not booting, having trouble with the settings, etc.  It's a hobbyist's thing.  I built a kernel to support my keyboard but it's not working quite well enough yet. 


One short-term suggestion - you could go for the microsoft remote keyboard battery pack that hooks onto the surface keyboard device, and then connect it as a standard bluetooth keyboard. That might work for now. The downside is that the battery doesn't last all day.So, your mileage may vary.

I would watch the github project that you were referred to earlier - the person there posts a few built kernels on google drive.  BUT, be careful applying new kernels to your machine. I would hope by next year sometime the drivers for these keyboards will be merged into the core of the standard Ubuntu kernel. Then we don't have to play this game, just get the standard OS updates which include the kernels with the drivers in them.

Ken

---

### Post by savage_moogle on 2015-10-29
Ah, I see.  I thought about building my own kernel but I'm going to take your advice and not do it.  I have too much important lab work on my Ubuntu partition that I would be very sad about if I lost and I am not at all comfortable with building a kernel.

The better part of valor is just to tote around my old Surface Pro 3 Type Cover and pull it out whenever I need to use Ubuntu and my SP3 is not plugged into an external keyboard.

Please update me if there any updates (reply to this thread) that support the SP4 Type Cover without complex jiggery!  Hopefully support for it will be included into updates in the next kernel!

Thanks again!

---

### Post by wothed2 on 2016-02-09
Xenial Xerus has the 4.4 kernel now but I couldn't get it working on first attempt.
[http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso)

I knoticed [pendrivelinux]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.9.6.3.exe") Has a persistant storage option maybe I will try that so I can restart the live session.
How do I apply what is put in /usr/share/X11/xorg.conf.d/10-evdev.conf without restarting the live cd?

I thought I read that 4.4 was now able to detect the typecover but I don't know if this included the pro 4 (mine).

---

### Post by gmalone on 2016-08-30
Good discussion on need for Surface Pro 4 drivers/capabilities re: Type cover.  Yeah, though I am comfortable with lots of things, rebuilding the kernel is a whole 'nother kettle of fish, mostly due to time involved and complexity leading to issues.  Hoping for 'native' support in Unbuntu for Surface Pro 4.

---

