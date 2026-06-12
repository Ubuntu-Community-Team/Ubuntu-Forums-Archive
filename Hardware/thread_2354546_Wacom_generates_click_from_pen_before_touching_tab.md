---
title: "Wacom generates click from pen before touching tablet"
date: 2017-03-03
forum: Hardware
---

### Post by kdo on 2017-03-03
I have a Toshiba dynaPad WT12PE-A64.  I'm trying to run Linuxium's 16.04.02 for cherry trail processors, which I downloaded from [http://linuxiumcomau.blogspot.com.au/2017/02/ubuntu-16042-and-updated-ubuntu-1704.html](http://linuxiumcomau.blogspot.com.au/2017/02/ubuntu-16042-and-updated-ubuntu-1704.html) .  The problem is that my stylus (identified by xsetwacom as "Wacom HID 5066 Pen stylus") sometimes causes a click when hovering.  It does not do this with the same hardware running Windows 10.

I tried to debug this using xev and evemu-record.  The events from evemu-record are only ABS_X, ABS_Y, MSC_SERIAL and BTN_TOOL_PEN.  Nevertheless, X Windows ButtonPress and ButtonRelease events are generated.  This sometimes happens and sometimes does not.  If it's not happening in one particular test it seems it will continue to not happen in the test, but if I do other things with the stylus (typing on the "onboard" keyboard, perhaps) it will switch to the state where it happens all the time in the same test where it previously worked correctly.

Any ideas?  I thought that the kernel events should be transformed into X Windows events in such a way that this would not happen.

I have set TabletPCButton with xsetwacom, though I don't think it should matter if I'm not pushing any of the stylus buttons.

Thanks.

---

### Post by opsusec on 2017-03-06
check manufacturer voltage recommendations from root/PCI/drive.

adjust accordingly, or find a driver that would suit the hardware. I had a battery fried in a phone about 6 years ago because of something exactly like this.

---

