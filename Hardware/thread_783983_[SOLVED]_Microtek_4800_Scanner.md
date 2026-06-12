---
title: "[SOLVED] Microtek 4800 Scanner"
date: 2008-05-06
forum: Hardware
---

### Post by alienexplorers on 2008-05-06
I have been trying to get my Microtek 4800 scanner to work.  When I run xsane I get the following message:
> Failed to open device 'sm3840:libusb:001:003': Access to resource has been denied.
when I run sane-find-scanner I get the following message:
> terminator@terminator-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05da, product=0x30cf) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


When I run scanimage -L I get the following message:
> terminator@terminator-desktop:~$ scanimage -L
device `sm3840:libusb:001:003' is a Microtek ScanMaker 4800 flatbed scanner


I have checked /proc/bus/usb and there are no files listed in the directory.

I have also checked to be sure my name is also listed in the following groups:
> scanner & saned

Any help getting this running would be helpful since it is the only piece of equipment I can not get running under Hardy 8.04..

---

### Post by alienexplorers on 2008-05-06
bump

---

### Post by alienexplorers on 2008-05-07
bump

---

### Post by alienexplorers on 2008-05-17
Found out the 1.0.19 driver is bad.  Reverted to the 1.0.15 driver and the problem is fixed.

---

### Post by jasonkwok on 2008-06-02
I have the same problem. But how to revert the driver?

Jason

---

### Post by jasonkwok on 2008-06-02
Oh Sorry. I found the driver in another post. It's working fine for me now!
Thank you.

---

### Post by grashdur on 2008-09-12
I have the same problem and am trying to fix it now. How do you revert to the older driver? Do I need to somehow uninstall the current driver first? 

And in Hardy Heron I'm having real difficulties installing any package that is not .deb -- it seems like the utilities for other package types that were there in Gutsy Gibbon have been gutted in HH. I'll look around more for ways to work around this.

Looking around, I haven't found any posts that explain how to revert this driver. But I did find [www.sane-project.org](www.sane-project.org) and [http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/) which seems to have the driver and a couple patches to it.

---

### Post by grashdur on 2009-02-07
For several years now I've had this problem of not being able to use my Microtek 4800 scanner with Ubuntu. Now I've tried uninstalling Xsane and installing earlier versions, but can't seem to make such a reinstallation work -- older versions are not in the repositories, and what I've found elsewhere is just a few files here and there, apparently not the whole package. Am I doomed to rely forever on Windows when using my scanner?

---

### Post by nigebj on 2010-12-01
I know this is an old thread, but it is the one I found trying to solve this, so thought I'd add this.

I've been trying to get my i800 working under Hardy and Jaunty off and on for a while (long time elapsed, not much time really focused).

Having upgraded to 10.10 I tried again today.

**sane-find-scanner** said it found a scanner (may be).

**scanimage -L** did not find anything.

**lsusb** - reports it fine (well as Microtek 4800 which is why I have added it here)

Given this I downloaded Vuescan v9 which found it, identified it correctly and was working in minutes.

So given you can waste $40 of time real quickly, I just licensed it and moved on (I have no affiliation with [www.hamrick.com](www.hamrick.com)).

---

