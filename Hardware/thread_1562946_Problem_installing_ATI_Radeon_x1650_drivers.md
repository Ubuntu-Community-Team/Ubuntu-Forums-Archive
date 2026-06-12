---
title: "Problem installing ATI Radeon x1650 drivers"
date: 2010-08-28
forum: Hardware
---

### Post by jcd29 on 2010-08-28
I downloaded the driver from here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

Following the driver search (Desktop graphics, Radeon X series, X1xxx series, Linux x86)

I followed the install instructions provided in a pdf they have there, but I got this:

```
user@user-desktop:~/Downloads$ ls
ati-driver-installer-9-3-x86.x86_64.run  linux_cat92-inst.pdf
user@user-desktop:~/Downloads$ sudo sh ./ati-driver-installer-9-3.x86.x86_64.run
sh: Can't open ./ati-driver-installer-9-3.x86.x86_64.run
```

Quick question also: Should I be trying to install this even if apparently when choosing *System, Administration, Hardware drivers* it doesn't find any proprietary drivers from my video card?

---

### Post by pme 72 on 2010-08-29
If you were running an older distribution it should work but with anything after 8.10 you will probably be limited to the open source driver or an experimental one.

"The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above."

---

### Post by pme 72 on 2010-08-29
There is an ongoing discussion about the ATI open source drivers here if you are interested:

[http://ubuntuforums.org/showthread.php?t=1238129&highlight=ATI+Open+source+drivers+coming+age](http://ubuntuforums.org/showthread.php?t=1238129&highlight=ATI+Open+source+drivers+coming+age)

---

### Post by jcd29 on 2010-08-30
Thanks, I'll check the link. So for now it's down to using open source drivers for every ATI card? (I'm guessing nvidia cards would be better for future planning?)

---

### Post by pme 72 on 2010-09-01
Well, yes, for every ATI card from the Radeon x1xxx series and earlier. I think 2xxx series and above are given the option to install the fglrx proprietary driver. I could be wrong.

---

