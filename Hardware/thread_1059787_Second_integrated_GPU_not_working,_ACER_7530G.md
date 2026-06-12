---
title: "Second integrated GPU not working, ACER 7530G"
date: 2009-02-04
forum: Hardware
---

### Post by Valygard84 on 2009-02-04
Hello forum, 

for the last couple of weeks I've been trying to get the second integrated GPU in my Acer Aspire 7530G to work, without success.

The situation is as follows:

The laptop has two integrated GPUs, one for power saving, one for performance. It uses Hybrid SLI which normally switches between the two cards depending on current performance needs. 
In Ubuntu, I can only get the power saving one to work.

Relevant lspci output:
```
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9100M G (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
```

Currently, my Device section in xorg.conf looks like this:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID	   "PCI:2:0:0"
    Option	   "NoLogo" "true"
EndSection
```

Without using BusID "PCI:2:0:0", Gnome won't start at all - when using PCI:3:0:0, Gnome doesn't start (screen stays black) and the nvidia driver throws the following errors in xorg.0.log: (emphasis mine)
```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
[B](II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0[/B]
(II) NVIDIA(0): NVIDIA GPU GeForce 9300M GS (G98) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.98.3c.00.11
(II) NVIDIA(0): Detected PCI Express Link width: 1X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9300M GS at PCI:3:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[B](WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.[/B]
```
The complete xorg.0.conf log may be found here: [http://pastebin.com/m5ce0a1ee](http://pastebin.com/m5ce0a1ee) 
An xorg log of a successful boot with BusID PCI:2:0:0 may be found here: [http://pastebin.com/m15956a22](http://pastebin.com/m15956a22)
lspci -nn -vv of the 2 GPUS: [http://pastebin.com/m559c07c](http://pastebin.com/m559c07c)
Ubuntu 8.10, Kernel 2.6.27-11-generic

I already tried nVidia propertiary drivers 180.17 and 180.22 and most of the Ubuntu repository provided drivers (173,177,180). Same error.
After fiddling around with the drivers so much I did a completely fresh installation with Ubuntu provided 180, just to be safe.

I also tried exporting the EDID information with nvidia-settings and loading them manually within xorg.conf (with PCI:3:0:0 as BusID), no luck either.

The weird thing is that the nVidia driver adresses the LCD screen as CRT-0 with the 9300M GS but as DFP-0 with the (working) 9100M G.

To be clear, I don't want to get HybridSLI itself to work, I just need to get the faster of the two GPUs working so I can do some gaming on Ubuntu. ;)

I would greatly appreciate any help or pointers.

---

### Post by Valygard84 on 2009-02-08
*bump*
I would really appreciate ANY help... even if it's just some things I could try. :)

---

### Post by creative blank on 2009-04-04
Having the exact same problem with 2 GeForce 6800 GTs and a Samsung SyncMaster 712N.

---

### Post by norwoods on 2009-04-04
nvidia has an extensive README file for each driver version.  google nvidia README version.number(nvidia README 180.44) it find the correct README file and look for information related to sli in the README file.

---

### Post by avilella on 2009-04-05
If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

   1. Linux and Sony Vaio Z-series (intel/nvidia)
   2. Linux and Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
   3. Linux and BenQ Joybook S42 (intel/nvidia)
   4. Linux and ASUS N10J (intel/nvidia)
   5. Linux and Dell Studio XPS 13 (nvidia/nvidia)
   6. Linux and ASUS Intros G71Gx (?/nvidia GeForce 260M)
   7. Linux and MSI GT628 (?/nvidia GeForce 160M)
   8. Linux and LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
   9. HP HDX 18t (?/nvidia GeForce GT 130M)
  10. Linux and Dell XPS M1730 (nvidia/nvidia)
  11. Linux and MSI EX630 (nvidia/nvidia)
  12. Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
  13. Acer Aspire 7530 (nvidia/nvidia -- 9100m + ?)
  14. Linux and Lenovo ThinkPad T500 (intel/ati)
  15. Linux and Lenovo ThinkPad T400 (intel/ati)
  16. Linux and ASUS M51Ta (intel/ati)
  17. Linux and Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
  18. Linux and MSI PX211 12'' (intel/ati)
  19. Linux and HP Pavilion tx2500 (intel/ati)


DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time.

If you've got a laptop with a IGP and a hybrid Nvidia or ATi card, and you have tried to use Linux on it, you may have noticed that there are issues with the hybrid graphics setup. To help improve the Linux hybrid graphics support for this laptop, please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

### Post by Valygard84 on 2009-04-05
Writing a quick bug report now.

---

### Post by jezjones on 2009-07-02
There seem to be a number of entries on that bug for Dell XPS studio 13, which i have so is there any use adding to that list.

Also given that the bug was opened 6 months ago and mentions that hybrid graphics / multiple graphics cards have been around for some time, how long are we going to be waiting for a fix for this?

The reason i ask this, is that the powerful graphics card in this Dell is sitting useless and the money spent on decent laptop is wasted.

Is linux really only suitable for old machines like detractors say or is this situation of catch up likely to ever change.

I bought another modern laptop a couple of years ago, waited a year for linux to catch and it never did, so got a mac. Now going back to linux and waiting for a driver for a core feature, again.

If manufacturers such as Nvidia and ATI don't get involved then linux on laptops / desktops can never hope to be anything like osx or vista.

I would even pay for a binary driver from Nvidia, if it meant my laptop was not sitting useless (well visually).

[end rant about regression in functionality]

---

### Post by Lokiii on 2009-08-16
> **jezjones said:**
> There seem to be a number of entries on that bug for Dell XPS studio 13, which i have so is there any use adding to that list.

Also given that the bug was opened 6 months ago and mentions that hybrid graphics / multiple graphics cards have been around for some time, how long are we going to be waiting for a fix for this?

The reason i ask this, is that the powerful graphics card in this Dell is sitting useless and the money spent on decent laptop is wasted.

Is linux really only suitable for old machines like detractors say or is this situation of catch up likely to ever change.

I bought another modern laptop a couple of years ago, waited a year for linux to catch and it never did, so got a mac. Now going back to linux and waiting for a driver for a core feature, again.

If manufacturers such as Nvidia and ATI don't get involved then linux on laptops / desktops can never hope to be anything like osx or vista.

I would even pay for a binary driver from Nvidia, if it meant my laptop was not sitting useless (well visually).

[end rant about regression in functionality]


Hi mate, I saw that you have the Studio XPS 13 laptop as well. I am also struggeling on getting Hybrid-SLI working but it seems we are on the oposite end of the problem and maybe you could help me out a bit?

Now, my problem is that Ubuntu 9.04 uses, if not both, then at least the 9400m card, killing the battery life. 

What I want is to run on the 9200m card only, while you seem to want to run on the 9400m card? Does that mean that you have somehow managed to disable the 9400m card in Linux?

Please get back to me ASAP as I really need to sort this issue out. 

Thanks!

---

