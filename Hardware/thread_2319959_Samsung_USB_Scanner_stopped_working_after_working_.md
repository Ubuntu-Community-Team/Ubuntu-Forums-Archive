---
title: "Samsung USB Scanner stopped working after working fine for years"
date: 2016-04-08
forum: Hardware
---

### Post by indyblue on 2016-04-08
A strange problem recently cropped up and my scanner is either not detected or xsane shows an I/O error.  It has worked for a couple years until today when I tried to use it.  I have made no changes to the config, I assume a system (udev???) update broke it but I have no idea what.

I know the scanner works fine, I got a couple of scans to work after I sent a print to it.  After I exited xsane, the next time I ran it it failed.  Worked fine plugged into a Win7 laptop.

My user is a member of lp and scanner (although I read that since systemd this membership is no longer needed).

SYMPTOMS:
[/CODE]
If I unplug/plug the scanner in, scanimage -L works ONCE, if I run scanimage again it fails (no matter how many times I run it).  The scanner wakes up when scanimage is run, so it does receive data.
```
[INDENT]root@euchre:/etc/sane.d# lsusb |grep Sams
Bus 003 Device 036: ID 04e8:3468 Samsung Electronics Co., Ltd 
root@euchre:/etc/sane.d# scanimage -L
device `xerox_mfp:libusb:003:036' is a Samsung C460 Series multi-function peripheral
root@euchre:/etc/sane.d# scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[/INDENT]

```
Same with scanimage -T, it behaves differently on the second try:
```
root@euchre:/etc/sane.d# scanimage -T
scanimage: sane_start: Error during device I/O
root@euchre:/etc/sane.d# scanimage -T
scanimage: no SANE devices found
```

The conf file has the same entry as always (for xerox_mfp.conf)
```
/etc/sane.d/dll.conf:
xerox_mfp
```

xerox_mfp.con has a valid usb address in it (found with lsusb)
```
/etc/sane.d/xerox_mfp.conf:
#xerox_mfp.conf

# Samsung C460
usb 0x04e8 0x3468
```

The USB device is logged with a strange message:
```
Apr  8 20:31:39 euchre kernel: [ 5001.556444] usblp 3-2:1.1: usblp1: USB Bidirectional printer dev 36 if 1 alt 0 proto 2 vid 0x04E8 pid 0x3468
Apr  8 20:31:40 euchre udev-configure-printer: URI contains USB serial number
Apr  8 20:31:40 euchre udev-configure-printer: URI match: usb://Samsung/C460%20Series?serial=ZEW1B8KF1B006HH&interface=1
Apr  8 20:31:40 euchre udev-configure-printer: URI of detected printer: usb://Samsung/C460%20Series?serial=ZEW1B8KF1B006HH&interface=1, normalized: samsung c460 series serial zew1b8kf1b006hh interface 1
Apr  8 20:31:40 euchre udev-configure-printer: URI of print queue: usb://Samsung/C460%20Series?serial=ZEW1B8KF1B006HH&interface=1, normalized: samsung c460 series serial zew1b8kf1b006hh interface 1
Apr  8 20:31:40 euchre udev-configure-printer: Queue ipp://localhost:631/printers/Samsung-C460-Series has matching device URI
Apr  8 20:31:40 euchre udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Samsung-C460-Series
**Apr  8 20:34:07 euchre kernel: [ 5149.683547] usb 3-2: usbfs: interface 1 claimed by usblp while 'scanimage' sets config #1**
```

sane-find-scanner has never found it but xsane worked fine anyhow.

I need my scanner, please help me track this down.

---

### Post by pqwoerituytrueiwoq on 2016-04-09
maybe this?
[http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system](http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system)

---

### Post by indyblue on 2016-04-09
[SIZE=3]> **pqwoerituytrueiwoq said:**
> maybe this?
[http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system](http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system)

Thanks, that's the most in-depth article I have read so far.  Too bad none of it worked for me.
At least I have "different" messages now:
```
kernel: [33290.775662] usb 3-1: usbfs: interface 0 claimed by usbfs while 'scanimage' sets config #1
```
I did unload usb_storage and usblp, still no luck.  scanimage -L works once and only once.

I managed to get it working via network (sorta), but the image is cut off an inch from the top and bottom.
xerox_mfp.conf:
```
net 10.0.0.115
```
I wish I could figure out what changed and when.  It must have been an update to kernel or systemd or udev that broke it.
[/SIZE]

---

### Post by pqwoerituytrueiwoq on 2016-04-10
have you tried a live cd,a 14.04 disc will not have systemd, if you upgrade from 14.04 i think you will not have systemd (until you upgrade to 16.04)

that article covers a issues some old scanners have with usb3 systems, i have a scanner like that, i really don't use it often the only reason i have it was for testing the scanner front end software i was working on (see signature)

you can hold shift during boot and select a older kernel if you think that was the issue

edit i just rememberer there is a ppa for the scanner backend, maybe it will fix your issue, please note that this ppa is bleeding edge
[https://launchpad.net/%7Erolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/%7Erolfbensch/+archive/ubuntu/sane-git)

---

