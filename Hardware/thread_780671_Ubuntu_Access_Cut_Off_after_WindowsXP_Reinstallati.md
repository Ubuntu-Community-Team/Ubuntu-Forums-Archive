---
title: "Ubuntu Access Cut Off after WindowsXP Reinstallation"
date: 2008-05-03
forum: Hardware
---

### Post by Guzzardo on 2008-05-03
I am dual booting with WindowsXP Media Edition on one partition and Ubuntu on another.  When I had previously tried to reinstall my WinXP, I would merely "repair" the existing version, but this time, I deleted the existing version on my C drive and then put on the entirely new one.

That is all working fine, but when I boot up my computer (Dell Inspiron 6000), the OS selection screen appears as usual, but the only option given to select is the new WinXP.

Also, when I am in WinXP and look at my partitions, the 16GB space where Ubuntu should be is marked as "Unknown" and "100% Free."  Does this mean that my Ubuntu is now completely gone?  Was my Ubuntu somehow dependent on my WinXP?  Is it actually still there?

I am very sure that I did not mess with the Ubuntu partition at all while I was reinstalling WindowsXP.  How can I recover my Ubuntu?  If I uninstall this new WinXP, shouldn't I go directly to Ubuntu when I boot up?  Ubuntu is my main OS, so if that would work, I could do that.

---

### Post by penguin steve on 2008-05-04
by reinstalling windows, it overwrote the MBR (master boot record) all you have to do is boot you ubuntu live cd and go in the teminal to setup GRUB. you just have to make GRUB write the MBR again to repair this problem. there are tutorials on how to do this in other threads so i wont go any more in depth.

---

