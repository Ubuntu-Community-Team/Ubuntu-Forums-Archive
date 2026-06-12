---
title: "HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu"
date: 2012-03-24
forum: Hardware
---

### Post by Favux on 2012-03-24
**Often rebranded as Aiptek, Genius, Monoprice, Princeton, or Trust tablets amongst other brands.**

Last updated: June 2, 2012


**[SIZE="3"]Preliminaries[/SIZE]**
Because of re-branding it is not always obvious what tablet you actually have.  You can determine your tablet's OEM Vendor ID and Product ID by entering the following command in a terminal:
```

lsusb

```
and looking for the tablet line in the output.
```

**KYE Systems** Vendor ID = 0458
**UC-Logic** Vendor ID = 5543
**Waltop** Vendor ID = 172F

```
The Product ID (essentially the model #) immediately follows the Vendor ID, separated from it by a colon.


**[SIZE="3"]Sources[/SIZE]**
**[DIGI*mend* project]("http://sourceforge.net/projects/digimend/")**
**[DIGI*mend* project mediawiki]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend")**
**[[PATCH v2] HID: kye: Add support for 3 tablets]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=blob;f=drivers/hid/hid-kye.c;h=b4f0d8216fd099bd69a2531600c02a241c42929f;hb=HEAD")**
**[Ubuntu Community Documentation KernelCompile]("https://help.ubuntu.com/community/Kernel/Compile")**
**[genius mousepen tablet i608 pen does not draw post #45]("http://ubuntuforums.org/showpost.php?p=11762830&postcount=45")**
**[HOW TO set up a Waltop tablet in Lucid & Maverick & Natty & Oneiric]("http://ubuntuforums.org/showthread.php?t=1595648")**


**[SIZE="3"]Summary[/SIZE]**
The UC-Logic and new KYE tablets are intended to use their HID kernel drivers and evdev as the X driver starting with Natty.  The Waltops can use the xf86-input-wacom driver starting with Maverick, however both stylus buttons are treated as the same button unless the Maverick kernel is patched.  This is fixed in Natty.  See the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

When we need to patch the kernel to add tablet support we'll start off as if we planned on rolling our own custom kernel.  But after patching the kernel rather than recompile the entire kernel we'll just compile and use the patched kernel drivers/modules.  This has the advantage of saving quite a bit of time.  The disadvantage is the use of the patched "vanilla" modules excludes other Ubuntu specific patches if they are also applied to those modules.  That may mean fixes or functionality for some devices may be absent if they depended on Ubuntu kernel patches to the modules.  Although unlikely breakage is also possible.  You could of course use the Ubuntu Community wiki's Kernel Compile to go ahead and recompile the kernel if you wished.

The HID section of the kernel does not permit a DKMS implementation of HID modules.  The reason is that the generic HID driver hid.ko has a list of devices with out-of-tree or special drivers in it and if the device is not present in the list the hid.ko can not chose a special driver (e.g. hid-kye.ko) for it.  This means a kernel update will break your tablet support and there is no way around it.  So if you need use of your tablet do not allow kernel updates until you have some time to recompile the modules you need.  Nikolai Kondrashov has come up with a way to implement DKMS for HID modules and submitted it to the kernel.  So maybe in a future kernel this limitation will be addressed.  [COLOR="Blue"]Update (4-2-12):[/COLOR]  Jiri Kosina (kernel HID maintainer) is not enthusiastic about the DKMS idea.  Instead he suggested trying [binding and unbinding modules]("http://lwn.net/Articles/143397/").  However when Nikolai tested this feature it did not work.  Currently Jiri and Nick are planning on seeing if they can get it working rather than doing the DKMS.


**[SIZE="3"]Patched pre-Compiled Kernels with KYE, UC-Logic, and Waltop Tablet Support[/SIZE]**
Pre-compiled kernels are now available from the DIGI*mend* site.  See the project blog post "[First kernel packages are out]("http://sourceforge.net/apps/wordpress/digimend/2012/04/17/first-kernel-packages-are-out/")" for details.  Instructions are on the DIGI*mend* mediawiki page "[Kernel packages]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_packages")".

The **patched kernels** are located at **[kernel-packages]("http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-5/")** in Files on the DIGI*mend* SourceForge site.  Pick the one closest to your current kernel, usually the most recent one.  You can determine your kernel version by entering in a terminal:
```
uname -r
```
And you can determine whether you have a 32-bit (i386) or 64-bit (amd64) install with:
```
uname -m
```
Then follow the instructions on the DIGI*mend* mediawiki.


**[SIZE="3"]HOW TO Add KYE Tablet Support to Ubuntu's Oneiric and Precise Kernels[/SIZE] (also includes the Waltop Pen button fix)**
**Genius EasyPen i405X, Genius MousePen i608X, and Genius EasyPen M610X**

**[SIZE="2"]I. Available Compiled Kernels with KYE Tablet Support[/SIZE]**

**Oneiric Ocelot (11.10)**
_**32-bit**_
[linux-headers-3.0.0-17-kye_3.0.0-17.30_i386.deb]("http://ponomarevs.no-ip.org:40404/pub/linux-headers-3.0.0-17-kye_3.0.0-17.30_i386.deb")
[linux-image-3.0.0-17-kye_3.0.0-17.30_i386.deb]("http://ponomarevs.no-ip.org:40404/pub/linux-image-3.0.0-17-kye_3.0.0-17.30_i386.deb")
* kernel by Nick, provided by [Janailson Leite]("http://janailsonleite.blogspot.com.br/2012/03/tablet-genius-easypen-i405x-em-ubuntu.html")

_**64-bit**_
[linux-headers-3.0.0-16-kye_3.0.0-16.28_amd64.deb]("http://ponomarevs.no-ip.org:40404/pub/linux-headers-3.0.0-16-kye_3.0.0-16.28_amd64.deb")
[linux-image-3.0.0-16-kye_3.0.0-16.28_amd64.deb]("http://ponomarevs.no-ip.org:40404/pub/linux-image-3.0.0-16-kye_3.0.0-16.28_amd64.deb")
* kernel by Nick, link provided by [viktoria.s]("http://ubuntuforums.org/showpost.php?p=11690620&postcount=28")


**[SIZE="2"]II. Compiling the KYE Modules[/SIZE]**
The KYE tablets are supported natively by the 3.3 kernel.  We'll do  everything on the Desktop.

First download on your Desktop HID-kye-Add-support-for-3-tablets.patch (and the waltop_button_fix_v2.patch if fixing your Waltop) attached below and extract it.  The Waltop patch also adds support for 2 models, the Q Pad and PID 0038.  Then open a terminal and download your Ubuntu kernel's source code onto your Desktop with the following commands.
```
cd Desktop

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)

apt-get source linux-image-$(uname -r)
```
The dependencies can take a while to download.  The kernel is about 94 MB and takes a few minutes to download depending on your connection. With Oneiric you'll see something like  linux_3.0.0.orig.tar.gz, linux_3.0.0-16.29.dsc, linux_3.0.0-16.29.diff.gz, and linux-3.0.0.  If the kernel source code doesn't download then you may need to check in Software Sources in the Ubuntu Software tab if you have the box in front of Source code checked.

To see the files you want to patch and then compile you can use Nautilus (Places) to go into the kernel's folder (e.g. linux-3.0.0) now on your Desktop and navigate to drivers/hid.

You'll apply the patch in the terminal using the following commands changing the folder name for Precise (to linux-3.2.0) of course.
```
cd linux-3.0.0

patch -p1 < ~/Desktop/HID-kye-Add-support-for-3-tablets.patch

*(needed if fixing the Waltop pen's buttons or adding the Q Pad or PID 0038 tablets)*
patch -p1 < ~/Desktop/waltop_button_fix_v2.patch

```
After the files are patched change directory to the downloaded kernel's source code /drivers/hid directory:
```
cd drivers/hid
```
Now you are ready to compile the HID modules. Use the following command:
```
make -C/lib/modules/`uname -r`/build M=`pwd` modules
```
This compiles all the HID modules, which you don't need, but the compile goes fast even so.

We want 4 of the compiled modules:  hid.ko, hid-kye.ko, usbhid.ko, and usbmouse.ko.  First make a backup of your current versions using some extension.  You want to be able to restore them from the Recovery Mode command line if you have to.
```
sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko.orig

*(only if the Waltop patch was applied)*
sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/waltop.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/waltop.ko.orig

```
Now copy the four newly compiled modules into your system kernel's modules directory with:
```
sudo cp hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko

sudo cp hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko

sudo cp usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko

sudo cp usbhid/usbmouse.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko

*(only if the Waltop patch was applied)*
sudo cp usbhid/waltop.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/waltop.ko

```
* need for usbmouse.ko from viktoria.s - Nick is dubious that this is needed, if your tablet works without it let me know

Rebuild all of the module dependencies:
```
sudo depmod -a
```
Then reboot and with luck the KYE tablet should be working.

*Thank you to viktoria.s for testing in Precise.*

---

### Post by Favux on 2012-03-24
Last updated: April 17, 2012


**[SIZE="3"]Preliminaries[/SIZE]**
You can determine your kernel version by entering the following command in a terminal:
```

uname -r

```
You should be able to determine your tablet model by running this command in a terminal:
```

xinput list

```


**[SIZE="3"]Summary[/SIZE]**
The HOW TO below adds HID kernel driver support for the following 4 UC-Logic tablets:  WP4030U, WP5540U, WP8060U, and PF1209.  And the following 4 Waltop tablets:  Slim Tablet 5.8", Slim Tablet 12.1", Media Tablet 10.6", and Media Tablet 14.1".  These models are supported natively in the 2.6.37 kernel.  In addition several patches make the HID drivers generally more drawing tablet capable.

This HOW TO is untested.  Several of the patches affect multiple hid drivers beyond hid-uclogic.ko and hid-waltop.ko.  This HOW TO does not copy all of the affected compiled drivers into the kernel's modules directory to save time.  The assumption is that will not break things.  So proceed at your own risk and please provide feed back if you test.  If it can not be made to work then compiling an entire custom kernel may be necessary.


**[SIZE="3"]HOW TO Apply the Backported digimend-kernel-patches to Kernel's 2.6.32 (Lucid), 2.6.35 (Maverick), and 2.6.36[/SIZE]**
**Kernel HID support for 4 UC-Logic (hid-uclogic.ko) and 4 Waltop (hid-waltop.ko) tablets**

We'll do  everything on the Desktop using Maverick's 2.6.35 kernel as an example.  Change the commands as needed for the kernel you are patching.

First download on your Desktop the digimend-kernel-patches tar from the [DIGI*mend* project site]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches") and extract it.  Then open a terminal and download your Ubuntu kernel's source code onto your Desktop with the following commands.
```
cd Desktop

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)

apt-get source linux-image-$(uname -r)
```
The dependencies can take a while to download.  The kernel is about 94 MB and takes a few minutes to download depending on your connection.   You'll see something like  linux_2.6.35.orig.tar.gz, linux_2.6.35-32.66.dsc, linux_2.6.35-32.66.diff.gz, and linux-2.6.35 if your release is Maverick.

To see the files you want to patch and then compile you can use Nautilus (Places) to go into the kernel's folder (e.g. linux-2.6.35) now on your Desktop and navigate to drivers/input/hid.  You might notice modules such as usbmouse.ko are missing depending on the kernel version.  This is because whether a driver is compiled as part of the baseline kernel (not visible) or as a loadable module is determined by the kernel's config file (/boot/grub).  These options are decided by the kernel team.  Loadable modules are selected with an "m".

**Example 1:  digimend-kernel-patches-0.4 tar (12-26-10)**
You'll apply the patches in the terminal using the following commands changing the folder name if using another kernel of course.
```
cd linux-2.6.35

patch -p1 < ~/Desktop/digimend-kernel-patches-0.4/vanilla/2.6.35/0001-HID-allow-resizing-and-replacing-report-descriptors.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-0.4/vanilla/2.6.35/0002-HID-rdesc-parser-remove-local-item-size-limit.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-0.4/vanilla/2.6.35/0003-HID-Add-Tablet-Pick-BTN_STYLUS2-mapping.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-0.4/vanilla/2.6.35/0004-HID-add-absolute-axis-resolution-calculation.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-0.4/vanilla/2.6.35/0005-Add-support-for-4-UC-Logic-tablets.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-0.4/vanilla/2.6.35/0006-Add-support-for-4-Waltop-tablets.patch

```

**Example 2:  digimend-kernel-patches-5 tar (4-16-12)**
As you can see a new patch adds tilt support for Waltops with tilt and another patch adds 3 KYE tablets.  Support is also added for an additional UC-Logic tablet and 3 Waltop tablets.  You'll apply the patches in the terminal using the following commands changing the folder name if using another kernel of course.
```
cd linux-2.6.35

patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0001-HID-allow-resizing-and-replacing-report-descriptors.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0002-HID-rdesc-parser-remove-local-item-size-limit.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0003-HID-Add-Tablet-Pick-BTN_STYLUS2-mapping.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0004-HID-add-absolute-axis-resolution-calculation.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0005-HID-hid-input-Add-digitizer-tilt-usage-support.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0006-Add-support-for-5-UC-Logic-tablets.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0007-Add-support-for-7-Waltop-tablets.patch
patch -p1 < ~/Desktop/digimend-kernel-patches-5/stable/2.6.32.59/0008-HID-kye-Add-support-for-3-tablets.patch

```
Since some of the patches have made their way into the kernel you'll notice that the 3.0.28 and 3.2.9 folders only contain 4 patches (and they are different for each).  See post #1 above for links to Oneiric and Precise kernels with the patches already applied.

After the files are patched change directory to the downloaded kernel's source code /drivers/hid directory:
```
cd drivers/hid
```
Now you are ready to compile the HID modules. Use the following command:
```
make -C/lib/modules/`uname -r`/build M=`pwd` modules
```
This compiles all the HID modules, which you don't need, but the compile goes fast even so.

We want 5 of the compiled modules:  hid.ko, hid-uclogic.ko, hid-waltop.ko, usbhid.ko, and usbmouse.ko.  First make a backup of your current versions using some extension.  You want to be able to restore them from the Recovery Mode command line if you have to.
```
sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-uclogic.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-waltop.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko.orig

```
Now copy the five newly compiled modules into your system kernel's modules directory with:
```
sudo cp hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko

sudo cp hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-uclogic.ko

sudo cp hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-waltop.ko

sudo cp usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko

sudo cp usbhid/usbmouse.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko

```

Rebuild all of the module dependencies:
```
sudo depmod -a
```
Then reboot and with luck your UC-Logic or Waltop tablet should be working or working better.

---

### Post by Favux on 2012-03-24
Last updated: March 25, 2012

In order to use the evdev X driver for tablet support in Lucid and Maverick with our shiny new kernel in post #2 we would need to patch it so that it has most of the functionality of evdev 2.5.99.  Unfortunately neither of the two patches currently available at the DIGI*mend* project site's "Evdev patches" in the [digimend-evdev-patches-0.1]("http://sourceforge.net/projects/digimend/files/evdev-patches/") tar work with Lucid's 2.3.2-5 or Maverick's 2.3.2-6 versions of evdev.  This is because one patch is for evdev version 2.0.8-1, which is the Debian Lenny version and the other is for evdev version 2.5.0.  The Lucid and Maverick versions lie in between and are too different for either patch to apply to their evdev deb package source code.


DIGI*mend* patches are available for evdev versions:
2.0.8-1
2.5.0


Natty evdev v. 2.6.0-1 - patching of evdev not needed
Maverick evdev v. 2.3.2-6
Lucid evdev v. 2.3.2-5

---

### Post by p1xelbud on 2012-10-05
So after doing depmod, does we need to compile the kernel? I follow your step but it's not working. 

Thanks before

---

### Post by Favux on 2012-10-05
Hi p1xelbud,

Welcome to Ubuntu forums!


No.  If the modules compiled successfully and you copied them into place correctly a tablet supported by the patches should start working after a reboot.  Although occasionally it take a few reboots for things to shake out.

That's the idea of the HOW TO.  It is a short cut to compiling the entire kernel.

---

### Post by Muy-burro on 2012-10-17
Greetings, and sorry for the inconvenience but I wonder if I could get some help with a Kanvus tablet, The H85 is not on the list of supported tablets.

Previously used WizardPen 0.8.1 driver for this tablet will work on a Debian 6, 32bit. But when you start using Kubuntu 4.12 amd64 (need to improve the support of proprietary bus) I lose the ability to use this driver.

A few hours ago I sent a diagnosis with the specifications of the tablet, and I wonder: Will there be simulated or support for this tablet with current driver components? If I can use with this driver, please tell me how? (I'm way too novice to compile kernel)

The tablet has specifications very paresidas to those shown by UC-Logic Tablet TWHA60 by Monoprince (5543:0781), but the H85 is 5543:0782 (UC-Logic from what I can see)

If it is useful here is the data used in the configuration of H85 with 70-wizardpen.conf driver, and I see that the syntax is similar.

```
Section "InputClass"
**** Identifier "WizardPen class"
**** MatchIsTablet "on"
# MatchVendor "UC-LOGIC | H850S | KYE Systems | Ace Cad"
**** MatchProduct "H850S"
**** MatchDevicePath "/ dev / input / event *"
**** Driver "wizardpen"
EndSection

Section "InputClass"
**** Identifier "WizardPen ignore mouse dev class"
**** MatchIsTablet "on"
# MatchVendor "UC-LOGIC | H850S | KYE Systems | Ace Cad"
**** MatchProduct "H850S"
**** MatchDevicePath "/ dev / input / mouse *"
**** Option "Ignore" "yes"
EndSection
```

Thanks for any help you can give.

---

### Post by Favux on 2012-10-18
Hi Muy-burro,

I saw your submission to DIGImend-devel.  That was the correct thing to do because the 0782 looks like a new UC-Logic tablet (5543).

Kanvus H85 tablet (5543:0782) = UC-Logic H850S

lsusb:
```
Bus 003 Device 016: ID 5543:0782 UC-Logic Technology Corp.
```

xinput-list:
```
&#9116;   &#8627; H850S                                     id=14   [slave  pointer  (2)]
&#9116;   &#8627; H850S                                     id=15   [slave  pointer  (2)]
```
Looks like maybe ID 15 is the pen.  Does the tablet come with a mouse?

Does anything happen when you use the pen on the tablet.  If so what?

---

### Post by Muy-burro on 2012-10-18
1) Yes, id = 15 is the pen, xinput --test 14 does not send results.

2) No, the tablet does not come with mouse.

3) Using xinput --test 15 are many movements, but do not move the mouse pointer on the screen, not even to the upper left corner. Although I notice canvios brightness on the screen, what the computer does when it passes only from inactive to active (PowerManager I guess).

The results of xinput --test 15 are in a file called xinput_test.txt, and all I could find on the tablet is stored in a file called kanvush85_digimend_report.txt.

If you need more information from the tablet, tell me what you need.

Thanks for the help.

---

### Post by Favux on 2012-10-18
Sure.

Let's confirm the tablet pen is on the evdev driver.  Make sure the ID # has not changed:
```
xinput list-props 15
```
You could also find the driver by looking at Xorg.0.log in /var/log.

If the pen is on the evdev driver but not working we could quick check if maybe it works on the wacom X driver.

I just compiled wizardpen in Precise (12.04) and it compiled and installed.  I have no idea if it works in Precise.  We would have to test it.

---

### Post by Muy-burro on 2012-10-18
xinput list-props 15
```
Device 'H850S':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (253):     0
        Device Accel Constant Deceleration (254):       1.000000
        Device Accel Adaptive Deceleration (255):       1.000000
        Device Accel Velocity Scaling (256):    10.000000
        Device Product ID (248):        21827, 1922
        Device Node (249):      "/dev/input/event11"
        Evdev Axis Inversion (572):     0, 0
        Evdev Axis Calibration (573):   <no items>
        Evdev Axes Swap (574):  0
        Axis Labels (575):      "Abs X" (522), "Abs Y" (523), "Abs Z" (570), "Abs Rotary X" (571), "Abs Pressure" (524)
        Button Labels (576):    "Button Left" (134), "Button Middle" (135), "Button Right" (136), "Button Wheel Up" (137), "Button Wheel Down" (138), "Button Horiz Wheel Left" (139), "Button Horiz Wheel Right" (140), "Button Side" (567), "Button Extra" (568), "Button Forward" (569), "Button Unknown" (565), "Button Unknown" (565), "Button Unknown" (565), "Button Unknown" (565)
        Evdev Middle Button Emulation (577):    0
        Evdev Middle Button Timeout (578):      50
        Evdev Third Button Emulation (579):     0
        Evdev Third Button Emulation Timeout (580):     1000
        Evdev Third Button Emulation Button (581):      3
        Evdev Third Button Emulation Threshold (582):   20
        Evdev Wheel Emulation (583):    0
        Evdev Wheel Emulation Axes (584):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (585):    10
        Evdev Wheel Emulation Timeout (586):    200
        Evdev Wheel Emulation Button (587):     4
        Evdev Drag Lock Buttons (588):  0
```

Xorg.0.log show:
```
[123009.773] (**) Option "xkb_rules" "evdev"
[123009.773] (**) Option "xkb_model" "pc105"
[123009.773] (**) Option "xkb_layout" "us"
[123011.965] (II) XKB: reuse xkmfile /var/lib/xkb/server-B3142C282A6EB2AFBD07343CF770AD5105004170.xkm
[123012.550] (II) XKB: reuse xkmfile /var/lib/xkb/server-B3142C282A6EB2AFBD07343CF770AD5105004170.xkm
[128304.053] (II) XKB: generating xkmfile /var/lib/xkb/server-DF0FDA660FAC626442D028C3B1CD301120D8A095.xkm
[129998.869] (II) config/udev: Adding input device H850S (/dev/input/mouse2)
[129998.869] (II) No input driver specified, ignoring this device.
[129998.869] (II) This device may have been added with another device file.
[129998.870] (II) config/udev: Adding input device H850S (/dev/input/event12)
[129998.870] (**) H850S: Applying InputClass "evdev pointer catchall"
[129998.870] (**) H850S: Applying InputClass "evdev keyboard catchall"
[129998.871] (II) Using input driver 'evdev' for 'H850S'
[129998.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[129998.871] (**) H850S: always reports core events
[129998.871] (**) evdev: H850S: Device: "/dev/input/event12"
[129998.871] (--) evdev: H850S: Vendor 0x5543 Product 0x782
[129998.871] (--) evdev: H850S: Found 3 mouse buttons
[129998.871] (--) evdev: H850S: Found scroll wheel(s)
[129998.871] (--) evdev: H850S: Found relative axes
[129998.871] (--) evdev: H850S: Found x and y relative axes
[129998.871] (--) evdev: H850S: Found keys
[129998.871] (II) evdev: H850S: Configuring as mouse
[129998.871] (II) evdev: H850S: Configuring as keyboard
[129998.871] (II) evdev: H850S: Adding scrollwheel support
[129998.871] (**) evdev: H850S: YAxisMapping: buttons 4 and 5
[129998.871] (**) evdev: H850S: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[129998.871] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input48/event12"
[129998.871] (II) XINPUT: Adding extended input device "H850S" (type: KEYBOARD, id 14)
[129998.871] (**) Option "xkb_rules" "evdev"
[129998.871] (**) Option "xkb_model" "pc105"
[129998.871] (**) Option "xkb_layout" "us"
[129998.872] (II) evdev: H850S: initialized for relative axes.
[129998.872] (**) H850S: (accel) keeping acceleration scheme 1
[129998.872] (**) H850S: (accel) acceleration profile 0
[129998.872] (**) H850S: (accel) acceleration factor: 2.000
[129998.872] (**) H850S: (accel) acceleration threshold: 4
[129998.901] (II) config/udev: Adding input device H850S (/dev/input/event11)
[129998.902] (**) H850S: Applying InputClass "evdev pointer catchall"
[129998.902] (**) H850S: Applying InputClass "evdev tablet catchall"
[129998.902] (II) Using input driver 'evdev' for 'H850S'
[129998.902] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[129998.902] (**) H850S: always reports core events
[129998.902] (**) evdev: H850S: Device: "/dev/input/event11"
[129998.902] (--) evdev: H850S: Vendor 0x5543 Product 0x782
[129998.902] (--) evdev: H850S: Found 10 mouse buttons
[129998.902] (--) evdev: H850S: Found scroll wheel(s)
[129998.902] (--) evdev: H850S: Found relative axes
[129998.902] (--) evdev: H850S: Found x and y relative axes
[129998.902] (--) evdev: H850S: Found absolute axes
[129998.902] (--) evdev: H850S: Found x and y absolute axes
[129998.902] (--) evdev: H850S: Found absolute tablet.
[129998.902] (II) evdev: H850S: Configuring as tablet
[129998.902] (II) evdev: H850S: Adding scrollwheel support
[129998.902] (**) evdev: H850S: YAxisMapping: buttons 4 and 5
[129998.902] (**) evdev: H850S: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[129998.902] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input47/event11"
[129998.902] (II) XINPUT: Adding extended input device "H850S" (type: TABLET, id 15)
[129998.902] (WW) evdev: H850S: touchpads, tablets and touchscreens ignore relative axes.
[129998.902] (II) evdev: H850S: initialized for absolute axes.
[129998.903] (**) H850S: (accel) keeping acceleration scheme 1
[129998.903] (**) H850S: (accel) acceleration profile 0
[129998.903] (**) H850S: (accel) acceleration factor: 2.000
[129998.903] (**) H850S: (accel) acceleration threshold: 4
[129998.907] (II) config/udev: Adding input device H850S (/dev/input/mouse1)
[129998.907] (II) No input driver specified, ignoring this device.
[129998.907] (II) This device may have been added with another device file.
```

About wizardpen driver, there is a [bug even detailed in the PPA]("https://bugs.launchpad.net/wizardpen/+bug/591767"), which prevents me to compile an amd64 driver.

Warning: I have nothing set for this tablet work as explained in the Digimend Wiki or explained here.

---

### Post by Favux on 2012-10-18
> Warning: I have nothing set for this tablet work as explained in the Digimend Wiki or explained here. 
Good!  Nothing to undo.  :)

Everything looks good for evdev driver setup.  The list-props shnows evdev knows it is a tablet pen because it uses Absolute (ABS) axes:
```
Axis Labels (575):      "Abs X" (522), "Abs Y" (523), "Abs Z" (570), "Abs Rotary X" (571), "Abs Pressure" (524)
```

Xorg.0.log looks correct.  The buttons look to be set up correctly as keyboard keys (evdev keyboard catchall):
```
[129998.870] (II) config/udev: Adding input device H850S (/dev/input/event12)
[129998.870] (**) H850S: Applying InputClass "evdev pointer catchall"
[129998.870] (**) H850S: Applying InputClass "evdev keyboard catchall"
[129998.871] (II) Using input driver 'evdev' for 'H850S'
[129998.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[129998.871] (**) H850S: always reports core events
[129998.871] (**) evdev: H850S: Device: "/dev/input/event12"
[129998.871] (--) evdev: H850S: Vendor 0x5543 Product 0x782
......
[129998.871] (II) XINPUT: Adding extended input device "H850S" (type: KEYBOARD, id 14)

```
The pen also appears correctly as a tablet (evdev tablet catchall):
```
[129998.901] (II) config/udev: Adding input device H850S (/dev/input/event11)
[129998.902] (**) H850S: Applying InputClass "evdev pointer catchall"
[129998.902] (**) H850S: Applying InputClass "evdev tablet catchall"
[129998.902] (II) Using input driver 'evdev' for 'H850S'
[129998.902] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[129998.902] (**) H850S: always reports core events
[129998.902] (**) evdev: H850S: Device: "/dev/input/event11"
[129998.902] (--) evdev: H850S: Vendor 0x5543 Product 0x782
.....
[129998.902] (II) XINPUT: Adding extended input device "H850S" (type: TABLET, id 15)

```
It is possible evdev just needs coordinates for the tablet.  The maximum X dimension and the maximum Y dimension.  Or it could be the kernel driver, the usb HID driver, doesn't quite work for evdev.  That's what Nick mainly does, fix the kernel driver for the tablet by fixing the usb descriptors.

So we could try coordinates or quickly try the wacom driver and see if it works with what the kernel driver is providing.

What do you want to do?

> About wizardpen driver, there is a bug even detailed in the PPA, which prevents me to compile an amd64 driver.
Hmm.  I compiled in on an AMD64 Precise install.  What error message(s) are you getting?

---

### Post by Muy-burro on 2012-10-18
> Hmm. I compiled in on an AMD64 Precise install. What error message(s) are you getting?

What kind of sorcery is this?[IMG]http://k14.kn3.net/socialphy/0/0/3/6/3/9/joshy_ml/45B.jpg[/IMG]

I just get an error and shuts down the process, when I read about the bug in the link I give up, spend two months trying to sell the tablet until I find this new method.

About using Wacom or evdev ... I do not see why not try both, if I can help this tablet to include in the list of supported hardware, I will help.

Sorry for the delay, I had a class in the afternoon.

---

### Post by Favux on 2012-10-18
No problem.

To get it on the Wacom X driver we'll do the following.  First change directory to where the user custom xorg.conf.d directory should be.
```
cd /etc/X11
```
Then run list to see if it is there:
```
ls
```
If not create the xorg.conf.d directory otherwise go onto the next step.
```
sudo mkdir xorg.conf.d
```
Then change directory into it.
```
cd xorg.conf.d
```
Now create a 52-tablet.conf file in /etc/X11/xorg.conf.d:
```
gksudo gedit 52-tablet.conf
```
Copy and paste the contents of the following snippet into the file opened in gedit:
```

Section "InputClass"
    Identifier "UC-Logic on wacom"
    MatchIsTablet "on"
    MatchProduct "H850S"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```
And Save.  Now restart.


> What kind of sorcery is this?

I just get an error and shuts down the process, when I read about the bug in the link I give up, spend two months trying to sell the tablet until I find this new method.
I problably have libraries (dependencies) installed you don't.  We'd need to look at what errors you get with configure, make, and make install to find out.  But WizardPen is a last resort because it hasn't had any development since May 2011.  So who knows if it works even if compiled?  But I would not mind finding out.  :)

---

### Post by Muy-burro on 2012-10-18
Ok, when I drew a line with the pen, the cursor moves to the top of the screen, and stays there, also when I logging into KDE, I get an error wacom tablet preferences: "No profile". I guess it is not configured. But at least we know that is detected, even if I disconnect or connect I get a message in the system tray.

---

### Post by Muy-burro on 2012-10-18
The tip of the pen is detected, but none of the other buttons of the pen, or the frame of the tablet show activity.

---

### Post by Favux on 2012-10-18
Does the cursor go to the top of the screen, the top left corner, or does it follow the pen tip?

What is the output of **xsetwacom list** in a terminal?

---

### Post by Favux on 2012-10-18
**[SIZE="3"]FYI HOW TO UPDATE[/SIZE]:  digimend-kernel-patches-6 released 9-8-12**


[Patch set 6 announcement]("http://sourceforge.net/mailarchive/forum.php?thread_name=CALu8Fe9yOcGmuiP4275xQ6V1K5x6Hi7yko2%3DdKnHtJ_jypaA7A%40mail.gmail.com&forum_name=digimend-users"):  This release adds support for slightly newer kernels, drops support for older ones and adds support for two more UC-Logic tablets:  Wireless Tablet TWHL850 and Tablet TWHA60.

[Kernel patch set version 6]("http://sourceforge.net/projects/digimend/files/kernel-patches/digimend-kernel-patches-6.tar.gz/download").  For available kernel patch sets see:  [http://sourceforge.net/projects/digimend/files/kernel-patches/](http://sourceforge.net/projects/digimend/files/kernel-patches/)

Kernel patches page on the DIGImend mediawiki:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches)

---

### Post by Muy-burro on 2012-10-18
1) Top left corner of the screen, and does not move or follows the movements of the pen.

2) xsetwacom list show:
```
H850S stylus                            id: 10  type: STYLUS    
H850S eraser                            id: 11  type: ERASER    
H850S pad                               id: 16  type: PAD 
```

Do I have to apply one of the patches listed above?

---

### Post by Favux on 2012-10-18
Unfortunately no.  Your tablet is not yet in the patch set.  Here is the Compatibility table that comes with the patch set:
> The table below shows tablet support added by patches for corresponding
kernels (+), tablet support already present there (=), i.e. not requiring a
patch, and missing support (-).

VID: PID     Original model                      stable  ubuntu      stable
                                                3.2.28  3.2.0-30.48 3.0.42

0458:5010   KYE EasyPen i405X                   +       +           +
0458:5011   KYE MousePen i608X                  +       +           +
0458:5013   KYE EasyPen M610X                   +       +           +
172f:0032   Waltop Slim Tablet 5.8"             =       =           =
172f:0034   Waltop Slim Tablet 12.1"            =       =           =
172f:0037   Waltop Q Pad                        +       +           +
172F:0038   Waltop PID 0038                     +       +           +
172f:0500   Waltop Media Tablet 14.1"           =       =           =
172f:0501   Waltop Media Tablet 10.6"           =       =           =
172F:0502   Waltop Sirius Battery Free Tablet   +       +           +
5543:0003   UC-Logic Tablet WP4030U             =       =           =
5543:0004   UC-Logic Tablet WP5540U             =       =           =
5543:0005   UC-Logic Tablet WP8060U             =       =           =
5543:0042   UC-Logic Tablet PF1209              =       =           =
5543:0064   UC-Logic Tablet WP1062              =       =           +
5543:0522   UC-Logic Wireless Tablet TWHL850    +       +           +
5543:0781   UC-Logic Tablet TWHA60              +       +           +

For detailed support information and rebranded model names see
tablet support status page at
[http://sf.net/apps/mediawiki/digimend/?title=Tablet_support_status](http://sf.net/apps/mediawiki/digimend/?title=Tablet_support_status)
So 0782 is not in there yet.  Nick will have to look at the diagnostics you submitted.  With luck your tablet will be in patch set 7.

Top left corner of the screen is the origin or 0,0.  So that means the X Server is not getting any coordinates from the Wacom X driver.  So the UC-Logic tablets don't work with Wacom.  Viktoria S. said a few weeks ago the KYE tablets work with Wacom so it was worth testing.

I would like to see the output of **xinput list-props 15** while the tablet is on the Wacom driver.  To disable the tablet.conf just comment out the wacom driver line:
```
#    Driver "wacom"
```
So Wacom is out.  That leaves giving evdev the coordinates or trying WizardPen.  Do you want to try one of them?  If so which one?

---

### Post by Muy-burro on 2012-10-18
xinput --list show:
```
&#9116;   &#8627; H850S stylus                              id=10   [slave  pointer  (2)]
&#9116;   &#8627; H850S eraser                              id=11   [slave  pointer  (2)]
&#9116;   &#8627; H850S pad                                 id=16   [slave  pointer  (2)]
&#9116;   &#8627; H850S                                     id=17   [slave  pointer  (2)]
```

No more ID 15, the only test that shows results was the xinput --test 11.

xinput list-props 11 show:
```
Device 'H850S eraser':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (252):     0
        Device Accel Constant Deceleration (253):       1.000000
        Device Accel Adaptive Deceleration (254):       1.000000
        Device Accel Velocity Scaling (255):    10.000000
        Device Node (249):      "/dev/input/event6"
        Wacom Tablet Area (262):        0, 0, 32000, 20000
        Wacom Rotation (263):   0
        Wacom Pressurecurve (264):      0, 0, 100, 100
        Wacom Serial IDs (265): 1922, 1, 0, 0, 0
        Wacom Serial ID binding (266):  0
        Wacom Pressure Threshold (267): 27
        Wacom Sample and Suppress (268):        2, 4
        Wacom Enable Touch (269):       0
        Wacom Enable Touch Gesture (271):       0
        Wacom Touch Gesture Parameters (272):   0, 0, 250
        Wacom Tool Type (273):  "ERASER" (337)
        Wacom Button Actions (274):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Device Product ID (248):        21827, 1922
        Wacom Debug Levels (275):       0, 0
```

xinput list-props 10 show:
```
Device 'H850S stylus':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (252):     0
        Device Accel Constant Deceleration (253):       1.000000
        Device Accel Adaptive Deceleration (254):       1.000000
        Device Accel Velocity Scaling (255):    10.000000
        Device Node (249):      "/dev/input/event6"
        Wacom Tablet Area (262):        0, 0, 32000, 20000
        Wacom Rotation (263):   0
        Wacom Pressurecurve (264):      0, 0, 100, 100
        Wacom Serial IDs (265): 1922, 0, 2, 0, 0
        Wacom Serial ID binding (266):  0
        Wacom Pressure Threshold (267): 27
        Wacom Sample and Suppress (268):        2, 4
        Wacom Enable Touch (269):       0
        Wacom Hover Click (270):        1
        Wacom Enable Touch Gesture (271):       0
        Wacom Touch Gesture Parameters (272):   0, 0, 250
        Wacom Tool Type (273):  "STYLUS" (251)
        Wacom Button Actions (274):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Device Product ID (248):        21827, 1922
        Wacom Debug Levels (275):       0, 0

```

xinput list-props 16 show:
```
Device 'H850S pad':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (252):     0
        Device Accel Constant Deceleration (253):       1.000000
        Device Accel Adaptive Deceleration (254):       1.000000
        Device Accel Velocity Scaling (255):    10.000000
        Device Node (249):      "/dev/input/event6"
        Wacom Rotation (263):   0
        Wacom Serial IDs (265): 1922, 0, 15, 2, 15
        Wacom Serial ID binding (266):  0
        Wacom Pressure Threshold (267): 27
        Wacom Sample and Suppress (268):        2, 4
        Wacom Enable Touch (269):       0
        Wacom Enable Touch Gesture (271):       0
        Wacom Touch Gesture Parameters (272):   0, 0, 250
        Wacom Tool Type (273):  "PAD" (338)
        Wacom Button Actions (274):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Strip Buttons (339):      "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Wheel Buttons (340):      "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Device Product ID (248):        21827, 1922
        Wacom Debug Levels (275):       0, 0
```

xinput list-props 17 show:
```
Device 'H850S':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (252):     0
        Device Accel Constant Deceleration (253):       1.000000
        Device Accel Adaptive Deceleration (254):       1.000000
        Device Accel Velocity Scaling (255):    10.000000
        Device Product ID (248):        21827, 1922
        Device Node (249):      "/dev/input/event7"
        Evdev Axis Inversion (279):     0, 0
        Evdev Axes Swap (281):  0
        Axis Labels (282):      "Rel X" (141), "Rel Y" (142), "Rel Vert Wheel" (277), "Rel Misc" (278)
        Button Labels (283):    "Button Left" (134), "Button Middle" (135), "Button Right" (136), "Button Wheel Up" (137), "Button Wheel Down" (138), "Button Horiz Wheel Left" (139), "Button Horiz Wheel Right" (140)
        Evdev Middle Button Emulation (284):    0
        Evdev Middle Button Timeout (285):      50
        Evdev Third Button Emulation (286):     0
        Evdev Third Button Emulation Timeout (287):     1000
        Evdev Third Button Emulation Button (288):      3
        Evdev Third Button Emulation Threshold (289):   20
        Evdev Wheel Emulation (290):    0
        Evdev Wheel Emulation Axes (291):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (292):    10
        Evdev Wheel Emulation Timeout (293):    200
        Evdev Wheel Emulation Button (294):     4
        Evdev Drag Lock Buttons (295):  0

```

WizardPen is discarded due to lack of updated versions, so we go with evdev.

---

### Post by Muy-burro on 2012-10-19
I forgot to say that when the pen stroke during xinput - test 11, the coordinates x, y and pressure do not change are always 0, and a new axis that is always the same value 63. The only button that detects the tip of the pen when pressed and when released.

---

### Post by Favux on 2012-10-19
Thank you for the wacom list-props.
> WizardPen is discarded due to lack of updated versions, so we go with evdev. 
Okay, it would be nice if you could use [xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator") (in the repositories) to determine the coordinates.  But we can calculate them from the specifications.
[http://global.kanvus-global.com/main/prod_in.aspx?mnuid=1524&modid=26&prodid=339](http://global.kanvus-global.com/main/prod_in.aspx?mnuid=1524&modid=26&prodid=339)

 Active Area	 	 8" x 5"
 Resolution		 4000 LPI

LPI is Lines Per Inch.  The 0781 has the same resolution and that's what Nick uses for its fixed u[sb descriptor]("http://thread.gmane.org/gmane.linux.kernel.input/26544").  So we will go with 4000 LPI.

X = 8" x 4000 LPI = 32,000

Y = 5" x 4000 LPI = 20,000

From **man evdev** entered in a terminal:
> Option "Calibration" "min-x max-x min-y max-y"

So to give evdev the coordinates we change the 52-tablet.conf in /etc/X11/xorg.conf.d to:
```
Section "InputClass"
#    Identifier "UC-Logic on wacom"
    Identifier "UC-Logic H850S"
    MatchIsTablet "on"
    MatchProduct "H850S"
    MatchDevicePath "/dev/input/event*"
#    Driver "wacom"
    Driver "evdev"
    Option "Calibration" "0 32000 0 20000"
EndSection
```
And while you are probably correct and WizardPen won't work, we do not yet know that for sure.

---

### Post by Muy-burro on 2012-10-19
ok, I'm back from my morning class, and this is the result of xinput_calibrator, but I have not deleted the previous changes with wacom driver.

xinput_calibrator show:
```
Warning: multiple calibratable devices found, calibrating last one (H850S pad)
        use --device to select another one.
Calibrating standard Xorg driver "H850S pad"
        current calibration values: min_x=0, max_x=0 and min_y=0, max_y=0
        If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).
```

In the settings of KDE Wacom tablet: I see the same size numbers of active area of the tablet: 0 0 32000 20000. This shows that at least some information about the tablet is coming to the driver.

About WizardPen, I think the same. In addition there are many reports of bugs in their PPA about malfunctions in Ubuntu 12.04, or to stop working in this version.

I will test the new settings.

---

### Post by Muy-burro on 2012-10-19
Changes already implemented and I restarted the computer, now the tablet does not move the cursor on the screen. Neither moves the cursor to the top left of the screen as he did with the wacom driver.

xinput_calibrator show:
```
Calibrating EVDEV driver for "H850S" id=10
        current calibration values (from XInput): min_x=0, max_x=32000 and min_y=0, max_y=20000
```

xinput --list show:
```
&#9116;   &#8627; H850S                                     id=10   [slave  pointer  (2)]
&#9116;   &#8627; H850S                                     id=11   [slave  pointer  (2)]
```

xinput list-props 10
```
Device 'H850S':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (261):     0
        Device Accel Constant Deceleration (262):       1.000000
        Device Accel Adaptive Deceleration (263):       1.000000
        Device Accel Velocity Scaling (264):    10.000000
        Device Product ID (248):        21827, 1922
        Device Node (249):      "/dev/input/event6"
        Evdev Axis Inversion (265):     0, 0
        Evdev Axis Calibration (266):   0, 32000, 0, 20000
        Evdev Axes Swap (267):  0
        Axis Labels (268):      "Abs X" (256), "Abs Y" (257), "Abs Z" (258), "Abs Rotary X" (259), "Abs Pressure" (260)
        Button Labels (269):    "Button Left" (134), "Button Middle" (135), "Button Right" (136), "Button Wheel Up" (137), "Button Wheel Down" (138), "Button Horiz Wheel Left" (139), "Button Horiz Wheel Right" (140), "Button Side" (253), "Button Extra" (254), "Button Forward" (255), "Button Unknown" (251), "Button Unknown" (251), "Button Unknown" (251), "Button Unknown" (251)
        Evdev Middle Button Emulation (270):    0
        Evdev Middle Button Timeout (271):      50
        Evdev Third Button Emulation (272):     0
        Evdev Third Button Emulation Timeout (273):     1000
        Evdev Third Button Emulation Button (274):      3
        Evdev Third Button Emulation Threshold (275):   20
        Evdev Wheel Emulation (276):    0
        Evdev Wheel Emulation Axes (277):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (278):    10
        Evdev Wheel Emulation Timeout (279):    200
        Evdev Wheel Emulation Button (280):     4
        Evdev Drag Lock Buttons (281):  0
```

xinput list-props 11
```
Device 'H850S':
        Device Enabled (131):   1
        Coordinate Transformation Matrix (133): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (261):     0
        Device Accel Constant Deceleration (262):       1.000000
        Device Accel Adaptive Deceleration (263):       1.000000
        Device Accel Velocity Scaling (264):    10.000000
        Device Product ID (248):        21827, 1922
        Device Node (249):      "/dev/input/event7"
        Evdev Axis Inversion (265):     0, 0
        Evdev Axes Swap (267):  0
        Axis Labels (268):      "Rel X" (141), "Rel Y" (142), "Rel Vert Wheel" (282), "Rel Misc" (283)
        Button Labels (269):    "Button Left" (134), "Button Middle" (135), "Button Right" (136), "Button Wheel Up" (137), "Button Wheel Down" (138), "Button Horiz Wheel Left" (139), "Button Horiz Wheel Right" (140)
        Evdev Middle Button Emulation (270):    0
        Evdev Middle Button Timeout (271):      50
        Evdev Third Button Emulation (272):     0
        Evdev Third Button Emulation Timeout (273):     1000
        Evdev Third Button Emulation Button (274):      3
        Evdev Third Button Emulation Threshold (275):   20
        Evdev Wheel Emulation (276):    0
        Evdev Wheel Emulation Axes (277):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (278):    10
        Evdev Wheel Emulation Timeout (279):    200
        Evdev Wheel Emulation Button (280):     4
        Evdev Drag Lock Buttons (281):  0
```

---

### Post by Favux on 2012-10-20
Assuming we have the coordinates correct, which is likely given what you are seeing with the KDE Wacom tablet app., then evdev doesn't work either.

So the kernel driver for the UC-Logic H850S does not yet support the evdev driver, even with the coordinates supplied, and it does not work with the Wacom X driver either.

It did work with WizardPen:
> Previously used WizardPen 0.8.1 driver for this tablet will work on a Debian 6, 32bit. 
I assume you meant the pen drew and the pen buttons worked.  Did the tablet buttons work too?

---

### Post by Muy-burro on 2012-10-20
Ok, I can wait for a working version because selling the tablet and find another tended to wait until next year.

About WizardPen driver,it worked properly, but never set the eight buttons that has the table, only using the three buttons on the pen. I'll get that necessary dependencies to see if the driver is still working but I using inkscape to work lately so I do not need to have the tablet working right now. I just want to avoid the ephemeral expense, sell and buy a wacom bamboo or something that is supported by the driver.

If you need more data about the tablet, let me know.

---

### Post by Favux on 2012-10-20
Thank you for the offer.  It makes sense that the WizardPen driver only supported the Pen buttons. 

Just in case you or someone else wants to try compiling WizardPen I have some WizardPen instructions for Precise.

[SIZE="3"]**HOW TO Compile the WizardPen Driver in Precise.**[/SIZE]
in collaboration with Muy-burro

Download the latest WizardPen driver tar from Martin Owen's Launchpad PPA onto your Desktop.  Open a terminal and run (copy and paste) the following commands:
```
cd Desktop

wget https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+files/xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz
```
Extract it onto your Desktop by right clicking on it and selecting 'Extract Here' or by running the following in the terminal:
```
tar xvzf xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz
```
Then to compile run the following commands:
```
sudo apt-get update

sudo apt-get install build-essential xutils-dev xutils libx11-dev libxext-dev xautomation xinput xserver-xorg-dev autoconf libtool pkg-config

sudo apt-get upgrade

cd xserver-xorg-input-wizardpen_0.8.1

make clean

./configure --prefix=/usr

make

sudo make install

```
Check for errors fter each of these commands:  **./configure --prefix=/usr**, **make**, and **sudo make install**.  If you see errors and aren't able to compile save your terminal output.  Post the output so we can figure out what is wrong.

If you see something like the following after **configure**:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: error: cannot run /bin/bash ./config.sub
```
Change the line:
```
./configure --prefix=/usr
```
to:
```
./autogen.sh --prefix=/usr
```

When it compiles and is installed you will end up with:
> /usr/lib/xorg/modules/input/wizardpen_drv.la or wizardpen_drv.so - the X driver
/etc/udev/rules.d/67-xorg-wizardpen.rules - the udev wizardpen rules, may want to delete these
/usr/share/X11/xorg.conf.d/70-wizardpen.conf - the wizardpen.conf, may want to delete this
/usr/bin/wizardpen-calibrate - calibration alternative to xinput_calibrator
/usr/share/man/man4/wizardpen.4 - the WizardPen manual, i.e. man wizardpen in a terminal

Tablet OEMs and models known to be supported by the WizardPen driver.
> # AceCad Corp
Flair II GT-504
VENDOR_ID="0460", Product ID="0004"

# KYE Systems Corp
KYE Systems Corp Wide Screen Design Tablet TB-7300
VENDOR ID="0458", Product ID="5003"
KYE Systems Corp Wide Screen Design Tablet TB-7300
VENDOR ID="0458", Product ID="5004"

# UC-Logic Technology Corp
SuperPen WP3325U Tablet
VENDOR_ID="5543", Product ID="0002"
# WP4030, Genius MousePen 4x3 Tablet/Aquila L1 Tablet
VENDOR_ID="5543", Product ID="0003"
# WP5540, Genius MousePen 5x4 Tablet
VENDOR_ID="5543", Product ID="0004"
# WP8060, Genius MousePen 8x6 Tablet, Trust TB-6300
VENDOR_ID="5543", Product ID="0005"
# Genius PenSketch 6x8 Tablet
VENDOR_ID="5543", Product ID="0041"
# Genius PenSketch 12x9 Tablet
VENDOR_ID="5543", Product ID="0042"
# Digital Organizer (may not exist)
VENDOR_ID="5543", Product ID="6000"
# Genius G-Note 5000
VENDOR_ID="5543", Product ID="6001"
* adapted from /etc/udev/rules.d/67-xorg-wizardpen.rules
* Product ID is Model ID in udev rules.

Other tablets not explicitly included in the Wizard Pen driver's udev rules, such as Muy-burro UC-Logic H850S (5543:0782), also work with use of a custom .conf file.

**Example - UC-Logic H850S (5543:0782):**
Comment out (#) the contents of 70-wizardpen.conf:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
And modify the 52-tablet.conf:
```
gksudo gedit /etc/X11/xorg.conf.d/52-tablet.conf
```
to:
```
Section "InputClass"
    Identifier "UC-Logic H850S"
    MatchIsTablet "on"
    MatchProduct "H850S"
    MatchDevicePath "/dev/input/event*"
#    Driver "evdev"
#    Option "Calibration" "0 32000 0 20000"
    Driver "wizardpen"
EndSection
```
Save and restart.

---

### Post by Muy-burro on 2012-10-21
./configure --prefix=/usr show:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: error: cannot run /bin/bash ./config.sub
```

Already installed all the dependencies that come in the README file, and I can not compile without a Makefile ... So I'm screwed with WizardPen driver.

---

### Post by Favux on 2012-10-21
Which libraries did you add?

Okay, I do not recognize:
> configure: error: cannot run /bin/bash ./config.sub
specifically but since it is happening with configure try adding to:
```
sudo apt-get install build-essential

```
these three:
```
sudo apt-get install build-essential autoconf libtool pkg-config

```
just to cover the bases.

---

### Post by Muy-burro on 2012-10-21
It did not work.

All these packages are installed: xutils-dev xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev autoconf libtool pkg-config

Many of them are mentioned in the README file that came with the driver.

Even so the error persists:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: error: cannot run /bin/bash ./config.sub
```

Apparently my system is not to the driver. It is a troll system.

---

### Post by Favux on 2012-10-21
Could you compress and attach the entire ouput of ./configure on your next post?  The commands you are using included?  I want to make sure I am not missing something.

So the line we are using is?
```
sudo apt-get install build-essential xutils-dev xutils libx11-dev libxext-dev xautomation xinput xserver-xorg-dev autoconf libtool pkg-config
```

---

### Post by Muy-burro on 2012-10-21
> Could you compress and attach the entire ouput of ./configure on your next post? The commands you are using included? I want to make sure I am not missing something.

What I have written above is all output displayed by the command ./configure --prefix=/usr

Just that: 
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: error: cannot run /bin/bash ./config.sub
```

No more.

> So the line we are using is?
```
sudo apt-get install build-essential xutils-dev xutils libx11-dev libxext-dev xautomation xinput xserver-xorg-dev autoconf libtool pkg-config
```
Yes, according to the README file that's all the dependencies, adding the packages you suggested.

> specifically but since it is happening with configure try adding to:
```
sudo apt-get install build-essential
```
these three:
```
sudo apt-get install build-essential autoconf libtool pkg-config
```
just to cover the bases.

---

### Post by Favux on 2012-10-21
Do you have automake installed?
```
sudo apt-get install automake
```

It worked for me so I can't see why it would need something like:
```
aclocal && automake && autoconf
```
We're not adding new files that need to be included in the build scripts after all.


Edit:  Another thought.  Are you running **make clean** between compile attempts?

---

### Post by Parker32 on 2012-10-22
Code:
cd Desktop

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)

apt-get source linux-image-$(uname -r) 
The dependencies can take a while to download. The kernel is about 94 MB and takes a few minutes to download depending on your connection. With Oneiric you'll see something like linux_3.0.0.orig.tar.gz, linux_3.0.0-16.29.dsc, linux_3.0.0-16.29.diff.gz, and linux-3.0.0. If the kernel source code doesn't download then you may need to check in Software Sources in the Ubuntu Software tab if you have the box in front of Source code checked.

To see the files you want to patch and then compile you can use Nautilus (Places) to go into the kernel's folder (e.g. linux-3.0.0) now on your Desktop and navigate to drivers/input/hid.

You'll apply the patch in the terminal using the following commands changing the folder name for Precise of course.

---

### Post by Muy-burro on 2012-10-22
> Do you have automake installed?
It was installed...

> Edit: Another thought. Are you running make clean between compile attempts?
I can not compile without being able execute the command ./Configure - prefix = / usr, since I can not run make without a makefile created by ./Configure - prefix = / usr.

Therefore I have not executed the command make clean. Do I have to do it without making a makefile, or used make?

aclocal && automake && autoconf show:
```
configure.ac:53: required file `./config.guess' not found
configure.ac:53:   `automake --add-missing' can install `config.guess'
configure.ac:53: required file `./config.sub' not found
configure.ac:53:   `automake --add-missing' can install `config.sub'
```

just that.

---

### Post by Favux on 2012-10-22
A lot of folks run **make clean** before they try another compile attempt as a matter of course.  To make sure nothing from a previous compile is clouding things.  I am nearly certain I ran **make clean** before my successful WizardPen compile.

What happens if you substitute for:
```
./configure --prefix=/usr
```
this line?
```
./autogen.sh --prefix=/usr
```

---

### Post by Muy-burro on 2012-10-22
make clean show:
```
make: *** No hay ninguna regla para construir el objetivo «clean».  Alto.
```
It say: No rule to make the target.

./autogen.sh --prefix=/usr show:
```
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if RANDR is defined... yes
checking if XINPUT is defined... yes
checking for XORG... yes
checking for ANSI C header files... (cached) yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking sysfs/libsysfs.h usability... no
checking sysfs/libsysfs.h presence... no
checking for sysfs/libsysfs.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating udev/Makefile
config.status: creating xorg/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
```
Process stops there.

Should I use now make && sudo make install?

---

### Post by Favux on 2012-10-22
Yes, please.

I think that might have done it.

---

### Post by Muy-burro on 2012-10-22
./configure --prefix=/usr show:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if RANDR is defined... yes
checking if XINPUT is defined... yes
checking for XORG... yes
checking for ANSI C header files... (cached) yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking sysfs/libsysfs.h usability... no
checking sysfs/libsysfs.h presence... no
checking for sysfs/libsysfs.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating udev/Makefile
config.status: creating xorg/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
```
make show:
```
make  all-recursive
make[1]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
Making all in src
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/src»
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
wizardpen.c:118:1: warning: initialization from incompatible pointer type [enabled by default]
wizardpen.c:118:1: warning: (near initialization for 'WIZARDPEN.default_options') [enabled by default]
mv -f .deps/wizardpen.Tpo .deps/wizardpen.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg    -I../src -module -avoid-version  -o wizardpen_drv.la -rpath /usr/lib/xorg/modules/input wizardpen.lo  
libtool: link: gcc -shared  -fPIC -DPIC  .libs/wizardpen.o    -O2   -Wl,-soname -Wl,wizardpen_drv.so -o .libs/wizardpen_drv.so
libtool: link: ( cd ".libs" && rm -f "wizardpen_drv.la" && ln -s "../wizardpen_drv.la" "wizardpen_drv.la" )
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/src»
Making all in man
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/man»
sed -e 's|__vendorversion__|"wizardpen 0.8.1" "X Version 11"|' -e 's|__xorgversion__|"wizardpen 0.8.1" "X Version 11"|' -e 's|__xservername__|Xorg|g' -e 's|__xconfigfile__|xorg.conf|g' -e 's|__projectroot__|/usr|g' -e 's|__appmansuffix__|1|g' -e 's|__drivermansuffix__|4|g' -e 's|__adminmansuffix__|8|g' -e 's|__miscmansuffix__|7|g' -e 's|__filemansuffix__|5|g' < wizardpen.man > wizardpen.4
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/man»
Making all in udev
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/udev»
make[2]: No se hace nada para «all».
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/udev»
Making all in xorg
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/xorg»
make[2]: No se hace nada para «all».
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/xorg»
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
gcc -DHAVE_CONFIG_H -I.     -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg    -I./src -MT wizardpen-calibrate.o -MD -MP -MF .deps/wizardpen-calibrate.Tpo -c -o wizardpen-calibrate.o `test -f 'calibrate/wizardpen-calibrate.c' || echo './'`calibrate/wizardpen-calibrate.c
mv -f .deps/wizardpen-calibrate.Tpo .deps/wizardpen-calibrate.Po
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg    -I./src   -o calibrate/wizardpen-calibrate wizardpen-calibrate.o  
libtool: link: gcc -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg -I./src -o calibrate/wizardpen-calibrate wizardpen-calibrate.o 
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
make[1]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
```
sudo make install show:
```
[sudo] password for usuario_lol: 
Making install in src
make[1]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/src»
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/src»
make[2]: No se hace nada para «install-exec-am».
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wizardpen_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wizardpen_drv.so /usr/lib/xorg/modules/input/wizardpen_drv.so
libtool: install: /usr/bin/install -c .libs/wizardpen_drv.lai /usr/lib/xorg/modules/input/wizardpen_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/lib/xorg/modules/input
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/xorg/modules/input

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/src»
make[1]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/src»
Making install in man
make[1]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/man»
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/man»
make[2]: No se hace nada para «install-exec-am».
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 wizardpen.4 '/usr/share/man/man4'
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/man»
make[1]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/man»
Making install in udev
make[1]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/udev»
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/udev»
make[2]: No se hace nada para «install-exec-am».
test -z "/etc/udev/rules.d" || /bin/mkdir -p "/etc/udev/rules.d"
 /usr/bin/install -c -m 644 67-xorg-wizardpen.rules '/etc/udev/rules.d'
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/udev»
make[1]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/udev»
Making install in xorg
make[1]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/xorg»
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/xorg»
make[2]: No se hace nada para «install-exec-am».
test -z "/usr/share/X11/xorg.conf.d" || /bin/mkdir -p "/usr/share/X11/xorg.conf.d"
 /usr/bin/install -c -m 644 70-wizardpen.conf '/usr/share/X11/xorg.conf.d'
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/xorg»
make[1]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1/xorg»
make[1]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
make[2]: se ingresa al directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c calibrate/wizardpen-calibrate '/usr/bin'
libtool: install: /usr/bin/install -c calibrate/wizardpen-calibrate /usr/bin/wizardpen-calibrate
make[2]: No se hace nada para «install-data-am».
make[2]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
make[1]: se sale del directorio «/home/usuario_lol/Escritorio/xserver-xorg-input-wizardpen-0.8.1»
```

I put a fake username in this to avoid problems, and I will restart. In a little while I tell you the results.

---

### Post by Muy-burro on 2012-10-22
LOL, WizardPen controller works. I am writing this in Cellwriter to test its functionality, but even acknowledges precise tolerance of the tip of the pen in MyPaint.

Thank you very much for the help and patience.

Here is the data provided by xinput_calibrator:
```
Calibrating standard Xorg driver "H850S"
        current calibration values: min_x=1600, max_x=30400 and min_y=1000, max_y=19000
        If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "H850S"
        Option  "MinX"  "1567"
        Option  "MaxX"  "30675"
        Option  "MinY"  "1058"
        Option  "MaxY"  "18964"
EndSection
```

---

### Post by Favux on 2012-10-22
Outstanding!  Nice work!  :)

[SIZE="3"][B]So we can get the WizardPen driver to compile in Precise and it works!!!
[/B][/SIZE]

Do the pen buttons work too?

Did you need a .conf file or other change to the configuration?

---

### Post by Muy-burro on 2012-10-23
Work with the settings you explained in a previous post
> Comment out (#) the contents of 70-wizardpen.conf:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
And modify the 52-tablet.conf:
```
gksudo gedit /etc/X11/xorg.conf.d/52-tablet.conf
```
to:
```
Section "InputClass"
    Identifier "UC-Logic H850S"
    MatchIsTablet "on"
    MatchProduct "H850S"
    MatchDevicePath "/dev/input/event*"
#    Driver "evdev"
#    Option "Calibration" "0 32000 0 20000"
    Driver "wizardpen"
```
EndSection

Of course this configuration is centered on the H85 Kanvus tablet, but the original configuration should work with other tablets like the Genius MousePen. And the pen buttons work perfectly, as the buttons of a mouse.

---

### Post by tastefuldeath on 2012-11-05
OMG thank you guys. People who make things work make Ubuntu the choice for me. :D My Genius EasyPen i405x is working perfectly :D

---

### Post by Stethea on 2012-11-17
Has anyone figure out how to get the tablet's button to work? I have a Digi Pro 640 (UC-LOGIC Tablet WP5540U) and the pen and it's buttons work automaticallly, but the preset buttons on the tablet don't. From what I've read it doesn't sound like there's been an answer to this.

---

### Post by Favux on 2012-11-17
Hi Stethea,

If you are talking about what are sometimes called the hotkeys or shortcut keys or whatever no they don't work.  There's usually a whole bunch of those things, right?  I have no idea how they are implemented.  A couple of folks have posted saying "hey I looked at them, no big deal to figure out".  Then they are never heard from again :(

If the tablet has actual frame or bezel buttons or a scroll wheel etc. then Nick enables them when he does a kernel driver for the tablet.

---

### Post by Stethea on 2012-11-17
Yeah.. well looking at it, [IMG]http://images.marketplaceadvisor.channeladvisor.com/hi/73/72897/digipro-640-un56.jpg[/IMG]
It doesn't seem like it would be too hard to implement. Just figure out the dimensions of each button and what function it should perform.... But being a noob, I don't know how to do any of that. So in reality it could be a lot more difficult than I think. I've been thinking of running the software cd that came with the tablet on a windows computer to see if it can give me some information about it, since I can't get it to run in Wine. If somehow I could figure it out I'll be sure to post back here.

---

### Post by Favux on 2012-11-17
Right.  That would be good.  What we need to know is what kind of signal do they send?  What would be handling that signal?

With bezel buttons or a scroll wheel it is a key signal, the kind of thing xev would pick up when you pressed the button with xev running.  A button press and release event.  Those signals naturally enough are handled like keyboard keys and when Nick is done with the kernel driver the evdev.conf file keyboard snippet in xorg.conf.d handles them.

---

### Post by Mediqiam on 2013-01-03
Hi again.
Does anyone know about the tablets working on Ubuntu 12.10? I'm still with 12.04, and thinking on updating.

Thanks.

---

### Post by Terraman on 2013-01-22
Hi,

I have been searching a lot to make my EasyPen i405x tablet to work, but on the first step, I can not see it in *lsusb* command.

```
herman@patricia-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b15c Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0458:5010 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 002: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]


```

How can I fix the problem to see the tablet in *lsusb*?

OS: Ubuntu 12.04; HW: Sony Vaio VPCW210AL.

Thanks in advance!

---

### Post by Favux on 2013-01-22
Hi Terraman,

This is your EasyPen:
```
Bus 002 Device 002: ID 0458:5010 KYE Systems Corp. (Mouse Systems)
```
That's why lsusb is so useful.  It tells you the OEM's name (Vendor ID 0458) and gives you the actual Product ID (5010).  For example:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

---

### Post by Terraman on 2013-01-22
> **Favux said:**
> Hi Terraman,

This is your EasyPen:
```
Bus 002 Device 002: ID 0458:5010 KYE Systems Corp. (Mouse Systems)
```
That's why lsusb is so useful.  It tells you the OEM's name (Vendor ID 0458) and gives you the actual Product ID (5010).  For example:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

Many thanks, Favux!

In the meantime, I have it figured out too!

---

### Post by Favux on 2013-01-22
Good!  :)

---

### Post by pandacakes on 2013-01-22
Hi, I'm quite new to Ubuntu and also just got a UC-Logic 5540U tablet.

It works when I plug it in without installing anything, but there are a couple issues I'm not sure of how to fix or if it needs the installs you wrote in this thread.

While hovering the pen over the tablet, it seems to register it as left-clicks, so while the cursor moves with the pen, text gets highlighted or images get dragged along with the movement. Also, touching the pen to the tablet doesn't do anything.

Do I need to go through the steps listed in the beginning of the thread? If so, I'm a little confused about it. On the first post it says to install the patched pre-compiled kernels and then the second post has extra instructions. Am I to install the pre-compiled kernels first and then go on to the second post? And I'm confused on how install those pre-compiled kernels since there are multiple downloads available and not sure what to do with them.

---

### Post by Favux on 2013-01-22
Hi pandacakes,

Welcome to Ubuntu forums!


Your UC-Logic 5540U tablet should work out of the box on any recent release.  What release of Ubuntu are you using?

Also let's establish the model for sure.  What is the output of the following command run in a terminal with the tablet plugged in?
```
lsusb
```

---

### Post by Terraman on 2013-01-22
> **Favux said:**
> Good!  :)

I have upgraded to Ubuntu 12.10 and it just works *out of the box*!

Thank you very much!

---

### Post by pandacakes on 2013-01-22
Hi Favux:

I'm using Ubuntu 12.04 and have all my updates.

lsusb says:
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 04f2:b35f Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U

---

### Post by Favux on 2013-01-22
Well according to the DIGImend project it should be working:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

The kernel driver should be good and the tablet should be on the evdev X driver and that should work.  What's the output of **xinput list** entered in a terminal?

---

### Post by pandacakes on 2013-01-22
xinput list:
> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                     id=10    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                     id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]

---

### Post by Favux on 2013-01-22
Let's look at the list-props output and see if it is on evdev.
```
xinput list-props 10
*and*
xinput list-props 11
```
One of those should be the pen.  You could also find out by looking in Xorg.0.log in /var/log.

---

### Post by pandacakes on 2013-01-23
For **xinput list-props 10**:
> Device 'UC-LOGIC Tablet WP5540U':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (256):    0
    Device Accel Constant Deceleration (257):    1.000000
    Device Accel Adaptive Deceleration (258):    1.000000
    Device Accel Velocity Scaling (259):    10.000000
    Device Product ID (249):    21827, 4
    Device Node (250):    "/dev/input/event7"
    Evdev Axis Inversion (260):    0, 0
    Evdev Axis Calibration (261):    <no items>
    Evdev Axes Swap (262):    0
    Axis Labels (263):    "Abs X" (253), "Abs Y" (254), "Abs Pressure" (255)
    Button Labels (264):    "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252), "Button Wheel Up" (138), "Button Wheel Down" (139), "Button Horiz Wheel Left" (140), "Button Horiz Wheel Right" (141)
    Evdev Middle Button Emulation (265):    0
    Evdev Middle Button Timeout (266):    50
    Evdev Third Button Emulation (267):    0
    Evdev Third Button Emulation Timeout (268):    1000
    Evdev Third Button Emulation Button (269):    3
    Evdev Third Button Emulation Threshold (270):    20
    Evdev Wheel Emulation (271):    0
    Evdev Wheel Emulation Axes (272):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (273):    10
    Evdev Wheel Emulation Timeout (274):    200
    Evdev Wheel Emulation Button (275):    4
    Evdev Drag Lock Buttons (276):    0And **xinput list-props 11**:
> Device 'UC-LOGIC Tablet WP5540U':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (256):    0
    Device Accel Constant Deceleration (257):    1.000000
    Device Accel Adaptive Deceleration (258):    1.000000
    Device Accel Velocity Scaling (259):    10.000000
    Device Product ID (249):    21827, 4
    Device Node (250):    "/dev/input/event8"
    Evdev Axis Inversion (260):    0, 0
    Evdev Axes Swap (262):    0
    Axis Labels (263):    "Rel X" (142), "Rel Y" (143), "Rel Vert Wheel" (277)
    Button Labels (264):    "Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139), "Button Horiz Wheel Left" (140), "Button Horiz Wheel Right" (141)
    Evdev Middle Button Emulation (265):    0
    Evdev Middle Button Timeout (266):    50
    Evdev Third Button Emulation (267):    0
    Evdev Third Button Emulation Timeout (268):    1000
    Evdev Third Button Emulation Button (269):    3
    Evdev Third Button Emulation Threshold (270):    20
    Evdev Wheel Emulation (271):    0
    Evdev Wheel Emulation Axes (272):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (273):    10
    Evdev Wheel Emulation Timeout (274):    200
    Evdev Wheel Emulation Button (275):    4
    Evdev Drag Lock Buttons (276):    0

---

### Post by Favux on 2013-01-23
Looks like the first event, ID #10, is the Pen, because it has a absolute axis.  If you enter **man evdev** in a terminal you'll get the evdev manual with the available options for it.

---

### Post by pandacakes on 2013-01-23
So, what exactly is making it register hover movements as left-clicks? And how do I fix it?

---

### Post by Favux on 2013-01-23
I'd say the more pressing problem is why doesn't touching the tablet with the stylus draw?  What app.s have you tried that in?

Everything looks like it is set up correctly.  I'm looking at the DIGImend site to see if there was anything about that in the last kernel patches update.
[http://sourceforge.net/projects/digimend/](http://sourceforge.net/projects/digimend/)
Not seeing anything relevant so far.

Can you test the tablet in Windows or OS X and confirm it works?  Rule out a hardware problem in other words.

---

### Post by pandacakes on 2013-01-23
It seems like it's having the same issues on a Windows PC. I even tried changing the settings available and it didn't fix anything. I'm guessing this means it's a hardware problem and I should exchange it for another one?

---

### Post by pandacakes on 2013-01-23
I also tried to use it in GIMP but it's not even registering the tablet as an input device.

---

### Post by Favux on 2013-01-23
Right, if it is not working in Windows then you could be looking at a hardware problem.  Windows said it recognized the tablet and had the drivers for it?  I'm guessing so because it had settings for you to change.

Basically it sounds like something is broken proximity wise.  So it could just be a stylus issue and not the tablet.

---

### Post by pandacakes on 2013-01-23
Yes, the tablet was recognized in Windows and drivers were installed for it. Could I possibly just get a new/different stylus for it?

---

### Post by Favux on 2013-01-23
Yes.  It would be nice if there was a store nearby that would let you test a new stylus.  Otherwise probably quicker to get a new tablet if it is still under warranty.

---

### Post by pandacakes on 2013-01-23
Oh, does GIMP not recognizing it as an input device mean anything?

---

### Post by pandacakes on 2013-01-25
So I got a new pen and it works now! So it really was the other pen that was giving me problems. Thank you, Favux, for helping me through this.

---

### Post by tamccullough on 2013-02-05
The patches for UC-logic tablets are also meant for the monoprice tablets correct?

Will any  of these patches into the next official release of ubuntu, or will we always need to patch the kernel?

If it won't make it in, why is that?

Is there a current distro that automatically patches the kernel?

---

### Post by Favux on 2013-02-05
Hi tamccullough,

Depends on what **lsusb** indicates is the tablet's actual OEM.  Lots of rebranding going on.

When a tablet's kernel driver is fixed it is submitted to the kernel.  When the kernel maintainers approve and commit the fix it will show up in the current kernel under development.  The Tablet Support status page tells you the kernel version you can expect support in:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

I doubt any Distro backports kernel modules for these tablets.

That's what the HOW TO is for.  The patches are backports of tablet support from newer kernels you can apply to older kernels yourself.

DIGI*mend* site:
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)
[http://sourceforge.net/projects/digimend/](http://sourceforge.net/projects/digimend/)

---

### Post by tamccullough on 2013-02-05
So, can I expect these kernel changes to be in place with the next Ubuntu release?

What is the turn around time for these kernels?


Using lsusb - my [monoprice 12x9 tablet]("http://www.monoprice.com/products/product.asp?c_id=108&cp_id=10841&cs_id=1084101&p_id=6815&seq=1&format=2")
is a rebranded UC-Logic Technology Corp. Tablet PF1209

The tablet works, but the pressure sensitivity is not recognized by Ubuntu 12.04 even though I have kernel 3.2.0-37-generic.

The guys developing MyPaint have made the pressure sensitivity work within the app itself though, so I am sure there is something I can do it remedy it.

I am very hesitant to try patching things on my own.  I ALWAYS break my OS.

---

### Post by wgac-ton on 2013-02-23
hello!.. I'm using Ubuntu 12.10 (3.2.0-31) and  I have created  /etc/X11/xorg.conf.d/52-genius-on-wacom.conf  whit the following  content:
Section "InputClass"
   Identifier "Kye class"
   MatchProduct "i608X"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   Driver "wacom"
EndSection
according to this topic:
[http://forum.kde.org/viewtopic.php?f=139&t=98347&start=30](http://forum.kde.org/viewtopic.php?f=139&t=98347&start=30)
 ..But I can not click  in anything .. I can only move the cursor.. [IMG]http://forum.kde.org/images/smilies/cry.gif[/IMG]  
any suggestions please?

---

### Post by wgac-ton on 2013-02-23
> **wgac-ton said:**
> hello!.. I'm using Ubuntu 12.10 (3.2.0-31) and  I have created  /etc/X11/xorg.conf.d/52-genius-on-wacom.conf  whit the following  content:
Section "InputClass"
   Identifier "Kye class"
   MatchProduct "i608X"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   Driver "wacom"
EndSection
according to this topic:
[http://forum.kde.org/viewtopic.php?f=139&t=98347&start=30](http://forum.kde.org/viewtopic.php?f=139&t=98347&start=30)
 ..But I can not click  in anything .. I can only move the cursor.. [IMG]http://forum.kde.org/images/smilies/cry.gif[/IMG]  
any suggestions please?

CONSEGUI! I just updated the kernel to the latest version 3.5.0-24.. voilá!

---

### Post by Favux on 2013-02-23
Hi wgac-ton,

Welcome to Ubuntu forums!


Congratulations on getting your Kye tablet working.  :)  As you no doubt discovered from DIGI*mend* wiki's [Tablet support status]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status") page the i608X is supported by the 3.4 kernel or later.  And once the kernel has Nick's fixes for the i608X then as Viktoria S. discovered Kye tablets will work on the Wacom X driver xf86-input-wacom.  And using the Wacom X driver gets you around the bug Qt has with the xf86-input-evdev X driver.  So the i608X will work in Krita etc.

---

### Post by wgac-ton on 2013-02-24
> **Favux said:**
> Hi wgac-ton,

Welcome to Ubuntu forums!


Congratulations on getting your Kye tablet working.  :)  As you no doubt discovered from DIGI*mend* wiki's [Tablet support status]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status") page the i608X is supported by the 3.4 kernel or later.  And once the kernel has Nick's fixes for the i608X then as Viktoria S. discovered Kye tablets will work on the Wacom X driver xf86-input-wacom.  And using the Wacom X driver gets you around the bug Qt has with the xf86-input-evdev X driver.  So the i608X will work in Krita etc.

Thank you Favux! my tablet is working perfectly! :)  including krita! (google translate)

---

### Post by alexljz on 2013-03-02
Hi, I just got a UC-Logic TWHA60 sold by Monoprice.

uname -a:
Linux hpee 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lsusb:
Bus 002 Device 007: ID 5543:0781 UC-Logic Technology Corp. 

xinput --list:
&#9116;   &#8627; HA60S                                   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; HA60S                                   	id=14	[slave  pointer  (2)]


I installed the following files from [http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-6/ubuntu_12.04_amd64/](http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-6/ubuntu_12.04_amd64/)
linux-headers-3.2.0-31_3.2.0-31.50+digimend.6.1_all.deb
linux-headers-3.2.0-31-generic-digimend_3.2.0-31.50+digimend.6.1_amd64.deb
linux-image-3.2.0-31-generic-digimend_3.2.0-31.50+digimend.6.1_amd64.deb

The tablet seems to be operational. When i hover the stylus over the tablet, a blue light appears. If i click the side of the button closer to the nib, my browser goes forward in history and if I touch the stylues to the tablet, the browser goes backwards.
However, it doesn't seem to track motion and nothing happens when I try moving the stylus or clicking buttons when I tried it with mypaint and with GIMP.

I would love some help, thanks!

---

### Post by tamccullough on 2013-03-02
Just last night, I did a clean install of Ubuntu 12.10, and have discovered to my surprise that I now have pressure sensitivity across all my painting programs and blender (with a modified .conf for Krita) with my monoprice 12x9.

The crazy thing is that it was only working with mypaint when I did a clean install a week ago.

A couple of differences this time, I am now using the release version of gimp (2.8.2) in the software centre and I am all using the default Nouveau display driver.

I am hesitant to update to the nvidia driver in the case it has been the cause of all my woes. Or upgrading the gimp.

I do think the gimp is bugged out. But could it change settings in some way that it would cause me to loose pressure sensitivity on other programs?

Or is more likely that the nvidia driver is the culprit? And if so what can I do about it?

I would like the ability to use cycles rendering in blender, but do not want to lose the ability to paint in it well.

---

### Post by Favux on 2013-03-17
@ alexljz,

Since the UC-Logic TWHA60 5543:0781 is supported in kernel >= 3.7 (Raring should support it out of the box) and patch set 6 it looks like you've done things correctly.  Installing:
```
linux-headers-3.2.0-31-generic-digimend_3.2.0-31.50+digimend.6.1_amd64.deb
linux-image-3.2.0-31-generic-digimend_3.2.0-31.50+digimend.6.1_amd64.deb
```
should provided tablet support as far as I can tell.  You are selecting the 3.2.0-31.50+digimend.6.1_amd64 kernel when booting, correct?  I am a little bothered by:
```
&#9116; &#8627; HA60S id=13 [slave pointer (2)]
```
in **xinput list**.  I'd hope after the usb descriptor was fixed the "device name" would be the standard "UC-LOGIC etc.".  Was there an error message when installing one of the deb.s?


@ tamccullough,

I'm assuming your UC-Logic Technology Corp. Tablet PF1209 returned 5543:0042 in **lsusb**?
> But could it change settings in some way that it would cause me to loose pressure sensitivity on other programs?
No, I don't think so.  Any Gimp settings should be internal to Gimp and not affect other programs.
> Or is more likely that the nvidia driver is the culprit?
While not impossible I doubt it.  I suspect more likely it was the change to the newer kernel or X Server in Raring that made the difference.  Although since the 0042 has allegedly been supported since kernel 2.6.36 I'm not quite sure how.
> I would like the ability to use cycles rendering in blender, but do not want to lose the ability to paint in it well. 
The pressure sensitivity bug in Blender has been fixed in Blender 2.66.
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Blender](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Blender)
[http://sourceforge.net/tracker/?func=detail&aid=3530625&group_id=233297&atid=1089171](http://sourceforge.net/tracker/?func=detail&aid=3530625&group_id=233297&atid=1089171)

---

### Post by Espionage724 on 2013-12-15
Hmm, I have a VisTablet PenPad. Under Ubuntu, it's detected as a "     WALTOP    Tablet    stylus" (something like that; basically a lot of spaces with that exact casing). 

lsusb says "Bus 003 Device 005: ID 172f:0037 Waltop Internation Corp.".

The tablet itself works for cursor movement and taps, but not as expected. Essentially, the cursor on the screen will always move to the next location. If I tap the left side of the tablet, lift the pen up so the tablet can't see it, then tap the right side of the tablet, the cursor on the screen will move from left to right. The expected behavior is for the cursor to teleport from left to right.

I believe this has happened since 12.04, up till 13.10 (haven't tried 14.04 dailies yet). Same occurs on variants too (Xubuntu, Kubuntu, Lubuntu). The same happens on openSUSE 13.1 also.

Strangely though, on SteamOS (released yesterday), the tablet appears to work fine (cursor teleports). It's using Debian  7as a base, but even a LiveCD of Debian still had improper handling of the tablet.

Any ideas as to how I can get the cursor movement to work as-expected?

I should also add that a Wacom Bamboo I tested worked fine on both openSUSE 13.1 and Ubuntu 13.10. Here's a video showing the behavior of both tablets: [https://www.youtube.com/watch?v=NJgLeTG-R5k](https://www.youtube.com/watch?v=NJgLeTG-R5k)

In that video, as the cursor moves in osu!, it leaves a cursor trail. When tapping the sides of both tablets, the cursor trail isn't existent on the Wacom tablet (good behavior). With the VisTablet however, you'll see the cursor trail (not good).

This is only problematic for me mainly in osu! (it basically feels like the cursor is lagging behind or something).

---

### Post by Espionage724 on 2013-12-19
Bump, I would really love to get this tablet working properly under Linux.

---

### Post by Espionage724 on 2013-12-20
Bump

---

### Post by Espionage724 on 2013-12-23
Bump

---

### Post by icanhardly on 2014-01-12
> **Espionage724 said:**
> Bump

It would have been nice of you to have reported your solution here instead of leaving hanging bumps

[http://ubuntuforums.org/showthread.php?t=2195691](http://ubuntuforums.org/showthread.php?t=2195691)

---

