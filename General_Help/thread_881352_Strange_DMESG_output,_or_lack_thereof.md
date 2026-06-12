---
title: "Strange DMESG output, or lack thereof"
date: 2008-08-05
forum: General Help
---

### Post by ProfBib on 2008-08-05
Just yesterday, I noticed some strange information flash by me on shutdown, so I ran dmesg today when I had a minute and got a great many lines, all similar to this:

/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:1d.0-2/input3, status -32

There was none of the normal useful information.  What gives?  I am not a Linux wizard but have been an Ubuntu user for about 3 years now and am not scared of the command line.

If worse comes to worse, I'll just do a clean install, though I would like to avoid that drastic step.

I am using a fairly standard Hardy installation which has run problem free for a couple of months already.

Thanks.

BTW - If I try to read the log using the menu (System>System Log) the Log Viewer Freezes up and I have to kill the application to avoid severe system crawl.

---

### Post by ProfBib on 2008-08-06
OK, the problem is solved.  After staring at all of those very similar dmesg lines, is suspected that something I had plugged into a usb port could be generating the errors.  I assumed it was neither my mouse nor my ipod (since both those were working correctly) and unplugged a usb skype phone that I have been trying to get up and running.  Once I did that and rebooted, everything returned to normal.

I would, however, love for someone to explain this phenomenon to me.  Why did all the other dmesg information disappear just because of one malfunctioning usb device.  By the way, the usb phone was being recognized properly, I just haven't gotten it to work yet.

---

