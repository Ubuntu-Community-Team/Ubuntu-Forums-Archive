---
title: "Disabling &quot;legacy usb&quot; in BIOS: problems"
date: 2010-12-13
forum: Hardware
---

### Post by nac.est on 2010-12-13
I recently bought an external usb HD drive that I want to keep plugged into the computer (not a laptop) at all times.

However when I booted with the HD plugged in the PC would just hang at boot when "checking for devices". I searched for a solution and eventually found it: I disabled the "legacy usb support" feature in my BIOS and the computer started booting again without hanging.

However after that a new problem emerged with my usb keyboard. I am now unable to use the keyboard during grub and until the default OS (Ubuntu 10.10) is loaded. This is obviously related to the keyboard being a usb one.

How can I get both my HD and my keyboard to work at the same time?

---

### Post by nac.est on 2010-12-17
Is there something I can do to make this question more easily answerable?

---

### Post by efflandt on 2010-12-17
Check your drive boot order in BIOS.  I think you typically need to have Legacy or Auto enabled for USB legacy support in order to boot from a USB drive, but maybe your system is trying to boot the USB drive when there is no OS on it.  So that is why you should check your boot drive order.

How different computers handle that differs.  I have my laptop set to boot USB before its internal drive, so if a bootable USB is connected, it automatically boots USB.  But I have not tried booting that with a USB drive with no OS, or a boot loader and no OS.

For my old and new desktops and company laptop, regardless of boot order set in BIOS (other than which internal drive to boot), it will not even try to boot an internal drive unless I press a certain key during BIOS splash screen.  That is probably to avoid accidentally booting from something (possibly malicious) if you do not intend to.  The only virus I ever caught in Windows (3.1 and 95) was spread by floppy disks many years ago.

---

### Post by nac.est on 2010-12-20
Thank you, efflandt.
However the USB drive does not appear in the boot order list, only my regular SATA drives. If I turn legacy USB on, the process hangs at "Detecting USB drive:", right after successfully detecting the SATA drives.
I noticed that my keyboard is active during the first phase of the boot (I can press Del to get into the BIOS). It stops working only during boot.

Maybe there's another option I can set? Will disabling the USB 2.0 controller have negative effects on the performance of my drives?

---

### Post by nac.est on 2011-01-10
A friend told me that maybe I should update the usb drive's firmware. It sounds like a slightly risky endeavor, so I want to be sure it's really necessary.
Does anybody have advice on this? :D

---

### Post by pabouk on 2011-01-24
Do you have "removable devices" in the drive boot order menu? If yes try to disable them or put them back in the boot order list. Unfortunately I am not sure if this could avoid detection of USB drives.

---

### Post by nac.est on 2011-02-02
Thanks but no, the boot order list only contains "proper" drives. I don't think it's a boot priority problem, because the loading sequence stops during the POST, when it is just checking for devices, not yet trying to boot an OS.

The problem still persists. I wonder what all the other people with external drives do to prevent this... :(

---

### Post by Aewzzz1 on 2012-05-07
> **nac.est said:**
> I recently bought an external usb HD drive that I want to keep plugged into the computer (not a laptop) at all times.
 
However when I booted with the HD plugged in the PC would just hang at boot when "checking for devices". I searched for a solution and eventually found it: I disabled the "legacy usb support" feature in my BIOS and the computer started booting again without hanging.
 
However after that a new problem emerged with my usb keyboard. I am now unable to use the keyboard during grub and until the default OS (Ubuntu 10.10) is loaded. This is obviously related to the keyboard being a usb one.
 
How can I get both my HD and my keyboard to work at the same time?
 
[SIZE=2]_BIOS fails to recognize external USB Hard Drive when a USB mouse is connected_[/SIZE]
 
[SIZE=2]I known that this is an Ubuntu forum, but problems that occur during BIOS processing are often quite distinct from problems that may occur later as an operating system is booted.[/SIZE]
 
[SIZE=2]Note: If you want to use a USB mouse or USB keyboard before the operating system is fully loaded, then you must enable "Legacy USB Support" in the BIOS, otherwise they will not work during the BIOS processing or during the operating system boot until appropriate drivers have been loaded - See notes below. [/SIZE]
 
[SIZE=2]My Windows 7 home premium 64 bit Fujitsu PH300 desktop has an AMI Aptio 4.6 BIOS mounted on a Fujitsu D2990-A1 rev C motherboard. I use an External [/SIZE][SIZE=2]USB 2.0 hard drive (Samsung HD400LD WQ10) which has a separate power cable plugged into a mains socket that is switched on, a Fujitsu PS/2 keyboard [/SIZE][SIZE=2]and a Fujitsu USB mouse. [/SIZE]
 
[SIZE=2]My problem was that every other time I booted my PC, the BIOS would intermittently fail to recognize the external USB hard drive and when I looked in the BIOS list of detected USB devices, the external USB hard drive was absent. Also the blue LED activity light on the USB drive blinked continuously as the BIOS queried the drive for type and model information[/SIZE]
[SIZE=2]and the BIOS was kept so busy that anything I typed at the keyboard took about 10 seconds to appear and the screen rendering was incredibly slow. It took minutes for Windows 7 to boot and often Windows just wouldn't boot at all.[/SIZE]
 
[SIZE=2]**Solution**: I replaced the USB mouse with a PS/2 mouse and Hey Presto! - my PC has worked perfectly ever since. :p[/SIZE]
 
[SIZE=2]A day later, since I no longer use either a USB mouse or USB keyboard, I disabled the "Legacy USB Support" in the BIOS because it is no longer required.[/SIZE]
 
[SIZE=2]I don't know what the exact cause of the problem was, but replacing the USB mouse with a PS/2 mouse fixed it.[/SIZE]
[SIZE=2]Either the BIOS or the USB Controller cannot cope with an external USB Hard Drive and a USB mouse being plugged in at the same time, even when they were plugged into USB ports owned by different hubs.  [/SIZE]
[SIZE=2]A further complication was the presence of a USB mouse but with a PS/2 keyboard which may have confused the BIOS "Legacy USB Support". [/SIZE]
 
[SIZE=2]-----------------------------------------------------------------------[/SIZE]
[SIZE=2]Legacy USB Support refers to the USB mouse and USB keyboard support.[/SIZE]
[SIZE=2]When this option is not enabled, any attached USB mouse or USB keyboard will not work until a USB compatible operating system is fully booted with all USB drivers loaded. When this option is enabled, any attached USB mouse or USB keyboard can control the system even when there is no USB drivers loaded on the system.[/SIZE]
 
[SIZE=2]Disabled: set this value to prevent the use of any USB device in DOS or[/SIZE]
[SIZE=2]during system boot.[/SIZE]
[SIZE=2]Enabled: set this value to allow the use of USB devices during boot and while using DOS.[/SIZE]
[SIZE=2]Auto: this option detects automatically USB keyboards or mice and if found, allows them to be used during boot and while using DOS.[/SIZE]
[SIZE=2]-----------------------------------------------------------------------[/SIZE]

---

