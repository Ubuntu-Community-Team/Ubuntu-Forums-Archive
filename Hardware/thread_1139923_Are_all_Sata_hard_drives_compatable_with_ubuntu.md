---
title: "Are all Sata hard drives compatable with ubuntu?"
date: 2009-04-27
forum: Hardware
---

### Post by boyofford on 2009-04-27
Hi all,
in the process of making myself a media centre for my front room.
Got a 3ghz dell dimenison 4700 with a 512mb nvidia graphics card and 512mb of ram.
So far so good, tested it with a jaunty on a usb stick and runs pretty well, using XBMC which seems up to the job.

My question is will ubuntu work with any sata hard drive?
Planning to get a 1TB one to start with, as cheap as i can get.

Also going to format ext4, seems quicker.

cheers
Rich

---

### Post by Barry Carroll on 2009-04-27
I think that as long as your bios can see it ubuntu will have no problem.  Sata drives can operate in a native mode called AHCI or default back to what is like a legacy IDE mode.  If you have a common chipset I'm sure you could use ahci mode but if not you could always use the ide mode if your bios allows.

---

### Post by Mugzilla on 2009-04-27
I am having a prblem with my SATA HD. I am currently at work, and do not have the log with me.

Since my isue is similar to the OP's, I will build off of their post, instead of making a new one.  

My issue is when I start my computer:  Probably 1 out of 10 restarts, the computer hangs for 60 seconds, then drops to a shell, with an intrafs (?) error.  It tells me it cannot find my HD. I will post the actual log when I get home.

---

### Post by boyofford on 2009-04-27
figured I'd just take the plunge and get one!
seems to be working OK so far.

---

