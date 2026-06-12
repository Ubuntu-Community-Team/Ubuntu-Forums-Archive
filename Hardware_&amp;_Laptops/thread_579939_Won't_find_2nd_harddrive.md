---
title: "Won't find 2nd harddrive"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by SveinT on 2007-10-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153096](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153096) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

just installed 7.10 (RC, with updates) and it refuses to find my 2nd SATA HD. The first one it picks up fine, but not my second. I previously had 7.04 and I had no issues whatsoever. At boot time I get some "Failed to set xfermode" errors and some other ATA2.00 stuff. Never had that before and dunno if it's related.  Both hds are on same SATA controller, but the disk in question uses PATA->SATA converter. Any ideas for a workaround?

ps: irqpoll doesn't help

---

### Post by SveinT on 2007-10-19
Bump?

---

### Post by kaputme on 2007-10-19
same problem here but the difference is its a 7.04 ubuntu..
And the non detectability is only some times....

My hard disk in question is in NTFS format.

Any help????

---

### Post by SveinT on 2007-10-19
Do you actually get the ATA xfermode errors? Or is it just not detected? One problem I had with disks disappearing when using ubuntu and NTFS disks is that if you don't shut down your computer properly if using Windows, Ubuntu wouldn't mount the disk and said it had to be checked. So I had to boot into windows again and shut it down properly. Could this be your issue? (just a wild guess since it's sporadic...)

---

### Post by kaputme on 2007-10-20
No it doesnt show any error message just doesnt detect the drive..
But when i log in and log off windows it works...
Any solution??:guitar:

---

### Post by SveinT on 2007-10-20
Well, not really except that you need to shutdown windows properly when using windows. Or else you can't mount them in ubuntu.

---

### Post by kaputme on 2007-10-23
Is there any other solution other than that....
Coz when ever my sis logs into windows it never shuts down properly???




Dont know why?/:guitar:

---

