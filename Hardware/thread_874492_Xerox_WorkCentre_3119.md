---
title: "Xerox WorkCentre 3119"
date: 2008-07-30
forum: Hardware
---

### Post by lostdave on 2008-07-30
Hey All,
Long time reader...first time poster...annnnnyway...

I am posting this for those that may be having issues with the Xerox WorkCentre 3119.

There is a relatively old solution posted [HERE]("http://ubuntuforums.org/showthread.php?t=392225&highlight=xerox+3119"), but it did not suit my particular needs.

I shall start at the beginning..
Mixed network, Apple, Ubuntu, RHEL/CentOS and XP.
The Xerox hangs of an XP Machine..for now, and not likely to change in the near future.  Now the problem lies in the siuation that the Print driver supplied by Xerox only allows for direct USB Connection..nothing else.

Some research thru the drivers shows that the WC 3119 is actually a Samsung SCX-4200 and Lo and behold, Samsung have a much better driver that allows for connection out of the box(so to speak) for Network connected Printers.

Simply download the driver from the Samsung website [http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=SCX-4200&mType=DR&dType=D&vType=L&cttID=828690]("http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=SCX-4200&mType=DR&dType=D&vType=L&cttID=828690")
Extract to a folder and run the install script
```

sudo install.sh

```
and Bob's your uncle.

Haven't tested the scanner side of things as it is a network printer, but seeing as though they are the same device, it SHOULD work, but YMMV

Hope I have saved someone some pain :-)

Dave

---

