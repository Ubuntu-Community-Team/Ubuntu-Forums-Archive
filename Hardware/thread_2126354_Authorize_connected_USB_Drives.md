---
title: "Authorize connected USB Drives"
date: 2013-03-16
forum: Hardware
---

### Post by Cyrebo on 2013-03-16
Hi, I want to make my Kubuntu(12.10) system authorize all usb drives that are connected to my system. I would like my usb drive to have a special authentication/authorization with my system when it connects and if another usb drive is connected and doesn't have this authentication/authorization mechanism it should fail to mount or not be authorized.

Thanks in advance for any help on this.

---

### Post by agillator on 2013-03-16
Check the man page for the mount command. When you connect/plug in a USB device such as a drive, no one has access to it until it is mounted, i.e. given a place in the file system. Be default only root can mount or unmount a device. However if you check the options section of the mount command you will see that a user or a group can be given permission to mount/unmount a specific device. Once the device is mounted, the permission system takes over as to who may access the device and what combination of access permissions they have: read, write, execute. I believe what you are referring to as 'authorization' will be handled by those two subjects.

---

### Post by dabl on 2013-03-16
However, I believe the default configuration will automatically mount a USB device in /media, when the user clicks on it in the device notifier.  So then the question is, what is the filesystem, and what folders exist, and what permission settings are on the folders?  If it is FAT or NTFS, you probably can't control/limit user access.  If ext3/4 then you could set group and/or user permissions on the folders, and thereby control access to existing folders, but you probably can't stop another user from making a new folder (maybe you don't care).

Alternatively, you could manually mount the device, in /mnt or /media and use it like a conventional hard drive, at the expense of losing the USB hotplug capability.

---

### Post by Cyrebo on 2013-03-23
I understand what you guys are saying but /i believe what i'm trying to do is slightly different....I started another thread here once I discovered more about linux scripting: [http://ubuntuforums.org/showthread.php?t=2128557](http://ubuntuforums.org/showthread.php?t=2128557)

Please take a look at this.

---

