---
title: "Can't mount 160GB  external Hard drive in Fiesty"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by maluze on 2007-06-06
Hi there...I just bought a seagate 160GB external hard drive, received it on monday, and set everything up yesterday. Initially the HD was formatted in FAT32, and Ubuntu did not recognize it, so i reformatted to NTFS in windows. I then  installed ntfs-3g, and everything was working fine yesterday, except that it wouldnt mount automatically (had to do it manually in terminal), and it does not eject properly (meaning, at all). I managed to copy my 20GB music collection to the hard drive. Today, I turn on my computer and external HD, to find that...the hard drive won't mount anymore! if it doesnt mount, then i cant use ntfs-3g, and if i cant use ntfs-3g, my HD doesnt work at all in ubuntu. Strangely enough, i connected it to my sisters' windows laptop, and i could mount it, read from it, write from it, delete, and dismount it, all without a hitch!.

why does mounting and using NTFS have to be such a pain in Ubuntu? isnt it reasonable to think that users are likely to purchase additional hard drives which need to be accessed by windows as well, requiring NTFS or FAT32? Please help! :(

---

### Post by IntuitiveNipple on 2007-06-06
You'll need to give some specific details of your hardware, configuration, and connections. You don't say how the drive is connected, whether it is via a hub or directly into the PC, what bus type, powered externally or via the bus.

Edgy and Feisty don't have any widespread problems connecting external USB drives or auto-mounting partitions.

It is possible that some change to your particular system in the past is contributing to the problem now.

Have you inspected the various log files (System > Administration > System Log) for reports when you plug/unplug the device?

Have you got System > Preferences > Removable Drives and Media -> Storage set to:

[LIST]
[*]Mount removable drives when hot-plugged
[*]Mount removable media when inserted
[*]Browse removable media when inserted
[/LIST]
?

I've got an external 160GB Freecom USB2 drive and it hot-plugs, mounts, unmounts without a problem whatever file system is on it.

---

### Post by maluze on 2007-06-06
well, it turns out i cant mount much of anything on my computer now...not flash drives, not my iPod; it shows up in /dev/, but now it doesnt automount anymore :(. the first signs of trouble came in today when i first booted up my external HD, and it said, I dont have permissions to mount (it literally said that). I dont know what to do, all i did pretty much was edit fstab to include the new hard drive under ntfs-3g, i didnt do much else. (and a side not, the devices are recognized on the computer, they show up in /dev, but they just dont mount)

to give further information about the hard drive, it is a external hard drive with an external power source, connected directly to my PC via USB 2.0. And yes, i went to the removable drives and checked the things that you mentioned..

if you want i can post the system log, or whatever commands you want me to run, but i didnt see any error messages, (but then again, i dont know how to interpret it :P )

---

### Post by maluze on 2007-06-07
anyone? please? this is kind of an urgent issue for me..

---

### Post by maluze on 2007-06-07
> **maluze said:**
> anyone? please? this is kind of an urgent issue for me..

Ok, it seems as if my computer now mounts my iPOd, yet my external HD still does not mount :(

Here is a sys. log of of what was recorded as i turned on my hard drive: 

> Jun  7 14:31:33 justin-desktop kernel: [ 2327.780245] usb 4-3: new high speed USB device using ehci_hcd and address 7
Jun  7 14:31:33 justin-desktop kernel: [ 2327.892162] usb 4-3: device descriptor read/64, error -71
Jun  7 14:31:33 justin-desktop kernel: [ 2328.107989] usb 4-3: device descriptor read/64, error -71
Jun  7 14:31:33 justin-desktop kernel: [ 2328.323828] usb 4-3: new high speed USB device using ehci_hcd and address 8
Jun  7 14:31:33 justin-desktop kernel: [ 2328.659692] usb 4-3: device descriptor read/all, error -71
Jun  7 14:31:34 justin-desktop kernel: [ 2328.775483] usb 4-3: new high speed USB device using ehci_hcd and address 9
Jun  7 14:31:34 justin-desktop kernel: [ 2329.183156] usb 4-3: device not accepting address 9, error -71
Jun  7 14:31:34 justin-desktop kernel: [ 2329.295089] usb 4-3: new high speed USB device using ehci_hcd and address 10
Jun  7 14:31:35 justin-desktop kernel: [ 2329.702759] usb 4-3: device not accepting address 10, error -71

hope someone can make any sense out of this and help me :(

---

