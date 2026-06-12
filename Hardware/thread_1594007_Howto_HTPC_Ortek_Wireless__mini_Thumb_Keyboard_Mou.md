---
title: "Howto: HTPC Ortek Wireless  mini Thumb Keyboard Mouse Combo PKB-1700"
date: 2010-10-11
forum: Hardware
---

### Post by asmoore82 on 2010-10-11
I bought this keyboard/mouse combo for my birthday: [http://www.ortek.com/prod_detail.asp?pid=131&cname=Keyboard%3E%3EWireless%20Keyboard%3E%3EPKB-1700&ppid=101&id=164](http://www.ortek.com/prod_detail.asp?pid=131&cname=Keyboard%3E%3EWireless%20Keyboard%3E%3EPKB-1700&ppid=101&id=164)

The mouse thumbstick and media hotkeys work out of the box but not the keyboard.
Googling I found this solution but it's in German: [http://forum.ubuntuusers.de/topic/generalkeys-tastatur-maus-kombi-px-2537-675-o/#post-2628472](http://forum.ubuntuusers.de/topic/generalkeys-tastatur-maus-kombi-px-2537-675-o/#post-2628472)

After translating, it looks like an easy fix whereby the existing
Ortek WKB2000 driver tweak from here: [http://patchwork.kernel.org/patch/74366/](http://patchwork.kernel.org/patch/74366/)
works perfectly with the PKB-1700. The kernel just doesn't know to load this driver module
for the different model and the module itself doesn't know to claim the model.

The German post uses an "either/or" approach that fixes the PKB1700 by breaking the WKB2000.
I've used this knowledge to add support for the PKB1700 without breaking the WKB2000 -
creating my first ever real Linux kernel patch!!

If you have this keyboard too, you can use this method: [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
to quickly compile just the hid modules with my patch and get your keyboard working.

I worked out these steps on Ubuntu Desktop 10.04 with kernel "2.6.32-25-generic"
Assuming you've downloaded the patch to your Desktop ...

```
[COLOR="Blue"]#get the kernel source[/COLOR]
sudo apt-get install linux-source

[COLOR="Blue"]#extract just the hid code[/COLOR]
tar jxvf /usr/src/linux-source-2.6.32.tar.bz2 linux-source-2.6.32/drivers/hid

[COLOR="Blue"]#change dir and apply the patch[/COLOR]
cd linux-source-2.6.32/drivers/hid
zcat ~/Desktop/pkb1700-usb-hid.patch.gz | patch

[COLOR="Blue"]#compile[/COLOR]
make -C /usr/src/linux-headers-$(uname -r) M=$(pwd) modules

[COLOR="Blue"]#copy to "install" the patched binary modules[/COLOR]
sudo cp -v hid.ko hid-ortek.ko /lib/modules/$(uname -r)/kernel/drivers/hid/
sudo cp -v usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/

[COLOR="Blue"]#remove/reinsert modules
# this is all together because the first step will disable HID keyboards/mice[/COLOR]
sudo rmmod usbhid hid; sudo depmod -a; sudo modprobe usbhid
```
^this last step may need adjustment if you have HID bluetooth devices.

[COLOR="Blue"]EDIT: If you are using an initial ramdisk (initrd) style of booting, which *buntu
typically does, you'll also have to update the hid modules inside the initrd...[/COLOR]
```
sudo update-initramfs -u
```
^this will make sure the new patched modules get loaded at boot time.

Remember you will have to re-do this procedure for future kernel upgrades!

---

### Post by asmoore82 on 2010-10-12
Oops! Here's the patch.
```
diff -rup ../oldhid/hid-core.c ./hid-core.c
--- ../oldhid/hid-core.c	2010-10-11 20:58:34.000000000 -0400
+++ ./hid-core.c	2010-10-11 21:00:23.000000000 -0400
@@ -1338,6 +1338,7 @@ static const struct hid_device_id hid_bl
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_WIRELESS_OPTICAL_DESKTOP_3_0) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MONTEREY, USB_DEVICE_ID_GENIUS_KB29E) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_NTRIG, USB_DEVICE_ID_NTRIG_TOUCH_SCREEN) },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_ORTEK, USB_DEVICE_ID_ORTEK_PKB1700) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ORTEK, USB_DEVICE_ID_ORTEK_WKB2000) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_PETALYNX, USB_DEVICE_ID_PETALYNX_MAXTER_REMOTE) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_QUANTA, USB_DEVICE_ID_QUANTA_OPTICAL_TOUCH) },
diff -rup ../oldhid/hid-ids.h ./hid-ids.h
--- ../oldhid/hid-ids.h	2010-10-11 20:58:34.000000000 -0400
+++ ./hid-ids.h	2010-10-11 21:00:04.000000000 -0400
@@ -366,6 +366,7 @@
 #define USB_DEVICE_ID_ONTRAK_ADU100	0x0064
 
 #define USB_VENDOR_ID_ORTEK		0x05a4
+#define USB_DEVICE_ID_ORTEK_PKB1700	0x1700
 #define USB_DEVICE_ID_ORTEK_WKB2000	0x2000
 
 #define USB_VENDOR_ID_PANJIT		0x134c
diff -rup ../oldhid/hid-ortek.c ./hid-ortek.c
--- ../oldhid/hid-ortek.c	2010-10-11 20:58:34.000000000 -0400
+++ ./hid-ortek.c	2010-10-11 21:01:03.000000000 -0400
@@ -30,6 +30,7 @@ static void ortek_report_fixup(struct hi
 }
 
 static const struct hid_device_id ortek_devices[] = {
+	{ HID_USB_DEVICE(USB_VENDOR_ID_ORTEK, USB_DEVICE_ID_ORTEK_PKB1700) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_ORTEK, USB_DEVICE_ID_ORTEK_WKB2000) },
 	{ }
 };
```

---

### Post by seymansey on 2010-10-27
Thanks for this!

This keyboard is also being sold in Maplins at the moment ([http://www.maplin.co.uk/Module.aspx?ModuleNo=399217](http://www.maplin.co.uk/Module.aspx?ModuleNo=399217)). Your patch didn't quite compile in 10.10, it complained of the addition of the line in hid-ortek.c - I added this manually though and the compile was fine.

---

### Post by Jose Catre-Vandis on 2010-10-27
Typing this from my PKB1700!!! :)

Thanks for the howto and for teaching me how you only compile modules and not the whole kernel.Much quicker and easier (unlike typing on this keypad :D )

Also you need to put a **sudo** in front of the **tar & make** commands ;)

oh, this worked for me on Xubuntu 10.04 - off to try it out on XBMC LIVE :)

EDIT: there doesn't seem to be a **hid.ko** file in XMBC Live - how can that be?

---

### Post by Eastender1970 on 2010-10-28
Thanks for this, it works almost perfectly in XBMC Live Dharma B3.
 
I say almost because on reboot the controller goes back to mouse function only.
 
I have discovered that if you re-enter the last line:
 
sudo rmmod usbhid hid; sudo depmod -a; sudo modprobe usbhid
 
....it works again.
 
Can anyone tell me (Linux Newbie) how to make this unloading and loading of usbhid permanant? I am running XBMC off a Hard Drive.
 
Thanks again for this patch, you have made my life so much easier!:P:P
 
Dan.

---

### Post by seymansey on 2010-10-28
I believe what is happening is that when you reboot, the kernel loads the usbhid driver which is already 'baked' into it. 

I think the solution here is to build a new kernel with the newer driver. It would be really good to get this patch submitted for inclusion into a newer kernel, but i'm pretty clueless on how to do that :)

---

### Post by Jose Catre-Vandis on 2010-10-28
> **Eastender1970 said:**
> Thanks for this, it works almost perfectly in XBMC Live Dharma B3.
 
I say almost because on reboot the controller goes back to mouse function only.
 
I have discovered that if you re-enter the last line:
 
sudo rmmod usbhid hid; sudo depmod -a; sudo modprobe usbhid
 
....it works again.
 
Can anyone tell me (Linux Newbie) how to make this unloading and loading of usbhid permanant? I am running XBMC off a Hard Drive.
 
Thanks again for this patch, you have made my life so much easier!:P:P
 
Dan.

If all the commands are required on each boot, then try putting them in your rc.local file.

---

### Post by Eastender1970 on 2010-10-29
> **Jose Catre-Vandis said:**
> If all the commands are required on each boot, then try putting them in your rc.local file.
 
Thanks Jose, that worked a treat.

---

### Post by Unmensch on 2010-10-31
Many thanks from me as well, worked great... although I had to take the instructions from the German site (link given) to change the files manually, probably as I'm running on Maverick. And I'm a complete noob at this.

---

### Post by Jose Catre-Vandis on 2010-10-31
If it helps anyone, here is the patch that was implemented on kernels prior to Lucid to get the Ortek WKB 2000 keyboard working. The OP's patch augments this one.

> 
diff -uprN linux-2.6.32.3.vanilla/drivers/hid/Kconfig linux-2.6.32.3/drivers/hid/Kconfig
--- linux-2.6.32.3.vanilla/drivers/hid/Kconfig	2010-01-11 20:09:17.876428259 +0000
+++ linux-2.6.32.3/drivers/hid/Kconfig	2010-01-11 21:16:24.529052956 +0000
@@ -204,6 +204,13 @@ config HID_NTRIG
 	---help---
 	Support for N-Trig touch screen.
 
+config HID_ORTEK
+	tristate "Ortek" if EMBEDDED
+	depends on USB_HID
+	default !EMBEDDED
+	---help---
+	Support for Ortek WKB-2000 wireless keyboard + mouse trackpad.
+
 config HID_PANTHERLORD
 	tristate "Pantherlord support" if EMBEDDED
 	depends on USB_HID
diff -uprN linux-2.6.32.3.vanilla/drivers/hid/Makefile linux-2.6.32.3/drivers/hid/Makefile
--- linux-2.6.32.3.vanilla/drivers/hid/Makefile	2010-01-11 20:09:17.877427529 +0000
+++ linux-2.6.32.3/drivers/hid/Makefile	2010-01-11 21:14:29.281429408 +0000
@@ -34,6 +34,7 @@ obj-$(CONFIG_HID_LOGITECH)	+= hid-logite
 obj-$(CONFIG_HID_MICROSOFT)	+= hid-microsoft.o
 obj-$(CONFIG_HID_MONTEREY)	+= hid-monterey.o
 obj-$(CONFIG_HID_NTRIG)		+= hid-ntrig.o
+obj-$(CONFIG_HID_ORTEK)		+= hid-ortek.o
 obj-$(CONFIG_HID_PANTHERLORD)	+= hid-pl.o
 obj-$(CONFIG_HID_PETALYNX)	+= hid-petalynx.o
 obj-$(CONFIG_HID_SAMSUNG)	+= hid-samsung.o
diff -uprN linux-2.6.32.3.vanilla/drivers/hid/hid-core.c linux-2.6.32.3/drivers/hid/hid-core.c
--- linux-2.6.32.3.vanilla/drivers/hid/hid-core.c	2010-01-11 20:09:17.872426973 +0000
+++ linux-2.6.32.3/drivers/hid/hid-core.c	2010-01-11 21:56:44.505053026 +0000
@@ -1333,6 +1333,7 @@ static const struct hid_device_id hid_bl
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_WIRELESS_OPTICAL_DESKTOP_3_0) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MONTEREY, USB_DEVICE_ID_GENIUS_KB29E) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_NTRIG, USB_DEVICE_ID_NTRIG_TOUCH_SCREEN) },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_ORTEK, USB_DEVICE_ID_ORTEK_WKB2000) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_PETALYNX, USB_DEVICE_ID_PETALYNX_MAXTER_REMOTE) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_SAMSUNG, USB_DEVICE_ID_SAMSUNG_IR_REMOTE) },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_SONY, USB_DEVICE_ID_SONY_PS3_CONTROLLER) },
diff -uprN linux-2.6.32.3.vanilla/drivers/hid/hid-ids.h linux-2.6.32.3/drivers/hid/hid-ids.h
--- linux-2.6.32.3.vanilla/drivers/hid/hid-ids.h	2010-01-11 20:09:17.880426925 +0000
+++ linux-2.6.32.3/drivers/hid/hid-ids.h	2010-01-11 20:20:01.931428309 +0000
@@ -352,6 +352,9 @@
 #define USB_VENDOR_ID_ONTRAK		0x0a07
 #define USB_DEVICE_ID_ONTRAK_ADU100	0x0064
 
+#define USB_VENDOR_ID_ORTEK		0x05a4
+#define USB_DEVICE_ID_ORTEK_WKB2000	0x2000
+
 #define USB_VENDOR_ID_PANJIT		0x134c
 
 #define USB_VENDOR_ID_PANTHERLORD	0x0810
diff -uprN linux-2.6.32.3.vanilla/drivers/hid/hid-ortek.c linux-2.6.32.3/drivers/hid/hid-ortek.c
--- linux-2.6.32.3.vanilla/drivers/hid/hid-ortek.c	1970-01-01 01:00:00.000000000 +0100
+++ linux-2.6.32.3/drivers/hid/hid-ortek.c	2010-01-12 18:37:32.203180509 +0000
@@ -0,0 +1,56 @@
+/*
+ *  HID driver for Ortek WKB-2000 (wireless keyboard + mouse trackpad).
+ *  Fixes LogicalMaximum error in USB report description, see
+ *  [http://bugzilla.kernel.org/show_bug.cgi?id=14787](http://bugzilla.kernel.org/show_bug.cgi?id=14787)
+ *
+ *  Copyright (c) 2010 Johnathon Harris <jmharris@gmail.com>
+ */
+
+/*
+ * This program is free software; you can redistribute it and/or modify it
+ * under the terms of the GNU General Public License as published by the Free
+ * Software Foundation; either version 2 of the License, or (at your option)
+ * any later version.
+ */
+
+#include <linux/device.h>
+#include <linux/hid.h>
+#include <linux/module.h>
+
+#include "hid-ids.h"
+
+static void ortek_report_fixup(struct hid_device *hdev, __u8 *rdesc,
+		unsigned int rsize)
+{
+	if (rsize >= 56 && rdesc[54] == 0x25 && rdesc[55] == 0x01) {
+		dev_info(&hdev->dev, "Fixing up Ortek WKB-2000 "
+				"report descriptor.\n");
+		rdesc[55] = 0x92;
+	}
+}
+
+static const struct hid_device_id ortek_devices[] = {
+	{ HID_USB_DEVICE(USB_VENDOR_ID_ORTEK, USB_DEVICE_ID_ORTEK_WKB2000) },
+	{ }
+};
+MODULE_DEVICE_TABLE(hid, ortek_devices);
+
+static struct hid_driver ortek_driver = {
+	.name = "ortek",
+	.id_table = ortek_devices,
+	.report_fixup = ortek_report_fixup
+};
+
+static int __init ortek_init(void)
+{
+	return hid_register_driver(&ortek_driver);
+}
+
+static void __exit ortek_exit(void)
+{
+	hid_unregister_driver(&ortek_driver);
+}
+
+module_init(ortek_init);
+module_exit(ortek_exit);
+MODULE_LICENSE("GPL");


---

### Post by asmoore82 on 2010-10-31
I haven't tested yet to be 100% sure, but I would say that the reboot problem
is caused by not having the patched modules slipped into the initial ramdisk (initrd).

I've edited this into the end of the procedure.

---

### Post by Jose Catre-Vandis on 2010-11-03
Just to confirm that the update to the initrd file works for me

---

### Post by sebw on 2010-11-23
I confirm the patch works with the Twintech TT-WKB-145F ([http://claviers.franceprix.fr/compare/twintech-tt-wkb145f](http://claviers.franceprix.fr/compare/twintech-tt-wkb145f)), which is actually an Ortek PKB-1700 sold under another brand.

Will someone submit the patch upstream ?

---

### Post by sapg on 2010-11-29
This worked for me, thanks.

---

### Post by chrish50 on 2010-12-09
Also need sudo before patch in zcat statement. So:-

zcat ~/Desktop/pkb1700-usb-hid.patch.gz | patch should read 
zcat ~/Desktop/pkb1700-usb-hid.patch.gz | sudo patch ;)

Worked a treat, thanks.

---

### Post by shaunconn on 2010-12-11
Hi

This worked, but after a reboot it never seems to work again!?  I have rerun the command:

sudo rmmod usbhid hid; sudo depmod -a; sudo modprobe usbhid

but ubuntu still just sees the unit as a mouse not a keyboard.  Below is the commands I use:

sudo apt-get install linux-source
sudo tar jxvf /usr/src/linux-source-2.6.35.tar.bz2 linux-source-2.6.35/drivers/hid
cd linux-source-2.6.35/drivers/hid
sudo zcat ~/Desktop/pkb1700-usb-hid.patch.gz | sudo patch
sudo make -C /usr/src/linux-headers-$(uname -r) M=$(pwd) modules
sudo cp -v hid.ko hid-ortek.ko /lib/modules/$(uname -r)/kernel/drivers/hid/
sudo cp -v usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/
sudo rmmod usbhid hid; sudo depmod -a; sudo modprobe usbhid
sudo update-initramfs -u

Am I missing something?

TIA
Shaun

---

### Post by phantom_ on 2010-12-25
excellent tutorial, thank you!

now my PKB-1700 is fully running.

i am using xbindkeys and some other utilities for further customization of X usage with the keyboard. please note the below;

default cfg. file: **~/.xbindkeysrc**
to list keys bindings: **xbindkeys_show**
to discover keyboard & mouse codes: **xev** and **xbindkeys -k**
to send keyboard presses and mouse clicks: **xte**

---

### Post by JoseDeSousa on 2011-01-09
Hi there, managed to get this to work on XBMCFreak livecd 10, yet I'm now having the same issue as shaunconn. This guide worked like a treat on my machine, and with a little prodding it managed to work after a reboot. 

Yet it has now stopped working at all even if I go through the whole process again it fails. Has anybody got any ideas?

---

### Post by dadoef on 2011-01-11
You just made me love North Carolina a little more... Thanks loads!

---

### Post by mnrbig on 2011-01-18
Does anyone know if this can be submitted for inclusion into the kernel?

---

### Post by asmoore82 on 2011-01-30
> **shaunconn said:**
> Hi
This worked, but after a reboot it never seems to work again!?

The whole process has to be re-done after kernel updates.

@All-
All of the extra sudo's are definitely not necessary.
If you take care to extract the code and compile it purely from within
your own home folder, you only need sudo to install the modules.

That having been said, keeping the sudo's and doing this minor change as root
in the system folders isn't the end of the world. But handle with care.
[quote=Linus Torvalds]To do the actual install you have to be root, but none of the normal
build should require that. Don't take the name of root in vain.[/quote]

:biggrin: Upstream sounds good to me!

---

### Post by miodraggolubovic on 2011-02-14
can you tell me what did you inserted into the original patch, so it will install  on 10.10. I'm a Ubuntu noob so please leave a detailed reply 
Thanks

---

### Post by pelle.k on 2011-03-04
I modified the patch slightly, so it applies cleanly on 2.6.35 (maverick sources). Also, i updated the kernel version used in the OPs script.
**The new patch is attached to this post, and need to be downloaded (to /home/Downloads) before you run the following**.

```
sudo apt-get install linux-source build-essential
tar jxvf /usr/src/linux-source-2.6.35.tar.bz2 linux-source-2.6.35/drivers/hid
cd linux-source-2.6.35/drivers/hid
# ATTENTION -> assumes patch in "Downloads" directory...
zcat ~/Downloads/ortek-2.6.35.patch.gz | patch
make -C /usr/src/linux-headers-$(uname -r) M=$(pwd) modules
sudo cp -v hid.ko hid-ortek.ko /lib/modules/$(uname -r)/kernel/drivers/hid/
sudo cp -v usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/
sudo rmmod usbhid hid; sudo depmod -a; sudo modprobe usbhid
```

You may remove the linux-source-2.6.35 folder from your home folder when you're finished.
**As previously pointed out, you have to rerun this procedure after a kernel update**.

Have fun! :D

**EDIT:** Remember to *sudo update-initramfs -u* when you're done...

---

### Post by magwe on 2011-03-19
merged to linux-next:

[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=commit;h=270fdc0748bd3f7b625caff985f2fcf8e2185ec7](http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=commit;h=270fdc0748bd3f7b625caff985f2fcf8e2185ec7)

---

### Post by djyoung4 on 2011-03-22
confirmed working with the [SMK-Link Ultra-Mini Keyboard.]("http://www.smklink.com/vp6360.html")  Currently typing on it now.  Thanks asmoore82

---

### Post by tej1984 on 2011-05-27
HEllo - i JUST tryed this with a palm style wireless keyboard

[http://claviers.franceprix.fr/compare/twintech-tt-wkb145f](http://claviers.franceprix.fr/compare/twintech-tt-wkb145f) 

and it has picked up the mouse but the keyboard does not work please help!!! 

Thanks

---

### Post by bouncingwilf on 2011-06-22
I've just plugged this device into a box running Lucid 2.6.32.32 and keyboard and mousepad seems to work "out of the box" (except gestures etc) so presumably the kernel has now been patched. 

Now I seem to vaguely remember how to re-map keys under the old tty Unix system (long long time ago.....) but I wondered if there was anybody out there who could point me in the right direction to re-map the touchpad keys to something useful (to me)

Bouncingwilf.

---

### Post by Olaba on 2011-10-26
Hello:
Do you think this keyboard migth be work in Ubuntu 9.04?

Thabk you in advance

---

