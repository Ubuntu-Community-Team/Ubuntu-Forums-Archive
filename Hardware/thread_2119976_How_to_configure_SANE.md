---
title: "How to configure SANE?"
date: 2013-02-25
forum: Hardware
---

### Post by nickdc on 2013-02-25
Having finally got a new psu for it I'm trying to run an old scanner (Visioneer OneTouch 9320 USB) on Ubuntu 12.04. Its status is listed as "Complete" on the SANE: Supported Devices page, with avision as its backend. But the scanner isn't detected, even when attempting to use it as root. But Ubuntu knows it's there, indeed weirdly seems to find three scanners, when only one is connected! Here's the read-out from a couple of commands I tried after reading up on the problem:

nick@nick-build-1:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0471, product=0x0329) at libusb:002:002
found USB scanner (vendor=0x04a7, product=0x0362) at libusb:001:008
found USB scanner (vendor=0x0529, product=0x0001) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
nick@nick-build-1:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


I'm at the limits of my understanding here. Would some kind soul help me get a bit further?

---

### Post by nickdc on 2013-02-26
Woops! Further investigation today has brought to my attention that my scanner is not supported! I had assumed that the 9320 was the same as the OneTouch 9320. :oops: Way down the list I've now found the OneTouch 9320 which is "probably not supported". Dammit!

---

### Post by aikishugyo on 2013-02-26
> **nickdc said:**
> Woops! Further investigation today has brought to my attention that my scanner is not supported! I had assumed that the 9320 was the same as the OneTouch 9320. :oops: Way down the list I've now found the OneTouch 9320 which is "probably not supported". Dammit!

I'm sorry that you went through that disappointment. I suggest you mail the SANE mailing list (sane-devel) and see if someone there know about this scanner---it seems the report dates from 2010 so maybe there is more information now.
If it uses Genesys chips then there is a possibility that it could be tested with development code (although it would also require development and a heck of a lot of testing).

Regards,
Gernot Hassenpflug

---

### Post by nickdc on 2013-02-26
Thanks for that suggestion. I might do that, though it is an old scanner, no longer supported by the manufacturer, so I'm not sure it's worth anyone's trouble. I've just set up a virtual XP box, in the hope that I may get round it that way, but no joy so far. Seems a more productive route, though, as Ubuntu knows the scanner is there, so in theory I'd have thought it ought to work in a virtual environment. I may post for help in that section of the forums.

---

### Post by nickdc on 2013-02-26
Success! Having added myself to the Vbox users group my old scanner now works fine inside an XP virtual machine. So now I can use it without having to leave Ubuntu and/or reboot my actual machine. Great stuff! ( - though I'd still prefer it to work natively in Ubuntu!)

---

### Post by paulnewall on 2013-03-01
We all suggest people do "sane-find-scanner" and "scanimage -L as root".
Maybe it would be useful to have a little more explanation?

I imagine that sane-find-scanner searches your usb connected devices looking for the ones that describe themselves as a scanner? So that proves they are connected to your usb system and does not at all imply that they will, or will not, be supported by sane?

Whereas scanimage - L will actually try to use sane to connect to the scanner. sane runs all its different backends to see if any of them detect the scanner.

---

### Post by nickdc on 2013-03-02
Thanks, paulnewall, that makes sense and is a helpful clarification. And I suppose it's confirmed by the scanner now working in a virtual XP machine: Ubuntu as host knows it's a usb scanner so can make it available to the virtual XP, which does have the drivers to run it.

---

