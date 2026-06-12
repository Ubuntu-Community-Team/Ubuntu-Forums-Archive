---
title: "USB flash drive does not mount"
date: 2022-09-16
forum: Hardware
---

### Post by Joe_Linux on 2022-09-16
I have a USB flash drive that does not automatically mount (when other USB flash drives do) in the same USB port. 
```
joe@joe-X555LAB:~$ lsusb
Bus 002 Device 005: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 13d3:3501 IMC Networks 
Bus 001 Device 006: ID 0bda:57b5 Realtek Semiconductor Corp. USB Camera
Bus 001 Device 018: ID 3938:1032 MOSART Semi. 2.4G RF Keyboard & Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-X555LAB:~$ 

```
The USB flash drive is the first listed. Thank you

---

### Post by TheFu on 2022-09-16
What file system does it have on which partition?  Impossible to guess answers without that basic information.

BTW, automatic mounting is dangerous.  May want to consider if that is smart or not for your situation.

---

### Post by sudodus on 2022-09-17
> **TheFu said:**
> What file system does it have on which partition?  Impossible to guess answers without that basic information.

BTW, automatic mounting is dangerous.  May want to consider if that is smart or not for your situation.

+1

Please run the following command line and post its output between code tags like this
 
[noparse]```

lsblk -o name,size,fstype,label,mountpoint,model
output
...

```[/noparse]
 
to get output like this
 
```

lsblk -o name,size,fstype,label,mountpoint,model
output
...

```

---

### Post by mIk3_08 on 2022-09-17
> **Joe_Linux said:**
> I have a USB flash drive that does not automatically mount (when other USB flash drives do) in the same USB port. 
```
joe@joe-X555LAB:~$ lsusb
Bus 002 Device 005: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 13d3:3501 IMC Networks 
Bus 001 Device 006: ID 0bda:57b5 Realtek Semiconductor Corp. USB Camera
Bus 001 Device 018: ID 3938:1032 MOSART Semi. 2.4G RF Keyboard & Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-X555LAB:~$ 

```
The USB flash drive is the first listed. Thank you
Run the command below in your terminal. Regards and cheers
```
ls -l /dev | grep "sd"
```

---

### Post by TheFu on 2022-09-17
> **mIk3_08 said:**
> Run the command below in your terminal. Regards and cheers
```
ls -l /dev | grep "sd"
```

There are many edge cases missed with that command, but the command could be shortened to
```
ls -l /dev/sd*
```
Some storage volumes won't show up with either command, but I'd guess over 85% used by people at home would.  For example, file systems on RAID (mdadm) or using virtio drivers won't show up.

```
$ ls -l /dev/sd*
ls: cannot access '/dev/sd*': No such file or directory
```

But
```
$ ls -l /dev/vd*
brw-rw---- 1 root disk 252,  0 Sep 17 01:15 /dev/vda
brw-rw---- 1 root disk 252,  1 Sep 17 01:15 /dev/vda1
brw-rw---- 1 root disk 252,  2 Sep 17 01:15 /dev/vda2
brw-rw---- 1 root disk 252,  5 Sep 17 01:15 /dev/vda5
brw-rw---- 1 root disk 252, 16 Sep 17 01:15 /dev/vdb
brw-rw---- 1 root disk 252, 17 Sep 17 01:15 /dev/vdb1
```

Subtle stuff.

---

### Post by mIk3_08 on 2022-09-18
Thanks a lot TheFu
mine uses sda
```
ls -l /dev/sd*
brw-rw---- 1 root disk 8, 0 Sep 18 13:24 /dev/sda
brw-rw---- 1 root disk 8, 1 Sep 18 13:24 /dev/sda1
brw-rw---- 1 root disk 8, 2 Sep 18 13:24 /dev/sda2
```
If I don't know with the root disk I can just remove the sd with the command below. Regards and cheers
```
ls -l /dev/
```

---

### Post by TheFu on 2022-09-18
The 'lsblk' command above should tell us the file system types in the system, then someone can look up the package names to install.
Without that data, nobody can really help.

To see the device used when a USB is connected, I will run 

```
dmesg -w
``` # BEFORE connecting the device, some ubuntu releases require a sudo with that command.
Then connect the USB device, see the 15 lines of output, including any partitions, 
then I'll know how to mount it using the fusermount or mount command, should my autofs mount not work.

If the goal is to see the mount via a GUI, say using a file manager, be certain that the preferences allow gvfs or gio to mount storage in the file manager prefs. Also, if the type of file system is not supported by a base install, some other packages to bring that support will need to be installed.  Different linux distros include different non-native file system support, so it is hard to say if you do or don't need to install it.

---

### Post by csae2608 on 2022-10-11
you could install "mkusb" and with it format the usb drive to a "standard usb drive", provided it gets seen by mkusb in the first place.
it is a very handy tool; but in doing so, you will loose all the data on the stick. maybe it just got wrongly formatted at some time.
all the best.

---

