---
title: "Panasonic Y7 Hotkeys"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by plrsmith on 2007-07-15
I've just taken delivery of a panasonic Y7 laptop. I have installed Ubuntu Feisty and have managed to get most things working to my satisfaction, althiugh I had to use ndiswrapper to get the wireless to work.  However, try as I might, I cannot get the hotkeys to cahnge the screen brightness and the gnome applet says "cannot get laptop panel brightness".  I have tried the various fixes given for the Y5 without success.  Has anyone managed to do this on a Y5 yet?  Help would be most welcome.

---

### Post by who_me? on 2007-07-21
Sorry, I don't have an answer for you but a question instead.  Have you tested support for the external display? (I 'm looking to purchase a Y7 and installing linux but have seen a couple of reports that it doesn't work properly on the Y5).

---

### Post by bean1975 on 2007-07-24
Yes testing i810switch would be rather interesting.

---

### Post by idlewild on 2007-07-24
Panasonic support is broken. You'll need to download pcc-acpi and compile it. The scripts for hal are also broken so if you want to have gnome power manager control the brightness (rather than adjusting with the hotkeys) you'll have to modify the hal scripts.

---

### Post by firepulaski on 2008-01-17
I have a Y7 running gutsy and am unable to get the brightness working correctly.  I cannot change brightness from within linux.  I have the pcc_acpi module running, and the fn-f1 and fn-f2 keys do change the values stored in /proc/acpi/pci/dc_brightness or ac_brightness.  But there is no actual effect on the screen.  

These registers change when I press the keys, I can read them and see that.  But if I try to echo a value directly from the command line (sudo echo "1" > /proc/acpi/pcc/ac_brightness), I get "permission denied".

I have tried the gutsy package pcc-acpi, and I have compiled the driver from [http://www.da-cha.jp/letsnote](http://www.da-cha.jp/letsnote).  Neither works. I am using the hotkeys package from gutsy rather than the 0.6 version availabel at [http://www.da-cha.jp/letsnote](http://www.da-cha.jp/letsnote), but I don't think that is my problem (I can't compile the0.6 version from [http://www.da-cha.jp/letsnote](http://www.da-cha.jp/letsnote) becauseit depends upon lib3db-dev which is not in gutsy repositories.


The suspend and hibernate _keys_ work (although suspend does not work, or at least there is no resume) .  The mute and volume keys responnd but are not doing the right thing.  But that is no big deal.

---

### Post by firepulaski on 2008-01-17
Update:

pcc_acpi is still not working for me to control brightness.  I've compiled several different version of the pcc_acpi module, any that load correctly behave the same: no brightness control.

I can manually change the registers/files in /proc/acpi/pcc, I was not using su before and this works:

sudo su root -c "echo 1 > /proc/acpi/ac_brightness"

then cat ac_brightness returns 1. Still no effect on the physical screen, however.  Setting /proc/acpi/pcc/mute to 1 does stop the speakers, so something in the pcc driver is working.

I also had a directory /proc/acpi/video which had an entry for a screen and a brightness control that did work either.  By setting the register /proc/acpi/video/GFX0/DD02/brightness to 0, I could dramatically darken the screen, but any other value gave full brightness.  have blacklisted the video module to see if that was interfering with pcc_acpi, but no luck yet.

 I'll worry about hotkeys once I get the driver actually controlling brightness.

---

### Post by liddish on 2008-02-06
any news on this topic? struggeling with the same problem on the cf-r7

---

### Post by herme on 2008-02-15
Exact same problem on a (US) Y7 and Gutsy. The function keys do bring up the 
small brightness window with the slider and move the slider, but I get only two 
levels: maximum and very dark. Cat'ing to /proc/acpi/ac_brightness has no 
effect.

---

### Post by danosaka on 2008-07-15
HELP...I am having the same problem. I have installed Ubuntu 8.04 in my Japanese Panasonic CF-W4 and cannot adjust the brightness. The computer is unusable because of this. Can anyone help me? I am a beginner using Ubuntu.

I tried the

sudo modprobe pcc_acpi

But had the reply:

FATAL: Module pcc_acpi not found

What should I do? My lap top in unusable!

---

### Post by dimension6 on 2008-07-15
Has anyone had any success with these drivers, which appear to be built specifically for the W7/Y7? I'm using a Y7 now, and have no idea how to get the hotkeys working properly...

[http://wiki.myrix.net/doku.php?id=panasonic_y7_hotkeys]("http://wiki.myrix.net/doku.php?id=panasonic_y7_hotkeys")

---

### Post by Paradoxalley on 2008-07-15
In case no-one has answered you regarding the hotkeys driver for panasonic lets-note (I have a CF-Y4 but it should apply to all recent "Let's Note" and toughbook laptops).
assuming you have Ubuntu 8.04:
sudo apt-get install linux-headers (if you haven't done it already)
cd /usr/src
wget [http://www.da-cha.jp/files/pcc-acpi-0.9.tar.bz2](http://www.da-cha.jp/files/pcc-acpi-0.9.tar.bz2)
-tar -jxvf pcc-acpi-0.9.tar.bz2


now create a file on your desktop called patch with the following information in it (don't change spacing, punctuation, etc)

```
--- pcc_acpi.c	2006-11-21 02:38:41.000000000 -0500
+++ pcc_acpi.c.new	2008-07-15 18:44:33.000000000 -0400
@@ -168,7 +168,6 @@
 #define METHOD_HKEY_SQTY	"SQTY"
 #define METHOD_HKEY_SINF	"SINF"
 #define METHOD_HKEY_SSET	"SSET"
-#define HKEY_HID		"MAT0012,MAT0013,MAT0018,MAT0019"
 #define HKEY_NOTIFY		 0x80
 
 /* for brightness control */
@@ -212,13 +211,22 @@
 
 static int acpi_pcc_hotkey_add(struct acpi_device *device);
 static int acpi_pcc_hotkey_remove(struct acpi_device *device, int type);
-static int acpi_pcc_hotkey_resume(struct acpi_device *device, int state);
 
+static int acpi_pcc_hotkey_resume(struct acpi_device *device);
+
+static const struct acpi_device_id pcc_device_ids[] = {
+       {"MAT0012", 0},
+       {"MAT0013", 0},
+       {"MAT0018", 0},
+       {"MAT0019", 0},
+       {"", 0},
+       };
+MODULE_DEVICE_TABLE(acpi, pcc_device_ids);
 
 static struct acpi_driver acpi_pcc_driver = {
 	.name =		ACPI_PCC_DRIVER_NAME,
 	.class =	ACPI_PCC_CLASS,
-	.ids =		HKEY_HID,
+	.ids =		pcc_device_ids,
 	.ops =		{
 				.add =		acpi_pcc_hotkey_add,
 				.remove =	acpi_pcc_hotkey_remove,
@@ -622,7 +630,7 @@
 	case HKEY_NOTIFY:
 		if (acpi_pcc_hotkey_get_key(hotkey)) {
 			/* generate event like '"pcc HKEY 00000080 00000084"' when Fn+F4 pressed */
-			acpi_bus_generate_event(hotkey->device, event, hotkey->status);
+			acpi_bus_generate_proc_event(hotkey->device, event, hotkey->status);
 		}
 		acpi_pcc_generete_keyinput(hotkey);
 		break;
@@ -834,7 +842,7 @@
                          module init
    -------------------------------------------------------------------------- */
 
-static int acpi_pcc_hotkey_resume(struct acpi_device *device, int state)
+static int acpi_pcc_hotkey_resume(struct acpi_device *device)
 {
 	struct acpi_hotkey *hotkey = acpi_driver_data(device);
 	acpi_status	    status = AE_OK;

```

cd /usr/src/pcc-acpi-0.9/
cp $HOME/Desktop/patch ./
sudo patch -p0 <patch
make
sudo make install
modprobe pcc_acpi

that should get everything working, try your Fn+F2 and Fn+F1 to see if your brightness changes...
Best of luck
Seth

---

