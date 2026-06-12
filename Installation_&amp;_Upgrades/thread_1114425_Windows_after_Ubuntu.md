---
title: "Windows after Ubuntu"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Aksha on 2009-04-02
How can I install windows along side ubuntu.

I currently have ubuntu only and would like to partition for windows xp

---

### Post by Pumalite on 2009-04-02
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by Aksha on 2009-04-03
the windows installer said its aborted to prevent corruption or something o_O

---

### Post by phoenixblue on 2009-04-03
I've tried to install Windows after KUBUNTU, and I couldn't access the Linux partition any more!!! so I had to reinstall KUBUNTU on the "unaccessible partition" which was basically an ext3 filesystem partition, unknown by windows. In fact I was wondering why did Linux cold'nt be bootable any longer after the installation of windows... maybe windows modified something on the booting sector or some like....

---

### Post by dandnsmith on 2009-04-03
> **phoenixblue said:**
> I've tried to install Windows after KUBUNTU, and I couldn't access the Linux partition any more!!! so I had to reinstall KUBUNTU on the "unaccessible partition" which was basically an ext3 filesystem partition, unknown by windows. In fact I was wondering why did Linux cold'nt be bootable any longer after the installation of windows... maybe windows modified something on the booting sector or some like....
Yes, indeed it does (regardless).
It replaces whatever primitive boot code was there (in this case the first stage grub) with the 'standard' Windows boot primitive.

---

