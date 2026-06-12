---
title: "External USB Hard disk problem"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by Chosen on 2005-04-23
Hello there,
I'm not sure if I'm posting to the right forum since my problem is basicly in Windows XP.
I have an AMD64 based Fujitsu-Siemens laptop and I recently installed "Hoary", on a dual boot configuration with the existing Windows XP installation.
The 60Gb hdd is divided in the following partitions:
1. Windows XP - 10Gb (NTFS)
2. Ubuntu AMD64 5.04 - 4.7Gb (ReiserFS)
3. Ubuntu Swap - 256Mb
4. Documents and data - 45Gb (NTFS, read-only mounted for Ubuntu)

I'm having 3 external disk enclosures:
1. USB2.0 for a 80Gb 2.5" (USB powered)
2. USB2.0 for a 80Gb 3.5" (external power supply)
3. USB2.0/1394 combo for a 200Gb 3.5" (external power supply, connected through the 1394 interface)
I also have a 2Gb flash disk.

Before installing Ubuntu, all devices mentioned above would connect without a problem to Windows XP.
After installing Ubuntu and grub, when I get to the Windows installation, I will get a desktop freeze as soon as I connect any of the devices, except the firewire and the flash disk.
Step by step troubleshooting I've completed so far:

1. Really early, even in the P.O.S.T. screen of my laptop, if I connect a USB disk, it will freeze. If I disconnect it, it will continue.
2. Same thing happens even in the grub loader; it will "pause" in the menu with the USB disk connected, and "un-pause" and continue after I disconnect it.
3. As soon as I login to my Windows installation, when I connect the USB disk, it will freeze, BUT after I disconnect it, it will remain hung and I have to hit the reset button.

I have concluded that it's not related to the Windows installation since a) it's been working fine before and b) it happens even in the BIOS POST procedure. For the same (b) reason I concluded that it's not Ubuntu's fault either.
I can only imagine a hard disk/partition conflict somehow but I cannot actually trace the problem.
The fact that the firewire disk and the USB flash disk do not cause this problem, only makes it more confusing.

fyi in the Ubuntu environment the problem does not appear, but as I mentioned, it does happen before any OS choice (in the grub menu and before, even in the hardware detection)


Has anybody seen that before? Is there something that's so obvious but I cannot see? Any suggestions?
Any help/hint would be appreciated,
Thank you.

---

### Post by Mat10 on 2005-04-24
Try turning off Plug n Play in the BIOs, let the BIOS assign devices.  Nothing to lose trying this.

As you probably already know before installing Linux as a dual boot, do a scan disk and defrag of XP before hand.  Do the scan disc in safe mode for safe and faster checking.  Have everything off when doing the defrag.

USB stuff is a new frontier for every operating system.

Tom

---

### Post by Chosen on 2005-04-25
[QUOTE=Mat10]Try turning off Plug n Play in the BIOs, let the BIOS assign devices.  Nothing to lose trying this.

As you probably already know before installing Linux as a dual boot, do a scan disk and defrag of XP before hand.  Do the scan disc in safe mode for safe and faster checking.  Have everything off when doing the defrag.

USB stuff is a new frontier for every operating system.

Tom[/QUOTE]
Unfortunately my laptop's BIOS doesn't have this option. The only related options for this issue are the ones for boot order and USB devices. At the moment they're all turned off (I only put the optical and hard disk available for boot)

---

### Post by Mat10 on 2005-04-25
[QUOTE=Chosen]Hello there,
I'm not sure if I'm posting to the right forum since my problem is basicly in Windows XP.
I have an AMD64 based Fujitsu-Siemens laptop and I recently installed "Hoary", on a dual boot configuration with the existing Windows XP installation.
The 60Gb hdd is divided in the following partitions:
1. Windows XP - 10Gb (NTFS)
2. Ubuntu AMD64 5.04 - 4.7Gb (ReiserFS)
3. Ubuntu Swap - 256Mb
4. Documents and data - 45Gb (NTFS, read-only mounted for Ubuntu)

I'm having 3 external disk enclosures:
1. USB2.0 for a 80Gb 2.5" (USB powered)
2. USB2.0 for a 80Gb 3.5" (external power supply)
3. USB2.0/1394 combo for a 200Gb 3.5" (external power supply, connected through the 1394 interface)
I also have a 2Gb flash disk.

Before installing Ubuntu, all devices mentioned above would connect without a problem to Windows XP.
After installing Ubuntu and grub, when I get to the Windows installation, I will get a desktop freeze as soon as I connect any of the devices, except the firewire and the flash disk.
Step by step troubleshooting I've completed so far:

1. Really early, even in the P.O.S.T. screen of my laptop, if I connect a USB disk, it will freeze. If I disconnect it, it will continue.
2. Same thing happens even in the grub loader; it will "pause" in the menu with the USB disk connected, and "un-pause" and continue after I disconnect it.
3. As soon as I login to my Windows installation, when I connect the USB disk, it will freeze, BUT after I disconnect it, it will remain hung and I have to hit the reset button.

I have concluded that it's not related to the Windows installation since a) it's been working fine before and b) it happens even in the BIOS POST procedure. For the same (b) reason I concluded that it's not Ubuntu's fault either.
I can only imagine a hard disk/partition conflict somehow but I cannot actually trace the problem.
The fact that the firewire disk and the USB flash disk do not cause this problem, only makes it more confusing.

fyi in the Ubuntu environment the problem does not appear, but as I mentioned, it does happen before any OS choice (in the grub menu and before, even in the hardware detection)


Has anybody seen that before? Is there something that's so obvious but I cannot see? Any suggestions?
Any help/hint would be appreciated,
Thank you.[/QUOTE]
 The first post is a little confusing to me.  When you say going to the windows installation, do you mean you are installing Windows ""After the Ubuntu"" install ?  Just a wild shot but you know Windows must be the first install before any Linux.  If it was then just ignore my question, only trying to be helpful.

Tom

---

