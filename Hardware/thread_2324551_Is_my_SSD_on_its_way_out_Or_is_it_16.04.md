---
title: "Is my SSD on its way out? Or is it 16.04?"
date: 2016-05-14
forum: Hardware
---

### Post by 98cwitr on 2016-05-14
Didnt start happening until I did a clean install of 16.04, but about every 4th or 5th reboot I get presented with a initramfs prompt. Prior to this the system acts unstable (terminal wont open, chrome acts funny, etc). I then have to run fsck to get the system to boot. Here's a screenshot: [https://www.dropbox.com/s/h0vremtk7c49ces/2016-05-14%2017.30.42.jpg?dl=0](https://www.dropbox.com/s/h0vremtk7c49ces/2016-05-14%2017.30.42.jpg?dl=0)

---

### Post by weatherman2 on 2016-05-14
What's the S.M.A.R.T. status of your SSD?  If the SSD is on its way out, you should see an indicator there in one of the S.M.A.R.T. Attributes.  You can use GSmartControl, but it may not have updated Attribute names for your SSD - you may have to look them up.

---

### Post by 98cwitr on 2016-05-14
here's the smart status

[img]http://i.imgur.com/DTX6COy.png[/img]

---

### Post by weatherman2 on 2016-05-14
Doesn't look like it's on its way out.  I suspect the OS.

---

### Post by 98cwitr on 2016-05-15
Well that's relieving. Now it's experienced the issue on back to back reboots. Ubuntu loads after fsck and throws and error report about plymouthd. Wonder if these are related or separate issues. Should I move this to another subforum?

---

### Post by Linuxisfast on 2016-05-15
It could also be the HDD controller going south, have seen this kind of behavior before with older h/w.

---

### Post by weatherman2 on 2016-05-15
Personally, I'd go back to 14.04 if that was stable.  I never install the latest-and-greatest Ubuntu until it's been out for a few months and had some updates.  14.04 will be supported until 2019.  (I'm still using 12.04 for another few months on most machines.)

---

### Post by Linuxisfast on 2016-05-15
> **weatherman2 said:**
> Personally, I'd go back to 14.04 if that was stable.  I never install the latest-and-greatest Ubuntu until it's been out for a few months and had some updates.  14.04 will be supported until 2019.  (I'm still using 12.04 for another few months on most machines.)


I have deployed 16.04 in many machines around and laptops, only on one of my PCs thats attached to my Epson L800 printer, I have to use 14.04 LTS due to missing LSB that Epson driver needs for it to be installed. So far after few updates, its smooth sailing with 16.04

---

### Post by weatherman2 on 2016-05-15
That's good to hear!

Whenever I move to the new OS version, I always make a complete backup of the old OS version or just use another hard drive, at least on important machines.  (Having spare hard drives is really helpful!)  I'll be moving my primary laptop to 14.04 soon - one step at a time!

---

### Post by Linuxisfast on 2016-05-15
> **weatherman2 said:**
> That's good to hear!

Whenever I move to the new OS version, I always make a complete backup of the old OS version or just use another hard drive, at least on important machines.  (Having spare hard drives is really helpful!)  I'll be moving my primary laptop to 14.04 soon - one step at a time!

Thats good advice indeed.

---

### Post by 98cwitr on 2016-05-31
Thanks for all the good advice guys...I was able to snap a little screenshot. Maybe the system is shutting down too early/fast?

[img]http://imgur.com/oMF2a7N.jpg[/img]
[img]http://imgur.com/R91l4a1.jpg[/img]

---

### Post by houstonbofh on 2016-05-31
It will sound silly, but try changing your SATA cables, and the port on the motherboard if you can.  This is looking a lot like a bad SATA cable or connector.

---

