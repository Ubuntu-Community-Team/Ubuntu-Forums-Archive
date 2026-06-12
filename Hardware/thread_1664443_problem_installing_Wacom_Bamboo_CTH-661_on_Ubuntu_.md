---
title: "problem installing Wacom Bamboo CTH-661 on Ubuntu 10.10"
date: 2011-01-11
forum: Hardware
---

### Post by LexRiver on 2011-01-11
I'm trying to install my new tablet Wacom Bamboo Pen&Touch M (CTH-661) on Ubuntu 10.10, but I have no luck for a few days.

I was trying to compile from source from [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

and using wacom-dkms, and linux-backports-modules-input and some other options.

Please tell me exact steps. What should I uninstall and what should I install to get the tablet work.

Here is my parameters
$ uname -r
2.6.35-24-generic-pae

--

$ lsusb | grep -i wacom
Bus 002 Device 003: ID 056a:00d8 Wacom Co., Ltd 

--

$ udevadm info --export-db
...
...
...

P: /devices/pci0000:00/0000:00:02.0/usb2/2-4
N: bus/usb/002/003
S: char/189:130
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/usb2/2-4
E: SUBSYSTEM=usb
E: DEVNAME=bus/usb/002/003
E: ID_VENDOR=Wacom_Co._Ltd.
E: ID_VENDOR_ENC=Wacom\x20Co.\x2cLtd.
E: ID_VENDOR_ID=056a
E: ID_MODEL=CTH-661
E: ID_MODEL_ENC=CTH-661
E: ID_MODEL_ID=00d8
E: ID_REVISION=0111
E: ID_SERIAL=Wacom_Co._Ltd._CTH-661
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:030000:
E: MAJOR=189
E: MINOR=130
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=56a/d8/111
E: TYPE=0/0/0
E: BUSNUM=002
E: DEVNUM=003
E: DEVLINKS=/dev/char/189:130

...
...
...

---

### Post by Favux on 2011-01-11
Hi LexRiver,

You have one of the new models, the 00d8.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  The model box near the top shows the new models and tells you to go to the mini HOW TO in post #2 for adding the new models.  The HOW TO has the general instructions.

You'll need to uninstall at least the wacom.ko you've set up in dkms.  You basically just want to start with the default xserver-xorg-input-wacom and wacom.ko.

---

### Post by LexRiver on 2011-01-11
Thank you for your reply, Favux.

I've already xserver-xorg-input wacom,
then I've uninstalled wacom-dkms,
then I've added
--
static struct wacom_features wacom_features_0xD8 =
	{ "Wacom Bamboo Comic 2FG", WACOM_PKGLEN_BBFUN,   21648, 13530, 1023, 63, BAMBOO_PT };
--

and 
--
	{ USB_DEVICE_WACOM(0xD8) },
--

to my wacom_wac.c,
then build,
then copy wacom.ko to /lib/modules/...../drivers/input/wacom.ko,
then sudo depmod -a,
then reboot...

nothing works

then lsmod | grep wacom

nothing shows,
then I've added "wacom" to /etc/modules/

then lsmod | grep wacom 
shows "wacom 28370 0"

tablet is still not working,
then I've installed xf86-input-wacom from git,
then restart,
then nothing works again...

..

Should the tablet work now? Or what should be my next steps?

..
My 50-wacom.conf:
```

Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection


```

---

### Post by LexRiver on 2011-01-11
And I have no "/dev/input/wacom"
changing xorg.conf has no success.

---

### Post by Favux on 2011-01-11
Hi LexRiver,

Should be working now.

My guess is you have the wrong wacom.ko at /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko or there are multiple versions.  Look around in the kernel directory and make sure there is only one copy of wacom.ko and that it has the same date as the one you compiled (at src/2.6.30/wacom.ko) in the xf86-input-wacom folder.  Also check in Troubleshooting and make sure you have the correct kernel headers and do not need the 64-bit flag.

---

### Post by LexRiver on 2011-01-11
The problem was that I should uninstall all my linux-backports-modules-*

---

### Post by Favux on 2011-01-11
Hold on.  I'm getting a 0xd8 who's reporting no stylus but erratic touch on the Bamboo P&T thread.  Do you have any touch?

xf86-input-wacom is broken for touch right now for the rest of us.  They know that and Chris just submitted some patches to fix it.  I'm wondering if they also managed to break the stylus for the 0xd8 with all the new code.

---

### Post by LexRiver on 2011-01-11
pen works, buttons works, touch is strange, I'm trying to setup it.

---

### Post by Favux on 2011-01-11
Good.  Then it's just the known touch bugs.  Hopefully fixed in a few days.  Did you do anything more to get the stylus and stylus buttons working?  Or did I misunderstand your last post?

The other 0xd8 must have an unrelated problem.

---

### Post by LexRiver on 2011-01-12
No, nothing else. I think wacom.ko is working.
So stylus, stylus buttons, tablet buttons are working. And I turned off the touch via xsetwacom for now.

Where can I track this bug about the touch?

And is it possible to set up gestures then?

---

### Post by Favux on 2011-01-12
Not until 2 FG touch works.  There's a bunch of recent posts/patches submitted on linuxwacom-devel.

---

### Post by seriyPS on 2011-01-14
Favux: my 0xd8, with manually patched linuxwacom-0.8.8-10 wacom.ko by instruction in [http://ubuntuforums.org/showpost.php?p=9496756&postcount=2](http://ubuntuforums.org/showpost.php?p=9496756&postcount=2), has problem with pen too. Touch work normal.

Also, my 0xd8 don't detects by "Wacom Control Panel" [http://gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309](http://gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309)

---

### Post by Favux on 2011-01-15
Hi seriyPS,

Are you still using the default Maverick xf86-input-wacom 0.10.8?  That doesn't have your model in it.  You need to clone the git repository and get 0.10.10+ or use the 0.10.10+ snapshot after the final commit for your model and hopefully before they broke touch:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=snapshot;h=d678efb371ead5421031e32e590ef6f796e664a4;sf=tgz](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=snapshot;h=d678efb371ead5421031e32e590ef6f796e664a4;sf=tgz)

Then we can look at the Control Panel if things are working.  I need to check that app. out.

---

### Post by bloodniece on 2011-01-19
How did you toggle the touch off and pen only?

---

### Post by Favux on 2011-01-19
Hi everyone, touch is working again.  Go ahead and reclone the git repository (part II.) on the [Bamboo HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") if you had cloned one of the broken versions.  And check out my last post on the thread on using xinput commands to further refine your touch experience.  Haven't added that to the HOW TO yet.


Hi bloodniece,

Several ways you can do it.  You can use the touch-toggle script in the HOW TO, part V. or use the xsetwacom commands in the script.  Or for "permanent" disable add an option to the usb snippet in the wacom.conf.

---

### Post by LexRiver on 2011-01-20
I've updated to new version.
My touch is working but very ugly. It's lagging when moving and it clicks and holds left click pressed about an every second. Is it a bug, or should I adjust my settings?
I was trying "xinput set-prop ...". It works, but the buggy movement is still exists.

---

### Post by Favux on 2011-01-20
Hi LexRiver,

> My touch is working but very ugly. It's lagging when moving and it clicks and holds left click pressed about an every second. Is it a bug, or should I adjust my settings?
I was trying "xinput set-prop ...". It works, but the buggy movement is still exists. 
Not sure.  I'm not seeing that.  Which wacom.ko are you using?  The one from linuxwacom 0.8.8-10?  Which model (product ID) do you have?

---

### Post by mmpsych on 2011-03-08
Hello ... I'm trying to get a new CTH-661/S(A) to work, but it doesn't work at all.

I'm using 9.10, not 10.10, so I followed in detail the Karmic instructions; I'm posting here because I can't see any threads about this new tablet in Karmic, and the problem appears generic (?)

I compiled and installed linuxwacom-0.8.8-10, so that
"lsmod | grep wacom" gives "wacom 33756  0"
"lsusb" also recognises it as 00d8
but "more /proc/bus/input/devices" shows no evidence of detecting the tablet (no wacom entry).
I've tried both the last wacom.rules file that I could find recommended for Karmic, and also tried:
Favux_unofficial_updated\(12-16-10-\)_60-wacom.rules.txt

Any help would be appreciated.
Sincerely
Michael.> 

---

### Post by Favux on 2011-03-08
Hi mmpsych,

That'll take a little doing, are you sure you want to?  Karmic only has 2 months of support left.

You have one of the 5 new models so it is not in either the linuxwacom wacom.ko (usb kernel driver) or the linuxwacom X driver (wacom_drv.so).

For the wacom.ko you could patch the linuxwacom's wacom_wac.c before compiling to add your model, see post #2 on the Bamboo P&T HOW TO thread:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)  Or maybe use input-wacom-0.10.10-2?  I doubt input-wacom works with the linuxwacom X driver.  I don't think anyone has tried it.

Then you'd have to patch the linuxwacom X driver to add your model.  It's different and a little more complicated than patching the xf86-input-wacom driver which is shown.  But similar.  I think you'd have to patch validate.c too for example.  Anyway not sure it's worth it.

You could check the PPA's linked before part I. but I don't know if they support Karmic and your model in Karmic if they do.

---

