---
title: "Mounting USB Mass Storage exposed by Windows CE handheld device"
date: 2011-06-16
forum: Hardware
---

### Post by SwordAngel on 2011-06-16
Hello,

I am trying to connect a Windows CE handheld device to my Xubuntu (Natty) box and mount the USB Mass Storage exposed by the former. I have explicitly set the USB mode on the Windows CE device to "Mass Storage" instead of "ActiveSync". Windows desktops have no problem recognizing the Mass Storage, but my Xubuntu box seems to have difficulties.

I have attached the output of dmesg.

Note that even though dmesg mentions sdb, I don't actually see an sdb device file in /dev/. I don't see a new device file in /dev/disk/by-id, /dev/disk/by-path, or /dev/disk/by-uuid. I also don't see a new block device in /dev/block.

If I execute lsusb, I see one relevant line:
```
Bus 003 Device 009: ID 05e0:3000 Symbol Technologies 

```

(The device in question is a Symbol/Motorola MC3090 handheld terminal, the kind used by retailer chains to do inventory and warehousing)

I suspect this problem is not confined to Xubuntu, so I have prefixed the thread as [all variants]

**EDIT**: I finally got the USB Mass Storage to mount. It looks like sdb and sdb1 disappeared when the handheld device went to sleep without my knowledge. But there is a second, more challenging part to my problem:

Now that I can manually mount the mass storage, is there a way to configure the system such that non-root users are allowed to mount any number of mass storage instances **of the same hardware model or vendor only**? Normally, if I plug in more than one usb mass storage devices, they would appear as /dev/sdb, /dev/sdc, /dev/sdd, etc. It wouldn't make sense to just add all of /dev/sdb, /dev/sdc, /dev/sdd, etc. to fstab because the USB mass storage could be of any model. I'm asking this because, ultimately, the handheld device will be used at the shops of a retailer chain and I want to make it harder for someone to just plug in any USB flash drive and steal data, while still allowing the handheld device to exchange data with the Linux-powered POS.

---

### Post by adzy1981 on 2011-06-21
May i ask how you explicitly set the USB mode on thw windows ce device to USB mass storage mode.
 
I have looked here:
 
[http://nicolasbesson.blogspot.com/2009/11/usb-function-profile-switcher.html](http://nicolasbesson.blogspot.com/2009/11/usb-function-profile-switcher.html)
 
But I cannot find those registry values on my Windows Ce device. Im running a Motorola MC3090 with Windows CE 5.0 and I'm trying to force the device to connect as a USB MASS storage device when it connects to a Windows PC / VISTA / WIN 7
 
I have tried numerous software tools without any luck.
 
Surley it cannot be difficult to change its mode?
 
Any guidance / registry code / software would be greatly appreciated
 
- Adam

---

### Post by SwordAngel on 2011-06-21
> **adzy1981 said:**
> May i ask how you explicitly set the USB mode on thw windows ce device to USB mass storage mode.
 
I have looked here:
 
[http://nicolasbesson.blogspot.com/2009/11/usb-function-profile-switcher.html](http://nicolasbesson.blogspot.com/2009/11/usb-function-profile-switcher.html)
 
But I cannot find those registry values on my Windows Ce device. Im running a Motorola MC3090 with Windows CE 5.0 and I'm trying to force the device to connect as a USB MASS storage device when it connects to a Windows PC / VISTA / WIN 7
 
I have tried numerous software tools without any luck.
 
Surley it cannot be difficult to change its mode?
 
Any guidance / registry code / software would be greatly appreciated
 
- Adam

You shouldn't have to mess with the registry manually.

The MC3090 I have on hand is running Windows CE 5 Professional, but I imagine that it shouldn't be all that different among the WinCE/WinMo versions that Motorola supports. If you open the Start menu --> Settings --> Control Panel, there should be an item called "USBConfig". That's where I set the USB mode to USB Mass Storage.

I hope this helps.

---

### Post by adzy1981 on 2011-06-22
Yeah, it is in Control Panel / PC Connection for me and I have it set to "USB Default".
 
The only problem I have is that I cannot directly access or referece the memory card in the MC3090 in windows Vista / 7 without going to windows explorer / my computer / and then to "Portable devices" and selecting the MC3090 from there.
 
I am trying to have the MC3090 Mount its Storage Card as a drive letter for use in Windows and also through Citrix when the user plugs it nto its base station (connected to PC via USB cable).
 
Does anybody know if this is possible (without activsync)?
 
(My goal is to connect the MC3090 to the base station and have it connect to a PC which is running a database via Citrix, and in this database the user selects the Portable devices memeory card and import files / data.)
 
I cannot do this at present as Citrix doesn't recognise Portable devices, but it DOES recognise "USB MASS STORAGE" devices (i.e - memory cards)
 
I have tried softick card export II, but it won't install onto a win ce 5.0 or 6.0 device (unless someone knows how). I have also tried HDD.cab (USBTOOLS) and WM5torage... all without any luck.

---

### Post by SwordAngel on 2011-06-22
> **adzy1981 said:**
> Yeah, it is in Control Panel / PC Connection for me and I have it set to "USB Default".

No no. "PC Connection" is a *completely separate* module. There should be a module called "USBConfig".

---

### Post by adzy1981 on 2011-06-22
Oh dear.... well it seems I am missing some files or options in my MC3090. Do you know if this USBConfig is something I can install to the device / downloadable?
 
I might have been pulling my hair out for nothing !!

---

### Post by SwordAngel on 2011-06-22
> **adzy1981 said:**
> Oh dear.... well it seems I am missing some files or options in my MC3090. Do you know if this USBConfig is something I can install to the device / downloadable?
 
I might have been pulling my hair out for nothing !!

I can think of a few possible causes as to why you don't have the USBConfig applet in Control Panel, and the proper solution may depend on the cause:
[LIST=1]
[*]Somebody removed the USBConfig applet in Platform Builder, when preparing a platform image for your device. In this case, you should ask the original person who prepared the platform image to put the USBConfig applet back.
[*]Somebody removed the USBConfig applet from the Control Panel after the device is booted. In this case, back up your data and applications, then a cold reset should bring back that applet. Now restore the data and applications.
[*]USBConfig was never included in your flavour of Windows CE 5.0. There are two flavours: "Core" and "Professional". I am told that my device is running the "Professional" flavour; I don't know whether the "Core" flavour ever came with USBConfig and I don't know what flavour of Windows CE 5.0 is on your device.
[/LIST]

**Disclaimer**: you really need to know what you are doing if you decide to cold reset or modify the platform image. Don't hold me responsible if anything bad happens. If you got this device as part of a system solution from a Motorola redistributor/partner, you should really ask them. ;-)

---

### Post by adzy1981 on 2011-06-22
Thank you very much for the info and assistance. I'll ask the guys who supplied us with the devices.

---

### Post by adzy1981 on 2011-06-25
Hi again Sword angel,
 
I have d/loaded a 120 day eval version of platform builder, using the Microsoft website I have located some update files for windows ce 5.0 pro - Rollup 2010 for ARMV4I as well as Jan 2011, Feb 2011, Mar 2011, Apr 2011 and May 2011 update files (they are all MSI files).
 
I don't want to perform this update unless i'm sure i'm not going to render the device useless, so I'm just going to ask.....
 
 
If I attempt to update WinCE5.0 Pro on my MC3090 will I loose the BSP from Motorola and all the current drivers etc that enable my scanner to work. I do not have the build support package from motorola and they are of course requesting I pay more $$ for this to be sent to me.
 
Or, if I attempt to update WinCE5.0 Pro , is it just like updating your regular home version of windows - where it only really touches the core operating system files and nothing else.
 
I am worried if I conduct an update of WinCE5.0 Pro in an attempt to re-enable or re-install the usbtool for the control panel, that I will loose my ability to scan barcodes etc.
 
The package that was installed on my scanner is very very basic and there are no programs that are needed (as I can re-install my custom built VisualCE database).

---

### Post by SwordAngel on 2011-06-25
> **adzy1981 said:**
> Hi again Sword angel,
 
I have d/loaded a 120 day eval version of platform builder, using the Microsoft website I have located some update files for windows ce 5.0 pro - Rollup 2010 for ARMV4I as well as Jan 2011, Feb 2011, Mar 2011, Apr 2011 and May 2011 update files (they are all MSI files).
 
I don't want to perform this update unless i'm sure i'm not going to render the device useless, so I'm just going to ask.....
 
 
If I attempt to update WinCE5.0 Pro on my MC3090 will I loose the BSP from Motorola and all the current drivers etc that enable my scanner to work. I do not have the build support package from motorola and they are of course requesting I pay more $$ for this to be sent to me.
 
Or, if I attempt to update WinCE5.0 Pro , is it just like updating your regular home version of windows - where it only really touches the core operating system files and nothing else.
 
I am worried if I conduct an update of WinCE5.0 Pro in an attempt to re-enable or re-install the usbtool for the control panel, that I will loose my ability to scan barcodes etc.
 
The package that was installed on my scanner is very very basic and there are no programs that are needed (as I can re-install my custom built VisualCE database).

You cannot update/upgrade the platform image "in-place" (i.e. changing bits and pieces directly in the device's flash storage). Instead, you need to prepare a new image using the platform builder on the desktop, and completely overwrite what is in the device's flash storage. Therefore, you really need the BSP from Motorola.

---

