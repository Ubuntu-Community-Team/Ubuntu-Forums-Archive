---
title: "Dynamic Hardware Detection (Post-Boot)"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by masinger53 on 2006-06-26
Simple question that I cannot seem to get answered (have googled & been searching forum & spent some time in IRC):

What do I run for hardware detection on-the-fly in [X,U]buntu?  Kudzu from my RedHat days is the only one I know by name and the issue never came up on my little Gentoo server.

Thanks in advance,
M.A.

---

### Post by Staceman on 2006-08-17
Wow, still no answer on this?

I've run into the same problem today. Fresh server install, found that I had a faulty ethernet card, so I threw in a new one. Upon rebooting, I get nothing. The system sees the card, but it did nothing to configure it, and the card is well supported in the kernel.

I didn't feel like mucking about with modprobes and editing files. I mean, this *is* Ubuntu, I shouldn't have to go through all that, right? ;) So, I just said screw it, and reinstalled the OS.

Anyway, I hate to say it, but this is pathetic. And I am a huge Ubuntu fan. I too searched high and low online for an answer to this, to no avail. (that's how I found this thread!) RedHat/Fedora has had Kudzu for many years now for things like this. Sure, you can throw kudzu on Ubuntu later on... but it, or something like it, should be there from the get-go.

---

