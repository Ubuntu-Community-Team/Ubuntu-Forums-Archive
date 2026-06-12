---
title: "Advent USB memory stick not showing"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by Sera88 on 2007-11-22
Hi!
The day before yesterday out of nowhere I decided to try out a Linux operating system as Windows XP was running so slow on my computer. I chose Ubuntu (7.10) as it was said to be very suitable for a Linux beginner. It has been all positive and I was stunned when I discovered all kinds of possibilities in it (for example compiling C++ code is amazingly easy with Terminal).

So... Now I have run into some problems after several hours of use. For a complete Linux beginner setting up a network neighborhood (with Samba) was somewhat difficult, but now I have a real problem:
**I have an Advent-branded MP3 player, sized 512 MB, which connects with a USB cable onto the computer. When I connect it, the player lights up but it doesn't show on the computer on *Places -> Computer*.**

I have searched this forum about this issue but I haven't found any working solutions. I tried the method of unplugging the device and during a boot plugging it in again. There were still no signs of a USB device.

What would you suggest so the problem could be solved? I'd very much like to have at least one device to store data from this computer. I have a few other USB devices - memory card reader - that I have tried, but they don't work either. One has Windows and Macintosh drivers, but they assumably can't be installed onto Ubuntu (I think Wine can't emulate drivers)?

- Sami

---

### Post by linuxonbute on 2007-11-22
> **Sera88 said:**
> Hi!
The day before yesterday out of nowhere I decided to try out a Linux operating system as Windows XP was running so slow on my computer. I chose Ubuntu (7.10) as it was said to be very suitable for a Linux beginner. It has been all positive and I was stunned when I discovered all kinds of possibilities in it (for example compiling C++ code is amazingly easy with Terminal).

So... Now I have run into some problems after several hours of use. For a complete Linux beginner setting up a network neighborhood (with Samba) was somewhat difficult, but now I have a real problem:
**I have an Advent-branded MP3 player, sized 512 MB, which connects with a USB cable onto the computer. When I connect it, the player lights up but it doesn't show on the computer on *Places -> Computer*.**

I have searched this forum about this issue but I haven't found any working solutions. I tried the method of unplugging the device and during a boot plugging it in again. There were still no signs of a USB device.

What would you suggest so the problem could be solved? I'd very much like to have at least one device to store data from this computer. I have a few other USB devices - memory card reader - that I have tried, but they don't work either. One has Windows and Macintosh drivers, but they assumably can't be installed onto Ubuntu (I think Wine can't emulate drivers)?

- Sami
Linux comes with its own 'Drivers'  but it may be you need some software which you don't have installed.
 I am not an expert on this topic but try the following code from a terminal,

first without your mp3 player plugged in :

```

fdisk -l

```

( that's a lower case L not 1 )

Then with the player plugged in - before you run it this time wait about 30 seconds.

Post the results of the command each time and we will look at it.

---

### Post by Sera88 on 2007-11-22
Thank you for the fast reply, **linuxonbute**!

First I tried the command **fdisk -l** (with the lower case L) without the MP3 player plugged in, and this is how it went:
```
sami@sami-desktop:~$ fdisk -l
sami@sami-desktop:~$
```

And after plugging it in, waiting for 30 seconds, I got the same result: it just jumped onto the next row with no output at all.

Maybe my USB ports aren't working all right? How could I check that?

---

### Post by ajgreeny on 2007-11-22
The command you need is ```
sudo fdisk -l
```and then type your user password and hit enter.  You will then see your hard disks displayed in codes and if your mp3 player is found it will also show up something like this:-

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44cd44c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5229    42001911    7  HPFS/NTFS
/dev/hda2            5230       19747   116615835   83  Linux
/dev/hda3           19748       19929     1461915    5  Extended
/dev/hda5           19748       19929     1461883+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62c86a43

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         729     5855661   83  Linux
/dev/hdb2            4852        4998     1180777+   5  Extended
/dev/hdb3             730        4851    33109965   83  Linux
/dev/hdb5            4853        4998     1172745   82  Linux swap / Solaris

---

### Post by Sera88 on 2007-11-22
OK, thanks for clarifying, **ajgreeny**.

So let's get it on. This is what I get when the device is unplugged:
```
sami@sami-desktop:~$ sudo fdisk -l
[sudo] password for sami:

Disk /dev/hda: 20.4 Gt, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8cbf8cb

    Device Boot     Start          End    Blocks   Id  System
/dev/hda1   *           1        2381    19125351   83  Linux
/dev/hda2            2382        2490      875542+   5  Extended
/dev/hda5            2382        2490      875511   82  Linux swap / Solaris
```

And this when it's plugged:
```
sami@sami-desktop:~$ sudo fdisk -l

Disk /dev/hda: 20.4 Gt, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8cbf8cb

    Device Boot     Start          End    Blocks   Id  System
/dev/hda1   *           1        2381    19125351   83  Linux
/dev/hda2            2382        2490      875542+   5  Extended
/dev/hda5            2382        2490      875511   82  Linux swap / Solaris
```

I tried the procedure with the other USB port as well. The results were identical.

---

### Post by linuxonbute on 2007-11-23
Well I don't need to run sudo on my system

which is Kubuntu running kernel 2.6.20-16-386

```

fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+  83  Linux
/dev/sda2            6375        6505     1052257+  82  Linux swap / Solaris
/dev/sda3            6506       19929   107828280   83  Linux

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14596   117242338+  83  Linux

```

I wonder why yours are different.

But it does look like something is wrong with the usb sub-system

---

### Post by Sera88 on 2007-11-23
Yes, I think so too. My BIOS firmware must be too old then: it says it's from 1999. Maybe a BIOS firmware upgrade would solve the problem.

How do I check the motherboard information in Ubuntu? Ubuntu's built-in hardware information tool didn't provide me any understandable info. Can it be checked with Terminal (as you can check the CPU and memory info with it)?

---

### Post by Sera88 on 2007-11-23
Hey hey!
I got it working! I read my motherboard's manual some ten minutes and it said the USB function had been disabled by default. So I went and changed the BIOS setup to enable USB, and plugged the MP3 player into the slot and... the removable media showed up into the Desk!
It's working, and I didn't even need to upgrade the BIOS's firmware.

Thank you very much for the help and support, **linuxonbute** and **ajgreeny**.

---

