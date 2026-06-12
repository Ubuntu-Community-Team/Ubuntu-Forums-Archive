---
title: "Canon CanoScan N670U not recognized in Dapper Drake"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by reztho on 2006-07-07
Hi, 

 I'm in Dapper and I have got a Canon CanoScan N670U scanner not recognized. But in Breezy it was recognized so the scanner is supported by Sane. Does somebody know something about the thing?

This is the output of some commands:

- lsusb:
Bus 003 Device 024: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20

(As you notice here... I plugged and unplugged the scanner many many times, and the Device number is increasing every time too)

- sane-find-scanner:

found USB scanner (vendor=0x04a9 [Canon], product=0x220d [CanoScan], chip=LM9832/3) at libusb:003:024

-  scanimage -L:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

From [http://www.sane-project.org/man/sane-plustek.5.html](http://www.sane-project.org/man/sane-plustek.5.html) my scanner is this:
CanoScan N670/676U LM9833  600x1200dpi 48bit 512Kb 0x220D

I tried inserting the Vendor and Product ID in /etc/sane.d/plustek.conf in this way: [USB] 0x04A9 0x220D and "device auto"

But that doesn't work. And yes I'm in the 'scanner' group. 
I can confirm than Udev creates the device file in /dev/bus/usb/ with the 'scanner' group at least.

My kernel is the official 2.6.15-25-k7.

Edit: I actually fixed it! I added a dll.conf file in /etc/sane.d/dll.d/ and this text line inside:
plustek

Now I'm having other problems with the scanner but that's another story.

Edit 2: And fixed again my problems with the scanner. I had to disable the calibration of the scanner. Changing this line in /etc/sane.d/plustek.conf:
#
# for skipping whole calibration step
#
option skipCalibration 0

to 

option skipCalibration 1

Edit 3: So this doesn't fix my problem. My scanner gets very noisy and doesn't scan anything, it gets hung up. In breezy at least it worked well.

Edit 4: Fixed at all it seems. Disabled every calibration and the speedup in the same file. Sorry for this continous editing.

---

### Post by tonderai on 2006-07-17
I had the same problem with grinding under Dapper (although mine was recognised initially).

Thanks - your fix worked!

---

