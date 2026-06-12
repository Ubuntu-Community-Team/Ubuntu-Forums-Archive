---
title: "USB keeps connecting and disconnecting"
date: 2024-01-19
forum: Hardware
---

### Post by pkrizk on 2024-01-19
I am having problems with usb-c stick on Ubuntu 23.04.3 on my new laptop. The usb device keeps connecting and disconnecting in time of few seconds. I tried to find solution on internet, but havent found any. So I would like to ask you kindly for help. Solution or any advice would be apprecieted.

** I have checked/done the following:**
The usb stick works on other computers.
The same USB stick worked with previous OS on the same port without any problems.
When I connect the stick into docking stations usb-c port, it works just fine (unfortunately I cannot take the docking station all the time with me).
Another usb (classic sized usb) stick works just fine.
I turned off usb autosuspend.
I tried to format the flash disk.
** despite that I am still getting the same behavior**

** dmesg -w gives following repeatedly:**

```

[ 1599.927676] usb 2-1: new SuperSpeed USB device number 124 using xhci_hcd
[ 1599.966441] usb 2-1: New USB device found, idVendor=0951, idProduct=172b, bcdDevice= 0.01
[ 1599.966470] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1599.966480] usb 2-1: Product: DataTraveler 70
[ 1599.966488] usb 2-1: Manufacturer: Kingston
[ 1599.966495] usb 2-1: SerialNumber: 4CEDFB74A463F61139740291
[ 1599.980969] usb-storage 2-1:1.0: USB Mass Storage device detected
[ 1599.981730] scsi host0: usb-storage 2-1:1.0
[ 1600.985215] scsi 0:0:0:0: Direct-Access     Kingston DataTraveler 70       PQ: 0 ANSI: 6
[ 1600.986528] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1600.987905] sd 0:0:0:0: [sda] 60437492 512-byte logical blocks: (30.9 GB/28.8 GiB)
[ 1600.988902] sd 0:0:0:0: [sda] Write Protect is off
[ 1600.988917] sd 0:0:0:0: [sda] Mode Sense: 4f 00 00 00
[ 1600.989352] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1600.996375]  sda: sda1
[ 1600.997284] sd 0:0:0:0: [sda] Attached SCSI removable disk
[ 1601.239393] audit: type=1107 audit(1705676713.090:294): pid=1198 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" name=":1.15" mask="receive" pid=4592 label="snap.firefox.firefox" peer_pid=1227 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[ 1601.241410] FAT-fs (sda1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 1601.242259] audit: type=1107 audit(1705676713.090:295): pid=1198 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" name=":1.15" mask="receive" pid=4592 label="snap.firefox.firefox" peer_pid=1227 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[ 1605.638840] usb 2-1: USB disconnect, device number 124
[ 1605.639007] xhci_hcd 0000:00:0d.0: WARN Set TR Deq Ptr cmd failed due to incorrect slot or ep state.

```


(everytime the log is a bit different, but most of the lines keeps to be the same)
(after formating the usb stick with another filesystem the FAT warning disappeared - FAT-fs (sda1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck)

---

### Post by TheFu on 2024-01-19
23.04 support ended a few weeks ago.

Move to 23.10 or back to 22.04 for support.


USB disconnections are likely a physical issue, often caused by vibration. The plug male or female or both could be the problem.  The best advice I have is

a) avoid using USB for long-term storage connections.  SATA, eSATA, Infiniband are better, when possible.  SATA cables come with clips these days. The other two connection types have clips and screws.

b) try using a different USB port in the system

c) try using a different USB cable for the connection

If you keep using this storage through a bad connection, you risk data corruption. Eventually, it will happen.

When choosing a file system for USB connections, prefer journalled file systems like ext4 and NTFS.
If the USB storage device is using flash storage (i.e. a "thumb drive" or microSC card), journaled file system increase the total writes to the storage, so many people choose non-journalled file systems.  Of those, the best choices are f2fs or exfat.

Avoid FAT16 and FAT32 unless those are absolutely mandated by a hardware device. Any supported OS should support exFAT today and most cell phones and cameras support exFAT as well. If your camera is from 2016 or earlier, you may be stuck with FAT32.  I feel that pain myself.  About once a month, when heavily used, I have to format the storage due to corruption problems. My short-term USB connections don't have issues.  Every few months, some external USB3 backup storage that is always connected will become corrupted and disappear until a reboot.  At reboot, the file system (ext4) gets an fsck.

---

### Post by pkrizk on 2024-01-22
Thank you for the advises, I have got a lot of knew knowledge. It is just a thumb drive. But because few hours before I got these problems it worked on Windows, until I installed Ubuntu on the system. I think it wont be hardware problem... because the usb-c ports works fine with docking station (connected trough usb-c) and the usb-c thumb drive works in other devices without any problems (unless there happened something specific). 

I have formatted the thumb-drive to exFAT as advised and will probably do for other flash storage devices as well. I will try to buy the adapter cable and see if it works. If not, I guess I will have to find a workaround totally around that would suit my needs.

Thank you!

---

### Post by TheFu on 2024-01-22
For flash drives that aren't SSDs and are only used on Linux, definitely prefer f2fs.  It supports native Linux and POSIX standards, while being "flash friendly", since it isn't journaled.  Some cameras and some Android devices (Samsung Note and Pixel 3 and crdroid ROMs) support f2fs as well, but sadly, not all of them do even though it is patent free, 100% F/LOSS, and free to deploy on any hardware, unlike exFAT.

[https://source.android.com/docs/core/architecture/android-kernel-file-system-support](https://source.android.com/docs/core/architecture/android-kernel-file-system-support) in Android 13, looks like f2fs is supported by default, but I only have Android 11 in my devices. It looks like Google doesn't allow unapproved file systems anymore like they did previously for claimed "security reasons".  I suppose that is true, especially if it behaves like a root-kit and hides / blocks access to the real file system underneath.

Of course, sometimes we are stuck and don't have any good choices.

f2fs has some really good performance, often faster than ext4 and other "modern" file systems.  [https://www.phoronix.com/search/F2FS](https://www.phoronix.com/search/F2FS) will show a reputable set of performance articles and other data about this file system.  I see a day when f2fs is the default file system on all flash storage, especially under android.

---

