---
title: "Apps do not recognize scanner"
date: 2009-11-19
forum: Hardware
---

### Post by cscj01 on 2009-11-19
I have been using my HP 3570c flatbed scanner and my Nikon CoolScan V ED film and slide scanner with both Jaunty and Karmic.  The applications I use are XSane and Vuescan (only the Nikon).  Suddenly today, these two applications do not find my Nikon.  I ran the following in a terminal:

```
~$ lsusb
Bus 002 Device 007: ID 04b0:4001 Nikon Corp. LS 50 ED/Coolscan V ED
Bus 002 Device 005: ID 0bc2:3001 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 03f0:1212 Hewlett-Packard 
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 413c:2006 Dell Computer Corp. 
Bus 006 Device 003: ID 03f0:2005 Hewlett-Packard ScanJet 3570c
Bus 006 Device 002: ID 413c:1004 Dell Computer Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b0 [Nikon], product=0x4001 [LS-50 ED]) at libusb:002:007
found USB scanner (vendor=0x03f0, product=0x2005) at libusb:006:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


~$ sudo scanimage -L
device `hp3500:libusb:006:003' is a Hewlett-Packard ScanJet 3500 scanner
device `coolscan2:usb:libusb:002:007' is a Nikon    LS-50 ED         film scanner
device `hp_rts88xx:libusb:006:003' is a Hewlett-Packard ScanJet 3530C flatbed scanner
device `hp_rts88xx:libusb:006:003' is a Hewlett-Packard ScanJet 3570C flatbed scanner

~$ scanimage -L
device `hp3500:libusb:006:003' is a Hewlett-Packard ScanJet 3500 scanner
device `hp_rts88xx:libusb:006:003' is a Hewlett-Packard ScanJet 3530C flatbed scanner
device `hp_rts88xx:libusb:006:003' is a Hewlett-Packard ScanJet 3570C flatbed scanner
```


So, I have a few questions.

(1)  Is this about permissions?
(2)  If so, is the file I need to set permissions on /dev/bus/usb/002/007?
(3)  If things are correct so far, to what do I need to set the permissions?
(4)  Why would my permissions have changed?

---

### Post by cscj01 on 2009-11-20
bump

---

### Post by Reini68 on 2009-11-21
I stumbled upon your post, because I had the same problem with my Nikon Coolscan V ED (LS50). What made me wonder was that you have the same flatbedscanner that I do.

As I had to move back to Jaunty's version of libsane ([https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476)) to make the HP3570C work, I wondered if you were trying the same for the HP scanner.

Here is what I did to find out more about this problem:

I took another computer running Karmic that I had never used for scanning before and that I hadn't updated for about two weeks. I installed Vuescan and it worked like a charm out of the box.

After that I installed all the necessary updates via synaptic, but NOT the old libsane. As a new kernel was part of the updates I rebooted and it still works.

So it seems to be a problem of either using the HP3570C on the same system or more likely a problem of the libsane 1.0.19-23ubuntu7.

Can you confirm that you installed the old libsane version?

---

### Post by cscj01 on 2009-11-21
Reini68: > Can you confirm that you installed the old libsane version? 

Yes, I removed libsane-1.0.20 and installed libsane-1.0.19.

There is one thing that is curious though.  Initially, both my scanners were recognized after doing that (XSane saw them both; Vuescan saw only the Coolscan V ED since it doesn't support the 3570c under Linux).

I think I removed libsane-extras-1.0.20 and sane-utils-1.0.20 and then installed libsane-extras-1.0.19 and sane-utils-1.0.19 **after** first trying the applications.  I did that assuming the packages should be at the same level to avoid problems.

Later today, I am going to upgrade sane-utils-1.0.19 to sane-utils-1.0.20 and try the programs.  If that doesn't fix things, I am going to remove the libsane-extras-1.0.19 and try the apps.

I don't know whether there is something about the combinations or not, but I do know everything worked at one point.  I may just go back to the beginning and start over.

Did you only remove and install the libsane packages, or did you include any others?

Of course, XSane had to be removed and reinstalled in all this.

---

### Post by Reini68 on 2009-11-21
> **cscj01 said:**
> Did you only remove and install the libsane packages, or did you include any others?

I included all three packages, as xsane didn't work with only libsane downgraded.

---

### Post by cscj01 on 2009-11-21
I put everything back the way it was before all this started.  XSane failed as many people have documented.  I then removed libsane and installed the Jaunty libsane package and re-installed XSane.  I am back to the same problem:  I have to run with sudo to have my applications recognize the Coolscan V ED.

This has to be a permissions problem, but I do not know enough to find what is wrong.  root owns the scanners as I understand root should.  The rules I have in /etc/udev/rules.d are:

55-usx2yloader.rules which contains

```
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8000", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/ld2-ezusb.hex -I /lib/firmware/usx2yloader/us428fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8001", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader; /usr/bin/us428control -m mixxx&'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/ld2-ezusb.hex -I /lib/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
```

70-persistent-cd.rules and 70-persistent-net.rules.  The only other rules.d directory I have is /lib/udev/rules.d.  My understanding is that these are rules distributed with the system.  I have not changed any of them.

I did find an entry in /lib/udev/rules.d/50-udev-default.rules which has MODE ="0664" for USB devices.  Should this be "0666"?

Does anyone have any suggestions as to how I can find out why I have to use sudo to see my scanner in an application?

---

### Post by cscj01 on 2009-11-21
I just copied the /lib/udev/rules.d/50-udev-default.rules to /etc/udev/rules.d and edited the USB nodes entry.  I changed MODE="664" to MODE="666".  Now XSane and Vuescan see my Coolscan V ED.

Is this a bug in Karmic or libsane or what?

---

### Post by cscj01 on 2009-11-21
BTW, I rebooted to get the new rules loaded.

---

