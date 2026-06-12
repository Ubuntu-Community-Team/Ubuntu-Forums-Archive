---
title: "snapscan1212u dosn't work after installing xubuntu 16.0.4"
date: 2017-02-27
forum: Hardware
---

### Post by mwarm on 2017-02-27
Hello,
my AGFA Sanner dosn't work after installing xubuntu. (before it works well with kubuntu 8 .. 14.0.4.)

When I run xsane I got the following message:

...
[I]No driver available
...[/I]

lsusb shows me:
*Bus 006 Device 003: ID 06bd:2061 AGFA-Gevaert NV SnapScan 1212U (?)*
[I]
ls -l /usr/share/sane/snapscan/
insgesamt 64
lrwxrwxrwx 1 root root    13 Feb 26 21:33 FIRMWARE.bin -> snap1212u.bin
-rwxrwxrwx 1 root root 32768 Feb 26 21:20 snap1212u.bin
-rwxrwxrwx 1 root root 32768 Feb 25 20:30 SnapScan1212U_2.bin

 sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x06bd [AGFA ], product=0x2061 [SNAPSCAN]) at libusb:006:003


[/I]Can somebody tell me whats wrong?

thanks

---

### Post by mwarm on 2017-03-04
Like in the Thread: [https://ubuntuforums.org/showthread.php?t=2266355](https://ubuntuforums.org/showthread.php?t=2266355) mentioned I didn't have a USB3 Port.

---

