---
title: "[SOLVED] DVD drive not recognized"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by comandrei on 2008-01-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176133](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176133) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've been struggling with Kubuntu 7.10 to recognize my DVD drive. The drive is a TSSTcorp SN-S082D, and it's recognized by Windows XP Pro SP2 and Vista Business.
I've read that after a firmware upgrade everything will work just right. Well it dosen't (at least for my drive).
I've made a [ bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176133").
But no luck so far. The device dosen't even appear listed in /dev .
I think i has something to do with the ICH7 SATA-IDE controlller driver in the kernel. The strange thing is that the device works with the Kubuntu 7.10 liveCD, and is recognized as /dev/scd0.
I tried the kernel from hardy ```
Linux fawkes 2.6.24-3-386 #1 Thu Jan 3 22:50:17 UTC 2008 i686 GNU/Linux
```

LE :I SOLVED IT it was soo easy. You just disable the drive in BIOS, and it's going to be seen in Ubuntu.
More on this here  [http://linux.developers.dk/ich8m/](http://linux.developers.dk/ich8m/)

---

