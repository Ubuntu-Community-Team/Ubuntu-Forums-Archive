---
title: "Lenovo Ideapad S10-3t"
date: 2010-02-25
forum: Hardware
---

### Post by manthony121 on 2010-02-25
I am looking at the new Lenovo touchscreen laptop, S10-3t.  It comes with Win7, which I would like to replace with Linux, preferably Ubuntu.  Does anyone have any experience with this device?

---

### Post by DeeMenace on 2010-02-25
My daughter has this computer and she also wants to run Ubuntu. I tried to install it through Wubi with no luck. Windows 7 doesn't like the wubi installer at all. On reboot into ubuntu I got an all black screen then after powering down and rebooting again I couldn't boot into ubuntu at all it would just dump me to a grub prompt. I haven't tried Usb stick yet that will be my next attempt. But I really do like this netbook and am interested to see how multi-touch works in Ubuntu (or if it works at all :) ) it's actually not that bad running win 7 but i know i'm gonna hate it once i have to renew all the crap that came with it lol .

---

### Post by manthony121 on 2010-02-25
Thanks for the info.  I see that the S10-3t does not have a CD-ROM, which would mean booting Ubuntu from USB or PXE, and avoid booting Win7 altogether.  Have you tried that?

---

### Post by bit_junkie on 2010-02-26
I bought this laptop 2 weeks ago, while it is a great machine under win7, ubuntu is still a little lacking.
Touchscreen does not work at all, I have tried everything I could think of and everything i could find through google.
Built in wireless card does not work either, I had to dig out my usb dongle to get online, although the hardline connection works just fine.

Now if you dont mind having to use an extra wireless card and not being able to use the touch screen it works perfectly fine under ubuntu :)

---

### Post by thevillage88 on 2010-02-26
I have the S10-3t and also would like to install Linux on it.  I have tried Karmic Koala standard and Netbook Remix versions by using an SD card with UNetbootin.

It boots fine and everything seems to work except the wifi and the touchscreen, which happens to be pretty much the whole point of this netbook.

Lenovo has provided little to no documentation on this machine and windows 7's Device Manager is essentially useless as per usual. The wifi card is a Broadcom 4313 and as Broadcom is not exactly Open Source Friendly, this will be a bit of a challenge, but not too entirely difficult.

There are a couple solutions to getting wifi working.  One is to use the drivers provided by Broadcom.  You can download the source at [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php").  According to the readme file Ubuntu already has these drivers precompiled in their repos.

Another possibility is to use ndiswrapper.   Although ndiswrapper is present, some other things need to be set up to get it working.  The instructions to do that are at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  

Since the only drivers that Lenovo provides for this netbook are for windows 7, you are going to have to look elsewhere for drivers.  I have found windows xp drivers for the Compaq Mini at [http://www.userdrivers.com/Notebook-Tablet-PC/Compaq-Mini-CQ10-PC-Broadcom-Wireless-LAN-Driver-5-60-18-41-for-Windows-XP/download/]("http://www.userdrivers.com/Notebook-Tablet-PC/Compaq-Mini-CQ10-PC-Broadcom-Wireless-LAN-Driver-5-60-18-41-for-Windows-XP/download/") which may or may not work.  I haven't tried it yet.

As far as the touch screen goes, windows 7's Device Manager lists this as "HID-compliant device" and uses the driver file "c:\windows\system32\DRIVERS\ApsHM86.sys."  I'm yet to find an actual name of the device or the manufacturer.  This may be a stretch, but could it be possible to extrapolate the drivers from the already functional "Quick Start?"

Anyway, I'm going to continue trying to get this thing working, and update if I make any significant progress.

---

### Post by bit_junkie on 2010-02-26
> **thevillage88 said:**
> I have the S10-3t and also would like to install Linux on it.  I have tried Karmic Koala standard and Netbook Remix versions by using an SD card with UNetbootin.

It boots fine and everything seems to work except the wifi and the touchscreen, which happens to be pretty much the whole point of this netbook.

Lenovo has provided little to no documentation on this machine and windows 7's Device Manager is essentially useless as per usual. The wifi card is a Broadcom 4313 and as Broadcom is not exactly Open Source Friendly, this will be a bit of a challenge, but not too entirely difficult.

There are a couple solutions to getting wifi working.  One is to use the drivers provided by Broadcom.  You can download the source at [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php").  According to the readme file Ubuntu already has these drivers precompiled in their repos.

Another possibility is to use ndiswrapper.   Although ndiswrapper is present, some other things need to be set up to get it working.  The instructions to do that are at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  

Since the only drivers that Lenovo provides for this netbook are for windows 7, you are going to have to look elsewhere for drivers.  I have found windows xp drivers for the Compaq Mini at [http://www.userdrivers.com/Notebook-Tablet-PC/Compaq-Mini-CQ10-PC-Broadcom-Wireless-LAN-Driver-5-60-18-41-for-Windows-XP/download/]("http://www.userdrivers.com/Notebook-Tablet-PC/Compaq-Mini-CQ10-PC-Broadcom-Wireless-LAN-Driver-5-60-18-41-for-Windows-XP/download/") which may or may not work.  I haven't tried it yet.

As far as the touch screen goes, windows 7's Device Manager lists this as "HID-compliant device" and uses the driver file "c:\windows\system32\DRIVERS\ApsHM86.sys."  I'm yet to find an actual name of the device or the manufacturer.  This may be a stretch, but could it be possible to extrapolate the drivers from the already functional "Quick Start?"

Anyway, I'm going to continue trying to get this thing working, and update if I make any significant progress.

I tried using ndiswrapper, it would install the windows driver, but then it would complain about not being able to see the hardware. At first I thought the toggle switch on the side of the netbook was turned off, but that wasn't the case. I will try the link for the drivers you posted, maybe I will have better luck with those.

From what I have been able to determine about the touch screen, it seems it is made by a Korean manufacturer [www.digitechsys.co.kr](www.digitechsys.co.kr) they have an english site, but it is still mostly in Korean, and I have not found any drivers on their site, you might have better luck than I did :)

I would really like to see the touch screen work, as the UNR interface just screams for a touch screen, the wireless I can live with having to use my usb dongle for now if I can not get the built in card to work.

---

### Post by thevillage88 on 2010-02-26
Yep.  NDIS 6 drivers don't work with ndiswrapper, so the drivers Lenovo included in the second partition are useless.  I have since tried the Compaq drivers and they do work!  I got the same message about hardware not being found, but when I clicked on the NetworkManager icon 6 access points appeared in the menu.

I was able to connect for about a half hour before it stopped working.  I may have caused my router to block me when I hit the home button in Firefox like 20 times.:oops:  Because the other APs are still visible in NM, I don't think it's an issue with ndiswrapper.

---

### Post by bit_junkie on 2010-02-26
> **thevillage88 said:**
> Yep.  NDIS 6 drivers don't work with ndiswrapper, so the drivers Lenovo included in the second partition are useless.  I have since tried the Compaq drivers and they do work!  I got the same message about hardware not being found, but when I clicked on the NetworkManager icon 6 access points appeared in the menu.

I was able to connect for about a half hour before it stopped working.  I may have caused my router to block me when I hit the home button in Firefox like 20 times.:oops:  Because the other APs are still visible in NM, I don't think it's an issue with ndiswrapper.

No I think its an issue with the driver, It doesn't stay connected to encrypted networks, at least thats been the case for me. It connected after the install but I needed to reboot to do something in windows and when I logged back in, it wouldn't connect at all. I tried connecting to one of the open routers around me here and it connected just fine, no problems at all. I'm running WPA2 on my router, its a linksys with the tomato firmware installed.

---

### Post by manthony121 on 2010-02-27
Regarding the wifi, Broadcomm has a linux driver for the chipset on their support page.  Does this driver not work?  According to the Lenovo forum, the wifi uses the Broadcomm BCM4313 11 b/g/n chipset.

---

### Post by DeeMenace on 2010-02-27
Has anyone tried 10.04 alpha 2 ? I recently got a new laptop and 10.04 was the only version of ubuntu i could get to work. I know it's just and alpha and not meant for work computers, but my guess is not many are using this computer for work lol. Anyway i'll probably give 10.04 a shot this weekend. Unless someone has already tried it and can verify that it doesn't work.

---

### Post by thevillage88 on 2010-02-27
> **manthony121 said:**
> Regarding the wifi, Broadcomm has a linux driver for the chipset on their support page.  Does this driver not work?  According to the Lenovo forum, the wifi uses the Broadcomm BCM4313 11 b/g/n chipset.

These drivers will likely work fine.  The only thing is, that they need to be compiled from source, which from my own experiences typically lands me in dependency hell.:twisted:  Although Ubuntu's Software Center has added Source Code to the list of software sources, indicating that the necessary development tools are probably present.

Currently, ndiswrapper is mostly working for me, so I've shifted my focus to getting the touch screen working.  Since Quick Start already has a working touch screen driver, it seems logical to try using existing drivers.

By the way, the S10-3t's that were released last month did not have Quick Start 2.0 installed as advertised.  However, Quick Start 2.0 has been released and can be downloaded at [http://consumersupport.lenovo.com/au/en/driversdownloads/Drivers_Show_2578.html]("http://consumersupport.lenovo.com/au/en/driversdownloads/Drivers_Show_2578.html").  I've tried it, and the wifi drivers are now working just fine.

Anyway, I've located the xorg.conf file for Quick Start, and this is what it says:

Section "InputDevice"
    Identifier "Cando Touch Panel"
    Driver     "evdev"
    Option     "Device"			"/dev/input/touchscreen"
    Option     "ReopenAttempts"  "81"
EndSection

So it appears that Quick Start is using a multi-touch mouse driver for the touch screen.  I've checked /dev/input for the touchscreen device, and it is absent in Ubuntu, so it's not as simple as just plugging it into xorg.conf.  Wouldn't that be nice.

Quick Start's filesystem is contained in four squashfs files.  Since the newer version of squashfs will not mount older versions of sqx files, we have to instead, extract them to the hard drive.  Here's what I did:

- I made sure the universe and multiverse repositories were enabled in Software Manager.  Just in case.

$ sudo apt-get install squashfs-tools

$ unsquashfs -d ~/Desktop/qstart /media/*c drive*/QSTART.SYS/bs-persist.sqx

$ unsquashfs -d ~/Desktop/qstart /media/*c drive*/QSTART.SYS/bs-xorg-1.6.0.sqx

$ unsquashfs -d ~/Desktop/qstart /media/*c drive*/QSTART.SYS/va-FF-3.0.sqx

$ unsquashfs -d ~/Desktop/qstart /media/*c drive*/QSTART.SYS/va-pack-LVSPCS20.sqx

Somewhere, hidden in these files, is our answer to getting the touch screen working.  I'm going to continue looking, but if one of you figures it out that's great.  I can use all the help I can get.

---

### Post by mtate5000 on 2010-02-27
I really have my heart set on this ideapad, but before i purchase anything, i would really love to hear of some good luck with these driver issues. I've been using karmic with netbook-laucher as a desktop shell for some time now. It was just to try out for a little while, but i managed to fall in love with the interface. I agree that it does indeed scream for a touch screen. Has anybody gotten the netbook interface to work any sort of touchscreen devise? I will keep searching for a solution.

---

### Post by thevillage88 on 2010-02-28
> **mtate5000 said:**
> I really have my heart set on this ideapad, but before i purchase anything, i would really love to hear of some good luck with these driver issues. I've been using karmic with netbook-laucher as a desktop shell for some time now. It was just to try out for a little while, but i managed to fall in love with the interface. I agree that it does indeed scream for a touch screen. Has anybody gotten the netbook interface to work any sort of touchscreen devise? I will keep searching for a solution.

Don't let the lack of hardware support be a deterrent from buying the S10-3t.  This is a really great netbook.  And Ubuntu runs incredibly fast on it.  This netbook  has only been available for a little less than two months, so there is no surprise that some things don't work.

In this case, the only things that don't "just work" out of the box are the wifi and touch screen.  We've already discussed that there are two methods to installing the wifi drivers.  I can tell you that the wifi is working, because I'm currently using it to send this message.  That just leaves the touch screen.

Quick Start is a custom version of Linux for Lenovo products.  The touch screen driver is working fine in QS, so it's only a matter of time before we figure out how to get it working in Ubuntu.  Go ahead and buy your computer, it will be ready for Linux in no time.

---

### Post by thevillage88 on 2010-02-28
Sorry to double post, but I have found the device in Ubuntu, and it appears to be working!  Sort of.](*,)

It seems that the touch screen is located at /dev/usb/hiddev0.  You can demonstrate this to yourself by opening a terminal window and typing:

$ sudo cat /dev/usb/hiddev0

You will notice that when you touch the screen, some garbage will begin to appear in the terminal window.  This is a very good sign!

Now it comes down to loading he evdev driver in xorg.conf and figuring out what the calibration values need to be.](*,) again.

---

### Post by manthony121 on 2010-02-28
Looking at the "Splashtop" website ([www.splashtop.com](www.splashtop.com)), where splashtop seems to be the same as "Quickstart", which is a pre-loaded Linux OS (in BIOS?  On disk?), it indicates that the touchscreen works perfectly.  Thevillage88 confirms that the touchscreen works under QS.  Ergo, there is a linux driver that is working just fine.  That is very good news.  I have sent an email to Lenovo asking if they could provide any info about the driver, but I'm not holding my breath.

I think I will go ahead and order a S10-3t and join the struggle to get the driver out into the open where it can be used with Ubuntu instead of Win7.

---

### Post by kayrozen on 2010-03-01
> **manthony121 said:**
> Looking at the "Splashtop" website ([www.splashtop.com]("http://www.splashtop.com")), where splashtop seems to be the same as "Quickstart", which is a pre-loaded Linux OS (in BIOS?  On disk?), it indicates that the touchscreen works perfectly.  Thevillage88 confirms that the touchscreen works under QS.  Ergo, there is a linux driver that is working just fine.  That is very good news.  I have sent an email to Lenovo asking if they could provide any info about the driver, but I'm not holding my breath.

I think I will go ahead and order a S10-3t and join the struggle to get the driver out into the open where it can be used with Ubuntu instead of Win7.

There's an opensource section with sourcecode. 

[http://www.splashtop.com/open_source.php](http://www.splashtop.com/open_source.php)

Hope this will helps you out. I would like to have fully supported s10-3t in ubuntu.

---

### Post by manthony121 on 2010-03-02
That is excellent.  I am not a master programmer by any means, but I do have a passing knowledge of C and C++.  I am downloading the source file (616 MB), and I'll have a look-see.  Perhaps the driver code is in there that *somebody* (not me) might be able to use to get complete functionality of the 10-3t touchscreen under Linux!

---

### Post by Roman Shuvalov on 2010-03-03
I'm going to buy netbook with touchscreen. Candidates are Asus EEEpc T91 and this Lenovo S10-3t. Looks like Lenovo is better but problems with touchscreen driver is bad news. 

I can't download 616 MB of QS source code, manthony121, maybe you can send me index of archive? unpack it into any folder, open terminal and write:
```
 tree NameOfFolder > ~/file_list.txt 
```List of all files will be saved in file_list.txt in your home directory so you can send it to me (romanshuvalov {at} gmail dot com). When I'll see this list I will ask you to send me some files that will help me to compile the driver. 

I'm not professional programmer but I will try to do it. My choice between Asus and Lenovo depends on success of getting this touchscreen driver :)

P.S. what is touchscreen brand name? lsusb

P.P.S. vote for getting touchscreen driver [**here**](http://splashtop.uservoice.com/forums/23135-lenovo/suggestions/520231-lenovo-s10-t3-touchscreen-linux-driver-?ref=title)

---

### Post by kayrozen on 2010-03-03
If this helps the panel is a CANDO Touch panel 

[http://consumersupport.lenovo.com/au/en/driversdownloads/Drivers_Show_2422.html](http://consumersupport.lenovo.com/au/en/driversdownloads/Drivers_Show_2422.html)

---

### Post by Roman Shuvalov on 2010-03-03
I've just send 2 letters to CANDO (by email and by form in their site) about linux driver. Linux driver EXISTS so I hope Cando help us to get it.

---

### Post by thevillage88 on 2010-03-03
Here is the output for lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2087:0a01  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 5986:0190 Acer, Inc

This is the output of lshal | grep hiddev0

  hiddev.device = '/dev/usb/hiddev0'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/usb/hiddev0'  (string)

I also want to warn those who have actually installed Ubuntu on their drives that when I updated my packages in synaptic, Something went wrong and the screen goes blank when gdm brings up the login screen.  You'll have to deselect any xserver-xorg-* packages until they work out the problem with the new xorg drivers, or you'll end up having to use the vesa driver instead.

---

### Post by thevillage88 on 2010-03-03
Romanv Shuvalov:  Here is the file you were asking for.  NM attachments not working for me.  Sent to your e-mail

---

### Post by Roman Shuvalov on 2010-03-03
By the way, what about 3G-modem? Driver exists and works? and I read that netbook has GPS optionally... what about GPS?

---

### Post by thevillage88 on 2010-03-03
> **Roman Shuvalov said:**
> By the way, what about 3G-modem? Driver exists and works? and I read that netbook has GPS optionally... what about GPS?

The most common version that is shipping is the S10-3t 0651.  The optional 4G Wimax card is not included.  There is not any 3G card or GPS that I am aware of either, although there is a place behind the battery for sim cards.

When you open the expansion bay you are given access to one ram slot, the hard drive and two PCI-E slots.  One for the Wifi and the other presumably for the Wimax card.

So when it comes to driver support for these devices, we're going to have to wait for these "optional" versions of the S10-3t to surface.  Or "optionally," you can purchase a PCI-E card of your choice for the additional slot.

When it comes to your choice between the S10-3t or the T91, the T91 is only 1.33GHz, has a 9in resistive(blech) touch screen, and has a small 16GB SSD hard drive.  It's worth the extra $50 to get the S10-3t.

I will reiterate that Quick Start is using evdev, a standard HID driver for the S10-3t's touch screen.  It's just a matter of time before it's up and running.

---

### Post by kayrozen on 2010-03-03
There are some infos on using multitouch on linux with evdev.

[http://lii-enac.fr/en/projects/shareit/xorg.html](http://lii-enac.fr/en/projects/shareit/xorg.html)

In ubuntu :

[http://ubuntuforums.org/showthread.php?t=1375047](http://ubuntuforums.org/showthread.php?t=1375047)

---

### Post by Roman Shuvalov on 2010-03-03
So... 3G and GPS is not included in this netbook in store where I've been.

But I can find this devices for PCI-E and set it into PCI-E slots? I need to find out the price.

About touchscreen: before Lenovo and Cando answer, maybe you try howtos above? 

In filelist I couldn't see anything about driver... :(

---

### Post by thevillage88 on 2010-03-03
> **Roman Shuvalov said:**
> In filelist I couldn't see anything about driver... :(

I looked through the files and I didn't find anything specific to the Cando touch screen.  However I did find something about mutouch.  I don't understand this, because there is no mention of mutouch in xorg.conf.

Mutouch is a driver for MicroTouch touch screens.  xserver-xorg-input-mutouch is not installed in Ubuntu by default.  I cannot currently test it out since I'm back to using the SD card because of the complications I had with synaptic.

It's likely though, that mutouch is either a residual driver from another version of Splashtop that they neglected to remove, or is it present for the purpose of being used on a different Lenovo computer.

There is also some software for Quick Start that is closed source.  It is possible that they are using a modified version evdev to drive the touch screen and this is why the source code was not included.  This is getting so frustrating to be so close, yet not actually getting the thing working.

Okay, so here's a run down of what we do know about the touch screen.

- It is a Cando 10.1in touch panel
- It can be driven by the evdev driver
- Ubuntu detects it as a standard Human Interface Device
- The device can be found at /dev/usb/hiddev0 and /dev/hidraw1
- $ cat /dev/usb/hiddev0 shows feedback from the device
- lsusb provides no usable information
- lshal provides little usable information

---

### Post by Roman Shuvalov on 2010-03-04
Default evdev driver can't work with touchscreen? Maybe you need to mark something like linux.sysfs_path ('/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/usb/hiddev0') somethere in driver config?

---

### Post by thevillage88 on 2010-03-04
Okay, lshal provides more info about the touch screen that had initially thought.  The touch screen is the no name device 2087:0a01.  Here is the relevant output:

udi = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'Cando 10.1 Multi Touch Panel with Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001'  (string)
  info.vendor = 'Cando Corporation'  (string)
  linux.device_file = '/dev/bus/usb/003/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Cando 10.1 Multi Touch Panel with Controller'  (string)
  usb_device.product_id = 2561  (0xa01)  (int)
  usb_device.serial = '20091003.001'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Cando Corporation'  (string)
  usb_device.vendor_id = 8327  (0x2087)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 2561  (0xa01)  (int)
  usb.serial = '20091003.001'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Cando Corporation'  (string)
  usb.vendor_id = 8327  (0x2087)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001_if0_hiddev'
  hiddev.application_pages = {'Unknown page 0xd0004'} (string list)
  hiddev.device = '/dev/usb/hiddev0'  (string)
  hiddev.product = 'Cando Corporation Cando 10.1 Multi Touch Panel with Controller'  (string)
  info.capabilities = {'hiddev'} (string list)
  info.category = 'hiddev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001_if0'  (string)
  info.product = 'Cando Corporation Cando 10.1 Multi Touch Panel with Controller'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_2087_a01_20091003_001_if0_hiddev'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/usb/hiddev0'  (string)

---

### Post by Gendo on 2010-03-05
I was able to get this somewhat working using a slightly modified method from the thread mentioned previously here [http://ubuntuforums.org/showthread.php?t=1375047](http://ubuntuforums.org/showthread.php?t=1375047) using the hidtouch driver. 

First create an /etc/udev/rules.d/99-touchscreen.rules that contains

```

SUBSYSTEM=="usb", ATTRS{idVendor}=="2087", ATTRS{idProduct}=="0a01", SYMLINK+="usb/cando_touch"
SUBSYSTEM=="input", KERNEL=="event*", ATTRS{idVendor}=="2087", ATTRS{idProduct}=="0a01", SYMLINK+="input/cando_touch"

```

Next download the hidtouch suite from [http://sourceforge.net/projects/hidtouchsuite/](http://sourceforge.net/projects/hidtouchsuite/)

and unzip the file. 

Next grab the patch from 
[http://ubuntuforums.org/attachment.php?attachmentid=142789&d=1262890781](http://ubuntuforums.org/attachment.php?attachmentid=142789&d=1262890781)
and from the parent directory of the unzipped file (xf86-input-hidtouch-9.04.04) run 

```

patch -p0 < hidtouch.patch.txt

```

Now enter the xf86-input-hidtouch-9.04.04 and run a 
```

./configure --prefix=/usr
make
make install or checkinstall

```

Finally create an /etc/X11/xorg.conf that contains 

```

Section "Module"
	Load  "hidtouch"
EndSection

Section "InputDevice"
 Identifier      "Cando TouchScreen"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/cando_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1024" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "600"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1024" # 1920 for 23"
 Option          "CornerBottomRightY"    "600"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1024" # 1920 for 23"
 Option          "CornerScreenHeight"    "600"  # 1080 for 23"
EndSection

Section "ServerLayout"
	Identifier "Touchscreen"
	InputDevice "Cando TouchScreen" "SendCoreEvents"
EndSection

```

Finally restart via your favourite method. 

Currently it is registering my touches but only at the bottom of the screen. The xorg.conf may be off so I need to review what the problem might be. I wanted to pass on this information so if anyone has any more information on what might resolve the coordinate issue they could share it too.

---

### Post by thevillage88 on 2010-03-05
Thank you Gendo!  This was a big step in the right direction.  With this information, I was able to get my touch screen working to a satisfactory degree.  I had to do a couple things differently in order to get it working right though.

First, when I tried to compile the patched source, it told me that I was missing xorg-server and xproto.  I remedied this with:

$ sudo apt-get install xserver-xorg-dev

Second, when I modified the xorg.conf file and rebooted, gdm refused to start.  I looked through the xorg.conf file again, and found that the line Identifier "Touchscreen" should not appear in Section "ServerLayout" so comment or delete this line.

I downloaded and compiled the hidDeviceDump program and in the terminal typed:

$ sudo hidDeviceDump /dev/usb/cando_touch

This seemed to be a very helpful program in determining the x and y coordinates for the touch screen.  The coordinates according to hidDeviceDump are as follows:

0,0                            4000,0


0,4000                      4000,4000

Of course these numbers are aproximate.  So I made these modifications to the xorg.conf file, and now my touch screen is working like a charm.

 Option          "CornerTopLeftX"        "80"
 Option          "CornerTopLeftY"        "80"
 Option          "CornerTopRightX"       "4020" # 1920 for 23"
 Option          "CornerTopRightY"       "80"
 Option          "CornerBottomLeftX"     "80"
 Option          "CornerBottomLeftY"     "4020"  # 1080 for 23"
 Option          "CornerBottomRightX"    "4020" # 1920 for 23"
 Option          "CornerBottomRightY"    "4020"  # 1080 for 23"

Minor tweaks to these values may need to be made, but it's working great for me!

**Update:** I've been playing with it for a while, and there are still problems with netbook launcher.  It seems most applications work fine with the touch screen.  The problem is when trying to tap icons in netbook launcher, it grabs them as if I'm trying to move them.

This doesn't happen with the touch pad or with the usb mouse.  Also, the problem doesn't seem to affect the "Favorites" and "Files & Folders" menus.

**Update again:**  It seems to be related to this bug report, so we'll need to keep an eye on their progress.  [https://bugs.launchpad.net/netbook-remix-launcher/+bug/486381]("https://bugs.launchpad.net/netbook-remix-launcher/+bug/486381").  At least that means it is an issue with netbook launcher rather than the touch screen or driver.

---

### Post by manthony121 on 2010-03-05
> **Roman Shuvalov said:**
> 
I can't download 616 MB of QS source code, manthony121, maybe you can send me index of archive? ... When I'll see this list I will ask you to send me some files that will help me to compile the driver. 



Did you get the tree listing from thevilliage88?  I see that a few days have gone by since you asked.  If you still need it, i'll be happy to send.

---

### Post by thevillage88 on 2010-03-07
I'm not sure this is going to work, but I have created an installation file for the touch screen driver.  If anyone can test this out and confirm that it is working, that would be great.

- Download hids103t.run from [http://www.zshare.net/download/734455741d866531/]("http://www.zshare.net/download/734455741d866531/").

- Right click on the file and click properties.

- Click the permissions tab, and make sure that "Allow executing file as program" is checked.  

- Double click the file and click "run in terminal."

- Enter your password when prompted.

- Wait 0.05 seconds for installation to complete.

---

### Post by manthony121 on 2010-03-07
I just ordered an S10-3t.  I intend to install U9.10 when it arrives.  I'll post the results here.  Thanks (in advance) for the help!

---

### Post by AllBuntu on 2010-03-07
Hey,

I got my S10-3t working just fine with the Broadcom binary Wi-Fi driver, for the touch screen display using the fixes posted here with Ubuntu 10.04 Alpha 3 Netbook

For 10.04, xf86 introduced Atom everywhere so I had to put in like 10 fixes. I used three buttons and two axes and set them all to 0,1,2... (they apparently are type int) I just couldn't believe it when it worked!

For 9.10, The patch does not work anymore with hidtouch, so it takes some C knowledge to patch. The uploaded binary here works for everything else but the driver

I also have the drag-drop vs. tap confusing bug in the launcher, so a mouse is still to recommend. The onboard application, an on-screen keyboard, kind of works

screen rotate does not seem to work

---

### Post by AllBuntu on 2010-03-07
Install Netbook 10.04 Alpha 3
run the funny hids103t.run attachment posted here as root
sudo apt-get install xserver-xorg-dev
Expand this archive to like Desktop
cd into the folder
./configure --prefix=/usr
make
sudo make install

Like god, you got heaven's touch

---

### Post by thevillage88 on 2010-03-08
> **AllBuntu said:**
> I got my S10-3t working just fine with the Broadcom binary Wi-Fi driver...

That's awesome.  What did you do to get the wifi working.  I have been using ndiswrapper, but it tends to disconnect when I try to make too many connections at once(eg apt-get).  I thought my router was blocking me for being to heavy a user, but now I don't think that's the case.  

I also have a Linksys WRT54G with DD-WRT firmware installed, and I'm using it as a wireless repeater to connect to my router hosting the internet connection.  I plug the hard line into that, and I'm able to use apt-get with no problems.  So it's not a problem with the router, but with ndiswrapper.

I have compiled the driver and copied wl.ko to /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless.  I also deleted b43 and b43legacy drivers.  Then I type:

$ sudo modprobe lib80211 

and this is what I get: 

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

I'm not sure where to go from here.

---

### Post by thevillage88 on 2010-03-08
> **AllBuntu said:**
> 
I also have the drag-drop vs. tap confusing bug in the launcher...

I used this fix on 9.10 and now netbook launcher is working great with the touch screen.

Source: [https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/434502/comments/11]("https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/434502/comments/11")

cd # ChDir HOME
mkdir netbook-launcher # make directory for our code manipulations
cd netbook-launcher # chdir
apt-get source netbook-launcher # grab netbook-launcher sources from repo
cd netbook-launcher-2.1.12 # chdir to source dir
wget [http://launchpadlibrarian.net/33315482/434502.patch](http://launchpadlibrarian.net/33315482/434502.patch) # download my "patch"
patch -p1 < 434502.patch # apply patch to the source tree (1 file should be patched)

done. compile and install as usual:
sudo apt-get build-dep netbook-launcher ; ./configure --prefix=/usr ; make ; sudo make install ; killall netbook-launcher

now you should have this workaround applied, hope it'll be useful for you.

---

### Post by AllBuntu on 2010-03-08
I posted about the Wi-Fi here:
[http://ubuntuforums.org/showthread.php?t=1424280]("http://ubuntuforums.org/showthread.php?t=1424280")

maybe you need Alpa 3 to get it working

---

### Post by AllBuntu on 2010-03-08
I posted about the Wi-Fi here:
[http://ubuntuforums.org/showthread.php?t=1424280]("http://ubuntuforums.org/showthread.php?t=1424280")

maybe you need Alpa 3 to get it working

---

### Post by the_real_bubba on 2010-03-10
Given that the fix works on alpha 3, we should expect the fix to work on the released 10.04?  Is there a reasonable expectation that the fix will be incorporated during the betas?

---

### Post by thevillage88 on 2010-03-10
> **the_real_bubba said:**
> Given that the fix works on alpha 3, we should expect the fix to work on the released 10.04?  Is there a reasonable expectation that the fix will be incorporated during the betas?

As it stands right now, it's not likely.  Although we've managed to get the touch screen working fairly well, it's not perfect.  The hid driver is a little spastic when grabbing and dragging items.  It has a strange tendency to release the object you're trying to drag and jumping to (0,0).  

Plus, we've had to patch netbook launcher in order to get it working properly.  It's not working well enough at this point to be considered for inclusion in the next release.

Also, the hid driver that we are using does not support multi touch events.  Although this does not bother me nearly as much as the jumpy cursor, the screen is multi touch and should be supported as such.  So HidTouch is not likely going to end up being the driver we decide to settle on for this touch screen.

---

### Post by manthony121 on 2010-03-11
I have my S10-3t in my sweaty little hands!  I just re-arranged the Windows partitions and installed 9.10 UNR.  I'm working on the wifi now... This thread should come in real handy...

---

### Post by manthony121 on 2010-03-11
Well, wasn't that fun!

I just got my wifi working.  I had no luck with installing bcmwl-kernel-source, or it did not seem to work, as nothing showed up in the "restricted drivers" box or under the "wireless" tab in Preferences|Network Connections.  

I wound up compiling the driver provided by broadcom at "http://www.broadcom.com/docs/linux_sta/README.txt"  The whole process wasn't hard, but it did take me a bit to realize that it had worked.  I typed "iwconfig" in a text window, and there it was!  So, I unplugged eth0, clicked on the network status indicator at the top right of the screen, selected my network, gave it the password to the hub, and all is well.  It remains to be seen if it survives re-boot.

Thanks to everybody who has been contributing to this thread.

BTW, it is worth mentioning that whoever wrote the README.txt file at [www.broadcom.com](www.broadcom.com) did an *excellent* job of describing the process.  It is rare to see such a complete and detailed description of the ins and outs of getting wifi working for various distros and different situations.  I think that a lot of manufacturers don't like supporting linux because there are so many different distros, and giving instructions that cover them all is a lot of work.  Broadcom has done an outstanding job, and they are to be commended.

---

### Post by Finder83 on 2010-03-12
Did some research on this tonight. First off, I feel like the OpcodePressure should be 852018 instead of 034 because it seems to track better...034 is modulated for some reason and sometimes returns false values (like it's duplicated).

Here are the opcodes and my research into them:
65585: Y axis
65584: X axis
852018: First item sent, determines if this x/y/tracker pair is pressed down on the screen
852034: Almost the same as 018...not sure of the difference other than extra values sometimes
852049: a 4 digit tracker(1-4) of the x/y being sent (it changes so that you can know where the cursor is for that finger last)
852052: is 2 if this is the second finger being used otherwise isn't sent

The order of sending is (with 052 potentially missing)
852052 - 852034 - 852018 - 852049 - 65584 - 65585

So for example...
852018 is sent with a 1 meaning this button is pressed
852949 is sent with a 2 which is the tracker id for this button pressing session
65585 is sent with the Y and 65584 is sent with the X

Another multitouch finger is added...
852018 is now sending the series 1111 instead of 1010 (meaning both are pressed)
852949 has two trackers, the new id is the new finger
X and Y are sent with the new finger

If one finger is removed, that 852018 for that tracker is set to 0 which lets you know you can remove it...the tracker is still sent over and over with the 0 in 852018 until the finger is replaced, then a new tracker is assigned and 852018 is set to 1 again.

I've attached a python program to test all of this (and is how I got the opcodes/figured out what they did), it needs root privileges. I believe this is everything we need to know to write a multi-touch driver (but I've never written a driver, have no clue how multitouch works in Linux/X, and am better in python than I am in C...may give it a shot but there may be others better at this here so I thought I'd share what I found out)

---

### Post by bit_junkie on 2010-03-12
I just wanted to give a quick thanks to everyone who have contributed to this thread and have put the time in to figure this out.

Also I used 10.04 alpha and the wifi driver is included as a restricted driver so you still need to be connected with a hard line to activate, but it works perfectly for me. The instructions to get the touch screen working under the alpha are dead simple and work perfectly as well, I dont seem to have the touch\grab problem that some of you are having though, but that may just be a fluke lol  :P 

I even installed e17, and while it is a little quirky it is fun and usable, now i just need to find a decent on screen keyboard and i can actually use this machine in tablet only mode ;) The ones I have tried are not very good, anyone have any suggestions ? I tried the matchbox keyboard and I think qwo.

---

### Post by Finder83 on 2010-03-12
The best I've found is onBoard (if you resize it to not full screen)
If you want something entirely different, try dasher. :-p Fun but not as useful

---

### Post by bit_junkie on 2010-03-13
> **Finder83 said:**
> The best I've found is onBoard (if you resize it to not full screen)
If you want something entirely different, try dasher. :-p Fun but not as useful

Yeah dasher was "different" lol :P
Onboard worked great at first but now it is stuck in full in fullscreen mode and for some reason i can not get it to revert, I'm still hoping to find some kind of integrated keyboard, something at least like the one in Win7, but Onboard works for now,even at full screen :P

---

### Post by manthony121 on 2010-03-13
So far, so good.  I have the touchscreen working as a single-touch, following the instructions given earlier in this thread.

I already posted what I had to do to get wifi working: I had to download and compile the driver provided by Broadcom.  It was easy to do.  Following the instructions in the README, I got it working without too much hassle.  In the section on making it work automatically on boot, I did have to add a command in the "/etc/rc.local" file to load the wl.ko module, as it describes for Fedora/SUSE users.

Touchscreen wasn't too bad.  I didn't use the shell script written by thevillage88.  I used the basic instructions posted by Gendo in message 30, then made the modifications to the screen coordinates as listed by thevillage88 in message 31.  I did not have any trouble with the "ServerLayout" section that tv88 had.

When compiling the "hidtouch" package, the "./configure" failed, and suggested that I needed to install xorg-dev and xorg-server-dev.  It turns out that there is no package named xorg-server-dev (perhaps they meant xserver-xorg-dev?)  In any case, installing xorg-dev by itself satisfied all the dependencies. 

Also, a bit of digging turned up a few useful utilities for touchscreens:

xrandr - allows you to rotate the display
cellwriter - onscreen keyboard and handwriting recognition
xournal - for taking notes
toshtools - various tablet utilities
onBoard - another onscreen keyboard

I've not tried these utilities myself yet, so if anyone has any experience with these or know of other favorites, please post them.

---

### Post by manthony121 on 2010-03-13
Regarding screen rotation:  it turns out that xrandr rotates the display, but does not rotate the mouse movements.  There are some utilities that correct for that, but all the ones I have found are for the Wacom touchscreen.  I haven't had time to play with it to see if it will work for the Lenovo.

---

### Post by thevillage88 on 2010-03-13
> **manthony121 said:**
> I didn't use the shell script written by thevillage88.

That's cool.  It's not necessary anyway, all I did was package a precompiled binary of the driver, the 99-touchscreen.rules file and a copy of xorg.conf, and copied them to the correct places.

Anyway, are you, or anyone else for that matter, having issues with the cursor jumping around the screen when you touch it.  It seems to happen a lot when I'm trying to drag something.  It will just let go of the object and reset to (0,0).  I had to move the "Go Home" button because it kept thinking I was clicking on it.

When I'm watching Hulu, the cursor goes very erratic, flying all over the screen.  It's very annoying, especially using grab and drag for Firefox, I have to use the touch pad or plug in a mouse to scroll down to the video.

---

### Post by Finder83 on 2010-03-13
I had the screen jumping issue until I switched the Pressure opcode to 852018. There still seems to be some issues...but it's not nearly as bad.

---

### Post by manthony121 on 2010-03-14
> **thevillage88 said:**
> 
Anyway, are you, or anyone else for that matter, having issues with the cursor jumping around the screen when you touch it.  It seems to happen a lot when I'm trying to drag something.  It will just let go of the object and reset to (0,0).  I had to move the "Go Home" button because it kept thinking I was clicking on it.

I've seen that happen when I am trying to use the scroll bar on the right side of the screen.  It seems to happen less if I drag my finger somewhat into the window before releasing, so some of it may be from generating a "mouse click" event with the cursor on the Desktop.  Other than that, I don't do a log of "drag and drop".


> When I'm watching Hulu, the cursor goes very erratic, flying all over the screen.  It's very annoying, especially using grab and drag for Firefox, I have to use the touch pad or plug in a mouse to scroll down to the video.

I haven't tried Hulu, so I can't speak to that.

I'm also looking at "home brew" stylus construction.  The best I've done so far (I forget the URL):  Take a *metallic* tube, like the handle of an Xacto knife.  Press a bit of dry sponge tightly into the open end.  Dip the end in a bit of salt water, then cover with a bit of plastic bag material, and hold it all together with tape.  It takes a fair amount of pressure to get it to register, and still seems to require a fairly broad area of contact.  So far, it is not as precise as I had hoped, but I'll keep working on it.

---

### Post by manthony121 on 2010-03-14
New problem now.  I am trying to get "onboard" to work.  When I invoke it from a terminal window, the keyboard flashes briefly on the screen, the disappears.  The program doesn't exit, or even generate any errors with "debug" enabled, it just waits for me to press ^C.  Anyone else have such a problem?

---

### Post by bit_junkie on 2010-03-14
> **manthony121 said:**
> New problem now.  I am trying to get "onboard" to work.  When I invoke it from a terminal window, the keyboard flashes briefly on the screen, the disappears.  The program doesn't exit, or even generate any errors with "debug" enabled, it just waits for me to press ^C.  Anyone else have such a problem?

I don't have that problem with onboard, mine is a whole other issue. For some reason it decides to go full screen and the only way to get rid of it is to log out :P Haven't quite figured that one out yet, but it does seem to only happen after an extended use period.

---

### Post by manthony121 on 2010-03-14
i still don't have onboard working, but i do have gok up, which is better than nothing

---

### Post by Subsanek on 2010-03-15
Bluetooth, webcam, cardreader work perfectly, and wi-fi and tablet after adjustment. I understood correctly?

---

### Post by manthony121 on 2010-03-15
I believe the S10-3t does not have bluetooth, but everything else you listed works

---

### Post by Subsanek on 2010-03-16
And in the description is written, that is.](*,)
Well me and it is not particularly necessary.
So in May, will buy)):popcorn:

---

### Post by manthony121 on 2010-03-16
If you are not buying until May, you might want to wait and see what the Ideapad U1 hybrid looks like: detachable screen that becomes a stand-alone tablet running Lenovo's customized Linux, called Skylight.  I got a S10-3t because I didn't want to wait that long.

One aspect of the S10-3t that I really appreciate is the battery life: I can leave it on all day and not run out of juice.  My (old) laptop has a battery that no longer holds any charge; if it's not plugged in, it won't last more than a few minutes!

---

### Post by Subsanek on 2010-03-16
I too important a good battery.
But I live in Russia, but now there are new items with a huge delay on the west.
And very much a detachable screen I do not need.

---

### Post by manthony121 on 2010-03-16
> **thevillage88 said:**
>   I had to move the "Go Home" button because it kept thinking I was clicking on it.



How do you move the "Go Home" button?  Is there a "Get Out of Jail Free" button, too? ;)

---

### Post by thevillage88 on 2010-03-17
Heh... I just right clicked the little Ubuntu icon, unchecked "Loc_k_ to panel," then moved it.  I've also made a number of other modifications.  Of course that seems to be the way with Linux.  I spend more time customizing it than I do actually using it.

I didn't want Netbook Launcher running every time I boot, so I went to System>Preferences>Startup Applications and unchecked Maximus Window Management, which was stealing focus from full screen apps such as Stepmania. I also unchecked Netbook Launcher of course.

Then, in System Tools>Configuration Editor, I went to /apps/nautilus/desktop and checked all the icons I wanted visible.  Then, in /apps/nautilus/preferences, check show_desktop.  This would bring up a standard desktop on boot.  I then created an icon on the desktop to run netbook-launcher, and then wherever that could be added to favorites another that would "killall netbook-launcher."  Not proper, but it seems to work... Most of the time.

The "Go Home" button will start Netbook Launcher when it's not running, so I replaced that with "Show Desktop," and I replaced "Window Selector" with Talika.  I found it annoying for applications to have two X butons.  :) 

Finally, I wanted to have a gnome menu for the desktop that wasn't present on the panel because having a gnome menu while in Netbook Launcher seems redundant.  So I installed xvkbd, another virtual keyboard you might try.  I'm not certain about onboard, but xvkbd takes command line commands.  I created and icon on the desktop with the command:

xvkbd -text "\[Alt_L]\[F1]"

Voila!  My version of Netbook Switcher.  :)

---

### Post by Subsanek on 2010-03-17
Someone tested KDE on it? Theoretically KDE will work better on the touch screen.

---

### Post by the_real_bubba on 2010-03-26
Has anyone (else) tried 10.04 beta1?

I've just installed it, and the proprietary driver "Broadcom STA wireless driver" is suggested, after installing it through the restricted hardware driver process... there is still no working wifi.  The package's info reads"These [sic] package contains Broadcom 802.11 Linux STA wireless driverfor [sic] use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based [sic] hardware." no mention of the BCM4313  chipset manthony121 says is in this thing.

---

### Post by the_real_bubba on 2010-03-26
So, I have tried just clicking on the install restricted drivers (as prompted?) in a default beta1 install, and I've tried following these instructions:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
both led to the same outcome (I think they did the same thing).

Currently, lsmod shows:
lib80211_crypt_tkip    7659  0
wl                  1959694  0
lib80211               5046  2 lib80211_crypt_tkip,wl

lspic -n | grep 14e4 shows 0x1692 (rev 1) and 0x4727 (rev 1) so this is the BCM4313 (not the intel alternative chipset 8086:0089 I've seen suggested elsewhere).

I havn't tried downloading the drivers from broadcom and compiling (per msg #6 in [http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)), but maybe I'll give it a go on Monday.  Something makes me think that since I've got bcmwl-kernel-source and bcmwl-modaliases 5.60.48.36+bdcom-0ubuntu2 modules installed (says synaptic) via the proceedures above, that compiling the v5.60.48.36 tarballs that are the current offering at broadcom.com isn't going to change much...

Any thoughts?

===edit===
Faceplam, cringe, was in airplane mode...  installed updates to beta1, flipped switch, much joy.

---

### Post by the_dusche on 2010-03-26
strange..sorrz but I am a newby on Linux, cant help you. I am just trying it via usb stick at the moment and wireless works just fine, but touchscreen, buttons and cam dont...will have to have look on it...

BTW:
Wouldnt it be possible that the ones who got the touchscreen etc running provide us with the COMPLETE Ubuntu System, all drivers etc. alreadz included coz for me it is impossible to find all the way through the command line etc....

---

### Post by thevillage88 on 2010-03-27
> **the_dusche said:**
> strange..sorrz but I am a newby on Linux, cant help you. I am just trying it via usb stick at the moment and wireless works just fine, but touchscreen, buttons and cam dont...will have to have look on it...

BTW:
Wouldnt it be possible that the ones who got the touchscreen etc running provide us with the COMPLETE Ubuntu System, all drivers etc. alreadz included coz for me it is impossible to find all the way through the command line etc....

You want us to roll you a new iso?  That is so cute.  Likely not gonna happen though.  I understand that there are typical expectations of prior knowledge with these boards, this will come in time, so I have made a new installation for the touchscreen driver with basic explanations of the commands used.

Run the hidtouch_s10-3t.run file with terminal.  Upon completion, the installation will copy the contents of itself to your home directory in "hidtouch."  Be sure to inspect the "install.sh" (right click - open with gedit) file and compare notes with what was written in posts #30, #31, and #38.  Restart your computer.

Click here to download:  [http://www.zshare.net/download/7429176496535396/](http://www.zshare.net/download/7429176496535396/)

---

### Post by the_real_bubba on 2010-03-29
> **thevillage88 said:**
> 
Run the hidtouch_s10-3t.run file with terminal.  Upon completion, the installation will copy the contents of itself to your home directory in "hidtouch."  Be sure to inspect the "install.sh" (right click - open with gedit) file and compare notes with what was written in posts #30, #31, and #38.  Restart your computer.


Thanks for this.  I downloaded and sudo ran it on my 10.04beta1 s10-st.

After rebooting I still have no touchscreen.

The Xorg log contains...

(EE) Failed to load module "hidtouch" (module does not exist, 0)

I see lots of compile errors... maybe these result from some change from alpha2 to beta1, outside of my league here.

In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function ‘HdtRawData__fillFromInputInfo’:
hidtouch__HdtRawData.h:42: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
In file included from hidtouch.c:71:
hidtouch__body.h: In function ‘hdtOnDeviceInit__initButtons’:
hidtouch__body.h:153: warning: passing argument 3 of ‘InitButtonClassDeviceStruct’ from incompatible pointer type
/usr/include/xorg/input.h:274: note: expected ‘Atom *’ but argument is of type ‘CARD8 *’
hidtouch__body.h:153: error: too few arguments to function ‘InitButtonClassDeviceStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes’:
hidtouch__body.h:174: warning: passing argument 3 of ‘InitValuatorClassDeviceStruct’ makes pointer from integer without a cast
/usr/include/xorg/input.h:280: note: expected ‘Atom *’ but argument is of type ‘int’
hidtouch__body.h:174: error: too few arguments to function ‘InitValuatorClassDeviceStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes__MinMax’:
hidtouch__body.h:213: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h:221: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes__FourCorners’:
hidtouch__body.h:239: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h:247: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

---

### Post by thevillage88 on 2010-03-30
**Update**: The source code that Allbuntu uploaded on comment #36 compiles without error.  Try replacing the content of install.sh with the code below, run the script and then download this file: [http://ubuntuforums.org/attachment.php?attachmentid=149353&d=1268018451]("http://ubuntuforums.org/attachment.php?attachmentid=149353&d=1268018451") Extract it and then:

./configure
make
sudo make install
Restart, and let us know what happens.

**Original Text**:
I have tested the script on 10.04 beta 1 and ran into many problems just like you did.  I have made a few adjustments(mainly having to give root access where I didn't seem to need it before), and have ultimately stumbled over the same problem compiling hidtouch.  Luckily, this is the only hurdle we need to get over since the rest of the script is now working fine.

It may have to do with the new X server, but I'm really not sure.  Anyway, here is the new script, broken as it may be.  It should still work with 9.10 and 10.04 alpha.  We may just have to wait until next month when the stable version is released.  For now, I'm going to stick with 9.10

```
# The text written after hash marks in a shell script will not be executed by bash
sudo cp ./data/99-touchscreen.rules /etc/udev/rules.d/ #cp copies files from one location to another; sudo gives you administrative access to system files.  Thus the reason you need to enter your password.
cd data #Like DOS, cd stands for "Change Directory"
if [ -f ./xf86-input-hidtouch-9.04.04/aclocal.m4 ] #Checks if the file aclocal.m4 exists in the subdirectory xf86-input-hidtouch-9.04.04.  If it does:
then
rm -r xf86-input-hidtouch-9.04.04 #Will remove the entire subdirectory xf86-input-hidtouch-9.04.04 in case you have run this shell script before and ran into problems.  This will help to eliminate further problems with the script.
fi #Closes the "if" statement 
sudo unzip xf86-input-hidtouch-9.04.04.zip #Self explanitory
sudo apt-get update #Updates apt repositories
sudo apt-get install patch #Installs patch
sudo patch -p0 < hidtouch.patch.txt #This will patch the contents of the xf86-input-hidtouch-9.04.04 directory with the code contained in hidtouch.patch.txt
cd xf86-input-hidtouch-9.04.04
sudo apt-get install xserver-xorg-dev #Installs the development files for the xserver.  This is needed to compile the source code in xf86-input-hidtouch-9.04.04
sudo apt-get install build-essential #New.  Contains required development tools.
./configure #The next three commands are used to compile programs and install them from source code.  Burn this in your memory right now.
#
#------------------------------------------------------
#
sudo make #This is our problem child
#
#------------------------------------------------------
#
sudo make install
cd .. #Again, same as DOS.  This will change to the parent directory.
sudo cp xorg.conf /etc/X11
if [ -f ./netbook-launcher/netbook-launcher-2.1.12/434502.patch ]
then
rm -r netbook-launcher
fi
sudo unzip netbook-launcher.zip
cd netbook-launcher/netbook-launcher-2.1.12
sudo patch -p1 < 434502.patch
sudo apt-get build-dep netbook-launcher #Installs build dependencies for netbook-launcher
sudo ./configure --prefix=/usr #--prefix=/usr tells program to install to /usr.  Default is /usr/local.
sudo make
sudo make install
killall netbook-launcher
cd ../..
rm -r xf86-input-hidtouch-9.04.04
rm -r netbook-launcher
clear #Equivilant to DOS's cls
echo The installation is now finished.  A copy of the installation has been copied to your home directory called "hidtouch."  Netbook-launcher has been patched and reinstalled, however those who are not running Netbook Remix will need to install Maximus and configure gnome to start netbook-remix and maximus on load.  This is beyond the scope of the intentions of this installation.
```

---

### Post by the_real_bubba on 2010-03-30
> **thevillage88 said:**
> I have tested the script on 10.04 beta 1 and ran into many problems just like you did.  I have made a few adjustments(mainly having to give root access where I didn't seem to need it before), and have ultimately stumbled over the same problem compiling hidtouch.  Luckily, this is the only hurdle we need to get over since the rest of the script is now working fine.


I just got touchscreen working using Allbuntu's post #36 method...

==edit==

all I did was configure; make; sudo make install Allbuntu's code after running your script dowloaded form post #68... anyone else following my method for 10.04 beta1 could probably do better by applying one or the other properly :).  Thanks to you both!

---

### Post by thevillage88 on 2010-03-30
Thanks the_real_bubba, at least we're managing to stay ahead of the game.  here's a new script for those of you who are brave enough to try 10.04 beta 1.

[http://www.zshare.net/download/744030136417657e/](http://www.zshare.net/download/744030136417657e/)

I didn't feel like packaging this one up. :P  Just extract and run install.sh in terminal.

**Edit**:  Alright!  This one fits on a floppy disk! ;)

---

### Post by jmate24 on 2010-03-30
> **mtate5000 said:**
> I really have my heart set on this ideapad, but before i purchase anything, i would really love to hear of some good luck with these driver issues. I've been using karmic with netbook-laucher as a desktop shell for some time now. It was just to try out for a little while, but i managed to fall in love with the interface. I agree that it does indeed scream for a touch screen. Has anybody gotten the netbook interface to work any sort of touchscreen devise? I will keep searching for a solution.

My suggestion is to get yourself a Lenovo ideapad y510 because for the price I got mine ~$760US it was 64-bit dual core when the core 2 was ~$900US.

and it runs ubuntu 32 and 64-bit just fine and the graphics are just as good as nvidia.

jmate24

---

### Post by thevillage88 on 2010-03-31
thevillage88 slaps jmate24 with large trout.

---

### Post by manthony121 on 2010-04-02
> **thevillage88 said:**
> thevillage88 slaps jmate24 with large trout.

The "fish slap dance"!  I haven't seen that in years!  Awesome!

---

### Post by manthony121 on 2010-04-02
> **the_real_bubba said:**
> So, I have tried just clicking on the install restricted drivers (as prompted?) in a default beta1 install, and I've tried following these instructions:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
both led to the same outcome (I think they did the same thing).

Currently, lsmod shows:
lib80211_crypt_tkip    7659  0
wl                  1959694  0
lib80211               5046  2 lib80211_crypt_tkip,wl

lspic -n | grep 14e4 shows 0x1692 (rev 1) and 0x4727 (rev 1) so this is the BCM4313 (not the intel alternative chipset 8086:0089 I've seen suggested elsewhere).

I havn't tried downloading the drivers from broadcom and compiling (per msg #6 in [http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)), but maybe I'll give it a go on Monday.  Something makes me think that since I've got bcmwl-kernel-source and bcmwl-modaliases 5.60.48.36+bdcom-0ubuntu2 modules installed (says synaptic) via the proceedures above, that compiling the v5.60.48.36 tarballs that are the current offering at broadcom.com isn't going to change much...

Any thoughts?

===edit===
Faceplam, cringe, was in airplane mode...  installed updates to beta1, flipped switch, much joy.

When I tried using the "restricted drivers", I couldn't get anything to show up on the drivers list.  So, I did as described in message 44: downloaded the source code and compiled it, following the instructions in the README.txt file.  The instructions are unusually clear and complete; they even tell you what packages you need to install to run the compiler.  Give it a try.

BTW, my lsmod gives different sizes for the modules than the ones you have:


lib80211_crypt_tkip     8636  0
wl                   1963332  0 
lib80211                6432  2 lib80211_crypt_tkip,wl

So, perhaps the "compile-yer-own" drivers are different from the pre-compiled?

---

### Post by Subsanek on 2010-04-03
&#1061;&#1086;&#1095;&#1091; &#1087;&#1088;&#1086;&#1089;&#1090;&#1086; &#1079;&#1085;&#1072;&#1090;&#1100; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1077;&#1090; &#1080;&#1083;&#1080; &#1085;&#1077;&#1090;!
&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;&#1067;

---

### Post by xmypoeytpo on 2010-04-03
I've installed touchscreen driver on my S10-3t just like described in previous posts. But still there is a bug with cursor. When you  tap a screen for some time (more than 1 sec), the coursor jumps and clicks on a 0,0 position (left corner of the screen) and then comes back several times. This makes using my Ubuntu NBR very uncomfortable. Does anybody has such a bug or any walkaround?

P.S. I've found  useful touchscreen plugin for Google Chrome - ChromeTouch. It makes surfing very iPhone-like!

P.P.S Does anybody found ubuntu MBR touchscreen interface enchancements?

---

### Post by thevillage88 on 2010-04-03
> **the_real_bubba said:**
> So, I have tried just clicking on the install restricted drivers (as prompted?) in a default beta1 install...

For me, the restricted driver utility automatically found the wireless card, but it was unable to install.  I just ran "sudo apt-get update" in the terminal and retried.  It worked fine.

---

### Post by the_real_bubba on 2010-04-07
> **xmypoeytpo said:**
> 
P.S. I've found  useful touchscreen plugin for Google Chrome - ChromeTouch. It makes surfing very iPhone-like!

P.P.S Does anybody found ubuntu MBR touchscreen interface enchancements?

Firefox Grab and Drag is similar to ChromeTouch, but not as nice: [https://addons.mozilla.org/en-US/firefox/addon/1250](https://addons.mozilla.org/en-US/firefox/addon/1250)

Havn't seen nice collection of NBR touchscreen/tablet enhancements... seems like it'll come in handy with this summer's fashion in hardware.

---

### Post by the_real_bubba on 2010-04-09
FWIW, I tried a fresh install of beta2 and failed (ubi-language fails, and attempting to ignore failed early in the installation process).

---

### Post by sinarisx on 2010-04-09
Same thing. attempted on beta 2 and no joy

---

### Post by jeffbarish on 2010-04-13
Are there any problems running Ubuntu inside VirtualBox running on the default Windows installation?

---

### Post by freehunt on 2010-04-15
It's not impossible to run Ubuntu in VirtualBox, but you'd want to upgrade the memory to 2GB, and I would have reservations about running a VM on an Atom processor.

---

### Post by zythar on 2010-04-16
i've installed lucid beta2 netbook remix without any problems.
wifi and touchpanel doesn't work "out of box" (but, of course, before installation i knew it). now i'm trying to make them work.

wifi worked immediately, just after i installed bcmwl-kernel-source.
i've read in this topic somewhere that webcam doesn't work out of box. well, for 10.04  beta2 that is not true. i have working webcam, and i even managed to take some photos.

touchscreen worked in "onetouch" (multitouch.. onetouch) mode.
there was only one problem. when installed hidtouch module it was in /usr/**local**/lib/xorg/modules/input, so i edited my /etc/X11/xorg.conf's modulepath and added /usr/local/lib/xorg/modules.
problem also can be solved by adding --prefix=/usr in install.sh in corresponding line. but i think editing xorg.conf is correct.

ps some questions. i must recompile hidtouch each time i update xorg?
there is netbook-launcher installed in my package list. when i'm going to update my system, and there would be new version of netbook-launcher what would be?

---

### Post by zythar on 2010-04-16
delete

---

### Post by zythar on 2010-04-16
i'm suggesting to use this package.

in install.sh i added some debug info. i mean, while script is running, beside of work he is doing he writes what he is doing, that may be useful. and also i've added in that script check for /etc/X11/xorg.conf. if the file exists then script copies it as /etc/X11/xorg.conf.bak and only then installs it's own xorg.conf. 

because hidtouch is compiling without --prefix, which means that it's prefix is /usr/local and lib for xorg will lie in /usr/local/lib/xorg/modules/input,  i've updated xorg.conf too.

i've wanted to add some check for packages xorg-xserver-dev and build-essentials also. i mean, if there already are in system then don't run apt-get but i couldn't do it.
here is new package. [download](http://www.zshare.net/download/75040081c56f7ba7/)

---

### Post by the_real_bubba on 2010-04-16
> **zythar said:**
> 
i've read in this topic somewhere that webcam doesn't work out of box. well, for 10.04  beta2 that is not true. i have working webcam, and i even managed to take some photos.


I'm still running beta1 (but updates continue to come so maybe it is effectively beta2) and just installed skype, the webcam worked, no problem, but microphone didn't.

---

### Post by zythar on 2010-04-17
heh.. now i have much problems with beta2.. for first, this morning, when i tried to log in with "Ubuntu network edition" (or smth like that) session, and i failed to log in. i tried GNOME, Ubuntu Network Edition 2d and the attempt of login was succesfull. then i tried UNE again. at 4th attempt i logged in. now, the wifi, which was working excellent yesterday, now is not working. it couldn't connect to network with 64-bit encryption.

wow, now that was really funny!!!! ((*
somehow, i've got my wifi card off (you know, there is a slider in right corner of computer, where you can on/off your card)...
but then why, if i just disable my wifi card there are going some crash processess in system?

---

### Post by floem on 2010-04-17
Hi everyone,

just a quick update on the touchpad: Stephane Chatty has posted a patch for Linux 2.6.34 to the linux-input list, patch available here:

[http://www.spinics.net/lists/linux-input/msg08065.html](http://www.spinics.net/lists/linux-input/msg08065.html)

I've given it a try, and it seems to work fine with the evdev driver in xorg. Maybe you'll need something like the following in /etc/hal/fdi/policy/preferences.fdi:

```

<device>
   <match key="info.product" contains="Cando">
       <merge key="input.x11_driver" type="string">evdev</merge>
   </match>
</device>

```Floe

---

### Post by jeffeulogy on 2010-04-17
how exactly do i use this patch? i've tried a lot of things over the last couple hours and nothing is working. i got my touchscreen working using this thread but it's still glitchy, and single touch.

---

### Post by floem on 2010-04-18
> **jeffeulogy said:**
> how exactly do i use this patch? i've tried a lot of things over the last couple hours and nothing is working. i got my touchscreen working using this thread but it's still glitchy, and single touch.
You'll need to install the Ubuntu kernel source first (see here: [https://help.ubuntu.com/community/Kernel/Compile )]("https://help.ubuntu.com/community/Kernel/Compile") Then, change to the source directory and use patch -p1 < touchscreen.patch to apply. After that, rebuild the kernel once and install it (I've used the "old-fashioned Debian way" described on that page).

Note: around line 218 in hid-cando.c, you might need to change
        ret = hid_hw_start(hdev,HID_CONNECT_DEFAULT);
to
        ret = hid_hw_start(hdev,HID_CONNECT_DEFAULT|HID_CONNECT_HIDINPUT_FORCE);

This somewhat depends on the base kernel version you're using - I had to add the FORCE flag for 2.6.31.9.

Floe

---

### Post by jeffeulogy on 2010-04-18
awesome, thanks a lot. i was tearing my hair out messing around with git. i'll start over with a fresh install and try it with 2.6.31-9

---

### Post by zythar on 2010-04-18
so, now, just applaying this patch to kernel, we get dual touch working withot 3rd party hidtouch and netbook-launcher patching, yeah?

ps and, if it is not difficult for you, please upload separate patch file somewhere.. i just can't understand, from where to where copy (never patching anything before)

---

### Post by jeffeulogy on 2010-04-18
make is giving this output:

drivers/hid/hid-cando.c: In function &#8216;cando_probe&#8217;:
drivers/hid/hid-cando.c:217: error: &#8216;HID_CONNECT_&#8217; undeclared (first use in this function)
drivers/hid/hid-cando.c:217: error: (Each undeclared identifier is reported only once
drivers/hid/hid-cando.c:217: error: for each function it appears in.)
drivers/hid/hid-cando.c:217: error: expected &#8216;)&#8217; before &#8216;HID_INPUT_FORCE&#8217;
make[2]: *** [drivers/hid/hid-cando.o] Error 1
make[1]: *** [drivers/hid] Error 2
make: *** [drivers] Error 2

i'm not getting the error after changing that line back to the default. here's hoping the rest goes well.

god i wish i was smarter.

---

### Post by zythar on 2010-04-19
[deleted]

i've applied patch that was suggested in previous page to kernel and comile kernel without any problems.
now, how i can enable dual touch?

---

### Post by floem on 2010-04-19
> **jeffeulogy said:**
> make is giving this output:

drivers/hid/hid-cando.c: In function ‘cando_probe’:
drivers/hid/hid-cando.c:217: error: ‘HID_CONNECT_’ undeclared (first use in this function)
drivers/hid/hid-cando.c:217: error: (Each undeclared identifier is reported only once
drivers/hid/hid-cando.c:217: error: for each function it appears in.)
drivers/hid/hid-cando.c:217: error: expected ‘)’ before ‘HID_INPUT_FORCE’
make[2]: *** [drivers/hid/hid-cando.o] Error 1
make[1]: *** [drivers/hid] Error 2
make: *** [drivers] Error 2

i'm not getting the error after changing that line back to the default. here's hoping the rest goes well.

god i wish i was smarter.

Oops, sorry, I've just seen that there was an error in my post. There's no space to be supposed between HID_CONNECT_HIDINPUT_FORCE, it's all one word.

[QUOTE=zythar]
i've applied patch that was suggested in previous page to kernel and comile kernel without any problems.
now, how i can enable dual touch? 	
[/QUOTE]
Basically, there's nothing to enable, it's there from the start. Now you just need some software that's able to use the new data - AFAICT in Lucid, you'll be able to use xf86-input-evdev and get two mouse cursors as soon as you touch the screen with two fingers.

Floe

---

### Post by zythar on 2010-04-20
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Cando TouchScreen" "SendCoreEvents"
        InputDevice    "dummy"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    ModulePath   "/usr/local/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri"
    Load  "extmod"
    Load  "dri2"
    Load  "glx"
    Load  "dbe"
    Load  "hidtouch"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
 Identifier      "Cando TouchScreen"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/cando_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852018"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "80"
 Option          "CornerTopLeftY"        "80"
 Option          "CornerTopRightX"       "4020"
 Option          "CornerTopRightY"       "80"
 Option          "CornerBottomLeftX"     "80"
 Option          "CornerBottomLeftY"     "4020"
 Option          "CornerBottomRightX"    "4020"
 Option          "CornerBottomRightY"    "4020"
 Option          "CornerScreenWidth"     "1024"
 Option          "CornerScreenHeight"    "600"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Pineview Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```
here is my xorg.conf. what should i change? 
package of evdev (xserver-xorg-input-evdev) is installed.
support of hid, evdev, cando dual touch are enabled in kernel.

---

### Post by floem on 2010-04-20
> **zythar said:**
> here is my xorg.conf. what should i change? 
package of evdev (xserver-xorg-input-evdev) is installed.
support of hid, evdev, cando dual touch are enabled in kernel.
I believe you can remove the entire "Cando Touchscreen" section. In fact, I don't even have an xorg.conf anymore, the entire configuration is done through HAL.
At first, the synaptics driver tried to handle my touchscreen and failed, but I've added the snippet from my earlier post to /etc/hal/fdi/policy/preferences.fdi. This switched the driver to evdev and it's working fine since.

Floe

---

### Post by ehabh on 2010-04-20
Whenever i try to download the file, it downloads zero bytes. Can you possibly upload it elsewhere?

> **zythar said:**
> i'm suggesting to use this package.

in install.sh i added some debug info. i mean, while script is running, beside of work he is doing he writes what he is doing, that may be useful. and also i've added in that script check for /etc/X11/xorg.conf. if the file exists then script copies it as /etc/X11/xorg.conf.bak and only then installs it's own xorg.conf. 

because hidtouch is compiling without --prefix, which means that it's prefix is /usr/local and lib for xorg will lie in /usr/local/lib/xorg/modules/input,  i've updated xorg.conf too.

i've wanted to add some check for packages xorg-xserver-dev and build-essentials also. i mean, if there already are in system then don't run apt-get but i couldn't do it.
here is new package. [download](http://www.zshare.net/download/75040081c56f7ba7/)

---

### Post by ehabh on 2010-04-20
I am running the latest kernel  2.6.32-21 and this is the error I get when I try to patch the kernel.


patch -p1 < /home/ehab/Documents/touchscreen.patch 

patching file drivers/hid/hid-cando.c
patching file drivers/hid/hid-core.c
Hunk #1 FAILED at 1295.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/hid-core.c.rej
patching file drivers/hid/hid-ids.h
Hunk #1 FAILED at 123.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/hid-ids.h.rej
patching file drivers/hid/Kconfig
Hunk #1 FAILED at 86.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/Kconfig.rej
patching file drivers/hid/Makefile
Hunk #1 FAILED at 26.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/Makefile.rej

t 
and the reject file for ......

cat drivers/hid/hid-ids.h.rej


--- drivers/hid/hid-ids.h       2010-04-14 13:35:09.000000000 +0200
+++ drivers/hid/hid-ids.h       2010-04-07 23:14:25.000000000 +0200
@@ -123,6 +123,9 @@
 #define USB_VENDOR_ID_BERKSHIRE                0x0c98
 #define USB_DEVICE_ID_BERKSHIRE_PCWD   0x1140
 
+#define USB_VENDOR_ID_CANDO            0x2087
+#define USB_DEVICE_ID_CANDO_MULTI_TOUCH 0x0a01
+
 #define USB_VENDOR_ID_CH               0x068e
 #define USB_DEVICE_ID_CH_PRO_PEDALS    0x00f2
 #define USB_DEVICE_ID_CH_COMBATSTICK   0x00f4




> **floem said:**
> You'll need to install the Ubuntu kernel source first (see here: [https://help.ubuntu.com/community/Kernel/Compile )]("https://help.ubuntu.com/community/Kernel/Compile") Then, change to the source directory and use patch -p1 < touchscreen.patch to apply. After that, rebuild the kernel once and install it (I've used the "old-fashioned Debian way" described on that page).

Note: around line 218 in hid-cando.c, you might need to change
        ret = hid_hw_start(hdev,HID_CONNECT_DEFAULT);
to
        ret = hid_hw_start(hdev,HID_CONNECT_DEFAULT|HID_CONNECT_HIDINPUT_FORCE);

This somewhat depends on the base kernel version you're using - I had to add the FORCE flag for 2.6.31.9.

Floe

---

### Post by zythar on 2010-04-21
> **ehabh said:**
> Whenever i try to download the file, it downloads zero bytes. Can you possibly upload it elsewhere?

hm.. i tried to download it, right now and it was downloaded normally.
anyway, here is new link: [http://url.file.am/?CaGAA.]("http://url.file.am/?CaGAA")

when i compiled kernel with suggested edit of hid-cando.c (which was on 9 page) and added /etc/hal/fdi/policy/preferences.fdi touchscreen worked normal.
but when i restarted something went wrong.
when i touch to screen mouse  pointer goes to upper-left corner of screen.
also, lshal | grep -i input.x11_driver has no output.
it means that hald doesn't read fdi file correctly?

---

### Post by ehabh on 2010-04-21
Thanks for the new upload the file just downloaded now :)

---

### Post by ehabh on 2010-04-21
I am on the KDE version of netbook remix, I think this is why the installation does nothing for me, or should it?

---

### Post by zythar on 2010-04-21
> **ehabh said:**
> I am on the KDE version of netbook remix, I think this is why the installation does nothing for me, or should it?

it makes no difference you're running on gnome, kde, xfce, icewm or self-written desktop environment. the point is to patch kernel for supporting this device, then, with hal, reassign device's driver to evdev. there is no dependency on gnome, .... , as you can see.

---

### Post by ehabh on 2010-04-21
Ok got that.
Now I am still a bit confused.

The script provided here what does it do?

Also can someone upload a working kernel that would ease things a lot for others like me who are having trouble patching the kernel.


[www.elmotaheda-web.com](www.elmotaheda-web.com)

---

### Post by ehabh on 2010-04-21
I tried something new, since the patches where included in kernel 2.6.34 i downloaded it and its headers ( in total 3 debs ) from this ubuntu page of experimental kernels 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)

I installed them and booted.

Voila touchscreen works, but only tap, that is on first press the cursor goes to where my finger is, but as I move my finger the cursor does not move with it.

But this is not the only problem, wifi is gone, seems that the binary packages of the wifi driver do not have the bindings for this new kernel.

Hope this helps someone.

---

### Post by jeffeulogy on 2010-04-21
have you tried compiling the wifi driver from source? if the touchscreen is recognized by the kernel i'm hopeful it can be made to work like it should but no wifi is a deal breaker at least for now. 

my s10 is the only one of my four computers running windows (albeit dual booting) and it's infuriating.

---

### Post by zythar on 2010-04-21
> **ehabh said:**
> Ok got that.
Now I am still a bit confused.

The script provided here what does it do?

Also can someone upload a working kernel that would ease things a lot for others like me who are having trouble patching the kernel.


[www.elmotaheda-web.com]("http://www.elmotaheda-web.com")

if you have already patched kernel, then this package is not for you.
it is just compiling hidtouch module for xserver and patches netbook-launcher, then making it's xorg.conf, installing it. and voila, you've got working (but single touch) touchscreen.

[QUOTE=ehabh]But this is not the only problem, wifi is gone, seems that the binary packages of the wifi driver do not have the bindings for this new kernel.

Hope this helps someone.[/QUOTE]

you can compile it from source. [here](http://www.broadcom.com/support/802.11/linux_sta.php) is link for source package. and [here](http://www.broadcom.com/docs/linux_sta/README.txt) is very detailed instruction for compiling driver.

---

### Post by zythar on 2010-04-22
very often, even when i'm not doing anything serious on laptop, i heard that fan is noising like a beast.
i've installed tool for monitoring cpu temperature and found that it's temperature is >50 C.
so, i have some questions.
1. why if i'm not working on it, and it stays alone for about hour or two it's temperature grows over 50?
2. do anyone have same problem?
3. is it dangerous? i mean does it affect on lifetime of laptop?

---

### Post by ehabh on 2010-04-22
Zyther Thank you for the clarification :)


As for your heat issues, I do not know why it heats, BUT I do 100% know that all modern processors including the ATOM have built in overheating defenses that will shut down the CPU in the event that heat would damage it.

BUT still heat can damage other components in the motherboard.

---

### Post by ehabh on 2010-04-22
Zyther man thanks a lot for your help :)

---

### Post by jeffeulogy on 2010-04-22
is there hot air coming out of the fan vent? laptops and netbooks typically run pretty hot and like the previous post said modern processors will throttle back and then shutdown if there's a threat of heat damage. if the air coming out of the vent is cool though, it's an issue with a bios setting or acpi causing the fan to run needlessly. it won't hurt your computer but it will affect your battery life.

---

### Post by zythar on 2010-04-22
hm. okay, thanks then (*

one more question. i have problems with microphone and headphone jack in left side of laptop, also microphone itself.
microphone doesn't work, and jacks doesn't work either.

---

### Post by zythar on 2010-04-22
oh mother...
remember, in previous pages i have told that my touchscreen finally worked with evdev and kernel module?
remember, then i told that after restart it doesn't work, and when i touch to the screen mouse goes to upper left corner?
now listen. IT IS WORKING. i didn't change anything in conf. files of hal or xorg. i just tired of 2-day war between me and touchscreen and shut down computer. then, this morning i turned it on and got what i have.
i just don't know how to understand this...

i've read in googl: for testing multitouch just open kind of paint and start to draw with your fingers.
now, i've opened MyPaint and tried to draw something with two fingers, but got only one line.
it means, that driver for touchscreen is working but not for dual yet?

---

### Post by floem on 2010-04-23
> **zythar said:**
> 
now, i've opened MyPaint and tried to draw something with two fingers, but got only one line.
it means, that driver for touchscreen is working but not for dual yet?
No, that rather means that almost no software is able to deal with the additional data.
Try 'sudo evtest /dev/input/eventX' (you have to do a bit of trial and error to find out which X is your touchscreen). When the dual-touch is working properly, you should be seeing various reports with IDs 57, 53 and 54 in addition to the normal mouse X/Y reports.

Floe

P.S. evtest is in joystick package.

---

### Post by zythar on 2010-04-23
> **jeffeulogy said:**
> is there hot air coming out of the fan vent? laptops and netbooks typically run pretty hot and like the previous post said modern processors will throttle back and then shutdown if there's a threat of heat damage. if the air coming out of the vent is cool though, it's an issue with a bios setting or acpi causing the fan to run needlessly. it won't hurt your computer but it will affect your battery life.

there hot air is coming.
> 
No, that rather means that almost no software is able to deal with the  additional data.
Try 'sudo evtest /dev/input/eventX' (you have to do a bit of trial and  error to find out which X is your touchscreen). When the dual-touch is  working properly, you should be seeing various reports with IDs 57, 53  and 54 in addition to the normal mouse X/Y reports.

Floe

P.S. evtest is in joystick package. 	

here is output of evtest (part of it. there is more but they are practically identical):

```

Event: time 1272024393.598564, type 3 (Absolute), code 57 (?), value 2
Event: time 1272024393.598595, type 3 (Absolute), code 53 (?), value 607
Event: time 1272024393.598605, type 3 (Absolute), code 54 (?), value 2648

```

---

### Post by floem on 2010-04-24
> **zythar said:**
> here is output of evtest (part of it. there is more but they are practically identical):

```

Event: time 1272024393.598564, type 3 (Absolute), code 57 (?), value 2
Event: time 1272024393.598595, type 3 (Absolute), code 53 (?), value 607
Event: time 1272024393.598605, type 3 (Absolute), code 54 (?), value 2648

```
Looks good - these are the in-kernel multitouch reports (57 is finger ID, 53 is X, 54 is Y).
So now you either need a) software which can read /dev/input/eventX directly and make sense of it or b) Xserver 1.7 (which is going to be in Lucid) + a very recent version of xf86-input-evdev (I'm not sure if this will be in Lucid or not).

Floe

---

### Post by zythar on 2010-04-24
> **floem said:**
> Looks good - these are the in-kernel multitouch reports (57 is finger ID, 53 is X, 54 is Y).
So now you either need a) software which can read /dev/input/eventX directly and make sense of it or b) Xserver 1.7 (which is going to be in Lucid) + a very recent version of xf86-input-evdev (I'm not sure if this will be in Lucid or not).

Floe

can you recommend me some software for multitouch?
my xserver-xorg-core is 1.7.6 version and xserver-xorg-input-evdev (i don't have xf86-input-evdev) is 2.3.2.

---

### Post by zythar on 2010-04-24
have anyone problems with microphone and line in/out?
my microphone is not working at all.
when i insert mic or headset into jacks that are placed on left side of notebook, mic is not working too and sound is listened only from speakers, not from headset. i'm running custom kernel. maybe i have forgotten to enable some modules? what should be enabled for working jacks and mic?

ps i am running custom kernel on debian unstable too, and there is practically identical configuration, but i have got working jacks there.

---

### Post by ehabh on 2010-04-24
Usefull tablet programs on ubuntu


fennec
This is the mobile version of firefox, ultra finger friendly, needs about one hour to get used to.

onboard
Virtual keyboard, far from perfect but the best i could find for now.

---

### Post by zythar on 2010-04-27
> **zythar said:**
> have anyone problems with microphone and line in/out?
my microphone is not working at all.
when i insert mic or headset into jacks that are placed on left side of notebook, mic is not working too and sound is listened only from speakers, not from headset. i'm running custom kernel. maybe i have forgotten to enable some modules? what should be enabled for working jacks and mic?

ps i am running custom kernel on debian unstable too, and there is practically identical configuration, but i have got working jacks there.

i've tried to use kernel, that shipped with ubuntu, but there was  difference. same situation with internal mic and with jacks.

---

### Post by zythar on 2010-04-27
problems with jacks solved by adding to /etc/modprobe.d/alsa-base.conf followinf line:
options snd-hda-intel model="olpc-xo-1_5".
problem with internal mic is still waiting for solution.

---

### Post by zythar on 2010-04-28
i see thread is dead, yeah?
any case, i steel have problem with cpu temperature.
about 30 min ago i turned on netbook, logged in and runned gkrellm (to monitor cpu temperature)
nothing else was opened by me, no work was doing on netbook. it just lay on wood table.
during that 30 min cpu temperature increased from 50 C (also a question: why cpu temperature is 50 C on startup if it was turned of for about an hour) from 55 C.
i still worry about it. there was no such problem under win7.

---

### Post by bobpaul on 2010-04-28
How hot does it run in Win7? Does it feel warmer (back is hot, fans run more often, etc) or could it simply be the sensor isn't being read accurately?

---

### Post by zythar on 2010-04-29
> **bobpaul said:**
> How hot does it run in Win7? Does it feel warmer (back is hot, fans run more often, etc) or could it simply be the sensor isn't being read accurately?

in win7 it was about 34 C when i was not working on laptop.
about sensors: i don't know. it is for first time that i am dealing with such type of programs.

---

### Post by bobpaul on 2010-04-29
> **zythar said:**
> in win7 it was about 34 C when i was not working on laptop.
about sensors: i don't know. it is for first time that i am dealing with such type of programs.

If the battery life when idle is a lot better on Win7 than Ubuntu, or if the computer feels noticeably warmer/fans run more often (does this model even have fans?) it probably is running hotter.

But if the battery life is similar or it doesn't feel any hotter, it could be an issue with lm-sensors, libsensors, or whatever you're using to read the tempsensors with.

---

### Post by ttk153 on 2010-04-30
Alright, I just got one of these last night.

Thanks to this thread I was able to get the touchscreen working.

I also added fennec (awesome on a touchscreen) and onboard.

I am now working on screen rotation. I would like to script something like this...

xrandr -o left && xsetwacom set stylus Rotate CCW
exit 0

except we aren't using xsetwacom.  xrandr works to rotate the screen, but I need to rotate the touchsreen driver.  Does anyone know how I could rotate the touchscreen from the command line?

---

### Post by Abu_Dayya on 2010-05-01
I'm very interested in this netvertible, and I find this thread to be very helpful. But before I buy it, I need some questions to be answered. Can you guys help me with them?

- Does multitouch work? What are the recognized gestures (two-finger scroll, pinch-zoom, etc)?

- Is the screen responsive? Are the gestures fluid and smooth?

- How is the performance of UNR? any noticable lags or hiccups?

- Have anyone tried running Plasma Netbook? how is it?

- How is battery life?

- What hw/components doesn't work? Accelerometer? sound card? 

Thanks guys for your work and effort

---

### Post by ttk153 on 2010-05-01
> **Abu_Dayya said:**
> I'm very interested in this netvertible, and I find this thread to be very helpful. But before I buy it, I need some questions to be answered. Can you guys help me with them?

- Does multitouch work? What are the recognized gestures (two-finger scroll, pinch-zoom, etc)?

- Is the screen responsive? Are the gestures fluid and smooth?

- How is the performance of UNR? any noticable lags or hiccups?

- Have anyone tried running Plasma Netbook? how is it?

- How is battery life?

- What hw/components doesn't work? Accelerometer? sound card? 

Thanks guys for your work and effort

The screen is responsive and the touchscreen works well, but I don't have multi touch working.  The netbook remix runs very smooth for me.  Batter life is at 4-5 hours for me, and I have the 8 cell battery.  I don't have the accelermoter working, I don't know about the sound/microphone yet.  I haven't tried, but most of my sound issues are usually fixed by compiling the latest alsa driver.

After seeing the lenovo U1 below, I am kind of wishing I would have waited.  It will probably cost a bit more, but I am thinking it may have been worth the wait.

[http://www.engadget.com/2010/01/05/lenovo-ideapad-u1-hybrid-hands-on-and-impressions/](http://www.engadget.com/2010/01/05/lenovo-ideapad-u1-hybrid-hands-on-and-impressions/)

---

### Post by Abu_Dayya on 2010-05-01
Yeah, the U1 looks awesome, but how do we run ubuntu on it? On netbook mode or tablet mode? Or both? Anyway, it does look very futuristic. I'm sure some ubuntu gurus will put their hands on it and get it to work :)

Thanks for the answers btw. Why don't you have multitouch? Havnt you tried the .34 kernel patch?

---

### Post by floem on 2010-05-02
> **ttk153 said:**
> except we aren't using xsetwacom.  xrandr works to rotate the screen, but I need to rotate the touchsreen driver.  Does anyone know how I could rotate the touchscreen from the command line?

If you're using Lucid already, then it's pretty easy: the evdev driver has two properties called "Evdev Axis Inversion" and "Evdev Axes Swap". You can set them with
```

xinput set-prop --type=int --format=8 15 "Evdev Axis Inversion" 0 0
xinput set-prop --type=int --format=8 15 "Evdev Axes Swap" 0

```(of course, you need to choose appropriate values depending on your screen rotation).

EDIT: oops, I forgot: the number 15 is the device ID which you see in "xinput list --short". You can also use the entire name "Cando Corporation Cando 10.1 Multi Touch Panel with Controller" instead (in quotes).

Floe

---

### Post by xanadu1988 on 2010-05-02
I got my s10-3t's touchscreen working with the script posted in this thread (post #36), but I'm still getting the mouse jumping to (0,0) that was mentioned earlier in this thread.. has anyone found a way to fix this? Will the kernel patch solve this problem?

---

### Post by floem on 2010-05-04
> **xanadu1988 said:**
> I got my s10-3t's touchscreen working with the script posted in this thread (post #36), but I'm still getting the mouse jumping to (0,0) that was mentioned earlier in this thread.. has anyone found a way to fix this? Will the kernel patch solve this problem?
Yes, very likely. With Lucid, it's even a little easier to install the patch; you just have to replace the three modules hid.ko, usbhid.ko and hid-cando.ko in /lib/modules/. Of course, you can still take the dpkg route (and that's possibly a little less error-prone).

Florian

---

### Post by manthony121 on 2010-05-04
I tried installing fennec on my s10-3t, but it stops with a Segmentation Fault when I try to run it.  Are there any other browsers that are better for people with fat finger tips?

---

### Post by manthony121 on 2010-05-05
Wifi is DEAD!!!

Last night, a routine update installed some new kernel related files, and now my wifi won't work!  Looking at "/boot", the only new file is "initrd.img-2.6.31-21-generic", dated 2010-05-04.  The kernel image, "vmlinuz-2.6.31-21-generic" is dated 2010-03-24.
Looking at Synaptic History, last night (2010-05-04) saw an update of files, linux-generic(2.6.31.20.33) to 2.6.31.21.34.  Also, linux-headers-generic and linux-image-generic with the same version numbers.  NEW files added were linux-headers-2.6.31-21, linux-headers-2.6.31-21-generic, and linux-image-2.6.31-21-generic.

When I boot the default kernel, 2.6.31-21-generic, my wifi NIC is not recognized.  If I boot to the previous kernel, 2.6.31-20-generic, everything works fine.

To get my NIC working in the first place, I had to compile the drivers from the source code provided by Broadcomm, as described earlier in this thread.  As before, there is no listing for the Broadcomm device under the Hardware Drivers app.

Does this mean I have to re-compile the drivers with the new kernel-headers?  Has the new kernel image really been on my computer since 2010-03-24, or was it put on last night?  I'm not sure what the relationship is between the files as named in /boot, and the files as named in Synaptic.

---

### Post by masak on 2010-05-05
```
xinput set-prop --type=int --format=8 15 "Evdev Axis Inversion" 0 0
xinput set-prop --type=int --format=8 15 "Evdev Axes Swap" 0
```

Hi, this commands NOT WORK! on hidtouch. I'm confused because I need vertical screen for my project only. I don't know how to invert axe. To swap axis is only need to swap value in OpcodeY and OpcodeX. 

Any Ideas? I think that driver for hidtouch has no option for invert axe. This is really stupid...

---

### Post by zythar on 2010-05-08
i want to make my screen rotate button get worked, but...
i found that my keyboard's event file is /dev/event5.
when i do "sudo cat /dev/event5" and press on keyboard's buttons i see some symbols there.
also, i see symbols when i press mute button, but there is nothing if i press screen rotate button.

---

### Post by ehabh on 2010-05-15
Hey anybody that got multitouch to work, is it any good? Does it have any extras worth the effort?

---

### Post by gare on 2010-05-16
> **ttk153 said:**
> 

After seeing the lenovo U1 below, I am kind of wishing I would have waited.  It will probably cost a bit more, but I am thinking it may have been worth the wait.

[http://www.engadget.com/2010/01/05/lenovo-ideapad-u1-hybrid-hands-on-and-impressions/](http://www.engadget.com/2010/01/05/lenovo-ideapad-u1-hybrid-hands-on-and-impressions/)


Thank you for this heads up. The Demo says this device will be running Linux by default.  Exciting! :guitar:

---

### Post by jeffeulogy on 2010-05-16
i think skylight is yet another gimped distro trying to appeal to the masses. kind of like all those quickstart OS's floating around. it should provide a good starting point for real linux support though.

all i want is a bigger and slightly faster version of my phone (mytouch 3g). everybody has one in the works but nothing has materialized yet. the day i can buy a well made 7" tablet running android or some flavor of proper linux is the day my s10-3t goes on craigslist.

---

### Post by SomeoneE1se on 2010-05-18
> **floem said:**
> Yes, very likely. With Lucid, it's even a little easier to install the patch; you just have to replace the three modules hid.ko, usbhid.ko and hid-cando.ko in /lib/modules/. Of course, you can still take the dpkg route (and that's possibly a little less error-prone).

Florian

what's the dpkg route?

---

### Post by Kraggash on 2010-05-18
Hello  everyone. Thanks to this forum thread on my S10-3t  earned the third  single touch, it is very good. Found more additional information for multi-touch:
 [http://lii-enac.fr/en/projects/shareit/xorg.html](http://lii-enac.fr/en/projects/shareit/xorg.html)
> *Cando Multi Touch*. Capacitive panel, available in the Lenovo S10-3t netbook and the Acer Timeline 1825PTZ. Two fingers. Its HID protocol is a subset of the Windows 7 protocol (no Confidence  field).  Linux kernel driver available [here]("http://lii-enac.fr/en/projects/shareit/hid-cando.c"), and submitted for release in 2.6.34 or 2.6.35. I  understood offer a free driver for Cando Multi Touch. Sorry  for my english, &#1084;aybe this information :)

---

### Post by ehabh on 2010-05-19
I do not know if others are having this same problem, I am on the netbook remix and all system windows like when you shut down it ask you do you really want to shut down, are always shown below the current window.

Just to explain the above, if I am using firefox and from the top toolbar I select shutdown, what i see is that nothing happens. But in reality there is the shutdown dialog blow firefox that only shows if I close firefox. These dialogs should be above not below other apps. 

Is this happening only with me or are the norm?

---

### Post by roofies on 2010-05-19
Guys can any of you confirm if Ubuntu is working well with the S10-3t ? i mean touchscreen, wifi and so on. I really want to install it on mine but I'm not linux expert. Thanks!

---

### Post by SomeoneE1se on 2010-05-19
> **roofies said:**
> Guys can any of you confirm if Ubuntu is working well with the S10-3t ? i mean touchscreen, wifi and so on. I really want to install it on mine but I'm not linux expert. Thanks!
roofies, I've just installed 10.04 and with the use of the script in post #36(?) I've got everything working (haven't tested a few things) 

wifi works but you'll need a wired connection to install the extra driver

---

### Post by roofies on 2010-05-19
> **SomeoneE1se said:**
> roofies, I'v
e just installed 10.04 and with the use of the script in post #36(?) I've got everything working (haven't tested a few things) 

wifi works but you'll need a wired connection to install the extra driver

Woot! I'm gonna start downloading it now. thanks SomeoneE1se.

---

### Post by roofies on 2010-05-19
I've installed successfully and got my wifi working via update. I tried following the instructions to get the touchscreen working on post #36 , but I haven't been successful (because of my ignorance).

I downloaded the zip, unzipped it to the desktop. Opened a console session and ran this:

sudo apt-get install xserver-xorg-dev

which results in:
E: Couldn't find package xserver-org-dev

after that I tried:

./configure --prefix=/usr

but the result is

No package 'org-server' found
No package 'proto' found

Can someone help me with some step by step instructions? I would be eternally grateful :KS

---

### Post by SomeoneE1se on 2010-05-19
you misspelt xserver-Xorg-dev
you missed the X in xorg 
( I think )

---

### Post by roofies on 2010-05-19
> **SomeoneE1se said:**
> you misspelt xserver-Xorg-dev
you missed the X in xorg 
( I think )

You were right, thanks. After getting all of the steps done without any errors all the way to the sudo make install part, I rebooted but the touch screen isn't working still. Do i need to do anything else after this?

---

### Post by moftasa on 2010-05-21
I'd like to thank almost everyone for tinkering with the touchscreen and posting the information here, this helped me get the touchscreen working. It is currently working single touch, very usable at the moment but occasionally it gets a nervous 'tic' and the pointer jumps to 0,0 (or shoots to other corner) for a millisecond and comes back .. this makes thing jittery when you scroll, drag or sketch something e.g. in Xournal. 

I also wanted to write down the issues that I still have with the Lenovo s10-3t running UNR Lucid:

[LIST=1]
[*]Internal microphone not working
[*]When I log out, it fails to log back in. I think this started after I [applied the symlinks to unlock the panel in UNR]("http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25"). I wanted to change the size of the panel so they can be easier to touch.
[*]For some odd reason, when I run the Mouse settings in the preferences Linux crashes.
[*]I want the multimedia keys on the left side of the screen working.
[*]Onboard refuses to detect the second language layout (Arabic) with the gnome language selector but happily does it when I 'setxkbcomp ar' don't know where to file a bug report on this one.
[*]The jittery touch screen or multi-touch.
[/LIST]

Honestly, after fixing all of the above this device will be a DREAM.

---

### Post by ehabh on 2010-05-21
Are you also getting the odd issue that system prompts like shutdown dialog open below the current window?

> **moftasa said:**
> I'd like to thank almost everyone for tinkering with the touchscreen and posting the information here, this helped me get the touchscreen working. It is currently working single touch, very usable at the moment but occasionally it gets a nervous 'tic' and the pointer jumps to 0,0 (or shoots to other corner) for a millisecond and comes back .. this makes thing jittery when you scroll, drag or sketch something e.g. in Xournal. 

I also wanted to write down the issues that I still have with the Lenovo s10-3t running UNR Lucid:

[LIST=1]
[*]Internal microphone not working
[*]When I log out, it fails to log back in. I think this started after I [applied the symlinks to unlock the panel in UNR]("http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25"). I wanted to change the size of the panel so they can be easier to touch.
[*]For some odd reason, when I run the Mouse settings in the preferences Linux crashes.
[*]I want the multimedia keys on the left side of the screen working.
[*]Onboard refuses to detect the second language layout (Arabic) with the gnome language selector but happily does it when I 'setxkbcomp ar' don't know where to file a bug report on this one.
[*]The jittery touch screen or multi-touch.
[/LIST]

Honestly, after fixing all of the above this device will be a DREAM.

---

### Post by moftasa on 2010-05-21
@ehabh No.

---

### Post by zythar on 2010-05-21
> **moftasa said:**
> I'd like to thank almost everyone for tinkering with the touchscreen and posting the information here, this helped me get the touchscreen working. It is currently working single touch, very usable at the moment but occasionally it gets a nervous 'tic' and the pointer jumps to 0,0 (or shoots to other corner) for a millisecond and comes back .. this makes thing jittery when you scroll, drag or sketch something e.g. in Xournal. 

I also wanted to write down the issues that I still have with the Lenovo s10-3t running UNR Lucid:

[LIST=1]
[*]Internal microphone not working
[*]When I log out, it fails to log back in. I think this started after I [applied the symlinks to unlock the panel in UNR]("http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25"). I wanted to change the size of the panel so they can be easier to touch.
[*]For some odd reason, when I run the Mouse settings in the preferences Linux crashes.
[*]I want the multimedia keys on the left side of the screen working.
[*]Onboard refuses to detect the second language layout (Arabic) with the gnome language selector but happily does it when I 'setxkbcomp ar' don't know where to file a bug report on this one.
[*]The jittery touch screen or multi-touch.
[/LIST]

Honestly, after fixing all of the above this device will be a DREAM.

well, for now you CAN have multitouch (actually, only dual-touch).
_http://lii-enac.fr/en/projects/shareit/xorg.html. i have tried it, and all works fine, except that gnome doesn't support mpx (multi pointer) and it is freezing desktop often.

ps there is small patch that you must apply before compiling multitouchd, in other case you will get very bad error (*
i can post it, if needed.

pps actually i am running debian squeeze (*

---

### Post by sargunster on 2010-05-25
Could someone post a step-by-step tutorial on getting the wifi and the touch screen working for noobs? Starting with which version of Netbook Remix to install.

---

### Post by roofies on 2010-05-25
> **sargunster said:**
> Could someone post a step-by-step tutorial on getting the wifi and the touch screen working for noobs? Starting with which version of Netbook Remix to install.

+1 on this request. I know a lot about many technologies but Linux has always been my major weakness. Now, how about that guide, pretty please?

---

### Post by sargunster on 2010-05-25
According to here theres an easy way to get wifi working.
[http://blarneyrabble.wordpress.com/2010/04/27/ubuntu-lucid-rc-netbook-remix-on-a-lenovo-s10-3t-touchscreen-netbook/](http://blarneyrabble.wordpress.com/2010/04/27/ubuntu-lucid-rc-netbook-remix-on-a-lenovo-s10-3t-touchscreen-netbook/)

> I want my wifi.  With the ethernet connected, I click System-Administration-Hardware Drivers and then I click Activate for the Broadcom STA Driver. It starts Downloading and installing driver&#8230;

It&#8217;s done, within 20 minutes from the time I first clicked Install Ubuntu Netbook Remix 10.04

I unplug the ethernet, and am able to connect to my access point immediately.
I'm gonna try it. Still need a guide for touchscreen though.

---

### Post by zythar on 2010-05-26
> **sargunster said:**
> Could someone post a step-by-step tutorial on getting the wifi and the touch screen working for noobs? Starting with which version of Netbook Remix to install.

actually it is very easy to get working wi-fi on laptop.
you must install bcmwl-source (i don't remember exact name, so google it please) package or download driver from [here](http://www.broadcom.com/support/802.11/linux_sta.php) (also there is very clear readme about how to compile driver. this variant is for people who have custom kernel)

what about working touchscreen, here you must download kernel source and driver, then compile new kernel. it is very easy, though. there is complete manual in previous pages.

ps you could use search for getting answers for your questions.

---

### Post by sargunster on 2010-05-26
Well i got wifi working with an even simpler method. Just check post 157. 
I don't understand how to get the touchscreen working. Can someone post a tutorial for a complete noob to understand?

---

### Post by bioborg on 2010-05-26
[http://ubuntuforums.org/showthread.php?t=1415915&page=9](http://ubuntuforums.org/showthread.php?t=1415915&page=9) post #87
worked for me.  
First  I make sure xserver-xorg-input-evdev is installed, and install xserver-xorg-input-evtouch (but I'm not sure if that helped)
I downloaded the driver in the post from zshare ( [http://www.zshare.net/download/75040081c56f7ba7/](http://www.zshare.net/download/75040081c56f7ba7/) ), unzipped it, and, from the terminal, cd'ed into the directory it unzipped into, then typed ./install.sh

It compiled without error, I had to reboot a few times, and it worked.   You can check out the rest of my trials and tribulations here:
[http://blarneyrabble.wordpress.com/2010/04/27/ubuntu-lucid-rc-netbook-remix-on-a-lenovo-s10-3t-touchscreen-netbook/](http://blarneyrabble.wordpress.com/2010/04/27/ubuntu-lucid-rc-netbook-remix-on-a-lenovo-s10-3t-touchscreen-netbook/)

I have decided I'm cool with singletouch touchscreen right now, as I like my ureadahead fast boot, which I understand I would loose if i installed the 2.6.34 kernel without the ubuntu patches.

---

### Post by sargunster on 2010-05-26
I got it working with the instructions in the comments on your blog (I'm Sargun Vohra)
I just forgot to post back here. 

A couple more questions :)
Is there any way to make the internal mic work? I find it odd that the webcam works but the mic doesn't. 
Is there any fix for the crash when you go into the mouse settings?
Is there any fix for not being able to log in after logging out. Every time I log out, I need to restart.
Is there any way to enable drag-to-scroll for everything, instead of just using extensions for Firefox and Chromium?

EDIT: How did I manage to type "pack" instead of "back"? P and B are really far from each other on the keyboard...

---

### Post by moftasa on 2010-05-26
Upgraded to kernel 2.6.34 ([Downloaded the packages from here including headers]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/")).

Deleted the custom /etc/X11/xorg.conf I created before.
I made sure I have the xf86-input-evdev package installed.

Touchscreen worked but I had to recompile the broadcom wireless kernel module for the new kernel. This was simple following the instructions [here]("http://ubuntuforums.org/showpost.php?p=8989677&postcount=6").

The broadcom driver won't compile unless you open the file include/linuxver.h and change line 23 from

**#include <linux/autoconf.h>**

to
[B]
#include <generated/autoconf.h>[/B]

After this you will get:
[LIST]
Wireless working flawlessly.
[*]Touchpad buttons will stop working but tapping works.
[*]Touchscreen works (in dual-touch which is unintuitive) but when I press on an icon to launch an application it launches 10s of it.
[*]No more cursor flying for milliseconds to 0,0 using the touchscreen.
[*]No more log-in issues (they were related to the earlier touchscreen hack).
[*]No more Gnome mouse settings crash (also related to touchscreen hack).
[/LIST]

I think I need an xorg.conf file that has settings for the touchpad and the touchscreen to adjust their quirky behavior.

---

### Post by Subsanek on 2010-05-27
Thank you all!

---

### Post by sargunster on 2010-05-27
Any chance of getting this to work in Jaunty? I switched over to Jolicloud, and it's based on Jaunty, and the fix posted here doesn't work. One thing I noticed was that when I tap the screen with 2 fingers at the same time, it does a click at the cursor's current position.

---

### Post by Subsanek on 2010-05-28
[COLOR=#000000]Does anyone has  already laid out on YouTube recording of the Lenovo s10-3t on linux???[/COLOR]

---

### Post by arrjay on 2010-05-29
Well, I've been tinkering with this all day and it's been quite an adventure. My experience is this:

I had no trouble getting the single-touch and wi-fi to work on the current kernel. That made me brave for a noob. I'm now on kernel 2.6.34 and unfortunately no farther ahead (well except in terms of learning how to compile modules). In fact I'm a little worse off since the touch no longer tracks, it merely picks up the original location.

What I haven't done yet is try floem's advice in post #90. I think I'll give that a go.

Great thread!!

---

### Post by Subsanek on 2010-05-30
Touchpad works fine then?

---

### Post by arrjay on 2010-05-30
@Subsanek: Touchpad was a little fussy under 2.6.34 but worked okay under the release kernel (I had occasional issues with clicking), but I think I'm just too new at all the module patching and driver config to get it right. 

So I've re-rolled back to the original install and parked the exercise for today (I really had to get some Linear Algebra homework done).

As of this moment wi-fi is fine and I know how to get single-touch under 2.6.33. It does cause the problem others mentioned: namely that the login page gets into a loop if you select your ID with a touch instead of keyboard or touchpad. That's one of the reasons I started exploring the unreleased kernel 2.6.34.

If anybody has any advice on making multitouch stable under 2.6.33 I'm all ears!

I'd really like to get two-touch working. I bought this machine as a prototyping/development platform for work on a larger home-brew multitouch project at university. I can get by on Win 7 (where two-touch does work fine) but I'd much prefer to be in linux. The command line tools are just too good to pass up.

---

### Post by Subsanek on 2010-06-04
Auto turning  display work?

---

### Post by Skaarg on 2010-06-08
I'm using UNR 10.04 with all updates and I followed the instructions in this thread for getting the touch screen working, but I'm still having some problems. When I try to drag the cursor around I have the problem with it jumping to 0,0 like many users mention. I noticed in one of the posts upgrading to 2.6.34 kernel fixes this, but you lose fast boot times. Is there a way to have the fixes on my current kernel or is it a case of choose which is more important to you?

Also another thing I was curious about is when using Windows 7 if I clicked on a something that has text input an icon would pop up so I could open the on screen keyboard. Is there anything like that for Ubuntu. the closest thing I've had so far is using Cell Writers keyboard where I have to click the taskbar icon and show to get a keyboard.

Edit- Another thing I was curious about is in Windows 7 if I held my finger in place for a couple seconds it would act as a right click. Is it possible to enable a feature like this?

Edit 2 - I actually decided to give upgrading to 2.6.34 a shot and the touch screen would only work for single point actions. As in the cursor didn't follow my finger movements. Not to mention stability seemed much worse since often times the Netbook Launcher would lock up or just display a gray screen.

---

### Post by fcomstoc on 2010-06-12
so i have been using my lenovo s10-3t with ubuntu 10.04 netbook for a few weeks now and everything works good (touch, wireless ect,) the only problem i have is that if i rotate the screen using xrandr the touch driver doesnt rotate with it making the rotating screen worthless
has anybody been able to get this to work right 
thanks

---

### Post by zythar on 2010-06-12
> **Skaarg said:**
> 
Edit- Another thing I was curious about is in Windows 7 if I held my finger in place for a couple seconds it would act as a right click. Is it possible to enable a feature like this?


in gnome:
1. System -> Preferences -> Mouse -> Accessibility.
2. check the "Trigger secondary..."
3. ???
4. PROFIT

---

### Post by GustoEater on 2010-06-14
Just got my S10-3t this weekend.  I've worked out most of these solutions with Netbook Remix, but I realized that I'm not actually able to right click with the trackpad (is it actually a Synaptics Clickpad?).  Clicking the left side doesn't work either, only a tap to the pad works.

I was ready to dump Netbook Remix for standard Ubuntu becuase something wasn't feeling right when I realized this was the issue.

Anyone else have this problem?

---

### Post by novabox on 2010-06-16
Just wanted to chip in my input on this.  I've seen most of the posts dealing with patching the kernel.  

I'm using 10.04 Netbook on my s10-3t.  I upgraded the kernel to 2.6.34, which includes the touchscreen driver by default.  Follow this thread for the details, including getting the wireless working again:
[http://ubuntuforums.org/showthread.php?t=1488795](http://ubuntuforums.org/showthread.php?t=1488795)

I found this easier than patching the kernel, or messing about with xorg.

So far, everything's working except:
- No multitouch
- Can't get mouse dragging to work
- No screen rotation.

Everything else is perfect.

---

### Post by novabox on 2010-06-16
Gustoeater:
I have the same issue.  Clicks no longer work.  However, if you tap in the lower right of the touchpad, it should interpret that as a right-click.

---

### Post by nix.peter on 2010-06-16
I'd really love to see full support for this in the future which im sure there will be. We have to keep in mind that this is a fairly new netbook/tablet. Congrats to the progress you all have made and i'll definitely be following this thread.

I'm actually posting from my Lenovo Tablet as we speak but in windows :/

This tablet rocks and as soon as I see all features working in Linux, i'll be going to Linux (ubuntu hopefully) asap. I'm seeing more support in the next ubuntu release, anyone else feel the same?

---

### Post by GustoEater on 2010-06-16
> **novabox said:**
> Gustoeater:
I have the same issue.  Clicks no longer work.  However, if you tap in the lower right of the touchpad, it should interpret that as a right-click.

Thanks, Novabox.  I'll give that a shot.  I also found some information on this.  Take a look at [http://community.saugususd.org/swattec/page/Synaptics+Clickpads](http://community.saugususd.org/swattec/page/Synaptics+Clickpads) 

Unfortunately, I've switched to Meego instead of Ubuntu for the moment, so I haven't tried this fix.  If it works, I'll probably switch back (Meego boots in just a few seconds though, that's going to be tough to give up).

---

### Post by zythar on 2010-06-18
> **GustoEater said:**
> Just got my S10-3t this weekend.  I've worked out most of these solutions with Netbook Remix, but I realized that I'm not actually able to right click with the trackpad (is it actually a Synaptics Clickpad?).  Clicking the left side doesn't work either, only a tap to the pad works.

I was ready to dump Netbook Remix for standard Ubuntu becuase something wasn't feeling right when I realized this was the issue.

Anyone else have this problem?

```

zythar@nirvana-nb:~$ cat /etc/modprobe.d/psmouse.conf 
options psmouse proto=imps
zythar@nirvana-nb:~$ 

```

clicks work, but no vertical scrolling with touchpad

---

### Post by Subsanek on 2010-06-18
[http://www.youtube.com/watch?v=mLz_3SoVSKI](http://www.youtube.com/watch?v=mLz_3SoVSKI)

---

### Post by nix.peter on 2010-06-18
That looks very nice! Think that kernel version has something to do with his success?

---

### Post by nix.peter on 2010-06-18
[http://thenextweb.com/mobile/2010/06/11/ubuntu-multitouch-os-coming-for-tablets-next-year/](http://thenextweb.com/mobile/2010/06/11/ubuntu-multitouch-os-coming-for-tablets-next-year/)

Thats probably going to be our best bet I would think. It does mention that it will be built off of 10.10, which makes me think we can do 10.10 UNR and things should go smoother. Don't take my word for it though!

---

### Post by Subsanek on 2010-06-19
> **nix.peter said:**
> That looks very nice! Think that kernel version has something to do with his success?

[COLOR=#000000]Yes. [/COLOR]linux 2.6.34  or higher solves many problems.

---

### Post by psi_lizard on 2010-06-19
First, I'd like to thank everyone who has shared so much information about this, it has been very helpful. 

Second, I'd like to add an observation of my own. In 2.6.34, the cursor remains stationary, allowing you to tap for point and click, but not do things like draw windows and scroll bars. It seems that the mouse will follow your finger and allow you to drag only after you put a second finger on the screen. I have found that in the 2.6.35 rc3 kernel, this is fixed, the mouse will follow your finger as you glide on the screen allowing you to scroll, drag and drop and all of that fun stuff.

---

### Post by Subsanek on 2010-06-19
So wait for linux 2.6.35

---

### Post by nix.peter on 2010-06-19
so basically the kernel will fix our touch screen issues which is really the only thing holding me back at this point. When will 35 become available? Will there be multi-touch in this or future versions?

I have much googling to do :)

---

### Post by nix.peter on 2010-06-20
Ok guys I have done some testing and kernel 2.6.35 rc3 worked great! I installed headers(All pack) and kernel(i386) from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/)

Then rebooted and bam touch and drag works with the touchscreen. Touch Pad is still only double tap and no right click. Wireless doesn't work either and i couldn't get it to compile from the directions posted here, which was directions for 2.6.34 i believe. 

I also noticed that I cant enable any desktop effects on any kernel version either. Does anyone know whats going on with the graphic driver?

Is there a virtual keyboard available for UNR as well?

I have to say that UNR is the way to go on this tablet. Internet is about 5X faster and touch web navigation is so smooth. This is comparing to windows 7. Also HD movie and music is way faster to load-up and playback.

Its late now so I will do more testing tomorrow. :p

---

### Post by Subsanek on 2010-06-20
Is there a virtual keyboard available for UNR as well?

[http://linuxnow.ru/view.php?id=54](http://linuxnow.ru/view.php?id=54)

---

### Post by quantacat on 2010-06-20
Hey everyone.  I tried thevillage88's installation file from post #33 and it worked like a miracle!  I used 10.04 2.6.32-22-generic.  The touchscreen works well.  Although it jumps around a little bit, it doesn't seem as bad as what is discussed here.  I can drag and carry, it follows my finger, etc. Also, the touchpad works completely fine.  The only things that aren't working are:
1. rotating the screen
2. the internal microphone
3. dual-touch
Anyone have a way to get these three things working?

Anyway, post #33 was a super fast way to get my screen working on single touch and I'm pretty much a newb. (this was all shockingly easy for me)

Thanks to everyone (esp. thevillage88) for helping me get this awesome little netbook running.  Windows 7 almost drove me mad....

---

### Post by nix.peter on 2010-06-20
Simply amazing thread. So basically whats missing is graphic driver? 

Thanks very much Sub for the keyboard. 

And once i figure out how to get my wireless working under 2.6.35 i will be able to switch! :guitar:

This has a Intel GMA 3150 correct?

---

### Post by nix.peter on 2010-06-22
So I tested UNR to the max and came to the conclusion that I going to wait until things get finalized which is when Maverick is released. However I will share what I discovered :)

I got the graphics card working with a newer driver and had full desktop effects working great. Installed both built files here [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.11.0-1ubuntu1/+build/1780782](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.11.0-1ubuntu1/+build/1780782)

and rebooted, installed compiz in software center and desktop effects were able to be turned on.

I also found a virtual keyboard right the software center as well.

I also used Kernel 2.6.35 to have touch screen and touch drag working. So the only major thing i couldn't get to work was the wireless. Researched some and read here how the driver doesn't compile under 2.6.35. [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/590924](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/590924)

It just seems as of right now, things are just still not fully ready yet in the current release. It doesn't mean it wont work, it just takes some time to get it working right. Good news is they are working very quickly and when maverick comes around this device and others will all have decent out of the box support.

If anyone has any suggestions wit getting the wireless driver working under 2.6.35 i'm all ears. One thing i cant get over is  google chrome with touch extension. In windows its very laggy and slow while in Ubuntu its so smooth navigating and loading pages, its almost that reason alone is worth switching over to.

---

### Post by Subsanek on 2010-06-22
Please tell me how to get wi-fi and touch  screen?
I can not = (

---

### Post by GustoEater on 2010-06-22
I went back to Ubuntu and installed the 10.10 Alpha, then updated the system (which installed the 2.6.35 kernel) and touchscreen is working great.  Then I installed the broadcom drivers for wireless and that's working great.

I also set up burg as the bootloader, I was sick of the grub text when I turn on the netbook.

The only things I need now are right-click and click-and-drag working on the touchpad and the Fn keys working for volume, brightness, etc.

10.10 is fantastic...much faster than Windows 7.  Glad I came back to Ubuntu!!

---

### Post by nix.peter on 2010-06-22
How did you install broadcom driver?

Edit: And how did you install 10.10? I cant get into the live environment, it throws some error at me.

---

### Post by GustoEater on 2010-06-23
> **nix.peter said:**
> How did you install broadcom driver?

Edit: And how did you install 10.10? I cant get into the live environment, it throws some error at me.

I had trouble with 10.10 once, but re-downloaded it and put it on an SD card, it installed fine.  You can also update 10.04 to 10.10 with "update-manager -d" I think.

Once you've updated 10.10 (to give you the 2.6.35 kernel), you'll get a hardware driver icon in the panel, just click on that and it will install the broadcom driver (you just have to accept the fact that it's not open source).  Make sure you have an ethernet connection to the internet otherwise you won't be able to download it.

You have to update the kernel (just through Update Manager) first, otherwise the broadcom drivers won't work for the new kernel.

---

### Post by nix.peter on 2010-06-23
I actually got 10.10 to run by alternate install and i absolutely hated it lol. The unity bar is way too glitchy for my taste right now. 

I might try to reinstall to see if maybe I had a bad install, but like i said earlier, when 10.10 gets more finalized im sure it will be much better.

---

### Post by Skaarg on 2010-06-23
I tried upgrading from Ubuntu Netbook Edition 10.04 to 10.10 Alpha 1 and it installed, but when it boots it loads grub where I see it has Ubuntu with kernel 2.6.35, but after selecting it my screen flashes on and off a few times and then turns off. I tried pressing ctrl+alt+f1 to see if I'd get any terminal output, but nothing seems to change anything.

What's weird is there's still the option to boot with Kernel 2.6.32-22 which boots, but the touch screen doesn't work.

Should I maybe try doing a clean install? I haven't been saving anything to my Ubuntu partition yet since it wasn't fully working yet.

---

### Post by nix.peter on 2010-06-24
Im going to wait for Alpha 2 and hopefully it'll be smoother. A fresh install is best however were dealing with new hardware and software thats not official yet.

---

### Post by nnutter on 2010-06-24
Here is what I did to get 2.6.35 installed with Wi-Fi working.

Pros of 2.6.35:
[LIST]
[*]touch!
[/LIST]

Cons:
[LIST]
[*]suspend/resume breaks
[*]"physical" touchpad buttons don't work (but taps still do)
[/LIST]

```
sudo apt-add-repository ppa:kernel-ppa/ppa
sudo aptitude update
sudo aptitude install linux-generic-lts-backport-maverick linux-headers-generic-lts-backport-maverick
```

Get the latest [deb]("http://launchpadlibrarian.net/49947024/bcmwl-kernel-source_5.60.48.36%2Bbdcom-0ubuntu5_i386.deb") for [bcmwl-kernel-source from Maverick]("https://launchpad.net/ubuntu/maverick/+package/bcmwl-kernel-source") as it contains fixes for the failed building and missing files. Then install it either by double clicking on it to launch gdebi or use the command line:

```
sudo dpkg -i bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
```

Reboot and try tapping on the screen when you get to the login window. We should probably open a bug report for the suspend/resume problem but I don't know what information to collect for them.

---

### Post by Skaarg on 2010-06-24
I did a clean install of 10.10 Alpha 1 and updated to have the 2.6.35-5 kernel, and touch is working perfect for me, but whenever I try opening the applications window (uses file browser) it locks up after loading everything, making it impossible for me to launch any programs especially since for some reason alt+F2 doesn't bring up run prompt. Is anybody else having this problem and even better have a solution for this?

---

### Post by xanadu1988 on 2010-06-24
Okay so I got rotation working by editing some random script for a HP laptop. I'm pretty sure this requires the kernel patch and if you don't notice you have to lookup the device id of your touchscreen! 

```
xinput --list --short
``` to find that out

So just copy and paste this into a new file, change your device number and save it as rotator.sh wherever

```

#!/bin/sh
#
# enhanced rotate script, based on rafiyr's http://ubuntuforums.org/showpost.php?p=9133869&postcount=918
# and others (gathered on forums).
# Added rturn & lturn, to rotate screen left/right a quarter turn at a time (mainly
# because default hp-wmi module was not returning an 'event' for the 'Rotate' button on the bezel of my tx2z).
#
# This script can be 'attached' to a 'rotate' applet on the panel (w. 90° rotation).
#     with (for example) command: ...../rotator.sh rturn evdev touch wacom stylus
#
# Usage: rotator.sh   direction|position    method  device    [...]
#
# where:    direction = (lturn|l|rturn|r|right|left|normal|inverted)
#        method = (wacom|evdev)
#        device = (stylus|touch)
#

syntax_error=0

orientation=$1
shift

#
# Parse & get current orientation, and do integer conversion (in order to be
# able to (in/de)crement for each 90° rotation, also needed later for 'easier' comparison)
#
current_orientation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"
case $current_orientation in
    normal)
        current_orientation=0
    ;;
    left)
        current_orientation=1
    ;;
    inverted)
        current_orientation=2
    ;;
    right)
        current_orientation=3
    ;;
esac

#
# Parse the orientation parameter & in case of 'rturn' and 'lturn', check the current
# orientation and make sure that the next value is within bound.
#
case $orientation in
    rturn | r)
        orientation=$((current_orientation-1))
        if [ $orientation -le "-1" ]; then
            orientation=3
        fi
    ;;
    lturn | l)
        orientation=$((current_orientation+1))
        if [ $orientation -ge "4" ]; then
            orientation=0
        fi
    ;;
    normal | 0)
        orientation=0
    ;;
    left | 1)
        orientation=1
    ;;
    inverted | 2)
        orientation=2
    ;;
    right | 3)
        orientation=3
    ;;
    * )
        syntax_error=1
    ;;
esac

#
# Check if new orientation is different from current one.
#
if [ $orientation -eq $current_orientation ]; then
    echo "Nothing to do."
    exit
fi

#
# repeat the device rotation/calibration for all devices passed as parameters
#

    # get and (crudely) parse method for errors
    method=evdev

    #
    # get and (crudely) parse device for errors
    # and convert device name to number
    # LENOVO S10-3t CHANGE ==> Hard Coded my device number to 11!!
    device=11

    if [ $syntax_error -ne 0 ]; then
        echo "Usage: `basename $0` Direction|Orientation   Method Device  [...]"
        echo "\tdirection = (lturn|l)|(rturn|r)|(right|3)|(left|1)|(normal|0|(inverted|2)"
        echo "\tMethod: (wacom|evdev)"
        echo "\tDevice: (stylus|touch)"
        exit 1
    fi

    #
    # Set rotation plane/geometry parameters, and if using "wacom"
    # method, also perform device/calibration rotation
    #
    swap=0
    invert_x=0
    invert_y=0

    real_topx=0
    real_topy=0
    real_bottomx=4020
    real_bottomy=4020

    case $orientation in
        0)
            swap=0
            invert_x=0
            invert_y=0
            topx=$real_topx
            topy=$real_topy
            bottomx=$real_bottomx
            bottomy=$real_bottomy
        ;;
        1)
            swap=1
            invert_x=1
            invert_y=0
            topx=$real_topx
            topy=$real_topy
            bottomx=$real_bottomy
            bottomy=$real_bottomx
        ;;
        2 )
            swap=0
            invert_x=1
            invert_y=1
            topx=$real_topx
            topy=$real_topy
            bottomx=$real_bottomx
            bottomy=$real_bottomy
        ;;
        3 )
            swap=1
            invert_x=0
            invert_y=1
            topx=$real_topx
            topy=$real_topy
            bottomx=$real_bottomy
            bottomy=$real_bottomx
        ;;
    esac

    #
    # If using "evdev" method, adjust the device (touch/calibration) accordingly
    #
    if [ $method = "evdev" ]; then
        xinput set-prop "$device" "Evdev Axes Swap" $swap
        xinput set-prop "$device" "Evdev Axes Swap" $swap
        xinput set-prop "$device" "Evdev Axis Inversion" $invert_x $invert_y
        xinput set-prop "$device" "Evdev Axis Calibration" $topx $bottomx $topy $bottomy
        if [ $orientation = 2 ]; then        
            xrandr -o inverted
        fi
        if [ $orientation = 0 ]; then
            xrandr -o normal
        fi
    fi

#

```To run the script open up a terminal, go to the directory the script is stored in and type 
```
sh rotator.sh inverted
``` and to put it back
```
sh rotator.sh normal
```It works great on my s10-3t running 10.10 alpha 1... If someone wants to edit this script to get 90-degree rotations working feel free. I really have no need for it.

---

### Post by xanadu1988 on 2010-06-24
and before anyone asks -- no i don't know how to bind it to the physical button.

---

### Post by Subsanek on 2010-06-24
Only me with headphones, the  sound still comes from the speakers?

---

### Post by xanadu1988 on 2010-06-25
> **Subsanek said:**
> Only me with headphones, the  sound still comes from the speakers?

perhaps this will help?
[http://ubuntuforums.org/showpost.php?p=9182027&postcount=123](http://ubuntuforums.org/showpost.php?p=9182027&postcount=123)

---

### Post by Subsanek on 2010-06-25
> **xanadu1988 said:**
> perhaps this will help?
[http://ubuntuforums.org/showpost.php?p=9182027&postcount=123](http://ubuntuforums.org/showpost.php?p=9182027&postcount=123)

Thank you, as a microphone jack work?

---

### Post by xanadu1988 on 2010-06-25
> **Subsanek said:**
> Thank you, as a microphone jack work?

not that I know of... I haven't really looked into it though.

---

### Post by Subsanek on 2010-06-25
[COLOR=#000000]I just think it worth  to buy a headset with microphone.[/COLOR]

---

### Post by Subsanek on 2010-06-25
[COLOR=#000000]Anybody got a fully working touchpad on  linux 2.6.35?[/COLOR]

---

### Post by inportb on 2010-06-25
> **GustoEater said:**
> I went back to Ubuntu and installed the 10.10 Alpha, then updated the system (which installed the 2.6.35 kernel) and touchscreen is working great.  Then I installed the broadcom drivers for wireless and that's working great.

I also set up burg as the bootloader, I was sick of the grub text when I turn on the netbook.

The only things I need now are right-click and click-and-drag working on the touchpad and the Fn keys working for volume, brightness, etc.

10.10 is fantastic...much faster than Windows 7.  Glad I came back to Ubuntu!!

Thanks for the tip. That works for me. Incidentally, I am able to use the Fn keys for volume and brightness. For right-click, tap (but do not press down) the lower-right corner of the touchpad. I think the middle button is the upper-right corner.

---

### Post by Okar on 2010-06-26
> **GustoEater said:**
> Thanks, Novabox.  I'll give that a shot.  I also found some information on this.  Take a look at [http://community.saugususd.org/swattec/page/Synaptics+Clickpads](http://community.saugususd.org/swattec/page/Synaptics+Clickpads) 

Unfortunately, I've switched to Meego instead of Ubuntu for the moment, so I haven't tried this fix.  If it works, I'll probably switch back (Meego boots in just a few seconds though, that's going to be tough to give up).
what about the touchscreen in meego?
does it work?

---

### Post by GustoEater on 2010-06-26
> **Okar said:**
> what about the touchscreen in meego?
does it work?

Gave up on Meego until the 1.1 version which I think will use the newer kernel and would probably work.  Great interface for a netbook and especially with touch.

---

### Post by Okar on 2010-06-26
ok, I thought of using meego, too. but I read that touch will be not officially be supported before 1.1.

in order to avoid those tics to (0,0) I have to install a newer kernel right?
is there any way of solving this with the standard 10.04 kernel?

---

### Post by nix.peter on 2010-06-26
Yeah install the all headers package here and the i386 generic here. 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/)

worked for me on 10.04.

---

### Post by Okar on 2010-06-27
does suspens/resume and wireless still work with the new kernel?
I will try extracting just the needed modules of those kernel packages later on.

currently everything besides the touchscreen is working fine, just out of the box(wifi, resume/suspend), don't want to mess that up^^
well I haven't tried the

---

### Post by nix.peter on 2010-06-27
Well I finally made the switch. Went from 10.04 to 10.10 via upgrade command in terminal, update everything and bam wireless, touch works great. Even onboard keyboard works well. 

Will update manager update me to alpha 2 when it come out?

Suspend doesn't work but hibernate seems to. And be careful when using those they sometimes don't activate wireless on resume. I'm sure this will be fixed in future releases.

---

### Post by Skaarg on 2010-06-27
> **nix.peter said:**
> Well I finally made the switch. Went from 10.04 to 10.10 via upgrade command in terminal, update everything and bam wireless, touch works great. Even onboard keyboard works well. 

Will update manager update me to alpha 2 when it come out?

Suspend doesn't work but hibernate seems to. And be careful when using those they sometimes don't activate wireless on resume. I'm sure this will be fixed in future releases.

I was using Unity and browsing folders would lock up anytime there was a lot of icons (example the applications window). Did you have this problem too? I did a clean install and the problem still existed.

---

### Post by inportb on 2010-06-27
> **nix.peter said:**
> Well I finally made the switch. Went from 10.04 to 10.10 via upgrade command in terminal, update everything and bam wireless, touch works great. Even onboard keyboard works well. 

Will update manager update me to alpha 2 when it come out?

Suspend doesn't work but hibernate seems to. And be careful when using those they sometimes don't activate wireless on resume. I'm sure this will be fixed in future releases.

Suspend works; resume doesn't. While suspending, it disables networking. It needs to be manually re-enabled upon reboot after failed resume. Right-click the NetworkManager icon in the notification area to do this.

Other than that, things are great. Now we just need to bind these buttons on the display (to useful things such as screen rotation), and maybe accelerometer support.

---

### Post by nix.peter on 2010-06-28
Hibernate does seem to work for me and yes you can re enable network adapter. 

No I don't have any folder opening or browsing problems, im not sure why your having that problem skaarg.

---

### Post by inportb on 2010-06-28
I had a problem with Ubuntu One slowing down Nautilus. I just removed Ubuntu One and file browsing was improved.

---

### Post by xanadu1988 on 2010-06-29
file navigation is working great for me and so is 10.10 in general.. especially considering I'm too cheap to max out the RAM to 2gb.

---

### Post by SomeoneE1se on 2010-06-29
I've started a wiki page to help new people get everything working.  Maybe you'll help me build it out? 

[https://wiki.ubuntu.com/Lenovo_S10-3t](https://wiki.ubuntu.com/Lenovo_S10-3t)

---

### Post by xanadu1988 on 2010-06-29
> **SomeoneE1se said:**
> I've started a wiki page to help new people get everything working.  Maybe you'll help me build it out? 

[https://wiki.ubuntu.com/Lenovo_S10-3t](https://wiki.ubuntu.com/Lenovo_S10-3t)

Just put up a new and cleaned-up version of the script to rotate the screen. Hopefully this will help others get a little more out of their s10-3ts!

---

### Post by nnutter on 2010-06-29
I filed a bug report about the kernel failing to resume in Maverick. Please mark it as affecting you by clicking on "This bug affects..." at the top(-left) of the page. This is important because the devs can sort the bugs by how many people it effects.

If you have better information you can provide please do include it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664)

---

### Post by SomeoneE1se on 2010-06-29
> **inportb said:**
> Suspend works; resume doesn't. While suspending, it disables networking. It needs to be manually re-enabled upon reboot after failed resume. Right-click the NetworkManager icon in the notification area to do this.

I used wicd and don't have this problem, maybe you want to switch and make a bug report for network manager?

---

### Post by the_real_bubba on 2010-06-30
touchscreen working nicely with 10.10 for me.

Has anyone gotten the internal mic to work?  Doesn't with the current beta...

---

### Post by ehabh on 2010-07-03
I did a fresh 10.10 alpha 2 install.

Touch screen works, but I do not know how to get drag to scroll or multi touch scroll, please can someone help.

Otherwise 10.10 is a huge improvement in terms of hardware support for s10-3t.
The only problem is with the touch pad buttons and click and drag is impossible to do with the touch pad. I also can not enable enhanced desktop effects of compiz, but the graphics seem fast enough.

---

### Post by nnutter on 2010-07-04
ehabh: are you able to put the computer to sleep and wake up (suspend/resume) in 10.10 Alpha 2? If not please mark bug [#598664](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664) as affecting you.

---

### Post by Subsanek on 2010-07-05
[COLOR=#000000]I dreamed that left the driver with  support for multitouch to 4 fingers. :D
[/COLOR]

---

### Post by marcschh on 2010-07-05
I´ve a problem with the rotator.sh -skript. (both, with the one from this forum and with the one from the wiki.
which device ID should I use?
the device-ID from the "touchscreen" (slave), or the master-ID on the top. I tested both and nothing works.
so when i rotated the screen with the script, my input-devices are not inverted.

can anybody help me ?

---

### Post by marcschh on 2010-07-06
Do I need Kernel 2.6.35 for thi script`?
at the moment I have the lucid-kernel

---

### Post by Subsanek on 2010-07-07
[COLOR=#000000]In Linux 2.6.35 rc4 is better for the  s10-3t?[/COLOR]

---

### Post by codevel on 2010-07-08
Thanks all of you sharing your experience and these great information saved my time!  
In return, share with you two applications that I think is useful for tablet:

1) cellwriter - with both handwriting recognition and keyboard mode,
2) xournal - free writing notepad, you can load a pdf file for annotation too.

> **Subsanek said:**
> [COLOR=#000000]In Linux 2.6.35 rc4 is better for the  s10-3t?[/COLOR]
I've tried the rc4 but the keyboard and touchpad didn't work, the touch-screen works though. fallback to rc3.  Anyone got similar experience? or did I do something wrong?

---

### Post by alogghe on 2010-07-08
I'm pretty happily using 10.10 latest, most things work. Wireless with the proprietary driver, single click touch screen, and accelerated Compiz.

However I have no idea how to make use of the two-point multi-touch available on the "Cando" Multitouch panel, and no idea how to get a right-click out of it.

Has anyone experimented with -

Easystroke gesture recognition?
[http://ubuntuforums.org/showthread.php?t=837032](http://ubuntuforums.org/showthread.php?t=837032)

I was hoping to use it to help when the keyboard is folded away.

However it seems to be failing to recognize strokes when training it. I'm trying to make use of "gesture button - (click and hold) button 1" if anyone else wants to try.

This is the approach the author of Easystroke suggested for another tablet -

[http://old.nabble.com/Touchscreen-right-click-emulation-td21821882.html](http://old.nabble.com/Touchscreen-right-click-emulation-td21821882.html)

---

### Post by Skaarg on 2010-07-10
> **alogghe said:**
> I'm pretty happily using 10.10 latest, most things work. Wireless with the proprietary driver, single click touch screen, and accelerated Compiz.

However I have no idea how to make use of the two-point multi-touch available on the "Cando" Multitouch panel, and no idea how to get a right-click out of it.

Has anyone experimented with -

Easystroke gesture recognition?
[http://ubuntuforums.org/showthread.php?t=837032](http://ubuntuforums.org/showthread.php?t=837032)

I was hoping to use it to help when the keyboard is folded away.

However it seems to be failing to recognize strokes when training it. I'm trying to make use of "gesture button - (click and hold) button 1" if anyone else wants to try.

This is the approach the author of Easystroke suggested for another tablet -

[http://old.nabble.com/Touchscreen-right-click-emulation-td21821882.html](http://old.nabble.com/Touchscreen-right-click-emulation-td21821882.html)

I asked this a few pages back. If you go to the accessibility options > mouse settings, there should be something for enabling the hold left click to right click. It works alright, but an indicator like on Windows 7 would be nice.

I might have to see about doing another clean install soon. I've been installing updates as they come out and now Empathy, Update Manager, other misc. programs, and sometimes nothing (literally where it should say the program name there is just a space) have been crashing all the time slowing the system to a crawl.

---

### Post by SomeoneE1se on 2010-07-10
@Skarrg netbook remix or full distro?

---

### Post by Skaarg on 2010-07-12
Netbook Remix

---

### Post by xanadu1988 on 2010-07-14
> **marcschh said:**
> I´ve a problem with the rotator.sh -skript. (both, with the one from this forum and with the one from the wiki.
which device ID should I use?
the device-ID from the "touchscreen" (slave), or the master-ID on the top. I tested both and nothing works.
so when i rotated the screen with the script, my input-devices are not inverted.

can anybody help me ?
I have only tested this with 10.10. I imagine you need 2.6. You need to edit the script itself and replace the 12 with the device listed as touchscreen.

---

### Post by codevel on 2010-07-15
> **codevel said:**
> Thanks all of you sharing your experience and these great information saved my time!  
In return, share with you two applications that I think is useful for tablet:

1) cellwriter - with both handwriting recognition and keyboard mode,
2) xournal - free writing notepad, you can load a pdf file for annotation too.


I've tried the rc4 but the keyboard and touchpad didn't work, the touch-screen works though. fallback to rc3.  Anyone got similar experience? or did I do something wrong?

An update: Just upgraded to rc5, the keyboard and touchpad work, but suspend/resume still does not.

---

### Post by inportb on 2010-07-21
> **Skaarg said:**
> I asked this a few pages back. If you go to the accessibility options > mouse settings, there should be something for enabling the hold left click to right click. It works alright, but an indicator like on Windows 7 would be nice.

Agreed; is there a Launchpad entry for that? Also, the left-click registers upon mousedown, and the right-click registers upon mouseup (after a long-click). The behavior is different (and, imo, more sensible) on Windows 7: both types of clicks register on mouseup, so right-click does not trigger a left-click event first. I believe this is because Windows 7 draws a bigger distinction between the touch screen and the touchpad/mouse.

---

### Post by SomeoneE1se on 2010-07-21
I've just started to notice a (what I assume to be a driver error) quark in the way wicd handles wireless disconnects.

If I connect to 'Home AP' (wpa) and then put my computer to sleep, drive to work, wake computer up, it is unable to connect to 'Work AP' (wpa).  I also have the same problem if I try to connect to an unsecured ap. following a connection form a secured ap.  Like Starbucks or my gym.  But if I connect to a unsecured wireless ap connecting to the next AP 'just works'. 

I used to just reboot and that would solve the problem*.  Anyone having problems like this, or any suggestions?

*now I just
```

modprobe -r b43 ssb wl
modprobe wl

```

---

### Post by quantacat on 2010-07-22
Hey everyone,

Does anyone have 90 degree screen rotation working?

I used the script on the wiki and that works for a 180 degree flip.

---

### Post by Subsanek on 2010-07-24
[COLOR=#000000]In Linux 2.6.35-rc6 is better?[/COLOR]

---

### Post by Zarquon505 on 2010-07-27
> **quantacat said:**
> Hey everyone,

Does anyone have 90 degree screen rotation working?

I used the script on the wiki and that works for a 180 degree flip.

Yeah that works fine.  If I remember correctly it was just a small addition near the bottom of that script.  Just inserted a side rotate xrandr command down by the other if statements.  

eg 
```


	if [ $orientation = 1 ]; then        
            xrandr -o left
        fi
```

---

### Post by freehunt on 2010-07-27
I've got an issue with the latest 10.10 updates. I installed it from Alpha 1, and it all worked fine. I updated fully, and suddenly wifi won't connect anymore. Reinstalled, same thing. I tried wicd as well, still nothing. I even went as far as installing Mint, changing the upstream repos to maverick, and updating, same issue. Network Manager sees my wifi but can't connect. Works just fine before the update. Anyone know what's causing this?

---

### Post by Subsanek on 2010-07-28
> **freehunt said:**
> I've got an issue with the latest 10.10 updates. I installed it from Alpha 1, and it all worked fine. I updated fully, and suddenly wifi won't connect anymore. Reinstalled, same thing. I tried wicd as well, still nothing. I even went as far as installing Mint, changing the upstream repos to maverick, and updating, same issue. Network Manager sees my wifi but can't connect. Works just fine before the update. Anyone know what's causing this?

[COLOR=#000000]Switch wi-fi at the end of mode enabled?[/COLOR]

---

### Post by ehabh on 2010-07-29
Guys anyone have a problem with some dialogs going to the background behind the current window rather than to the front like they should like in the dialog that you use to confirm shutdown/reboot etc?

---

### Post by nnutter on 2010-07-31
I updated bug [#598664]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664") with a kernel config from Arch Linux for 2.6.34 which does not exhibit the sleep/resume problem for 2.6.34+ kernels as in Maverick and the Lucid backports. Please vote on the bug if it affects you or leave a commit. There has still not been any acknowledgment from the developers (as usual).

---

### Post by quantacat on 2010-08-01
@zarquon  Thanks!  That gets my screen rotating but not the mouse/touchscreen.  Do you know how to get that going too?

---

### Post by quantacat on 2010-08-01
nevermind!  i got it.  thanks!

---

### Post by ehabh on 2010-08-01
Did any one try the x86 android or meego on s10?

---

### Post by arobase40 on 2010-08-04
> **marcschh said:**
> I´ve a problem with the rotator.sh -skript. (both, with the one from this forum and with the one from the wiki.
which device ID should I use?
the device-ID from the "touchscreen" (slave), or the master-ID on the top. I tested both and nothing works.
so when i rotated the screen with the script, my input-devices are not inverted.

can anybody help me ?


In a terminal, type xinput list --short

then use the ID beside the "Cando      11.6" ref.
On my Acer 1825ptz, it is 10, but may be on a Idepad S10-3t, it could a different ID...

---

### Post by arobase40 on 2010-08-04
> **xanadu1988 said:**
> and before anyone asks -- no i don't know how to bind it to the physical button.

May be you could use the script from Tomfrancart ? ;)
On the Acer 1825pt(z), we have a physical P-button on the buttom left of the panel to bind this script... ^^
But this can be done with any keyboard touch using gnome-keybinding-properties... 

[http://ubuntuforums.org/showthread.php?t=1486671](http://ubuntuforums.org/showthread.php?t=1486671)

I changed his script a little to have a four directions rotation and his script is easy to understand.

---

### Post by Paul S on 2010-08-07
I'm thinking of buying one and have some general questions that I don't  see yet in this thread or in the wiki at [https://wiki.ubuntu.com/Lenovo_S10-3t:](https://wiki.ubuntu.com/Lenovo_S10-3t:)

1. When you install linux, does it kill the instant on feature or does grub play nice with it?
2. Do desktop effects work?
3. How long does it take to start firefox?
4. How is multi-tasking.  If you have firefox and openoffice open, does it get bogged down if you try to open synaptic?
5. Anyone now have buyer's remorse and regret buying it?
6. Is it possible to boot a usb (pen/hard)rive with linux loaded on it as an alternative installation to installing linux on the included drive?
7. I see some have had to compile kernels.  How long does it take to do that major task?  Were you able to do other things while it was compiling or was the atom overloaded?
8. Could you create and post the following files from a terminal (in fact, these would be great files to post on that wiki:
sudo dmesg > dmesg.txt
sudo dmidecode > dmidecode.txt
sudo lshw > lshw.txt
xdriinfo > xdriinfo.txt
xdpyinfo > xdpyinfo.txt
xvinfo > xvinfo.txt
You may have to gzip (or bzip2) your files before you upload them.

fwiw, I am writing from a dell with broadcom wifi and after the last updates in lucid, my wifi broke.  So, don't blame you're broadcom wifi problems on the lenovo, because it's a ubuntu wide problem now.

regards,

---

### Post by Paul S on 2010-08-07
I had to 

paul :~$ aptitude reinstall bcmwl-kernel-source
paul :~$ sudo restart network-manager

to fix my dell broadcom on lucid.  Seems it's not getting rebuilt properly when they update the kernel.  And, iwconfig is still screwed up:

paul :~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:228  Noise level:184
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

even though both the eth0 and wlan0 are now connected.  So, don't feel bad with lenovo.

regards,

---

### Post by fcomstoc on 2010-08-10
Hello Everyone
I have been using ubuntu 10.04 for about 6 months now so i am relatively new to the OS 
i upgraded today to 10.10 and immeditally noticed many problems that 10.04 did not have. 
one of the big problems is there is no right-click with out an external mouse 
has anyone come up with a solution for this ????

---

### Post by inportb on 2010-08-11
> **fcomstoc said:**
> one of the big problems is there is no right-click with out an external mouse 
has anyone come up with a solution for this ????

orly? Right-click and middle-click work just fine for me using the Synaptics touchpad. Did you, perchance, push the touchpad down by mistake while trying to right-click?

---

### Post by Paul S on 2010-08-12
Has anyone tried 64 bit on this lappy?  I'm running from the live cd right now and can't see any reason not to..

---

### Post by inportb on 2010-08-12
> **Paul S said:**
> Has anyone tried 64 bit on this lappy?  I'm running from the live cd right now and can't see any reason not to..

On the contrary, I don't see any reason to run the 64-bit kernel on this netbook. Why waste memory?

---

### Post by Paul S on 2010-08-13
I notice w7 has an auto rotate feature when you change the tablet position from horiz to vert.  Apparently this is connected to the accelerometer which is used to detect a fall and stop the hardrive (aka IBM Active Protection System).  I've been googling and reading and it turns out this can be activated in linux too.

The kernel driver is hdaps, for lucid:

```
paul :~/Desktop$ modinfo hdaps

filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/hwmon/hdaps.ko
license:        GPL v2
description:    IBM Hard Drive Active Protection System (HDAPS) driver
author:         Robert Love
srcversion:     0A53DA3975FFD9DDC3F44BE
depends:        input-polldev
vermagic:       2.6.32-24-generic SMP mod_unload modversions 586 
parm:           invert:invert data along each axis. 1 invert x-axis, 2 invert y-axis, 3 invert both axes. (int)
```

likewise, in lucid:
```
aptitude search hdaps
p   hdapsd   - HDAPS daemon for IBM/Lenovo ThinkPads and Apple iBooks/PowerBooks                                  
p   xfce4-hdaps   - plugin to indicate the status of HDAPS for the Xfce4 panel

```

All of this originates from [http://www.thinkwiki.org/wiki/HDAPS](http://www.thinkwiki.org/wiki/HDAPS)

Near the bottom is the script of interest (for screen rotation), called rotate.py, which links to:  [http://people.ksp.sk/~mic/Projects/Rotate](http://people.ksp.sk/~mic/Projects/Rotate)

I'm still working on my install, but thought I'd pass this on for anyone interested.

I also find that thinkwiki has loads of info on tablet pc's and our s10-3t appears to be quite similar.  So further reading may yield additional (existing) stuff.

regards,

---

### Post by inportb on 2010-08-15
This is very interesting, Paul S. On Windows, many users disable auto-rotate because it seems a bit sensitive. I too have the feature turned off. If this could be made adjustable on Linux, I sense a useful feature developing...

There is also tp_smapi, which is apparently recommended over hdaps; sources are available in the repos for dkms (tp-smapi-dkms).

***EDIT***
I could not manage to load the modules...
```
jyio@nutmeg:~$ sudo modprobe -a tp_smapi hdaps
WARNING: Error inserting tp_smapi (/lib/modules/2.6.35-15-generic/updates/dkms/tp_smapi.ko): No such device
WARNING: Error inserting hdaps (/lib/modules/2.6.35-15-generic/updates/dkms/hdaps.ko): No such device
```

---

### Post by Paul S on 2010-08-16
Too bad, I guess we're not supported.

I now have a 64-bit lucid and found the lucid touchscreen driver ppa, so didn't have to compile the kernel to get touch working.

I also vote for onboard osk because it's the only way I have found to do a right mouse click.  Firefox with grab and drag is better than IE on w7.  The rotator script works well too.

I checked in quick start and the rotation key does not work there either, so I suspect we will not be able to get it working in ubuntu.

---

### Post by nnutter on 2010-08-17
> **Paul S said:**
> Too bad, I guess we're not supported.

I now have a 64-bit lucid and found the lucid touchscreen driver ppa, so didn't have to compile the kernel to get touch working.


What PPA are you referring to Paul S?

---

### Post by pdzurilla on 2010-08-18
Hi, I have also few notes, about Lenovo IdeaPad S10-3T with ubuntu. I am using Ubuntu Netbook Edition 10.04, i find out how to enable headset speakers, touchscreen etc.

But I have couple problems / suggestions:

- When is Ideapad in the tablet pc mode and I initialize Lockscreen, there is no way how to enter the correct password cause there is no onboard keyboard.

- Missing native keyboard in ubuntu. In Windows 7 there is a small icon for initializing keyboard  on screen. In Ubuntu still missing

- I found there is a rotation screen script, but is there any way how to asociate it with rotate screen button on Ideapad? I have funcional Mute button, but not the rotation screen button. 

Any solution about this problem?

---

### Post by Paul S on 2010-08-18
> **nnutter said:**
> What PPA are you referring to Paul S?

Good question, because it's currently locked out.  It was at:

[https://launchpad.net/~xorg-edgers/+archive/multitouch](https://launchpad.net/~xorg-edgers/+archive/multitouch)

The apt sources.list entry is:

deb [http://ppa.launchpad.net/xorg-edgers/multitouch/ubuntu](http://ppa.launchpad.net/xorg-edgers/multitouch/ubuntu) lucid main

There's another site that you could also try if that fails, info at:

[https://launchpad.net/~chasedouglas/+archive/multitouch](https://launchpad.net/~chasedouglas/+archive/multitouch)

---

### Post by Paul S on 2010-08-18
> **pdzurilla said:**
> 
- When is Ideapad in the tablet pc mode and I initialize Lockscreen, there is no way how to enter the correct password cause there is no onboard keyboard.

- Missing native keyboard in ubuntu. In Windows 7 there is a small icon for initializing keyboard  on screen. In Ubuntu still missing


Install onboard.  You can configure it to start on lock screen as well as login screen.  It also has the only way I have found to do a middle mouse click and right mouse click.

> 

- I found there is a rotation screen script, but is there any way how to asociate it with rotate screen button on Ideapad? I have funcional Mute button, but not the rotation screen button. 

Any solution about this problem?

No, you have to create a launch button on the panel and link it to the rotation script.

I also am very unhappy with the trackpad driver.  I am unable to press the lower left corner and then move across the pad to select text.  Every time I try it it jumps off screen.  Anyone have any idea how to get it working like a normal track pad when selecting text?

I also have switched to gnome from netbook because I found netbook too difficult to customize.  No way to create an icon in the panel for rotation, etc.

By the way, I just notice another ppa covering multi touch interface development at [https://launchpad.net/canonical-multitouch](https://launchpad.net/canonical-multitouch)  Not sure what's there yet, but further study needed.

---

### Post by Subsanek on 2010-08-19
[URL="http://linuxnow.ru/view.php?id=83"]Configuring ethernet card on Lenovo s10-3t
[/URL]

---

### Post by schreibmaschine on 2010-08-19
Hi Guys,

sorry if I got something wrong. Touchscreen is working well after following the steps in 
[http://ubuntuforums.org/showpost.php?p=8929789&postcount=33](http://ubuntuforums.org/showpost.php?p=8929789&postcount=33) and
[http://ubuntuforums.org/showpost.php?p=8932808&postcount=36](http://ubuntuforums.org/showpost.php?p=8932808&postcount=36).

But I can't figure out how to right-click. Already tried holding the finger down for a moment or holding and tapping with a second finger.

Please let me know. I guess it's easier than it seems.

PS: Great work, appreciate that!

---

### Post by schreibmaschine on 2010-08-20
I found a solution which is working well:
I don't use the Mute key and use it as trigger for the script:

#!/bin/bash

if test 3 = $(/usr/bin/xmodmap -pp | awk '{print $2}' | tail -n 13 | head -n 1)
then 
/usr/bin/xmodmap -e "pointer = 1 2 3"
else
/usr/bin/xmodmap -e "pointer = 3 2 1"
fi

Mute is the only key located next to the screen which is working. Will try to use another key for switching a virtual keyboard.

---

### Post by pdzurilla on 2010-08-20
> **Paul S said:**
> 
I also have switched to gnome from netbook because I found netbook too difficult to customize.  No way to create an icon in the panel for rotation, etc.


There is a way how to create this button, first you have to unlock your panel, you can do it when you Log off as an user, and Switch the login method not Ubuntu Netbook Edition, but classic GNOME. Then you can customize your panel. I will try to find the correct method. Here is a screen of my Lenovo Netbook Edition, in the right down corner is also button for Switching screen rotation. As a proof that you can do it :D Please no comments about MS Office pack :) Since my childhood I was working with it, and is very hard to change it for another :)

[http://public.masmedialka.net/moj%20kompjuter.png]("http://public.masmedialka.net/moj%20kompjuter.png")

---

### Post by Paul S on 2010-08-20
> **schreibmaschine said:**
> Hi Guys,

sorry if I got something wrong. Touchscreen is working well after following the steps in 
[http://ubuntuforums.org/showpost.php?p=8929789&postcount=33](http://ubuntuforums.org/showpost.php?p=8929789&postcount=33) and
[http://ubuntuforums.org/showpost.php?p=8932808&postcount=36](http://ubuntuforums.org/showpost.php?p=8932808&postcount=36).

But I can't figure out how to right-click. Already tried holding the finger down for a moment or holding and tapping with a second finger.

Please let me know. I guess it's easier than it seems.

PS: Great work, appreciate that!

If you're running lucid, then you would be better off with the official cando touch driver, which is now available in a ppa.  See my prior post [http://ubuntuforums.org/showpost.php?p=9735414&postcount=263](http://ubuntuforums.org/showpost.php?p=9735414&postcount=263)

Regarding right click, check out [http://ubuntuforums.org/showpost.php?p=9735450&postcount=264](http://ubuntuforums.org/showpost.php?p=9735450&postcount=264)

But, I think it might be time to give up on lucid and go to maverick.  See [http://blog.canonical.com/?p=414](http://blog.canonical.com/?p=414)  and 
[http://www.phoronix.com/scan.php?page=news_item&px=ODUyMw](http://www.phoronix.com/scan.php?page=news_item&px=ODUyMw)  for an example. Wow!

---

### Post by Paul S on 2010-08-21
I have added a bug for the missing left / right click of this touchpad at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621821) in case you want to follow progress.

---

### Post by fcomstoc on 2010-08-21
hey there everyone 
i have the lenovo s10-3t with ubuntu 10.04 i have been able to get the touch screen working but i have not been able to get the screen rotation to work properly 
i have tried several scripts (including the one posted here earlier)to try to get the rotation to work and the screen rotates fine but the touch acts as if i didnt rotate the screen 
has anyone figured out how to rotate the screen image as well as the "touch driver" input 

thanks

---

### Post by Paul S on 2010-08-21
> **fcomstoc said:**
> hey there everyone 
i have the lenovo s10-3t with ubuntu 10.04 i have been able to get the touch screen working but i have not been able to get the screen rotation to work properly 
i have tried several scripts (including the one posted here earlier)to try to get the rotation to work and the screen rotates fine but the touch acts as if i didnt rotate the screen 
has anyone figured out how to rotate the screen image as well as the "touch driver" input 

thanks

You didn't say how you got your touch working, and maybe that makes a difference (or maybe not).  Did you backport the maverick kernel, patch and rebuild your own lucid kernel, use the multitouch backport driver, or use the evdev fix?

If you used the multitouch backport driver, did you also install multitouchd (the daemon for multitouch)?  I have both the multitouch-kernel-source_1.5 and multitouchd_1.0-0ubuntu1 installed.  I notice that the ppa for multitouchd seams to  have disappeared, but I searched for it on launchpad, and found this page [https://launchpad.net/~bryceharrington/+archive/ppa/+packages](https://launchpad.net/~bryceharrington/+archive/ppa/+packages) and this specific link to the 32 bit version [https://launchpad.net/~bryceharrington/+archive/ppa/+files/multitouchd_1.0-0ubuntu1_i386.deb](https://launchpad.net/~bryceharrington/+archive/ppa/+files/multitouchd_1.0-0ubuntu1_i386.deb) .

Attached is my rotater.sh script.

---

### Post by fcomstoc on 2010-08-21
> **Paul S said:**
> You didn't say how you got your touch working, and maybe that makes a difference (or maybe not).  Did you backport the maverick kernel, patch and rebuild your own lucid kernel, use the multitouch backport driver, or use the evdev fix?

If you used the multitouch backport driver, did you also install multitouchd (the daemon for multitouch)?  I have both the multitouch-kernel-source_1.5 and multitouchd_1.0-0ubuntu1 installed.  I notice that the ppa for multitouchd seams to  have disappeared, but I searched for it on launchpad, and found this page [https://launchpad.net/~bryceharrington/+archive/ppa/+packages](https://launchpad.net/~bryceharrington/+archive/ppa/+packages) and this specific link to the 32 bit version [https://launchpad.net/~bryceharrington/+archive/ppa/+files/multitouchd_1.0-0ubuntu1_i386.deb](https://launchpad.net/~bryceharrington/+archive/ppa/+files/multitouchd_1.0-0ubuntu1_i386.deb) .

Attached is my rotater.sh script.

i tried your script and got the same result, i am not sure how i got the touch screen working i was new at this when i got the touch driver working, i might just reinstall and start over 
i did get some error messages at the end of your script when i ran it if that gives you some insight to why i am having trouble with this 

property Evdev Axes Swap doesn't exist, you need to specify its type and format
property Evdev Axes Swap doesn't exist, you need to specify its type and format
property Evdev Axis Inversion doesn't exist, you need to specify its type and format
property Evdev Axis Calibration doesn't exist, you need to specify its type and format

thanks

---

### Post by schreibmaschine on 2010-08-23
> **Paul S said:**
> If you're running lucid, then you would be better off with the official cando touch driver, which is now available in a ppa.  See my prior post [http://ubuntuforums.org/showpost.php?p=9735414&postcount=263](http://ubuntuforums.org/showpost.php?p=9735414&postcount=263)
  Saying &quot;better off&quot; you refer to what exactly? Only problem I'm experiencing right now are X crashes when touching the screen before KDE is fully loaded. Just throws me back to login. No problem, entering the credentials via keyboard, waiting a few seconds, then turning the screen. From there on working very well.   > **Paul S said:**
>  Regarding right click, check out [http://ubuntuforums.org/showpost.php?p=9735450&postcount=264](http://ubuntuforums.org/showpost.php?p=9735450&postcount=264)   You mentioned onboard. Using the Menu key just lets the pointer just to the location of that key (where I tapped). Not opening a context menu...  

By the way I'm wondering if touchscreen support in Maverik will be &quot;enough&quot;. Also looked into Fedora and openSUSE with kernel 2.6.34 - touchscreen supported but not usable without calibration. Did not figure out how to get the timing for clicks right (for exmaple). Using the packages mentioned in this thread it's working. Althought I can't find the options responsible for proper timing when I look into xorg.conf... Where did you realize the calibration?

---

### Post by inportb on 2010-08-25
> **schreibmaschine said:**
> But I can't figure out how to right-click. Already tried holding the finger down for a moment or holding and tapping with a second finger.

To right-click or middle-click, you do not depress the touchpad. Instead, you tap the lower-right corner to right-click and tap the upper-right corner to middle-click. This is less than ideal, but it works.

---

### Post by ehabh on 2010-08-26
S10-3t Support is still flaky. Lenovo used some very non standard components here.

---

### Post by Paul S on 2010-08-26
> **Paul S said:**
> 
I also am very unhappy with the trackpad driver.  I am unable to press the lower left corner and then move across the pad to select text.  Every time I try it it jumps off screen.  Anyone have any idea how to get it working like a normal track pad when selecting text?


On lucid, I am experimenting with

```
syclient JumpyCursorThreshold=500
```

but, it's still not 100%.

YMMV

---

### Post by inportb on 2010-08-31
I just ran the uTouch tests on Maverick, and it's quite good. Hopefully, there will be lots of progress in this area.

Also, is it just me, or did the netbook launcher take a step back? I don't seem to be able to run many things from the graphical menu.

---

### Post by fcomstoc on 2010-08-31
> **inportb said:**
> I just ran the uTouch tests on Maverick, and it's quite good. Hopefully, there will be lots of progress in this area.

Also, is it just me, or did the netbook launcher take a step back? I don't seem to be able to run many things from the graphical menu.

the netbook launcher was a HUGE step back 
some of the who reason i use this operating system was because it did not have all that windows type crap. less gui less use of ram and on a netbook it doesn't make sense to run all the extra graphics. 
i installed 10.04 netbook on my netbook and immeditally stopped using it - i have completely switched to gnome 

_frank

---

### Post by Paul S on 2010-09-02
I think they have some work ahead on ubuntu-netbook, but I'm trying kubuntu-netbook and find it much more finger friendly.  Some improvements over ubuntu version are:

- can configure everything
- can enlarge scrollbars and icons to make them easier to "not miss" with finger touch
- kvkbd is usable
- animations are decent
- still a problem with right and middle mouse click, but a solution is to create a launcher and use xdotool command to create middle / right click

---

### Post by inportb on 2010-09-02
I agree that kubuntu-netbook is much more usable at this stage. I use KDE on my laptop and briefly tried the netbook version. How's the resource usage of plasma-netbook and kwin compared to Unity?

Mouse clicks work if you have access to the touchpad, but widgets help while in tablet mode.

I would try e17+illume, but it's not installable now. Any ideas on that?

---

### Post by datajack on 2010-09-10
My S10-3t arrived this morning, not two days after getting an apologetic email stating that the shop was out of stock and would be getting mine in on the 15th - a nice surprise :D
Apparently there was some software pre-installed on it but the first thing I saw was the Maverick installer ;)

> **inportb said:**
> There is also tp_smapi, which is apparently recommended over hdaps; sources are available in the repos for dkms (tp-smapi-dkms).

***EDIT***
I could not manage to load the modules...

Same here. I patched the module to bypass the DMI checks in case it is just not listed in DMI and it still didn't work, so it looks like a different accelerometer type to the other laptops :(

---

### Post by datajack on 2010-09-13
This may be a silly question.

I've just realised that this netbook comes pre-installed with Lenovo's 'QuickStart' version of splashtop. Does anyone know if the accelerometer works in that environment?

---

### Post by Subsanek on 2010-09-14
In Linux 2.6.36 Wi-fi should work out of the box =)

---

### Post by Paul S on 2010-09-14
> **datajack said:**
> This may be a silly question.

I've just realised that this netbook comes pre-installed with Lenovo's 'QuickStart' version of splashtop. Does anyone know if the accelerometer works in that environment?

I tried before and it does not work there either.  In fact, multi-touch does not work on any app's either.  Nor does the rotation button .. basically, the same bugs that occur in ubuntu are there in splashtop.

Also, I couldn't find a way to get to a terminal (C-A-F1) to be able to gather info with lspci, etc.

But, it's worth watching to see if splashtop gets updated in the future.

---

### Post by Paul S on 2010-09-14
If your still having problems with the internal mic not working, there's a backport alsa package available for lucid, and to be made for maverick .. see [https://bugs.launchpad.net/bugs/635907](https://bugs.launchpad.net/bugs/635907) for info.

Also, at some point in the future, the new broadcom open source driver will be backported via linux-backports-modules-wireless-[lucid:maverick]-generic.  I tried installing this now just to see what would happen and it killed the wifi altogether.  But, maybe I need to blacklist something.  I couldn't figure it out so uninstalled it.

Anyway, that'll be the package to watch if you want to have open source.

I notice that lspci shows this for my wireless:

07:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
        Subsystem: Broadcom Corporation Device 0510
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [d0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag+ PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
                        ClockPM+ Suprise- LLActRep+ BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 26-00-9b-ff-ff-82-00-00
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: wl

I'm puzzled by the device of BCM 4727.  Actually the sales order claims I have the BCM 4313.  I also have bluetooth, and there's no meantion of it in the output of lspci or lshw (but it shows up in lshal).  According to the Broadcom site, the BCM 4313 runs both a/b/g/n wifi and bluetooth, so it may be a combo device.  But, I'm still not sure what to think.  I think the new opensource broadcom driver supports 4313, but 4727 was not listed.  Anyone know for sure if we'll be covered?

---

### Post by inportb on 2010-09-16
Thanks for the tip. I'd applied the fix, but didn't know it fixed the internal microphone. I had to undeafen the microphone first :P

---

### Post by Skaarg on 2010-09-20
I had a problem where if I put the beta installer on my flash drive it would not boot, but I put 10.04 on there and upgrade to 10.10 which worked. Unfortunately I found Unity to be a buggy piece of garbage that was very unresponsive and would not launch programs everytime when I clicked them.

Kubuntu-netbook on the other hand is very nice. Just out of curiousity is there a way of enabling a hold to right click like in Unity/Gnome. Would be very handy for when I have the system in tablet mode.

---

### Post by inportb on 2010-09-23
I also tend to prefer KDE, but it seems to use a little bit more resources so I have switched back for now. I do not know how to enable hold-click, but I don't quite like Gnome's implementation -- it triggers a left-click event before registering the right-click.

---

### Post by JaseP on 2010-09-24
I now received my S10-3t (N470 with 2 GB RAM & Bluetooth)...

Thanks to many of you here for the great tips in getting started with it.

If someone has a fix for the screen bevel buttons on Maverick, that would be great,... also the lack of right click. What you CAN do in the meanwhile is to set your mouse to allow a held right click, which is not optimal for teh touchpad, but is great on the touchscreen.

Note for those using Cairo-dock (it's great on touchscreens),... Maverick's implementation is apparently broken. OpenGL cairo-dock doesn't work. It crashes. Using the command cairo-dock -c to start it without OpenGL is recommended until it's fixed...

I am using the "working" Audio-mute button for launching the "onboard" on screen keyboard...

---

### Post by nnutter on 2010-09-24
> **JaseP said:**
> ...also the lack of right click. What you CAN do in the meanwhile is to set your mouse to allow a held right click, which is not optimal for teh touchpad, but is great on the touchscreen.

If you allow tap clicking (enabled by default) you can right click by tapping on the very bottom right corner of the touchpad.

---

### Post by MedianMajik on 2010-09-26
What are your thoughts on the state of this tablet with Linux.  I've found one for $150, but just want to know if the touchscreen is up to snuff.  I'm a heavy writer/traveler who could use a replacement for my sluggish old iphone and overheating netbook.

---

### Post by JaseP on 2010-09-26
> **MedianMajik said:**
> ... I've found one for $150, but just want to know if the touchscreen is up to snuff. ...

In Maverick, the touch screen works out of the box... However, I just broke my sound trying to get the internal mic working though...

The only cons of this thing on Linux are some little annoyances in Maverick. You can get Lucid working, but it's supposedly a real pain...

All in all, this is said to be the "ultimate Linux tablet." ...
[http://www.jupiterbroadcasting.com/?p=2691](http://www.jupiterbroadcasting.com/?p=2691)

By the way,... How on ***Earth*** did you manage to get one for $150,... short of it being ***stolen***?!?!

---

### Post by fcomstoc on 2010-09-28
can anyone please post the script for the 90 deg screen rotation the one for the 180 works great !  
thanks a lot

---

### Post by Factoryworks on 2010-09-29
Here you are:
It just rotates to the left and back to normal, so no upside down and not to the right.
Also, with the screen rotated to the left, the touch-pad (mouse) is a bit funny to use.
I did not clean up the code, so it still contains elements for the other orientations.
> 
syntax_error=0
orientation=0

current_orientation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"
case $current_orientation in[INDENT]         normal)
[/INDENT][INDENT][INDENT]                 current_orientation=0
[/INDENT][/INDENT][INDENT]         ;;
        left)[INDENT]                 current_orientation=1
[/INDENT];;
        inverted)[INDENT]                 current_orientation=2
[/INDENT];;
        right)[INDENT]                 current_orientation=3
[/INDENT];;
[/INDENT]esac

if [ $current_orientation -eq 0 ]; then[INDENT]         orientation=1
[/INDENT]fi

if [ $current_orientation -eq 1 ]; then[INDENT]         orientation=0
[/INDENT]fi
method=evdev

# LENOVO S10-3t CHANGE ==> Hard Coded my device number to 11!!!!!!!!

device=11
 
swap=0
invert_x=0
invert_y=0
real_topx=0
real_topy=0
real_bottomx=4020
real_bottomy=4020

case $orientation in
        0)[INDENT]                 swap=0
                invert_x=0
                invert_y=0
                topx=$real_topx
                topy=$real_topy
                bottomx=$real_bottomx
                bottomy=$real_bottomy
[/INDENT];;
        1)[INDENT]                 swap=1
                invert_x=1
                invert_y=0
                topx=$real_topx
                topy=$real_topy
                bottomx=$real_bottomy
                bottomy=$real_bottomx
[/INDENT];;
        2 )[INDENT]                 swap=0
                invert_x=1
                invert_y=1
                topx=$real_topx
                topy=$real_topy
                bottomx=$real_bottomx
                bottomy=$real_bottomy
[/INDENT];;
        3 )
                swap=1[INDENT]                 invert_x=0
                invert_y=1
                topx=$real_topx
                topy=$real_topy
                bottomx=$real_bottomy
                bottomy=$real_bottomx
[/INDENT];;
esac

if [ $method = "evdev" ]; then[INDENT]         xinput set-prop "$device" "Evdev Axes Swap" $swap
        xinput set-prop "$device" "Evdev Axes Swap" $swap
        xinput set-prop "$device" "Evdev Axis Inversion" $invert_x $invert_y
        xinput set-prop "$device" "Evdev Axis Calibration" $topx $bottomx $topy $bottomy

        if [ $orientation = 2 ]; then           [INDENT]                 xrandr -o inverted
[/INDENT]fi
        if [ $orientation = 0 ]; then[INDENT]                 xrandr -o normal
[/INDENT]fi
    if [ $orientation = 1 ]; then        [INDENT]             xrandr -o left
[/INDENT]fi
[/INDENT]fi

#
I assigned it to the MOD4+1 key because the buttons next to the screen do not work. MOD4+2 is for onboard. MOD4 is the Tux / Linux or Windows button.

---

### Post by fcomstoc on 2010-09-29
thank you so much I appreciate it

---

### Post by Subsanek on 2010-10-01
To operate a built-in microphone, add the line
 ```
options snd-hda-intel model="ideapad"
```
In the file ```
/etc/modprobe.d/alsa-base.conf
```
After that, reboot.
[COLOR=#000000]The microphone works perfectly![/COLOR]

---

### Post by Factoryworks on 2010-10-01
> [COLOR=#000000]The microphone works perfectly![/COLOR]
Mine works, but produces more noise than I can hear my own voice.
Is yours really working in a usable way?

---

### Post by inportb on 2010-10-01
Make sure you're not covering the microphone...

---

### Post by Subsanek on 2010-10-02
I have no noise and everything can be heard clearly.
Look mixer settings ...

---

### Post by Factoryworks on 2010-10-02
On the external microfone, I have some white noise plus a slow "tack - tack - ...", like a slow moving ventilator with a broken motor. The internal ventilator is off.

alsamixer shows: capture: 100%, analog mic boost: 20dB (below that, I have to "kiss" the netbook to register my words).
chip is Conexant CX20582 (Pebble).
What are your settings?

But the headset works perfectly and I will most probably only use that one. So never mind.


By the way, I am now customizing my panels (using standard Gnome, not the netbook editions). It is about to become perfect for me.:)
Does anyone know how to a) hide the title bar of maximized windows without using maximus (maximizes all windows incl. the search in OOo) or compiz (eats too many resources)?
b) move the panels to the right (landscape screen) or top (vertical screen) via script?
---
edit:
got b) running: 
I added > gconftool --set apps/panel/toplevels/top-panel_screen0/orientation --type string top to the script to rotate the screen to the left, and "left" when rotating to normal. This gives optimum usage of the screen space.

got a) running as well with maximus and some settings in the configuration editor

---

### Post by vivek40 on 2010-10-02
Hi so this is the netbook that I am planning to buy for my wife tomo. I am totally new to netbooks and just need to know one thing .. does maverick's netbook edition work out of the box on ideapad s10 3t.. does it support all the touch screen stuff and all and would I need to write all those scripts listed on this thread time and again.. I am just too bad at that..

---

### Post by Factoryworks on 2010-10-03
If you read starting about message #284, you will get an impression of what it does.
Bottom line: In Linux you cannot do as much as with the W7 supplied with it.
Kernel >=2.6.35 is needed for the touch screen (multi-touch does not work, at least for me). Therefore, Ubuntu 10.04 is not suitable (unless you can omit touch screen). 
Note maverick is still beta.
And, you have to make some scripting, still no way around.
What disturbs me most, is that left-click-and-hold is not working on the touch-pad, so drag-and-drop and text select are not possible.
But I am enthusiastic about the device and it's possibilities (in the future).

---

### Post by vivek40 on 2010-10-04
Hi It might be a little out of context but how are you connecting the s10 3t to a 3g sim card usng the built in slot. Am tired doing that and dont find anything working. have inserted the sim card and all but nothing works

---

### Post by Canadian_Pirate on 2010-10-04
Is there any way to get the touch pad to work in 10.10?

---

### Post by Factoryworks on 2010-10-04
It works - mostly.

Just the left click and hold is not possible. See also these bugs:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/634017](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/634017)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621821)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)

They are discussing a patch and some settings, I haven't tried that yet.

Right click can be done with tapping the bottom-right corner of the touch pad.

---

### Post by inportb on 2010-10-05
I just noticed that tap-to-right/middle-click no longer works (by default, anyway). On the contrary, clicking with the finger on the bottom right corner seems to be the way to go now. I imagine there'd be a way to enable the tap mode in the usual fashion, since middle click is useful.

---

### Post by vivek40 on 2010-10-08
I just pray when Maverick comes out , it suports this device out of the box. 

Am tired of windows 7 on it . Mc cafe keeps saying it is going to expire in 10 days. MS office keeps saying it needs to be activated. Installed Firefox on it and it uses close to 120 MB of Memory.

---

### Post by inportb on 2010-10-08
It won't be completely supported out of the box -- you gotta jack into Ethernet and install a restricted wireless driver using Jockey, which should be a painless procedure. You might also have to perform the alsa fix, but that's just a line in a configuration file.

---

### Post by vivek40 on 2010-10-10
Thanks for replying inportb , but I was actually talking of all the touch functionalities.. any idea about the same!

---

### Post by vivek40 on 2010-10-11
Hii , has someone tried maverick released yesterday on s10 3t.I am really sorry to keep bumping this thread but it is just that I have run out of bandwidth and need some feedback before downloading the netbook edition of 10.10.

---

### Post by Paul S on 2010-10-11
> **vivek40 said:**
> Hii , has someone tried maverick released yesterday on s10 3t.I am really sorry to keep bumping this thread but it is just that I have run out of bandwidth and need some feedback before downloading the netbook edition of 10.10.

I tried it and there is no support of multitouch that I can find.  Also, the default netbook install creates a user interface that is difficult to use without a mouse / keyboard.  For example, just getting a right click to activate the network connection configuration is not possible.  Also, I didn't find any way to activate an on-screen-keyboard.  So, I think multitouch support has been delayed!

Maybe you should stay with W7 for tablet mode.

Ubuntu itself works well with the full netbook, using the keyboard and touchpad / touchscreen (for single clicks) (although the touchpad corner clicks need a bugfix).

hth

---

### Post by inportb on 2010-10-12
I found that EasyStroke makes this thing very usable in slate mode. I have mine set up for a Graffiti-like alphabet.

---

### Post by codevel on 2010-10-12
> **vivek40 said:**
> Hii , has someone tried maverick released yesterday on s10 3t.I am really sorry to keep bumping this thread but it is just that I have run out of bandwidth and need some feedback before downloading the netbook edition of 10.10.

I just did that (upgraded from 10.04) and I've got some 'enhancement' over the lucid:

1) suspend/resume works, and
2) multitouch works! (just tested it with utouch)
Anyone know some multitouch apps for demonstration/testing?

IMHO, the Unity environment looks cool but is less finger-friendly than the netbook-launcher in lucid.

---

### Post by Paul S on 2010-10-12
> **inportb said:**
> I found that EasyStroke makes this thing very usable in slate mode. I have mine set up for a Graffiti-like alphabet.

Hi, I might be interested in trying this.  The doc's are a bit sparse for easystroke.  Please post your config .. I think this should work:

```
tar cjvf easystroke.tar.bz2 ~/.easystroke/
```

and attaching it, so I can see what can be done on this touchscreen.  I should be able to use your commands and just input my own gestures .. could save a bunch of time.

TIA

---

### Post by vivek40 on 2010-10-13
thanks for replying codevel,& Paul , but now what do you recommend me to download and install which could work fine with all multitouch and touch gestures with on screen keyboard and all. I am tired of Win7 which takes a lifetime to boot up and then keeps reminding me to activate something or the other.

Please suggest and yes once again my apologies for bugging you all

---

### Post by Paul S on 2010-10-13
> **vivek40 said:**
> what do you recommend which could work fine with all multitouch and touch gestures with on screen keyboard and all.

I'm running ubuntu-desktop 10.10 with onboard osk , but I do not have any multi-touch applications.  In my last post I asked inportb to post his easystroke configuration files because he feels easystroke is helpful to replace 2nd touch events.  I haven't been able to figure out easystroke yet.  I hope he posts his configuration so I can try it.

I do not find any way to try android, so cannot comment on it.  I tried Smeego, but it is worse than ubuntu at this time.  I do not know of any other os to try.

Anyway, nothing is as good as W7 for multi-touch right now!  If you must have good multitouch, then you may have to wait for ubuntu 11.04.

---

### Post by LXUSeless on 2010-10-15
Hi there,

I'm following this thread for quite some time (I'm a proud owner of a S10-3T since February.) 
I Maverick and Opera for browsing make the S10-3T well usable.
However, I wanted to use multitouch so I kept googling for infos on the GINN demon. It's promised to be a part of Maverick, but it seems it's not in.
Are there any infos on how to use it?
(BTW: I pulled ginn from the repos, compiled and startet it without any parameters. When I use it this way, the pointer wouldnt react to touch inputs anymore, but Opera zooms in and out in response to a pinch guesture...)

---

### Post by altongary on 2010-10-16
Multi-touch is not installed by default on Ubuntu 10.10 desktop edition. You have to open a terminal and type *sudo apt-get install utouch* to have that ability. Click the attachment to see the the multi-touch gestures. Canonical has promised more multi-touch uses in the near future.

---

### Post by RuLong on 2010-10-17
> **altongary said:**
> Multi-touch is not installed by default on Ubuntu 10.10 desktop edition. You have to open a terminal and type *sudo apt-get install utouch* to have that ability. Click the attachment to see the the multi-touch gestures. Canonical has promised more multi-touch uses in the near future.
I've done that and have never been able to get the 'flick' gesture to work. And I think the only reason I can hold down for a right click is because I enabled it under the 'mouse' settings rather than anything with uTouch.

---

### Post by datajack on 2010-10-17
> **RuLong said:**
> I've done that and have never been able to get the 'flick' gesture to work. And I think the only reason I can hold down for a right click is because I enabled it under the 'mouse' settings rather than anything with uTouch.

From what I understand (I'd love to be shown wrong) is that the utouch system only adds a uniform interface for applications to make use of - each application must be specifically developed to make use of gesture input and I'm not aware of anything that does yet.

---

### Post by Paul S on 2010-10-17
Need help with lenovo onekey recovery.  It stopped on the 4th attempt here and after searching forums for hours, I can't find a fix.  But it seems like it might have something to do with the disk labels and or id's.  On mine, the original backup is on /dev/sda4.

Anyway, it would be a big help if from a linux terminal, you would post the output from these 2 commands:
```
$ sudo fdisk -l
$ sudo blkid
```
 , so I can compare mine to yours and (hopefully) get it fixed.

TIA

FWIW, the output for my broken system is:

paul :~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        4934    39426531    7  HPFS/NTFS
/dev/sda3            4935       28476   189093889    f  W95 Ext'd (LBA)
/dev/sda4           28476       30402    15471800    7  HPFS/NTFS
/dev/sda5           24524       28476    31737856    7  HPFS/NTFS
/dev/sda6            4935       11621    53710848   83  Linux
/dev/sda7           11621       11642      164864   83  Linux
/dev/sda8           11642       17721    48827392   83  Linux
/dev/sda9           17721       17739      145408   83  Linux
/dev/sda10          17739       23818    48827392   83  Linux
/dev/sda11          23818       23836      145408   83  Linux
/dev/sda12          23836       24523     5520384   83  Linux

Partition table entries are not in disk order

paul :~$ sudo blkid 
/dev/sda1: UUID="5AD82F66D82F401D" TYPE="ntfs" 
/dev/sda2: UUID="C2022E2B022E24BF" TYPE="ntfs" 
/dev/sda4: LABEL="LENOVO_PART" UUID="BA5AE6535AE60C47" TYPE="ntfs" 
/dev/sda5: LABEL="LENOVO" UUID="12F82034F820190D" TYPE="ntfs" 
/dev/sda6: UUID="2b769eb8-d7ec-432d-9d57-1d29f3bc0c32" TYPE="crypto_LUKS" 
/dev/sda7: UUID="0531a85b-8f33-429e-bfd6-c0cb491e1a8b" TYPE="ext4" 
/dev/mapper/sda6_crypt: UUID="CpvWu1-dNJI-CIIW-cPiJ-qpsC-EXuB-oix5HA" TYPE="LVM2_member" 
/dev/mapper/vgsda6-lvsda6--swap: UUID="15137317-e13d-4c8d-9c41-dd54b30f311c" TYPE="swap" 
/dev/mapper/vgsda6-vgsda6--root: UUID="2bbfb822-5e50-4c8b-a20d-7eebe66cd1bb" TYPE="ext4"

---

### Post by inportb on 2010-10-21
Paul, I don't have the configuration anymore; it got wiped when I installed Maverick. Nonetheless, I really do think you'd benefit more from EasyStroke if you set it up with the gestures that make sense to -you-. Try not to exactly duplicate the gestures you use while writing on paper -- simplified strokes tend to work well and let you write faster.

---

### Post by Charles34 on 2010-10-22
Hey all, first off let me start by saying that it's great to see so many other s10-3t lovers out there. Secondly, I am a total and complete (just started a month ago) Linux Noob, so please take it easy on me. If I seem ignorant it's because I am.

   So, I'm obviously faced with the same problems as everyone else on this thread. The bigger problem I'm having is translating these beautifully written responses into actual fixes on my machine. Can anyone tell me how to implement these patches or better yet, where to find a good reference manual (.pdf, .doc, .txt,  html etc?)

   I fell in love with Ubuntu the first time I used it. I have no problem learning the language, I just want to learn it right. Thank you in advance for any help you can give me.

---

### Post by inportb on 2010-10-22
protip: installing natty atm breaks wifi ;)
at any rate, i have easystroke installed again and this time i saved the files...

if you decide to use it, keep in mind that this is a modified graffiti alphabet. for caps-lock, you need to apt-get install xautomation. you will have to "relearn" handwriting, but for me it is more natural than using a vkbd. some strokes may not work as well as the others, so you may need to refine them. enjoy!

(post composed via easystroke)

> **Charles34 said:**
> So, I'm obviously faced with the same problems as everyone else on this thread. The bigger problem I'm having is translating these beautifully written responses into actual fixes on my machine. Can anyone tell me how to implement these patches or better yet, where to find a good reference manual (.pdf, .doc, .txt,  html etc?)

Welcome to the forums. While the Lenovo Ideapad S10-3t is almost perfect out of the box with the Maverick Meerkat, there are a couple of glitches and possible points of enhancement. I'd recommend that you have a look at the top of the [wiki page]("https://wiki.ubuntu.com/Lenovo_S10-3t") and see if there's anything left for you to do on the glitches front. Are there any specific issues that you're looking to address?

---

### Post by Bufke on 2010-10-23
Thanks for the config file inportb I found this really useful. I found it useful to add a gesture to disable it then I made a script to run that gesture using from the command line 

easystroke send "my new gesture name"

Basically I can just click on an icon to enable it or disable it. I put the icon in awn which i make always show for easy access.

I can't wait to do these gestures with multi touch!

---

### Post by inportb on 2010-10-23
That's a good idea. I just made a right-click gesture, which I use to access the icon in the notification area.

I'm also working on a predictive text entry tool in Python (to save me some strokes). The prediction works... but I'm getting stuck making a virtual keyboard out of it. Basically, the ibus documentation sucks :mad:

---

### Post by Skaarg on 2010-10-24
Just in case anyone one was curious. I disliked moving to Ubuntu 10.10 because of Unity, but wanted to have the improved touch screen support. Well now the 10.04 interface is available for download and I figured out how to make it fully customizable like in 10.04 by modifying that guide some.

Personally I feel this interface is very nice for a touch screen since you can resize and arrange the top panel to fit your needs. Then the application launcher is just much more user friendly and faster than Unity.

[http://ubuntuforums.org/showthread.php?t=1604393](http://ubuntuforums.org/showthread.php?t=1604393)

---

### Post by ta100 on 2010-10-28
i am using this laptop with ubuntu and it works great :)
touch screen is great :p
i can't go back to win7 after enjoying this OS
everything works fine to me

---

### Post by Charles34 on 2010-10-28
I have to assume you don't use it in portrait mode too often. Unfortunately, thanks to some cool ad-ons for Firefox, I've gotten quite used to reading all my news in portrait (ebook style.) This along with a few other minor issues means that I can't quite bring myself to remove Win7 yet. Looking forward to the day I can.

   TO ALL THE UBUNTU GURU'S WITH S10-3Ts: On a side note to the MANY Ubuntu users better than me, I noticed that the rotation hardware button works in QuickStart but it only goes from landscape to opposite landscape. The touch controls flip along with the screen rotation as well. I know QuickStart is a Linux-based OS but I don't really know anything about Linux yet. I'm curious whether it's possible to pull the code from QuickStart for the screen-rotation and touch-rotation and implement it in Ubuntu. Again as I said in my previous post, I am a complete noob when it comes to Ubuntu (and Linux in general) so if anyone with the know-how wants to check it out, it might just benefit all of us.

---

### Post by Canadian_Pirate on 2010-10-31
uTouch does not seem to work on my S10-3t. I do not know why...

For convenience I have created a script to make the touchpad work (with pressing buttons and scrolling) in 10.10. 
THIS SCRIPT WILL INSTALL DKMS IF IT IS NOT ALREADY INSTALLED.
THIS IS NOT TESTED. (tell me any bugs and I will fix them.)

Type this to run:
```
chmod +x mouse.sh
sudo ./mouse.sh
```

EDIT: Small bugs in the program. Fixed now

---

### Post by logdrum on 2010-11-05
I do not know if the problem is solved but I just got a Lenovo S10-3t 2 days ago. I am active Meego enthusiast and developer and Meego 1.1 recognized the wifi and the touch right off the bat. I know that this has always been an issue with most netbooks. I have a Dell netbook and I had to built the slasher/broadcomm driver before.  The Windows device driver control panel says that the wifi is an Atheros AR9285. The tablet is not explicit in the device manager but in the control panel, there is a pen and touch tool control. I'll boot of the meego live USB again and I'll see if I can get more information. I'll try the latest Ubuntu as well.  My first post btw. Nice to be here.

---

### Post by prshah on 2010-11-07
Hello,

I've recently got this laptop, and, after reading through 34 pages, thought I'd summarize my experiences this:

a) Short of Wifi, everything works perfectly off live CD (10.10) and after install, including display, sound, touch (not multi-touch)), fn-keys, compiz, etc. 

b) Initially installed netbook-remix, then removed it and installed 64-bit Desktop since was not comfortable with the remix interface and lack of control. Why 64-bit? Because I can (TM). USB live/install stick created using "Make startup disk" and ISO image of 64bit 10.10 from another system.

c) Wifi worked immediately once "Activated" in Hardware Drivers (restricted drivers). Needed a hardline (LAN) connection.

d) Quick Start was initially disabled in my BIOS settings, so enabled it to check what worked in SplashTop and to replicate if possible in Ubuntu.

e) Excellent battery life results (better than onboard Win7 HB).

f) Excellent ubuntu performance, much better than Win7 (jitters, especially during extensive HDD reads for no discernible reasons)

g) W7 HB features are comparable to Ubuntu's features since HB lacks multi-touch capabilities.

h) Flash, java etc worked immediately after hassle-free installation by clicking "Install missing plugins" in firefox.

i) Right click works fine by tapping lower-right corner of touchpad (but don't depress button). Screen right-click (dwell click) is little iffy, but usually works fine.

j) All in all, very happy with Ubuntu on this netbook, and don't think I will be going to W7 (though netbook is in dualboot setup now).

Hope this will put things into perspective for new owners of this hardware.

---

### Post by vivek40 on 2010-11-10
Thanks for that prshah, nice to hear that, how about the touchpad and the left-right clicks on that.. hoping that they make multi touch work soon !

---

### Post by fcomstoc on 2010-11-13
hello everyone
has anyone got this sound card driver to work right, 
all i can get it to do is analog duplex which is not compatable with several programs, is there any way to get a better driver or to use the windows one

thanks

---

### Post by Paul S on 2010-11-13
Experimental multitouch packages for maverick now available, haven't tried them yet.  Here's the info:

[https://wiki.ubuntu.com/Multitouch/XDevelopment](https://wiki.ubuntu.com/Multitouch/XDevelopment)

Two ppa's needed:

[https://launchpad.net/~utouch-team/+archive/xorg-unstable](https://launchpad.net/~utouch-team/+archive/xorg-unstable)

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

and developer info here:

[http://lists.x.org/archives/xorg-devel/2010-November/015347.html](http://lists.x.org/archives/xorg-devel/2010-November/015347.html)

Still not sure if this will enable actually doing anything in applications like firefox or evince.  If you try them, let us know.

---

### Post by Bufke on 2010-11-14
Tried the experimental, the mouse resets to a corner of the screen every second or so. Touch screen can click but not move the mouse. Obviously I couldn't test any multitouch features with this problem.

---

### Post by Paul S on 2010-11-15
> **Bufke said:**
> Tried the experimental, the mouse resets to a corner of the screen every second or so. Touch screen can click but not move the mouse. Obviously I couldn't test any multitouch features with this problem.

Same sad result here.

btw, if you aren't already aware, there's a ppa-purge program that will undo the special ppa packages.

Did you file a bug?  If not, I'll get to it a bit later today.

---

### Post by Paul S on 2010-11-16
if you want to follow, it's bug 675691 at [https://bugs.launchpad.net/ubuntu/+source/utouch/+bug/675691](https://bugs.launchpad.net/ubuntu/+source/utouch/+bug/675691)

---

### Post by greenreports on 2010-11-27
> **prshah said:**
> Hello,

I've recently got this laptop, and, after reading through 34 pages, thought I'd summarize my experiences this:

a) Short of Wifi,...

i) Right click works fine by tapping lower-right corner of touchpad (but don't depress button). Screen right-click (dwell click) is little iffy, but usually works fine.

j) All in all, very happy with Ubuntu on this netbook, and don't think I will be going to W7 (though netbook is in dualboot setup now).

Hope this will put things into perspective for new owners of this hardware.

Thank you PRShah and others who posted here!  I'm new to Ubuntu (&Linux) and am only able to use some of the suggestions due to newbie status.  However, I finally have a touchpad that works (mostly) due to hint i) above.  

Touchscreen itself seems to work OK in Ubuntu Netbook Remix 10.10, though without multitouch.

---

### Post by Paul S on 2010-11-27
For the touchpad fix, see postings 111 and 112 on this bug:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809?comments=all)

regards,

---

### Post by markyt23 on 2010-12-05
i have touch working on my lenovo s10-3t has anyone got multitouch working as seen here?
[http://www.youtube.com/watch?v=bcH3flhYHZI&feature=related](http://www.youtube.com/watch?v=bcH3flhYHZI&feature=related)

---

### Post by Skaarg on 2010-12-06
> **markyt23 said:**
> i have touch working on my lenovo s10-3t has anyone got multitouch working as seen here?
[http://www.youtube.com/watch?v=bcH3flhYHZI&feature=related](http://www.youtube.com/watch?v=bcH3flhYHZI&feature=related)
That's very interesting to see. I too am curious how they got multitouch fully working there.

---

### Post by Paul S on 2010-12-13
ginn was just made available for maverick and goes a long way.  Give it a try.  [https://lists.launchpad.net/multi-touch-dev/msg00617.html](https://lists.launchpad.net/multi-touch-dev/msg00617.html)

---

### Post by inportb on 2010-12-15
So basically, just install utouch? I see...

```
inportb@natty:~$ apt-cache search utouch
libutouch-grail-dev - Gesture Recognition And Instantiation Library - dev files
libutouch-grail1 - Gesture Recognition And Instantiation Library
libutouch-geis-dev - Gesture engine interface support - dev files
libutouch-geis-doc - Gesture engine interface support - documentation
libutouch-geis1 - Gesture engine interface support
utouch - A meta-package to install gesture libraries and tools
utouch-geis-tools - Gesture engine interface support - test tools
utouch-gesturetest - Test tool for the X Gesture extension
utouch-grail-tools - Gesture Recognition And Instantiation Library - test tools
xserver-xorg-input-mutouch - X.Org X server -- muTouch input driver
```

---

### Post by Paul S on 2010-12-16
hmmm, it seems like the utouch repo did not get the dist file updated properly.  Try this repo for direct download of ginn:  [http://ppa.launchpad.net/utouch-team/utouch/ubuntu/pool/main/g/ginn/](http://ppa.launchpad.net/utouch-team/utouch/ubuntu/pool/main/g/ginn/)

I think ginn is better than easystroke, although more difficult to configure.

1. you have to copy and edit your own version of /usr/share/ginn/wishes.xml .. open it in an editor to see the format

2. run "geistest" in a terminal and perform the new gesture you want to create.  copy the relevent terminal output into your version of wishes.xml and follow the model of the examples in your wishes.xml to create a new xml statement that describes your new gesture and the output mouse / key commands to perform.  see [http://ubuntuforums.org/showthread.php?t=1635401](http://ubuntuforums.org/showthread.php?t=1635401) and [https://lists.launchpad.net/multi-touch-dev/msg00621.html](https://lists.launchpad.net/multi-touch-dev/msg00621.html) for some more tips.

3. run "ginn <your-edited>wishes.xml" in a terminal to get ginn to do it's work

4. give bug or wish list feedback to utouch team

---

### Post by inportb on 2010-12-16
Thanks for the tip. I'll give this a spin :D

---

### Post by Skaarg on 2010-12-19
I'm surprised this hasn't been mentioned in this thread. It looks like someone working with Plasma Mobile on Meego got the S10-3t to rotate into portrait mode. It'd be nice if this could carry over to Ubuntu in some form. 

[http://mynokiablog.com/2010/11/22/video-plasma-mobile-on-meego-with-qml-demoed-on-lenovo-ideapad-s10-3t/](http://mynokiablog.com/2010/11/22/video-plasma-mobile-on-meego-with-qml-demoed-on-lenovo-ideapad-s10-3t/)

---

### Post by prshah on 2010-12-21
> **Skaarg said:**
> got the S10-3t to rotate into portrait mode. It'd be nice if this could carry over to Ubuntu in some form. 

Ubuntu CAN rotate into portrait mode. It's mentioned in this thread as well as in the Ubuntu Wiki for Lenovo s10-3t.

I have modified the script on the wiki slightly. I'm attaching it to this if you would like to try it.

Usage:```
./changeaxis.sh # rotate 90 deg clockwise
#or
./changeaxis.sh 0 #=normal or 1=portrait, 2=rev landscape, 3= rev portrait

```

Works great with EasyStroke for when in tablet mode!

However, please feel free to correct me if I have misunderstood your question.

---

### Post by ekeko on 2010-12-22
> **prshah said:**
> Ubuntu CAN rotate into portrait mode. It's mentioned in this thread as well as in the Ubuntu Wiki for Lenovo s10-3t.

I have modified the script on the wiki slightly. I'm attaching it to this if you would like to try it.

Usage:```
./changeaxis.sh # rotate 90 deg clockwise
#or
./changeaxis.sh 0 #=normal or 1=portrait, 2=rev landscape, 3= rev portrait

```Works great with EasyStroke for when in tablet mode!

However, please feel free to correct me if I have misunderstood your question.

Hi prshah,
your script works fine, thanks for it! i was looking for a script to have 90° rotation and not the other ones listed here allowing 180° only. your script belongs to the wiki I think.

regards,
ekeko.

---

### Post by prshah on 2010-12-23
> **ekeko said:**
> i was looking for a script to have 90° rotation and not the other ones listed here allowing 180° only. your script belongs to the wiki I think.

Thanks for pointing out this difference. However, I cannot take the credit; the script was cobbled together from various sources. I have just made some cosmetic modifications.

---

### Post by Skaarg on 2010-12-29
That 90 degree script is indeed very nice. It's just slightly a problem for me though because I'm not a fan of Unity so I use the 10.04 netbook interface on 10.10. Unfortunately it's not friendly with portrait resolutions. I lose a column of icons, and have that interesting bug. =(
[img]http://img148.imageshack.us/img148/695/screenshot1zb.png[/img]

If I were using a standard desktop mode interface I'm sure I would like this a lot.

---

### Post by msekolpsu on 2011-01-09
I love this thing running Ubuntu over Windows.  Two questions on running 10.10:

1.  Anyone know how to get the resolution higher than 1280x600?
2.  Can someone help me get an on screen keyboard working?  I saw the posts about iBus, but nothing is working.

Thanks!

---

### Post by inportb on 2011-01-21
Onboard works, as well as kvkbd.

---

### Post by marshcast on 2011-02-04
This may just be adding to Woes, but anyone know how to get the buttons by the keyboard to work?

Am excited... new s10-3t, lots of thread reading, lots of chance to get involved, (although a bit cagey), about to try easystroke (poss ginn). am a long time 'user' but wannabe dev, long way to go --- far too cagey.

and big Thanks to all for time effort and pleasant reading

---

### Post by marshcast on 2011-02-04
PS. Gagging to get multitouch to work, if there is anything I can do to help please let me know, not much ability yet, but anything I can do, i will ;)

---

### Post by marshcast on 2011-02-04
Hey inportb,

thanks for your input on these threads, been really helpful.

I been sat for a while now trying to get to grips with this. Multitouch (at least 2point) works with ginn -- twofinger drag fr scrolling etc), but am trying to get the easystroke going.

My main issue is that easystroke seems to require a keypress, and in tablet mode there is none.

How do you get around that?

---

### Post by prshah on 2011-02-05
> **marshcast said:**
> 
My main issue is that easystroke seems to require a keypress, and in tablet mode there is none.

In the Easystroke Preferences Tab, I have set the gesture button to button 1, no additional buttons, and timeout profile as default. This allows me to create the strokes on the screen. If I hold down my finger on the screen for a little under a second, gestures are cancelled, and a click is registered instead (Eg, for when scrolling in FireFox with the "Grab and Drag" extension.

---

### Post by marshcast on 2011-02-07
> **prshah said:**
> In the Easystroke Preferences Tab, I have set the gesture button to button 1, no additional buttons, and timeout profile as default. This allows me to create the strokes on the screen. If I hold down my finger on the screen for a little under a second, gestures are cancelled, and a click is registered instead (Eg, for when scrolling in FireFox with the "Grab and Drag" extension.

thanks prshah ;)

---

### Post by kimchimik on 2011-02-07
Hi Guys,

Newbie question here.  How do i get a right click with the touchscreen.  When i was using my tablet with windows 7 i just needed to press and hold but that doesn't seem to work.

Thank You,

---

### Post by prshah on 2011-02-08
> **kimchimik said:**
> How do i get a right click with the touchscreen.  When i was using my tablet with windows 7 i just needed to press and hold 

That is called a dwell click. You can find suitable settings for it in System-Preferences-Mouse-Accessibility-Simulated Secondary Click.

Be warned though, the process is not as satisfying as in Win7; there is no visual feedback and pointer positioning is usually iffy. This will also not play well with EasyStroke gesture recognition; ymmv.

I suggest you will be better off defining a gesture for right click in EasyStroke, rather than using dwell click. Just a suggestion.

---

### Post by jackofhearts on 2011-02-26
> **Canadian_Pirate said:**
> uTouch does not seem to work on my S10-3t. I do not know why...

For convenience I have created a script to make the touchpad work (with pressing buttons and scrolling) in 10.10. 
THIS SCRIPT WILL INSTALL DKMS IF IT IS NOT ALREADY INSTALLED.
THIS IS NOT TESTED. (tell me any bugs and I will fix them.)

Type this to run:
```
chmod +x mouse.sh
sudo ./mouse.sh
```

EDIT: Small bugs in the program. Fixed now

At row 21, you wrote 'dkmd' instead of 'dkms' :D

---

### Post by phlibi on 2011-02-26
Hi folks,

at first, I'd like to thank all of you for providing some tips to make this little device usable with [x|k]ubuntu. I'm running Xubuntu and really enjoy it, at least in netbook mode. Tablet mode still is a bit difficult due to the fact that touchscreen support lacks some important features (good onscreen keyboard, scrolling, rotation-key/accelerometer, etc.), but it gets better and better. Maybe it makes a jump forward when Natty finally arrives :)

To use the device at school, I need a way to attach it to a projector. I was quite surprised to see that this almost worked out of the box. But notice the word 'almost', xrandr has it's own opinion of choosing the 'right' resolution for the attached display, in my case it always used 800x600, which is a bit small.
Since I didn't manage to create a correct xorg.conf to choose some different modes, I've created a script to initialize the xrandr modes at login and switch between them dynamically. You can find it attached to this post.

Usage is quite simple:
- Add the script with parameter "init" to the autostart
- Create  a shortcut to "resolution.sh next" on the XF86Display-key (Fn+F3)
- Add some launcher(s) to the panel to select the different modes

I've got to do a presentation next week, let's see how it works :)

Regards,
Philipp

---

### Post by Flippy209 on 2011-03-06
First off, fantastic thread! This Lenovo Ubuntu build may quite be the best netbook tablet out there!

One question - is there a way to take prshah's script and bind it to a key stroke combination?

I'm using ubuntu 10.10 - do not like the netbook unity interface.

Thanks for an awesome thread and TIA for any suggestions!

---

### Post by prshah on 2011-03-07
> **Flippy209 said:**
> 
One question - is there a way to take prshah's script and bind it to a key stroke combination?

Yes, you can bind the script to a keystroke if compiz is active. Open System-Preferences-Compiz Config Settings Manager-Commands.

Enter the full path to the script as "command 0"; then, in the next tab (key bindings) choose your preferred key to trigger command 0.

I would suggest the mute button on the screen, so that it is accessible even when the netbook is in tablet mode (the other keys don't work). I would also suggest you set up an onscreen gesture to trigger the script.

---

### Post by Flippy209 on 2011-03-07
Perfect, thank you! I was using "super key" a.k.a. "windows key" +1 but that is hard when in tablet mode! And, I likely will never need to mute! Great suggestion.

> **prshah said:**
> I would also suggest you set up an onscreen gesture to trigger the script.

Is this accomplished with that EasyStroke program you have mentioned?

Edit: I have easystroke and it looks like it will do what I need. How do you bind actions to it?

Thanks again!
Jeff

---

### Post by prshah on 2011-03-08
> **Flippy209 said:**
> I have easystroke <..> How do you bind actions to it?

Easystroke is very simple and easy to use, but very versatile as well, so setting it up is a little tricky. You will have to play with the settings for the results that suit you best, but to start you off, these are my settings (you can then tweak to your convenience).

In the easystroke interface:

Preferences tab: 
Gesture button: Button 1
Timeout profile: Default
Method to show gestures: Default
Show popups: Enabled, Autostart: Enabled

Advanced tab:
Timeout Gestures: enabled
Show popups...: enabled
Move the cursor back...: enabled
Devices: "Cando Corporation Cando..." - enabled, touchpad - disabled

Actions:
Click "Add Action", give a Name (Eg, Max/Restore), select a Type (Eg, Key), and in details, enter the keycombo (Eg Alt+F10). 
Then click "Record Stroke", and make a gesture as suitable on the screen.

With that, you should be good to go. Create more gestures as required, and continue to fiddle with the options to tweak to your satisfaction.

Edit: Added easystroke screenshot to show some sample gestures to start you off.

---

### Post by Flippy209 on 2011-03-08
Awesome - I was able to get the rotate screen gesture working. One problem I'm having is that it appears that easystroke disabled the google chromium addon for flick and screen scrolling. I actually liked that interface better. 

I'm going to peek at your config and see if I can find something that will work better for me.

FWIW - I work in IT and all of the guys I work with are completely amazed at what this little netbook can do. I owe their amazement to this thread! Thanks again guys!

---

### Post by prshah on 2011-03-08
> **Flippy209 said:**
> One problem I'm having is that it appears that easystroke disabled the google chromium addon for flick and screen scrolling. I actually liked that interface better. 

are completely amazed at what this little netbook can do.

You can disable gestures on a per-application basis in Easystroke preferences. Or, if you don't want to do that, but still continue to use flick and scroll, just hold down your finger on the chrome window for a second or so for the gesture to timeout, and then it will flick and scroll as usual.

btw, I hope you are aware that you can install and use 64-bit on this netbook. Don't know about you, but mine came with 32-bit W7 Home, but I am using Ubuntu 10.10 64-bit. Any real advantage? I dunno, just seems more modern.

---

### Post by Flippy209 on 2011-03-08
Yep - running 64x ubuntu 10.10. Full compiz effects. runs like a champ!

I will check out those advanced commands tomorrow. Everyday I play with this thing and read this thread it becomes more and more the ideal netbook for the linux enthusiast. As well somebody who wants some flexibility with this type of purchase.

---

### Post by dante.eisenstein on 2011-03-09
hello together,

thanks for all the posts. i am writing this on an s10-3t running ubuntu netbook remix 10.10, using the touchscreen in tablet mode. camera, sound, wlan all work well. thanks!

cheers,
dante

---

### Post by girlgeek19 on 2011-03-12
Is there a way to fix the cursor orientation when in portrait mode? (Pointer still responds as if in normal landscape mode.)

Sooo close to being perfect!

EDIT: Could something similar to this be implemented?: [http://ubuntuforums.org/showthread.php?t=943297](http://ubuntuforums.org/showthread.php?t=943297)

---

### Post by robertwb on 2011-03-13
I am loving having ubuntu on my lenovoa s103t, but I cannot for the life of me figure out how to get the onscreen keyboarrd to appear?  
FWIW - I installed Ubuntu straight up using the universal installer, so I have not hacked in anything at all.


Any help would be appreciated!

r.b.

---

### Post by girlgeek19 on 2011-03-13
Do you already have one installed?

I added a launcher to the panel. Someone might have a better solution.

What I did:
*Right click the panel where you want your shortcut.
*Click "add to panel"
*Click "custom applications launcher"
*Type in a name for name and the name of the keyboard application for application (onboard in my case)

---

### Post by robertwb on 2011-03-13
[QUOTE=girlgeek19;10555442]Do you already have one installed?

I added a launcher to the panel. Someone might have a better solution.

I don't know what was going on, but now it is working well.  Added the onboard button to my panel.  Getting used to the whole gesture thing as well. very nice.

thanks,
r.b.

---

### Post by prshah on 2011-03-13
> **girlgeek19 said:**
> Is there a way to fix the cursor orientation when in portrait mode? (Pointer still responds as if in normal landscape mode.)

Please use the script from [post #349]("http://ubuntuforums.org/showpost.php?p=10263751&postcount=349") in this thread. Pointer orientation is working fine in all modes (Portrait, Landscape, Reverse Portrait, Reverse Landscape).

If your mouse still doesn't respond correctly, then please run the script from the terminal (Applications-Accessories-Terminal) and post back errors.

---

### Post by girlgeek19 on 2011-03-13
I'm getting this error message:
property Evdev Axis Calibration doesn't exist, you need to specify its type and format

Thank you!

---

### Post by prshah on 2011-03-14
> **girlgeek19 said:**
> property Evdev Axis Calibration doesn't exist, you need to specify its type and format

Check if you have the correct device number. It is hardcoded into the script as device=11.

Check with the following terminal (Applications-Accessories-Terminal) command```
xinput --list --short|grep -E -i cando\|panel
``` and you should get output as follows:> &#9116;   &#8627; Cando Corporation Cando 10.1 Multi Touch Panel with Controller	[color=red]id=11[/color]	[slave  pointer  (2)]

Note the "id" number mentioned, and edit the script to change line #28 to the id number mentioned. (Eg: device=12).

Please post back with results / errors.

---

### Post by girlgeek19 on 2011-03-14
Ahh...that did it. Changed device id to '12' and now it works fine. :D

Thank you so much!

---

### Post by prshah on 2011-03-14
> **girlgeek19 said:**
> Changed device id to '12' and now it works fine.

Please post the output of the xinput command from the previous posts.

---

### Post by girlgeek19 on 2011-03-14
&#9116;   &#8627; Cando Corporation Cando 10.1 Multi Touch Panel with Controller    id=12    [slave  pointer  (2)]

Edited the script to update the id and everything works fine now.

---

### Post by Bufke on 2011-03-14
Woo working multi touch.

[http://code.google.com/p/touchegg/](http://code.google.com/p/touchegg/)

---

### Post by robertwb on 2011-03-19
Got the basics working nicely, added in the rotate screen scripts associated with a easystroke gesture - very slick.  Also have successfully printed with my HP OfficeJet 6300 -- but there is a huge delay between clicking "print" and when the document actually gets out to the printer - like 5 minutes.  The printer is connected to the network via its own ethernet cable.

System:
- Ubuntu 10.10 remix
- HP OfficeJet 6300 printer - same symptoms printing from Firefix, chrome, openoffice, Flash (within browser).

I can live with this, just thought I would put this out there in case anyone else had a similar experience.

regards,
r.b.

---

### Post by MadnessRed on 2011-04-03
Hi, I am having problems with rotating the input with natty.
If I run list-props for the screen, id 14 I get:
```
anthony@Anthony-Tablet:~$ xinput list-props 14
Device 'Cando Corporation Cando 10.1 Multi Touch Panel with Controller':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (267):	0
	Device Accel Constant Deceleration (268):	1.000000
	Device Accel Adaptive Deceleration (269):	1.000000
	Device Accel Velocity Scaling (270):	10.000000
	Evdev Axis Inversion (271):	0, 0
	Evdev Axis Calibration (272):	<no items>
	Evdev Axes Swap (273):	0

```

However, the following command has no effect on the touchscreen input.
```
anthony@Anthony-Tablet:~$ xinput set-prop 14 "Evdev Axis Inversion" 1 1
```

The change is being registered though:
```
anthony@Anthony-Tablet:~$ xinput list-props 14
Device 'Cando Corporation Cando 10.1 Multi Touch Panel with Controller':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (267):	0
	Device Accel Constant Deceleration (268):	1.000000
	Device Accel Adaptive Deceleration (269):	1.000000
	Device Accel Velocity Scaling (270):	10.000000
	Evdev Axis Inversion (271):	1, 1
	Evdev Axis Calibration (272):	<no items>
	Evdev Axes Swap (273):	0
	...

```

The following commands do work, however, to enable/disable the input:
```
anthony@Anthony-Tablet:~$ xinput set-prop 14 "Device Enabled" 0
anthony@Anthony-Tablet:~$ xinput set-prop 14 "Device Enabled" 1
```

So for some reason the input rotation is being ignored. Any help getting this working would be great.

Thanks

Anthony

---

### Post by Canadian_Pirate on 2011-04-03
Hello, 
I was wondering if anybody got the side buttons above the mute working, or exactly what type of input they send. I would like the technical name so I can do more research.

---

### Post by Silthanis on 2011-04-03
> **MadnessRed said:**
> Hi, I am having problems with rotating the input with natty.

I can confirm this on another device with id=11.  The only help I can give is a link to the bug report I filed:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493)

---

### Post by MadnessRed on 2011-04-03
> **Canadian_Pirate said:**
> Hello, 
I was wondering if anybody got the side buttons above the mute working, or exactly what type of input they send. I would like the technical name so I can do more research.

They're mentioned in lsinput if that helps.

---

### Post by areyedancin on 2011-04-12
Hi everyone,

I'm new to the forum and to Ubuntu. I've bought an s10-3t and want to replace windows starter with ubuntu 10.10. I've been reading up on forums and am aware that the one key recovery won't work if the partitions are changed, so I guess OKR won't work after putting on ubuntu, but I have a question that hopefully someone here can answer for me...

If I burn recovery cds/dvds using OKR program before installing Ubuntu, will they still work after installing it? 

Or can I install ubuntu without messing with partitions? I'd like to get rid of windows completely/don't want to dual boot.

Like I say, I'm new to linux and want to have a way to get back to factory settings if I mess it up! Or if I want to sell the netbook in the future.

Thanks, :)

---

### Post by MadnessRed on 2011-04-12
> **areyedancin said:**
> Hi everyone,

I'm new to the forum and to Ubuntu. I've bought an s10-3t and want to replace windows starter with ubuntu 10.10. I've been reading up on forums and am aware that the one key recovery won't work if the partitions are changed, so I guess OKR won't work after putting on ubuntu, but I have a question that hopefully someone here can answer for me...

If I burn recovery cds/dvds using OKR program before installing Ubuntu, will they still work after installing it? 

Or can I install ubuntu without messing with partitions? I'd like to get rid of windows completely/don't want to dual boot.

Like I say, I'm new to linux and want to have a way to get back to factory settings if I mess it up! Or if I want to sell the netbook in the future.

Thanks, :)

The one key recovery works by creating the system at factory settings on a partition on your hard drive. If you remove this partition okr won't work.
I think that grub, Ubuntu's boot manager can boot okr like it would with any other operating system so it should be ok to remove windows and install ubuntu, a long as you leave the okr partition intact.

That said, if you are new to Ubuntu, unless you are short of space it may be worth dual booting windows. I have been using Ubuntu for about 4 years but I still keep a windows os in dual boot.

If you create a recovery disk then you should be able to recover from that and then remove the recovery partition.

Again this is all "**should**". I haven't experimented with it, my recovery partition is still intact and wasting space and I haven't burned any recovery cd's. It's probably worth contacting the manufacturers and asking if the recovery disks require the okr partition to be intact.

***_tl;dr_***
The safest thing to do is probably resize you windows partition to give yourself 40gb of space for Ubuntu or something like that. Leave the okr partition as it is. Creating a physical recovery disk is always a good idea.

---

### Post by MadnessRed on 2011-04-14
> **Silthanis said:**
> I can confirm this on another device with id=11.  The only help I can give is a link to the bug report I filed:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/749493)

Great, thanks, the bug report had a comment which helped, I have a solution, 1 sec while I code it.

Edit1: Ok, I can rotate the output is is a matrix rotation so it is about the origin. As in the entire is being rotated round the top left corner. So if it goes from 0=>100% for normal mode, it goes from -100%=>0 for the inverted mode. It's progress though.

Edit2: Since it is a 3d matrix and the z value appears constant is is possible to use that to create a linear translation :) Just need to find the right constants.

Edit3: Success, I have a fully working rotation script on natty!!! :) I'll post in a sec

---

### Post by MadnessRed on 2011-04-14
Attached rotation script for Ubuntu 11.04 Natty Narwhal

---

### Post by mairas on 2011-04-15
Hi,

after upgrading my S10-3t to Ubuntu Natty, I have been having terrible problems resuming the computer from suspended state - when I open the display, every second or third time, the standard power and battery leds are lit but other than that, the computer is unresponsive and there's nothing to do except a hard reboot. Obviously, /var/log/syslog has no indication of anything being wrong (or at least I didn't notice anything there).

Has anyone else had similar issues?

Cheers,

mairas

---

### Post by MadnessRed on 2011-04-15
> **mairas said:**
> Hi,

after upgrading my S10-3t to Ubuntu Natty, I have been having terrible problems resuming the computer from suspended state - when I open the display, every second or third time, the standard power and battery leds are lit but other than that, the computer is unresponsive and there's nothing to do except a hard reboot. Obviously, /var/log/syslog has no indication of anything being wrong (or at least I didn't notice anything there).

Has anyone else had similar issues?

Cheers,

mairas

I installed Natty directly and have not had these problems.

---

### Post by mairas on 2011-04-16
> **MadnessRed said:**
> I installed Natty directly and have not had these problems.

Thanks for the info - I might nuke my current setup and try that out.

---

### Post by nnutter on 2011-04-16
I have Natty installed and am unable to get my wireless working. The system starts up with the wireless disabled in software (rfkill list). If I try to toggle it on then the system freezes. I've also tried installing the Broadcom STA drivers and was still unable to get my wireless working. I believe with the Broadcom STA drivers installed the system would not lock up but trying to toggle the wireless on would have no effect.

The wireless is not hardware or BIOS disabled.

---

### Post by bartango007 on 2011-04-27
Hi.  Been running ubuntu on s10-3t for 5mths and love the set up.  Has any one got Gnome3 running on Maverick (don't want to step up to Natty just yet).  Pls link to any instructions if poss as these havent worked for me [http://bit.ly/c2ZMvf](http://bit.ly/c2ZMvf)

Great to see a [pro]active thread on this machine which I use for everything.  Never realised it could go 64bit.  Is there anyway to move from 32 to 64 via terminal/synaptics.

I'm no programmer just an enthused end user of Ubuntu since Edgy Eft and Lenovo fanboy

---

### Post by MadnessRed on 2011-04-27
Hm, I have heard of people installing 64 bit onto a partition which had 32 bit on before, which basically upgraded it, but leaving the configuration as it was. Unless you are fairly confident, I would give this a miss though.

Personally I would wait a couple of days till Natty is released, then download the 64bit version of that and start from scratch. Just remember to back up all your files first.

---

### Post by prshah on 2011-04-28
> **bartango007 said:**
> Never realised it could go 64bit.  Is there anyway to move from 32 to 64 via terminal/synaptics.

There is no real benefit to move to 64bit on these specs. If you already are running 32bit, then it's better not to worry about 64 bit until you plan to do a complete re-install.

---

### Post by ernia on 2011-05-01
> **MadnessRed said:**
> Attached rotation script for Ubuntu 11.04 Natty Narwhal

your scripts works, thanks.
if i'm getting it right and i'm not doing something wrong i've noted that ginn's coordinate system (and external mouse too) is screwed up from this script, e.g. when the screen is upside down gestures works conversely, e.g. html pages in firefox scrolls on the opposite side of where i'm scrolling my fingers.
i enclose the wishes.xml file i'm using and trying to edit (i still miss right click but got two fingers scroll in firefox and evince)
maybe the script could restart ginn sourcing a different wishes.xml ?
but what about external mouse?
sorry about my broken english.

---

### Post by ernia on 2011-05-02
git version of xserver-xorg-input-evdev supports (enabling it through xinput --set-prop or probably a .conf in xorg.xonf.d) right click emulation:```
fabio@s10:~$ xinput --list-props "Cando Corporation Cando 10.1 Multi Touch Panel with Controller"
Device 'Cando Corporation Cando 10.1 Multi Touch Panel with Controller':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (262):	0
	Device Accel Constant Deceleration (263):	1.000000
	Device Accel Adaptive Deceleration (264):	1.000000
	Device Accel Velocity Scaling (265):	10.000000
	Evdev Axis Inversion (266):	0, 0
	Evdev Axis Calibration (267):	<no items>
	Evdev Axes Swap (268):	0
	Axis Labels (269):	"Abs X" (283), "Abs Y" (284), "Abs Misc" (285), "Abs MT Position X" (286), "Abs MT Position Y" (287), "Abs MT Tracking ID" (288)
	Button Labels (270):	"Button Unknown" (254), "Button Unknown" (254), "Button Unknown" (254), "Button Wheel Up" (141), "Button Wheel Down" (142)
	Evdev Middle Button Emulation (271):	0
	Evdev Middle Button Timeout (272):	50
[COLOR="Red"][B]	Evdev Third Button Emulation (273):	1
	Evdev Third Button Emulation Timeout (274):	500
	Evdev Third Button Emulation Button (275):	3
	Evdev Third Button Emulation Threshold (276):	20
[/B][/COLOR]	Evdev Wheel Emulation (277):	0
	Evdev Wheel Emulation Axes (278):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (279):	10
	Evdev Wheel Emulation Timeout (280):	200
	Evdev Wheel Emulation Button (281):	4
	Evdev Drag Lock Buttons (282):	0

```
i don' have time right now to document this but basically it's
git clone git://anongit.freedesktop.org/xorg/driver/xf86-input-evdev
then install missing dependencies make and brutally subsitute /usr/lib/xorg/modules/input/evdev_drv.so with the one that you have just made.
this will make xorg crash and you will miss your changes at every xserver-xorg-input-evdev upgrade, if you have a cleanest way to do it post here :D
many thanks to Peter Hutterer for the patch:
[http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/commit/?id=d9001a6b](http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/commit/?id=d9001a6b)
this patch + ginn = touchscreen more usable :D:D:D

EDIT
i enclose the module if you trust me and don't want to bother to build it
remember to
```
fabio@s10:~$ xinput --set-prop "Cando Corporation Cando 10.1 Multi Touch Panel with Controller" "Evdev Third Button Emulation" 1
fabio@s10:~$ xinput --set-prop "Cando Corporation Cando 10.1 Multi Touch Panel with Controller" "Evdev Third Button Emulation Timeout" 500

```
the second command sets the timeout, check which one is the best for you
the module works with today natty's xorg

REEDIT it seems like the module like i posted breaks ginn, i will retrying appling ubuntu's patch or applying third button emulation to ubuntu's evdev -- no way for me, i know nothing about C and ubuntu's evdev is heavily patched, so i must choose between right-click or ginn. sorry about that

---

### Post by prshah on 2011-05-02
Hello,

I have a Lenovo S10-3t with the following information:```
BIOS Information
        Vendor: LENOVO    
        Version: 24CN22WW  
        Release Date: 03/12/2010
```

It has the SIM slot under the battery. However, putting in a 3G enabled SIM has no effect; neither in Windows 7 Home Basic nor in Ubuntu 10.10.

I have read that some of these netbooks do not have the 3G modem and that a minipci card has to be installed separately for this; however, when I opened it up, I found the minipci slot to be already populated.

Any idea on how I can confirm wether or not my model is 3G capable? If it is, how to I use 3G? If you have a working 3G S10-3t, can you please post the output from the following terminal (Applications-accessories-terminal) commands:```
lspci
lsusb
sudo dmidecode |grep -A 5 -i "bios info"
```

---

### Post by ernia on 2011-05-02
```
fabio@s10:~/evdevubuntu$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
fabio@s10:~/evdevubuntu$ lsusn
Comando "lsusn" non trovato. Forse si intendeva:
 Comando "lsusb" dal pacchetto "usbutils" (main)
lsusn: comando non trovato
fabio@s10:~/evdevubuntu$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
fabio@s10:~/evdevubuntu$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 10ab:0816 USI Co., Ltd 
Bus 003 Device 002: ID 2087:0a01  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04f2:b1a1 Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 0bdb:1902 Ericsson Business Mobile Networks BV F3507g v2 Mobile Broadband Module
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fabio@s10:~/evdevubuntu$ sudo dmidecode |grep -A 5 -i "bios info"
BIOS Information
	Vendor: LENOVO    
	Version: 24CN62WW  
	Release Date: 08/30/2010
	Address: 0xE69B0
	Runtime Size: 104016 bytes
fabio@s10:~/evdevubuntu$ 

```
but i've modified whitelist to allow f3507g at boot, i don't remember which would be the default allowed card, i thin f3697something.
i hade a spare full minipci slot with antenna cables already installed, just modified the bios with googled instuctions and inserted the card.

---

### Post by rrounsav on 2011-05-04
Has anyone had any success with using easystroke in Natty?

---

### Post by fearstaff on 2011-05-08
Hello to everyone. I've installed Ubuntu 11.04 on my S10-3t about a week ago and I have a big problem with videocard: after some random time of working I'm getting my system stucked and artefacts all over the screen. Has anyone had the same problems? Are there any solutions?
[SIZE=1]
Sorry if my english is a bit rusty[/SIZE]

---

### Post by MadnessRed on 2011-05-08
> **fearstaff said:**
> Hello to everyone. I've installed Ubuntu 11.04 on my S10-3t about a week ago and I have a big problem with videocard: after some random time of working I'm getting my system stucked and artefacts all over the screen. Has anyone had the same problems? Are there any solutions?
[SIZE=1]
Sorry if my english is a bit rusty[/SIZE]

Hm, can you provide a screenshot or photo?
Did this start happening right after you installed?
If you run on the live usb, does it happen?

> **rrounsav said:**
> Has anyone had any success with using easystroke in Natty?

No, sorry, I haven't tried it, GINN works well though.

---

### Post by fearstaff on 2011-05-10
> **MadnessRed said:**
> Hm, can you provide a screenshot or photo?
Did this start happening right after you installed?
If you run on the live usb, does it happen?

That's impossible to take a screenshot, so here is the photo. [http://img806.imageshack.us/img806/990/1005111553.jpg](http://img806.imageshack.us/img806/990/1005111553.jpg) 
 Well, I amn't sure but I think it started right after the installation. I've read about problems with videocard drivers, can't it be this case? About live mode, I can't try it now, but in a next few days.

---

### Post by brysonborg on 2011-05-12
> **rrounsav said:**
> Has anyone had any success with using easystroke in Natty?

I can't get easystroke to work with Natty using the S10-3t touchscreen.  It does with with the trackpad.
I can use the QuickScrolling plugin for Chrome to scroll with the touchscreen the way you'd expect.
Curiously, though, I can't use the touchscreen to scroll through a pdf using Evince, but the trackpad works as expected.
This is really wierd.  Anyone have any ideas why?

---

### Post by MadnessRed on 2011-05-12
> **brysonborg said:**
> I can't get easystroke to work with Natty using the S10-3t touchscreen.  It does with with the trackpad.
I can use the QuickScrolling plugin for Chrome to scroll with the touchscreen the way you'd expect.
Curiously, though, I can't use the touchscreen to scroll through a pdf using Evince, but the trackpad works as expected.
This is really wierd.  Anyone have any ideas why?

The trackpad uses the synaptics driver which implements 2 finger scrolling.

The touchscreen uses the evdev (I think) driver which does not implement it, however, geastures can be recognised by other programs such as GINN.

---

### Post by fearstaff on 2011-05-12
Back to my question, I don't know how it actualy helped but when I reinstalled flash plugin the problem almost gone. Now it appears as blinking of all the windows, but rather seldom, only once or twice a day.

---

### Post by MadnessRed on 2011-05-12
> **fearstaff said:**
> Back to my question, I don't know how it actualy helped but when I reinstalled flash plugin the problem almost gone. Now it appears as blinking of all the windows, but rather seldom, only once or twice a day.

Ok, glad you got it mostly sorted. I am afraid I don't have any suggestions regarding your blinking windows but hopefully someone with more knowledge can you you there.

---

### Post by brysonborg on 2011-05-13
> **MadnessRed said:**
> The trackpad uses the synaptics driver which implements 2 finger scrolling.

The touchscreen uses the evdev (I think) driver which does not implement it, however, geastures can be recognised by other programs such as GINN.


However, I cannot get easystroke to recognize any input from the touchscreen.  I have it configured to read input from mouse button 1.  When I go to train a gesture, the only thing that happens (from the touchscreen) is that the cursor highlights a rectangular area of the desktop.  When I do the same thing with the trackpad, easystroke draws the squiggly line that I've stroked.

---

### Post by prshah on 2011-05-14
> **brysonborg said:**
> I cannot get easystroke to recognize any input from the touchscreen. 
 happens (from the touchscreen) is that the cursor highlights a rectangular area of the desktop.  trackpad, easystroke draws the squiggly line that I've stroked.

Please see the advanced tab; enable the touchscreen, and (optionally) disable the touchpad for easystroke source device.

Advanced tab:
Timeout Gestures: enabled
Show popups...: enabled
Move the cursor back...: enabled
Devices: "Cando Corporation Cando..." - enabled, touchpad - disabled

For more details, including screenshot, please see [post #367]("http://ubuntuforums.org/showpost.php?p=10535879&postcount=367")

---

### Post by brysonborg on 2011-05-14
> **prshah said:**
> Please see the advanced tab; enable the touchscreen, and (optionally) disable the touchpad for easystroke source device.

Advanced tab:
Timeout Gestures: enabled
Show popups...: enabled
Move the cursor back...: enabled
Devices: "Cando Corporation Cando..." - enabled, touchpad - disabled

For more details, including screenshot, please see [post #367]("http://ubuntuforums.org/showpost.php?p=10535879&postcount=367")

Hey, Thanks for the reply!
Actually, googling that post is what led me to this discussion in the first place.  I have followed all the instructions, and easytouch still isn't working for me.
Like I had mentioned in an earlier reply, if I open up a pdf in Evince, I can click-and-drag on the touchpad to scroll back-and-forth through the document.  This doesn't work using the touchscreen: all I can do is select text.  This makes me wonder if there is a feature of the touchscreen driver that is disabled.  Any ideas?

---

### Post by mairas on 2011-05-15
> **mairas said:**
> Hi,

after upgrading my S10-3t to Ubuntu Natty, I have been having terrible problems resuming the computer from suspended state - when I open the display, every second or third time, the standard power and battery leds are lit but other than that, the computer is unresponsive and there's nothing to do except a hard reboot. Obviously, /var/log/syslog has no indication of anything being wrong (or at least I didn't notice anything there).

Has anyone else had similar issues?

Cheers,

mairas

A bit of experimentation revealed that resume failed 100% of times. Adding the acpi_sleep=nonvs boot option solved the issue:

[http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010](http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010)

After this modification, suspend/resume works fine again.

---

### Post by prshah on 2011-05-15
> **brysonborg said:**
> I have followed all the instructions, and easytouch still isn't working for me.

Can you post a screenshot of the advanced tab?

---

### Post by Okar on 2011-05-16
is suspend/resume working for you guys in ubuntu 11.04?
for me ubuntu will just shut down instead of suspending.

---

### Post by phlibi on 2011-05-16
> **mairas said:**
> A bit of experimentation revealed that resume failed 100% of times. Adding the acpi_sleep=nonvs boot option solved the issue:

[http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010](http://www.michali.org/ubuntu/sony-vaio-fw490j/73-suspendresume-on-ubuntu-1010)

After this modification, suspend/resume works fine again.
Hi mairas,

thanks for the hint. This doesn't seem to work for me, though. I've updated from 10.10 to 11.04 and have the same problem, the computer freezes most of the time when resuming from Standby (Suspend). With the posted option I was able to suspend/resume successfully twice, but after the next try, it crashed again.

Regards,
Philipp


EDIT: Just to be sure: I did update-grub after the modification and also checked the linux-line in GRUB. The option is there, but doesn't seem to change anything...

---

### Post by Okar on 2011-05-20
I put a "acpi_sleep=nonvs" to the grub config. however my ubuntu will still just shutdown instead of suspend... :(

Am I the only one having this problem?

---

### Post by phlibi on 2011-05-27
Hi folks,

to address the suspend issue (crash when resuming) I've just updated my BIOS to 24CN62WW. Didn't change anything however :(

Just wanted to inform you that it's not worth to get Windows back on the device just for this.

Regards,
Philipp

---

### Post by Okar on 2011-06-02
I added the prerelease  updates. the hibernation is now working.

i got still no luck with the suspend though.

---

### Post by fcomstoc on 2011-06-03
Hey all; 
My wireless stopped working (I think there is something wrong with the hardware switch), so I was thinking of ditching my wifi card and switching to 3g when I am not at home, has anyone tried using a 3g card with ubuntu on this computer?? 

Thanks 
Frank

---

### Post by zob on 2011-06-08
You're right there is a problem with the hardware switch. You can turn your wifi back on by resetting CMOS:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577114)

And never touch that hardware switch again.

---

### Post by nnutter on 2011-06-15
> **zob said:**
> You're right there is a problem with the hardware switch. You can turn your wifi back on by resetting CMOS:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577114)

And never touch that hardware switch again.

Thank you! I thought I tried restoring my BIOS defaults at some point but apparently not. Very happy to have wireless working again.

---

### Post by nnutter on 2011-06-15
For those who still have issues resuming from sleep you should mark [resume fails for Lenovo Ideapad S10-3t]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664") as affecting you and try the fix of adding 'nohpet' to Grub.

> Adding 'nohpet' to Grub allows resume to work correctly.

I edited /etc/default/grub to add 'nohpet' to GRUB_CMDLINE_LINUX_DEFAULT and then ran 'sudo update-grub' and rebooted. So my GRUB_CMDLINE_LINUX_DEFAULT line now reads:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohpet"

---

### Post by btnz on 2011-06-25
Any way to get the first two buttons on the screen panel to work (touch, rotation)?
xev doesn't display any events when I click them.
Otherwise I might have to fall back to remapping mute to something else and putting the rotation script on there…

---

### Post by phlibi on 2011-07-01
Hi nnutter,

thanks a lot for the "nohpet"-hint, this seems to have solved the suspend issue for me as well! What would be interesting now is how such a timer could cause these problems and if there are any downsides of having them disabled...

Best regards,
Philipp

---

### Post by rrounsav on 2011-07-22
There is an experimental driver that will map the touch and rotate buttons to keyboard presses.  I have already package the drivers for rpm, but have not learn to create deb packages yet.  The driver can be installed from source available here [http://gitorious.org/iaps/iaps](http://gitorious.org/iaps/iaps).  The original source has to be modified in order to change the default key mapping.

---

### Post by MadnessRed on 2011-08-01
> **rrounsav said:**
> There is an experimental driver that will map the touch and rotate buttons to keyboard presses.  I have already package the drivers for rpm, but have not learn to create deb packages yet.  The driver can be installed from source available here [http://gitorious.org/iaps/iaps](http://gitorious.org/iaps/iaps).  The original source has to be modified in order to change the default key mapping.

That's great news!! I'll have a play sometime.

---

### Post by StartedTheFire on 2011-08-25
I just ordered one of these and need to know how to get it working. The wiki links here but doesn't say where to find the answers. Would anyone be so kind as to repost basic instructions for what to do right after installing the OS? Apparently there exist fixes for wifi and the touchscreen, but I can't find them!

---

### Post by MadnessRed on 2011-08-25
> **StartedTheFire said:**
> I just ordered one of these and need to know how to get it working. The wiki links here but doesn't say where to find the answers. Would anyone be so kind as to repost basic instructions for what to do right after installing the OS? Apparently there exist fixes for wifi and the touchscreen, but I can't find them!

With that latest version of Ubuntu, everything worked out of the box for me.

---

### Post by StartedTheFire on 2011-08-27
How good is the touch screen support in software? Can you do things like swipe through pictures or do you have to just use it exactly as a mouse?

---

### Post by MadnessRed on 2011-08-27
> **StartedTheFire said:**
> How good is the touch screen support in software? Can you do things like swipe through pictures or do you have to just use it exactly as a mouse?
Out of the box it works just as a mouse. You can install gesture software where you map a gesture to a keypress. You can assign gestures for individual programs.
It's mentioned on this forum thread i think, don't have my laptop with of though and i can't remember what it's called, sorry. Hope this helps

---

### Post by StartedTheFire on 2011-09-03
I just got my s10-3t yesterday and the touchscreen doesn't seem to be working at all- on windows or on ubuntu. It's DEFINITELY supposed to work right when you open it right? There isn't something i missed to enable the screen?

I couldn't find a donwload of the "netbook edition" so I just made a regular 11.04 usb stick. Does 11.04 desktop edition not support touchscreens? I couldn't really find any other downloads, ubuntu.com just says "HURR CLICK THIS ONE BUTTON AND EVERYTHING JUST WORKS" rather than giving any detailed menus.

---

### Post by Jenopo on 2011-09-03
Hey, I've sifted through this thread, but not entirely, so apologies if I'm asking about previously covered material, but I'm looking to dual boot my s10-3t with Ubuntu 11.04 and keeping my windows 7. I've done all the preparations such as backing up and creating my installation usb, but I've reached an issue with regard to partitioning my hard drive, which is that it won't let me create an additional partition, stating the computer has the maximum number as it is. It currently has a C: drive of roughly 186gb, a D: logical drive of about 30, a small 200mb partition, which is listed as "primary" so presumably of some importance and an OEM partition of 14.75gb. 

As something of a computer illiterate, I'm just looking for guidance from someone who has dealt with this. Anyone able to help me?

---

### Post by MadnessRed on 2011-09-04
> **StartedTheFire said:**
> I just got my s10-3t yesterday and the touchscreen doesn't seem to be working at all- on windows or on ubuntu. It's DEFINITELY supposed to work right when you open it right? There isn't something i missed to enable the screen?

I couldn't find a donwload of the "netbook edition" so I just made a regular 11.04 usb stick. Does 11.04 desktop edition not support touchscreens? I couldn't really find any other downloads, ubuntu.com just says "HURR CLICK THIS ONE BUTTON AND EVERYTHING JUST WORKS" rather than giving any detailed menus.

The netbook edition was stopped a while ago, there is just the desktop edition.

Did it come with windows pre-installed and all the lenovo software? Or did you manually install windows.
The touch-screen should work, pretty much whenever the mouse works, so not during bios or grub, but once linux has started it should be fine.

The fact that it doesn't work with windows implies that is a hardware problem, or that you have disabled it somehow.

See if there is anything touchscreen related if you type lspci into terminal.


> **Jenopo said:**
> Hey, I've sifted through this thread, but not entirely, so apologies if I'm asking about previously covered material, but I'm looking to dual boot my s10-3t with Ubuntu 11.04 and keeping my windows 7. I've done all the preparations such as backing up and creating my installation usb, but I've reached an issue with regard to partitioning my hard drive, which is that it won't let me create an additional partition, stating the computer has the maximum number as it is. It currently has a C: drive of roughly 186gb, a D: logical drive of about 30, a small 200mb partition, which is listed as "primary" so presumably of some importance and an OEM partition of 14.75gb. 

As something of a computer illiterate, I'm just looking for guidance from someone who has dealt with this. Anyone able to help me?

You can split the hard drive into up to 5 physical partitions, however, some of these physical partitions can be split into several logical ones. Basically, you need to install Ubuntu onto a logical parition, probably next to the data partition if there is space.
Sorry, I'm not being very clear I don't think, I'm not really awake.

---

### Post by Jenopo on 2011-09-05
> **MadnessRed said:**
> The netbook edition was stopped a while ago, there is just the desktop edition.

You can split the hard drive into up to 5 physical partitions, however, some of these physical partitions can be split into several logical ones. Basically, you need to install Ubuntu onto a logical parition, probably next to the data partition if there is space.
Sorry, I'm not being very clear I don't think, I'm not really awake.

I'm not sure I get you so I'll just run this by you, do you mean I can elect to split C: or D: into a further partition, a logical one, which I can then install on?

---

### Post by MadnessRed on 2011-09-05
> **Jenopo said:**
> I'm not sure I get you so I'll just run this by you, do you mean I can elect to split C: or D: into a further partition, a logical one, which I can then install on?

Sort of. You can't really change a partition though, generally you have to remove one and create something new in it's place.

In windows, could you take a screenshot of disk management. Then we can explain it in the context of you're disk. It should look something like:
[img]http://cdn.nirmaltv.com/images/diskmanagement.png[/img]

Then we can give advice from there.

---

### Post by Jenopo on 2011-09-05
Ok mine's here, the C: drive was what I was trying to shrink before, and I managed in fact, but I attempted to "create new simple volume" and was told I could creat no more partitions. For reference I was using this installlation guide: [https://www.youtube.com/watch?v=FmN4Pj3VWpc](https://www.youtube.com/watch?v=FmN4Pj3VWpc) although it is for maverick meerkat and I'm installing natty.

---

### Post by MadnessRed on 2011-09-05
> **Jenopo said:**
> Ok mine's here, the C: drive was what I was trying to shrink before, and I managed in fact, but I attempted to "create new simple volume" and was told I could creat no more partitions. For reference I was using this installlation guide: [https://www.youtube.com/watch?v=FmN4Pj3VWpc](https://www.youtube.com/watch?v=FmN4Pj3VWpc) although it is for maverick meerkat and I'm installing natty.

Ok, what you need to do is shrink C. (Assuming you want to keep the other partitions that is, they are for recovering windows if you break it). You can possibly do that from within windows. This should leave you with some "**unallocated space**". If you shrink C by about 40gb, that should give you plently of space for Ubuntu. (Make sure the free space comes after C so that it is next to the D.)

You can now restart and run the Ubuntu install. You should specify partitions **manually** when it asks, and you then want to create a partition in the free space you have created. You should set it to ext4 (or ext3 if you prefer) and give it a mount point of **/**.

If it still naggs about a limit on the number of paritions, make the Ubuntu partition a logical one. You should be able to do this within the Ubuntu installer.

I hope this helps, I don't think I'm being very clear and I'm not that knowledgeable myself about partitions.

---

### Post by Jenopo on 2011-09-05
I think I follow but before I go mental, I want to shrink C: next to D: and make it into free or unallocated space, not a new simple volume or anything?

---

### Post by MadnessRed on 2011-09-05
> **Jenopo said:**
> I think I follow but before I go mental, I want to shrink C: next to D: and make it into free or unallocated space, not a new simple volume or anything?

Yes, that's right, you just want to create some free unallocated space. This free space should be next to D:\

---

### Post by Jenopo on 2011-09-10
> **MadnessRed said:**
> Yes, that's right, you just want to create some free unallocated space. This free space should be next to D:\

Excellent, thanks a lot for your help, I won't actually be doing this for a while, due to the lack of access to a wired connection at the mo, but I'll be back if there are any issues further down the line.

---

### Post by MadnessRed on 2011-09-11
> **Jenopo said:**
> Excellent, thanks a lot for your help, I won't actually be doing this for a while, due to the lack of access to a wired connection at the mo, but I'll be back if there are any issues further down the line.

Ok, no problem.

---

### Post by StartedTheFire on 2011-09-22
So I finally got my s10-3t back from Lenovo and the touch screen works fine in ubuntu. But I'd like to know what kind of gesture software is available. It seems like just being able to scroll using two fingers or something would be a huge improvement and not unreasonably complicated....

---

### Post by Jenopo on 2011-09-24
Ok so, I'm back with more beginner questions, when discussing this with a friend and somewhat of an ubuntu expert, he said something about selecting to "use available space" when installing on my unallocated space, the youtube vid I was using makes no mention of this and I was wondering if, first, this is correct? secondly, where in the process do I select that option?

---

### Post by Ghundio on 2011-09-25
I'm having a little trouble getting my webcam to work on 11.04. gstreamer-properties doesn't see it so I'm not sure whats wrong.  I assume the drivers should come preinstalled so... yea.

---

### Post by prshah on 2011-09-26
> **Ghundio said:**
> I'm having a little trouble getting my webcam to work on 11.04. gstreamer-properties doesn't see it so I'm not sure whats wrong.  I assume the drivers should come preinstalled so... yea.

The webcam works out of the box. However, there is a webcam enable/disable kill switch.

First, check if your device is already recognized and enabled```
ls -l /dev/video0
``` If you do not get any results, then it is probably disabled. You can enable it with the key combination Fn+Esc. Press Fn+Esc, wait a few seconds, and then repeat the above command to check if the device is enabled.

Please post back with results.

---

### Post by Ghundio on 2011-09-26
> **prshah said:**
> The webcam works out of the box. However, there is a webcam enable/disable kill switch.

First, check if your device is already recognized and enabled```
ls -l /dev/video0
``` If you do not get any results, then it is probably disabled. You can enable it with the key combination Fn+Esc. Press Fn+Esc, wait a few seconds, and then repeat the above command to check if the device is enabled.

Please post back with results.

That was it, thanks. Probably hit FN ESC when testing to see what fn keys did stuff. Any way to get the rotate button on the screen to work? I've seen the driver post a little earlier in the thread but im not sure how you make it work.

---

### Post by prshah on 2011-09-27
> **Ghundio said:**
> Any way to get the rotate button on the screen to work? I've seen the driver post a little earlier in the thread but im not sure how you make it work.

I personally did not try the method in the earlier post, because it requires install of software that is not in the repository.

However, I nearly never have to use the mute button (below rotate button) and so I have remapped that to a script to rotate the screen (See earlier posts for details.)

---

### Post by codevel on 2011-10-15
just upgraded from 11.04 to 11.10 without problem :D

---

### Post by unkabuzz on 2011-10-21
test

---

### Post by riscsys on 2011-10-25
Hi
I have 23" HP 2310ti touch monitor. It's using usb Quanta optical touch panel and xinput device 11

I installed ubuntu 11.10 to my atom deskpc and using 1920x1080 resulotion. I want to use my minitor 90' rotated verticaly but I can't  rotate touchpanel.
I try your changeaxis.sh file and control the device. Rotate the screen but not the rotate touchpanel

How can I do ?

Thank you for your kind.





> **prshah said:**
> Ubuntu CAN rotate into portrait mode. It's mentioned in this thread as well as in the Ubuntu Wiki for Lenovo s10-3t.

I have modified the script on the wiki slightly. I'm attaching it to this if you would like to try it.

Usage:```
./changeaxis.sh # rotate 90 deg clockwise
#or
./changeaxis.sh 0 #=normal or 1=portrait, 2=rev landscape, 3= rev portrait

```

Works great with EasyStroke for when in tablet mode!

However, please feel free to correct me if I have misunderstood your question.

---

### Post by MadnessRed on 2011-10-25
> **riscsys said:**
> Hi
I have 23" HP 2310ti touch monitor. It's using usb Quanta optical touch panel and xinput device 11

I installed ubuntu 11.10 to my atom deskpc and using 1920x1080 resulotion. I want to use my minitor 90' rotated verticaly but I can't  rotate touchpanel.
I try your changeaxis.sh file and control the device. Rotate the screen but not the rotate touchpanel

How can I do ?

Thank you for your kind.

Try this change axis script on this page which works for never versions of xinput which take a rotation matrix.

[http://ubuntuforums.org/showthread.php?t=1415915&page=40](http://ubuntuforums.org/showthread.php?t=1415915&page=40)

---

### Post by datajack on 2011-10-28
Hi,

I have upgraded to Oneiric after using Natty for a good while.

I am having an odd problem that often pressing any key on the keyboard (or sometimes a cursor key) will cause the touchpad to stop working. The touchscreen still works to operate the mouse cursor but I get no response to the touchpad. This happens on most boots, but it appears that if the system is running for 10-15 mins before a key is pressed, it will work fine.

There is nothing obvious showing in dmesg or syslog.

Is anyone else seeing similar behaviour?

TIA

---

### Post by pranav on 2011-11-06
Hi everyone,

Seems like a lot has been discussed over here since the previous distro releases. I just did a fresh install of ubuntu 11.10 and now i hv the following working fine:
1. wireless is working great!
2. mute button works alright (read earlier tht folks had trouble with it)
3. Fn key and the brightness and volume functions work just fine
4. sound is working great
5. Two finger scrolling on the trackpad is fantastic!

What i want to enable:
1. Touch :) the reason why we all got this computer. Currently even the mousepointer functionality isnt working via touch.

I understand the steps to enable the touch are covered already on this thread and i am rather confused between easystroke, ginn, touchegg, utouch, etc.

I would be grateful if somebody could tell me some basic steps to get started to enable touch.

Cheers to the helpful ubuntu community :)

---

### Post by prshah on 2011-11-07
> **pranav said:**
> 
What i want to enable:
1. Touch :) the reason why we all got this computer. Currently even the mousepointer functionality isnt working via touch.

rather confused between easystroke, ginn, touchegg, utouch, etc.


easystroke etc, are all the second step. You should have working touch in order to use these.

If you find touch is not available at all, probably the relevant modules are not loaded.

As a quick check, use lsmod to see if the hid_cando module is loaded. Open a terminal (Applications-Accessories-Terminal) and give the command ```
lsmod |grep cando
``` If no code is returned, the module is probably not loaded. To load the module, try ```
sudo modprobe hid-cando
``` It may not work, but will definitely not harm. If it works, you will be able to use touch (as mouse click) immediately, without need for logout and/or restart.

If it still does not work, please post back the output of the command```
dmesg|grep -i cando
```

---

### Post by khurtsiya on 2011-12-15
> **nnutter said:**
> For those who still have issues resuming from sleep you should mark [resume fails for Lenovo Ideapad S10-3t]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664") as affecting you and try the fix of adding 'nohpet' to Grub.

nohpet not helped

any other workarounds?

---

### Post by khurtsiya on 2011-12-15
very annoying issue - can not close my netbook without crash...

---

### Post by sciallo on 2011-12-23
> **rrounsav said:**
> There is an experimental driver that will map the touch and rotate buttons to keyboard presses.  I have already package the drivers for rpm, but have not learn to create deb packages yet.  The driver can be installed from source available here [http://gitorious.org/iaps/iaps](http://gitorious.org/iaps/iaps).  The original source has to be modified in order to change the default key mapping.

I got the touch and rotate buttons working with the iapps and lsrot from the link above.

```
sudo apt-get install git-core build-essential kubuntu-restricted-extras subversion libncurses5-dev
```
Not sure it's all needed but anyway...
```
mkdir src

cd src

git clone git://gitorious.org/iaps/iaps.git

git clone git://gitorious.org/iaps/lsrot.git

cd iaps

make

sudo make install

sudo modprobe iaps

cd ../lsrot
```


I changed the key mapping by changing two #define lines in lsrot.c to read as follow
```
#define SKEY_TOUCH_MAPPING      KEY_F13

#define SKEY_ROTATE_MAPPING KEY_CYCLEWINDOWS
```

The original defines mapped the touch button to the left windows button and the screen rotate button to switch video mode. the first makes it impossible to assign as a shortcut as it's a modifier button and the second is already assigned in kde and already available as Fn+F3 so i figured I'd change it to the more appropriate and currently unused CYCLEWINDOWS. These buttons and the "onetouch" (currently mapped to F8) send button press and release at once, making it impossible to use as a modifier (eg. hold touch+F1)...

```

make

sudo make install
```

lsrot module gets loaded automatically on reboot, iaps does not...
I am now able to assign those to buttons as shortcuts in kde. The accelerometer is loaded as a joystick device, and I was able to get it to calibrate and show values with the kde settings and jstest once, but it has not worked since. I remember it stopping to work in windows too, I'm wondering if the hardware itself has some quirks...

---

### Post by sciallo on 2011-12-27
Well, not sure how many are still using S10-3t, but I'm loving how it's shaping up....

A few more steps forward:

Using the above link as a start, I modified the lsrot driver some more to send button events when screen closes to tablet mode and reopens to netbook mode.

Using that My lenovo now acts as following:
When closed to tablet mode the screen rotates 180.

The rotate button rotates it further each time pressed.

reopening the laptop brings the screen back to normal

I use KDE, another scrips I wrote and integrated with the rotate script keeps my kde panel on the short side of the screen (left when landscape, bottom when portrait).

the other button by the screen toggles right click (with a settable timeout delay or as toggle on and off) been trying to tie the num lock led to that but it's getting to not be worth the effort, so I'm leaving that alone for now.

If anyone would like more details/files lmk :)

---

### Post by knoppi on 2011-12-29
Yes, there is still someone interested ;-) Probably even more.

First of all what do you mean with touch-button? The one above the rotate-button? Actually I did never really realize its existence, maybe because it never worked and I never used Windows...

---

### Post by MadnessRed on 2011-12-29
> **knoppi said:**
> Yes, there is still someone interested ;-) Probably even more.

First of all what do you mean with touch-button? The one above the rotate-button? Actually I did never really realize its existence, maybe because it never worked and I never used Windows...

Yh, I still follow this thread.


> **sciallo said:**
> The accelerometer is loaded as a joystick device, and I was able to get it to calibrate and show values with the kde settings and jstest once, but it has not worked since.

How did you do that? I spend a while looking to see if I could find any way of doing that but only found stuff for the old thinkpads.

---

### Post by sciallo on 2011-12-30
Glad to see the thread is still alive ;)

Yes, the button above the "rotate screen" button is now my "toggle right click", funny, in the whole 10 minutes I checked windows out when I first got this I don't remember what that did...

If you follow my first post I now have modified the lsrot.c file a little more, instead of editing it, replace it with the attached file (REPLACE lsrot.c with it, REMOVE .txt from the filename). Once you issue the "sudo modprobe iaps" command you will have a /dev/input/js0 input device. that's the accelerometer, in the kde settings under input devices I could see the movement by tilting the netbook. It keeps freezing up on me though. seems like maybe another bug in the bios, once it stops working the only way to get it back is to shut down and remove the battery!! :(

I have very little time right now, but I will try to post the rest of my scripts later on...

---

### Post by sciallo on 2011-12-30
Ok, so... I'm back with a little more time.

First see my first thread post about downloading and installing lsrot and iaps, but make sure to replace the lsrot.c file with the one I attached to my last post.

I ended up keeping all of this under my /home/<user>/src/ folder if you do otherwise, make sure to check scripts for and change paths....

The whole deal with keeping the kde panel on the short side of the screen is weird, hours of google didn't give me a better solution to run the script I created in desktop console for moving the panels. I had to install xdotool and have a dcop call open the desktop console program with my script, execute it and close the window. not the cleanest solution but it works. If anyone knows of a better way to run the simple js script from a shell PLEASE enlighten me!

So, we'll need xdotools...

sudo apt-get install xdotool

in /home/<user>/src/rotate/ folder:
(Of course throughout this "<user>" is your username) 

- I modified the rotate script that was posted here (I'm using kubuntu 11.10 so the script is the second one in the wiki) to also move the kde panel, see the attached "rotate.sh" and save in folder ~/src/rotate/

- The shell script that opens executes and closes desktop console:"movepanel.sh"


- and the js file loaded by desktop console "movepanel.js" (uploaded as movepanel.js.txt", RENAME IT, the forum doesn't accept .js)

in  /home/<user>/src/ folder:

- "RCtoggle.sh" shell script that toggles right click. If called with an argument eg. "./RCtoggle 5" it changes clicks for right clicks for 5 seconds, if called without argument until called again.

At this point all that's left to do is set some shortcuts:
in "kde system settings" -> "Custom Shortcuts" -> "edit"

Create 4 new shortcuts:

- "Rotate screen"      action: "/home/<user>/src/rotate/rotate.sh" (no quotes of course"
Trigger: close the screen to tablet mode, touch the button by "shortcut: " and press the rotate screen button. "Rotate Windows should appear there.
(the rotate windows button only works when in tablet mode, if you think you'll need to be able to rotate it while open create a different shortcut for it with the same action.

- "Close to Tablet"      Action: "/home/<user>/src/rotate/rotate.sh 2"
Trigger: this time click on the button first, when you close to tablet "Launch(7)" should appear.

- "Open to netbook"      Action: "/home/rick/src/rotate/rotate.sh 0"
Trigger: with the netbook in tablet mode, click (touch) the button then open to netbook mode, "Launch(8)" should appear.

- "Right Click Toggle"     Action: "/home/rick/src/RCtoggle.sh 4" (4 is the number of seconds before it goes back to left omit it and it will stay in right click mode 'till you press it again...
Trigger: just click the button then press the touch button (above the rotate button to the left of the screen.

Needless to say, I'm using KDE, if you don't you can skip all of the move panel stuff, use the original rotate screen script (or delete the last line from mine) and use whatever way your desktop manager uses to set shortcuts.

Now I'm wrecking my brain to try to get compiz to work on 11.10 with kde, any of the solutions I find so far on google are not working, compiz brakes the kde4 windows decorator, emerald is no longer in the repositories and does not compile right... at a loss.... Once I get that working I'm going to get some multi-touch gestures going ;) Any suggestion?

---

### Post by MadnessRed on 2012-01-11
> **sciallo said:**
> Glad to see the thread is still alive ;)

Yes, the button above the "rotate screen" button is now my "toggle right click", funny, in the whole 10 minutes I checked windows out when I first got this I don't remember what that did...

If you follow my first post I now have modified the lsrot.c file a little more, instead of editing it, replace it with the attached file (REPLACE lsrot.c with it, REMOVE .txt from the filename). Once you issue the "sudo modprobe iaps" command you will have a /dev/input/js0 input device. that's the accelerometer, in the kde settings under input devices I could see the movement by tilting the netbook. It keeps freezing up on me though. seems like maybe another bug in the bios, once it stops working the only way to get it back is to shut down and remove the battery!! :(

I have very little time right now, but I will try to post the rest of my scripts later on...

Awesome, thanks. It didn't work at first but it print DEPMOD 3.0-ARCH on my screen so I typed that into terminal, it took a while but now it seems to work. cat /dev/input/js0 shows when I move the laptop. Just downloading so programs to see how well it works. Many thanks :)

---

### Post by afrilas on 2012-01-15
Mine hang when wake up from suspend and also the touch screen stop responding when i touch it with two fingers , is there any solution to fix those bugs? i am using 11.10

---

### Post by jampe on 2012-01-23
> **afrilas said:**
> Mine hang when wake up from suspend and also the touch screen stop responding when i touch it with two fingers , is there any solution to fix those bugs? i am using 11.10

I'm with you on this one, it really bugs me :/

---

### Post by fcomstoc on 2012-02-24
> **afrilas said:**
> Mine hang when wake up from suspend and also the touch screen stop responding when i touch it with two fingers , is there any solution to fix those bugs? i am using 11.10

I just finished installing 11.10 with the same issues. Suspend does not work at all and I dont have multitouch turned on. Other than that it runs great. I have not used this computer in a few months (I am usually on my Mac) but I pulled it out and got it running for fun. It is a great little computer for around the house and although I have had it for a year and a half the battery life is still great. 

Another thing, I have never been a fan of the new Unity interface but on this tablet it works great. Still not sold on it for desktop use but on a tablet it is the best interface I have seen yet.

---

### Post by ydeardorff on 2012-02-29
I just installed 11.10 via a USB stick, and it installed almost pefectly.
Aside from the audio.
It states no sound card when I run aplay-l

Help?

Everything elsre installed and works perfectly (I think)

I dont know if there is compiz or 3D finctionality with this little idea pad. I have the S10e model.
Trying to run gksudo gedit /etc/modprobe.d/alsa-base.conf and plugging in the variables in the last line has had little if any effect.
Typically under sound settings and output i get the dummy sound card  listed.
On a couple of tries I have gotten an alsa volume bar under the applications tab. 
But nothing results in any sound.

Thanks

---

### Post by cuppsy on 2012-04-06
Picked up a used S10-3t last week, and so far it's awesome. Thank you to everyone who has contributed to this thread, I've found it immensely useful. Haven't read all of it yet, but I've tried to thumb through a lot of it.

One question I didn't see discussed a lot, and I was curious what everyone else is doing, is are you all generally running Unity 2D or 3D? Speed seems a bit better in 2D, though 3D is quite usable. The only drawback I've seen so far is that after a while, the netbook has a tendency to freeze up after awhile in 3D. The cursor still moves, and I can CTRL-ALT into another session, but my main graphical session stays frozen until I reboot.

I was curious if either a) I should just be running Unity 2D, or b) is there something I can do to make it a bit more stable in 3D.

Beyond that, the screen, sound, wireless all worked out of the box. The battery life (8-cell) seems excellent and overall the performance for this little machine is quite nice. Thanks again for all the advice and tips in this thread.

---

### Post by Boberman on 2012-05-21
Hello, everyone!
I'm totally new at linux stuff, but highly impressed how fast my old S10-3t runs under Ubuntu. Everything came "out of the box" but just little thing I'm eager to clear out:
**How to enable multitouch?**
I've been digging about it for days. There are many old threads and info about custom drivers, packs, setting in files and so on. As far as my limited abilities in undersatnding all this allowed I couldn't make it work. Singe-touch mode (Protocol A?) works fine, but I'm sure there's an easy way to enable multi-touch. As [wise guys say]("http://www.lii-enac.fr/en/architecture/linux-input/multitouch-devices.html"), the kernel of latest Ubuntu 12.04 I installed is to support it.
Please, enlighten me as I wander in the darkness. :)

---

### Post by MadnessRed on 2012-05-21
> **Boberman said:**
> Hello, everyone!
I'm totally new at linux stuff, but highly impressed how fast my old S10-3t runs under Ubuntu. Everything came "out of the box" but just little thing I'm eager to clear out:
**How to enable multitouch?**
I've been digging about it for days. There are many old threads and info about custom drivers, packs, setting in files and so on. As far as my limited abilities in undersatnding all this allowed I couldn't make it work. Singe-touch mode (Protocol A?) works fine, but I'm sure there's an easy way to enable multi-touch. As [wise guys say]("http://www.lii-enac.fr/en/architecture/linux-input/multitouch-devices.html"), the kernel of latest Ubuntu 12.04 I installed is to support it.
Please, enlighten me as I wander in the darkness. :)

Afraid I don't have this laptop any more so not sure how much I can help.

Could you run lsinput and lsmod | grep cando and post the results of both, and we'll go from there.

---

### Post by Boberman on 2012-05-22
**MadnessRed**, many thanks for being ready to help!
lsinput displayed Cando multitouch nicely:

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x2087
   product : 0xa01
   version : 273
   name    : "Cando Corporation Cando 10.1 Mul"
   phys    : "usb-0000:00:1d.1-1/input0"
   uniq    : "20091003.001"
   bits ev : EV_SYN EV_KEY EV_ABS

lsmod didn't give any matches for "cando", and I took liberty to show those seemingly important for the problem lines:

hid_multitouch         12851  0 
usbhid                 41906  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid

---

### Post by MadnessRed on 2012-05-22
> **Boberman said:**
> **MadnessRed**, many thanks for being ready to help!
lsinput displayed Cando multitouch nicely:

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x2087
   product : 0xa01
   version : 273
   name    : "Cando Corporation Cando 10.1 Mul"
   phys    : "usb-0000:00:1d.1-1/input0"
   uniq    : "20091003.001"
   bits ev : EV_SYN EV_KEY EV_ABS

lsmod didn't give any matches for "cando", and I took liberty to show those seemingly important for the problem lines:

hid_multitouch         12851  0 
usbhid                 41906  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid


Ok, can you try this, install mtview.
sudo apt-get install mtview

Then run 
sudo mtview /dev/input/event10
(it might have changed path, check it is still event10 in xinput)

Alt+f10 to make it full screen and see how many contact points it detects. I think the s10-3t can only do 2.

If that does work, try
sudo modprobe cando
and see if mtview works then.

Hope this helps.

---

### Post by Boberman on 2012-05-23
Indeed, mtview has shown  two working touch points! \\:D/

"sudo modprobe cando" gives "module cando not found".

What's the next move?

---

### Post by MadnessRed on 2012-05-23
> **Boberman said:**
> Indeed, mtview has shown  two working touch points! \\:D/

"sudo modprobe cando" gives "module cando not found".

What's the next move?

Well it seems that multi-touch is working and being recognised by utouch.

Some apps may already have multi-touch, I think eye of gnome (image viewer) might have pinch to zoom and possibly the ubuntu version of chromium may have some multi-touch stuff as well.

For "non multi-touch aware" applications. You can install a program called ginn (it should be in the software centre). This will recognise multi-touch gestures, like 2 finger scroll or pinching, and convert it to a keyboard shortcut which the applications will understand.

It uses a configuration in a file called wishes.xml which defines a few actions. You can also define your own actions by passing it a custom wishes.xml.

ginn /path/to/wishes.xml

Hope this helps.

---

### Post by Boberman on 2012-05-23
Yes, ginn is installed already. But it looks like it isn't functioning.
Is there a way to check why ginn ignores default gestures input?

Upd. I've checked ginn's work with a simple command "ginn > g.txt".
Ginn accepts all touches but somehow cannot identify them! It calculates angles and deltas but every time says "gesture name = unknown". Maybe that's why no "shortcut" happens?

Upd. I think I've found the cause of the problem: ginn was never loaded into the system.
I've put it into Startup Applications list and it seems working, though far not so well as I expected.
As I thought the answer turned out to be extremely simple. :)

---

### Post by Boberman on 2012-05-25
Two problems, I need help with, remain. :)
1. Single-touch had from the start and still has a strange bug:
the mouse/touchpad pointer and the touchscreen pointer have different  coordinates. It makes using touchscreen rather hard. I cannot  "left-click" only "select with a frame", because after touching the screen  the "real" pointer is reset to the lower right corner of the screen. Sometimes it appears where it was last time moved with touchpad or mouse. I hoped this bug to be  resolved along with multi-touch problem but alas.
2. Ginn works so badly that one may say it doesn't work at all. Only  "Tap" seems to be recognized, "Drag", "Pinch" and "Rotate" are not  catched by ginn despite playing with condition numbers in wishes.xls  file. 
Maybe I'm obsessed with the idea, but I really want to make my old buddy s10-3t to "live" fully under the marvel of Ubuntu. I got used to work in tablet mode. :)

---

### Post by Boberman on 2012-05-27
I tried MeeGo on my S10-3t (just for fun) and it had no problem with single-touch. Maybe that can be solved under Ubuntu? I've searched for the answer but to no avail.

---

### Post by MadnessRed on 2012-05-27
> **Boberman said:**
> Two problems, I need help with, remain. :)
1. Single-touch had from the start and still has a strange bug:
the mouse/touchpad pointer and the touchscreen pointer have different  coordinates. It makes using touchscreen rather hard. I cannot  "left-click" only "select with a frame", because after touching the screen  the "real" pointer is reset to the lower right corner of the screen. Sometimes it appears where it was last time moved with touchpad or mouse. I hoped this bug to be  resolved along with multi-touch problem but alas.
2. Ginn works so badly that one may say it doesn't work at all. Only  "Tap" seems to be recognized, "Drag", "Pinch" and "Rotate" are not  catched by ginn despite playing with condition numbers in wishes.xls  file. 
Maybe I'm obsessed with the idea, but I really want to make my old buddy s10-3t to "live" fully under the marvel of Ubuntu. I got used to work in tablet mode. :)

Hopefully fixing 1 may fix 2.
Could you try and reinstall xserver-xorg-input-synaptics.
Also, unplug any additional pointing devices.

> **Boberman said:**
> I tried MeeGo on my S10-3t (just for fun) and it had no problem with single-touch. Maybe that can be solved under Ubuntu? I've searched for the answer but to no avail.

It should work out of the box.
Could you try running the live usb and see if single touch works as expected on that. It could be something to do with your setup.

---

### Post by Boberman on 2012-05-27
I've tried the Ubuntu 12.04 LiveCD I'd installed from and the touch screen in it woks the same buggy way: one "touch" and one "real" (touchpad/mouse) pointer. Reinstalling  xserver-xorg-input-synaptics has changed nothing.
I'm ready to give up on multi-touch, but at least single-touch has to work properly, hasn't it? :)

---

### Post by MadnessRed on 2012-05-27
> **Boberman said:**
> I've tried the Ubuntu 12.04 LiveCD I'd installed from and the touch screen in it woks the same buggy way: one "touch" and one "real" (touchpad/mouse) pointer. Reinstalling  xserver-xorg-input-synaptics has changed nothing.
I'm ready to give up on multi-touch, but at least single-touch has to work properly, hasn't it? :)

There is a chance that it is the same issue. There isn't really much point working on multi-touch geastures until we have single touch working.

So when you click on the screen, it's as if there is a second coordinate that the pointer keeps jumping to, and as a result when you are touching the screen it selects an area, like when you click and drag with the mouse.

You tried MeeGo and it worked as expected.

Could you install the program xournal, it's a note taker program, and try drawing on it. If you try and draw on that, does it appear normally or do you get a kind of triangle fan effect.

---

### Post by Boberman on 2012-05-28
I've noticed more patterns in pointer's behavior. Touching the screen affects it as follows:
1. On the desktop (gnome or unity) the pointer "remembers" where it's been **left** by t-pad or mouse. 
2. In windows, including Xournal, "real" pointer jumps right and down from the last **touched** position. It looks like its coordinates receive +X and +Y. And those number are not fixed. Depending on which part of the screen is touched jumps differ:
a. from approx. 1/5 of the screen width and to the right brings the pointer to the lower right corner.
b. the first 1/5 is funnier, because it brings pointer to lower egde but with different +X. The closer a touch to the left egde the smaller +X.
3. Touching standart panel has the same effect as for windows. Oh, and Y works the same way, narrowness of the screen makes it not so obvious.

I dare to presume something like that: X=Xt*Mx, Y=Yt*My,
where (Xt, Yt) - the last touched on the screen position,
Mx and My - some multipliers.
The incrementation, most probably, is more complex. 

Thus, I see the two parts of the bugs.
1. Touching desktop is not relayed to "t-pad/mouse" pointer's coords at all.
2. In windows - coods are relayed but wrongly with some progression.
Xinput shows different coords ranges of the touchpad (1472-5570 for X & 1408-4654 for Y) and touchscreen (0 - 4095 for both X & Y). They are turned in display's 1024x600 eventually, but in the process they pass coordinates wrongly.
Any ideas? :)

---

### Post by Paul S on 2012-06-01
Bad news, it seems to be bug 946417 at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/946417](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/946417)

Also, I've tried Fedora with the same problems occuring.

The best possible alternative is android (a special remix for the s10-3t) at [http://code.google.com/p/android-x86/downloads/detail?name=android-x86-4.0-RC1-s103t.iso&can=2&q=](http://code.google.com/p/android-x86/downloads/detail?name=android-x86-4.0-RC1-s103t.iso&can=2&q=)  but android doesn't support ethernet yet, so you can only use it on wifi.

I'm going to continue running 12.04, but will stop using the touchscreen, and switch to android when I want to do touchscreen mode. At least that's my current plan. I'm now in the process of re-installing 12.04. I still have to demonstrate that the touchpad will not freeze over a long period of use, as long as I don't ever touch the touchscreen.

Suggest you also add your names to the bug subscription.

hth

---

### Post by Boberman on 2012-06-04
Ah, that's how it is.
Alright we have to wait for this bug to be resolved.
Meanwhile yes, I think it's interesting to try Android on the s10-3t. :)

---

### Post by blackboot on 2012-10-28
This thread seem to have died but anyone try 12.10 yet?
Any bugs to watch out for?

---

### Post by Paul S on 2013-04-28
> **blackboot said:**
> This thread seem to have died but anyone try 12.10 yet?
Any bugs to watch out for?

Yes, I continue to test each ubuntu version and alpha and beta releases as well as other distros (Slackware, Arch, Fedora, Debian) looking for a linux alternative. I post my results at the end of this bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/946417](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/946417)

Regards

---

### Post by www.rzr.online.fr on 2013-06-17
Does you bluetooth adapter still working ? if yes pm me if you dualboot *legacy* OS (win7 x86) ?

---

### Post by Paul S on 2013-06-19
Yes, I dual boot into win 7 still. But, I don't use bluetooth for anything. However, I think the bluetooth and wifi are on the same chip, and wifi still works, so probably bluetooth would too.

---

### Post by blackboot on 2013-07-14
Tired of waiting on ubuntu to fix their unity issue with the cando touch screen  ( I was updating 11.10 manually with source code and kernel packages) I have moved over to snowlinux4 cinnamon editon. Very impressed, while cinnamon does crash once or twice a day atleast I can use my s10-3t touch screen. Everything worked right after the install no extra tweaking needed. Desktop rotation is still messed up but the apps I use in portrait mode fix that issue. FBReader, Evince and CoolReader (cr3). Give snowlinux a try you won't be disappointed IMO.  Tripple booting now with windows 8 ( ewww), android and snowlinux on a Sandisk 128GB SSD. Good luck all and thanks too everyone who contributed to this thread.

Edit: Install Maximus if you want to get rid of title bars when running apps in fullscreen

---

### Post by www.rzr.online.fr on 2013-08-27
let me jump back in this thread , do you prefer to run x32 or x64 ? 1st one is said to be faster (it is on windows at least) 

I still run gnome-3.8 on debian x64 , it's seems to work but I was wondering if I should try or test something else ? ie sailfishos or some tablet distro ...

Note I am still looking for LENOVO_PART OKRBackup/Factory  can you help ?

---

