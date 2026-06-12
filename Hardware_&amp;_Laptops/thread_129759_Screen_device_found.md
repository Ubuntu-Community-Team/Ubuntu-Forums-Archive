---
title: "Screen device found"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by supmagc on 2006-02-14
I just installed ubuntu, everything goes fine untill I boot my computer...
after the install it displays an error about "unable to load the X server" and that i need to resolve it before restarting the GDM,
because I don't know what to do, I hope someone else here will be able to help me

[http://student.kuleuven.ac.be/~s0172695/xorg.log]("http://student.kuleuven.ac.be/~s0172695/xorg.log")

---

### Post by skwid on 2006-02-14
Dude there is like 1000 threads on here that talks about the same problem you are having.

What kind of videocard do you have exactly?

---

### Post by heimo on 2006-02-14
You could start by trying to reconfigure Xorg. Be sure to get your monitor specs correctly.
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by supmagc on 2006-02-14
I have a "saphire Radeon X700 Pro 128Mb DDR III PCI-E"

---

### Post by supmagc on 2006-02-14
done it, still doesn't work :(
I think the following lines are the problem:

```
(II) Primary Device is: PCI 05:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X700 Pro (RV410)".
(II) ATI:  Unshared 8514/A not probed.
(II) ATI:  Unshared Mach64 at PIO base 0x02EC not probed.
(WW) ATI:  PCI Mach64 in slot 5:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 5:0:1 will not be enabled
 because it conflicts with another non-video PCI device.
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by heimo on 2006-02-14
:???: Could you post output of *lspci? *Also it could be helpful if you can link to your xorg.conf file.

---

### Post by taurus on 2006-02-14
Maybe the name of your screen in xorg.conf is not the same as the identifier!!!  So, post your /etc/X11/xorg.conf if you want others to have a look at it...

---

