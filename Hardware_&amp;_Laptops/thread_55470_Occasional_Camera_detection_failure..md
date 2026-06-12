---
title: "Occasional Camera detection failure."
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by Whatsisname on 2005-08-09
Greetings.

I am experiencing a strange problem. After some time, my digital camera ceases to be detected once I plug it in. Usually it works fine, gets mounted automatically, etc. However, after awhile when I plug it in nothing happens. I run lsmod and dsmesg and I can see that the computer definitely sees it and knows its there, but no automounting takes place. No scsi device appears in /dev/ so I cannot mount it manually. Rebooting fixes everything. Unfortuantly I do not want to reboot all the time, and long uptime is something linux prides itself in. Does anyone know every process that is associated with hotplug and automounting and whatnot that I can try to restart whenever this happens? I have tried restarted hotplug and udev but doing so never worked.

Thanks for the help.

---

### Post by heimo on 2005-08-09
I've read many similar threads and recall that someone downgraded kernel to get autodetection of USB devices working again. Unfortunataly I think the kernel upgrade was because of security patch, so downgrading is not recommended. I'd go searching bugzilla and forums for more information on this, and of at least it's possible to try if it's kernel package specific. (Sorry, I don't have any detailed information on this.)

---

### Post by Whatsisname on 2005-08-09
I'm very suspicious of it being a kernel problem though. I would expect a kernel issue to make it not work all the time, instead of only after awhile. Like I mentioned, the camera appears in lsusb, always. It seems to be an issue with the automounter or 'fake scsi device maker' or something of that sort. Of course I could be wrong though. :(

[QUOTE=heimo]I've read many similar threads and recall that someone downgraded kernel to get autodetection of USB devices working again. Unfortunataly I think the kernel upgrade was because of security patch, so downgrading is not recommended. I'd go searching bugzilla and forums for more information on this, and of at least it's possible to try if it's kernel package specific. (Sorry, I don't have any detailed information on this.)[/QUOTE]

---

