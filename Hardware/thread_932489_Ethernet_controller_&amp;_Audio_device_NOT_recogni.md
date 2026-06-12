---
title: "Ethernet controller &amp; Audio device NOT recognised"
date: 2008-09-28
forum: Hardware
---

### Post by zoobave on 2008-09-28
```
02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev ff)



00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

This is output when i give lspci command. But, these devices are not properly detected in new HP dv5-1102tu laptop. Is there any extra lib/package to install in order to enable these drivers?

---

### Post by markbuntu on 2008-09-28
You can look in my guide here to getting you sound working:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The part about Intel HDA will probably be most helpful for you.

I'm sorry, but I cannot help you with the ethernet part, it is beyond me. I have noticed some threads about that particular card though. Have you tried to search the forums for RTL8101E or Realtek Ethernet in the search box near the top of this page?

---

