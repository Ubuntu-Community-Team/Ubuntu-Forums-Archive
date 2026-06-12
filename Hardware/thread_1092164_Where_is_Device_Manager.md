---
title: "Where is Device Manager?"
date: 2009-03-10
forum: Hardware
---

### Post by kunaly2k on 2009-03-10
Where is device manager as in windows? I want to disable my onboard USB as it conflicting with my USB card, in windows it was just as easy as it can be [Device manger > hardware > right click any device you want to disable] thats it! I want toknow is there any manager like this for Xubuntu Intrepid and how to install it offline as my pc doesnt have a net connection, Good Day!

---

### Post by orethrius on 2009-03-10
I know there's some sort of "Device Manager" for Ubuntu, but it's buried to encourage resolution of the actual problem.

When you say your onboard USB is conflicting with your USB card, what exactly do you mean?  There are at least three interpretations, and I've no doubt that your issue may be a fourth.

1.  You have an onboard USB hub and an external USB hub; the two appear to conflict.
2.  You have an onboard USB hub and a USB flash drive; the drive doesn't appear when plugged into the USB hub.
3.  Your USB hub is conflicting with some manner of flash memory (Secure Digital, XD, MemoryStick, CompactFlash, or other).
4.  ???

The simplest way to install the program offline (once I track down my copy of The Ubuntu Book, and assuming it's not installed by default) would involve downloading the .deb package on a separate system to some manner of removable media (USB drive, flash card, CD, DVD) then loading that media in your PC and double-clicking the file to run it.

UPDATE: It's **gnome-device-manager** but it requires at least one separate library to run it, and it's not included by default (yet).  It also doesn't allow you to disable modules (**modprobe -r module_name_here**), which - IMO, in Windows - is the equivalent of "never mind that it doesn't work, we'll work around that by killing some of your hardware".  Perhaps with further information, your system can be made to run properly?  Is a lack of software support also why it has no Internet connection, or does it simply lack the hardware for that (if it's software, then that can be fixed, too)?

---

### Post by TenPlus1 on 2009-03-10
You can install a package called HardInfo that will give you hardware information and details...  [www.getdeb.net](www.getdeb.net)

---

### Post by linux_tech on 2009-03-10
System > Administration >  Hardware drivers would be closest thing to hardware GUI

---

### Post by Yellow Pasque on 2009-03-10
If you have a USB controller card, and you don't want to use the USB ports built into the motherboard, you should disable the onboard USB in the BIOS, not in the OS.

---

### Post by kunaly2k on 2009-03-11
I have already done that but it doesnt solve the problem, i need a device manager like windows so that i can disable the onboard usb hub, please if anyone knows such a downloadable software for xubuntu intrepid ibex plz letme know so that i can download and have a happy linux experience! Also wherever i try to download win32/avi codecs and vlc/media player it says "dependency not satisfied" plz help! i cannot listen mp3 or play videos :-(

---

### Post by Yellow Pasque on 2009-03-12
> **kunaly2k said:**
> I have already done that but it doesnt solve the problem
So you disable it in the BIOS, but the OS still sees it? Are you sure you disabled it? Does your motherboard have BIOS updates that might fix this problem?

Furthermore, randomly disabling hardware in the OS may work around the issue, but it doesn't solve it. Just because you can do it in Windows, that doesn't mean it's a good idea.

How do you know that your onboard USB conflicts with the other USB controller?
Can you run this:
```
sudo update-usbids
sudo update-pciids
```
and post the output of:
```
sudo lshw -C bus
```

> Also wherever i try to download win32/avi codecs and vlc/media player it says "dependency not satisfied"
Try and get a more specific error message. "Dependency not satisfied" doesn't tell us much. Post output of:
```
sudo apt-get install vlc
```

---

### Post by MaxIBoy on 2009-03-12
The output of "apt-get install vlc" is probably going to be something like ```
Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```Because he **specifically said that he's working offline**. 


But I concur that randomly disabling hardware is an ugly solution.

---

### Post by kunaly2k on 2009-03-14
i want to disable my onboard usb controller! downloaded gnome device manager but it just gives details of the drivers, please help coz i am not able to use my usb drives as it sometimes detects them and the very next second doesnt, thanks

---

