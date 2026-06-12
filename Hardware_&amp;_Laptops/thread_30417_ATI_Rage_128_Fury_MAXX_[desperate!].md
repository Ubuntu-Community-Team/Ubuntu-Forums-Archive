---
title: "ATI Rage 128 Fury MAXX [desperate!]"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by metalLord on 2005-04-28
hy everybody. first of all i'm italian so sorry for my poor english!

i've got the "ATI Rage 128 Fury MAXX" video card, first time after installing ubuntu (first login) it all works very good but if i reboot or halt and restart computer, it freezes with the black x on black background, just before the login screen. it freezes when load gdm I think.

after many attempts I've settled that the key of all is this:
```

# lspci
[...]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TDMS
0000:01:01.0 Display controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TDMS

```

in fact my xorg.conf says:
```

Section "Device"
Identifier  "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
Driver       "ati""
BusID  **"PCI:1:0:0"**

```

so I think the problem is in those PCI numbers...I have two "pieces", one in 1:0:0 and one in 1:1:0....but I dont' know how to configure xorg.conf to see both of them.

i've tried to change the PCI:1:0:0 in xorg.conf with PCI:1:1:0. X doesn't freeze but "blink" 3 times, and then i've to read Xorg.0.log when it says:
```

(II) Multi device card detected: **[1:0:0][1:1:0]**
(EE) R128(0): Cannot read V-BIOS
[...]
Fatal server error
xf86MapPciMem:
Could not mmap PCI memory [...] (Invalid argument)

```

so how can I properly configure xorg.conf??

please,,,I LONG FOR UBUNTU!
thanx to all

---

### Post by alastair on 2005-04-28
Are you trying to use 2 video cards? Or will one be enough?
Is one on the motherboard?

Perhaps you can disable (at least as a test) one of them e.g. in the BIOS? Then try again?

---

### Post by metalLord on 2005-04-29
no i've only one video card...  ](*,) 

me poor!

---

