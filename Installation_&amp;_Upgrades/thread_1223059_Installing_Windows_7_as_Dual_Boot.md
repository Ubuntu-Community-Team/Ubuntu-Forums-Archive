---
title: "Installing Windows 7 as Dual Boot?"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by razorboy5 on 2009-07-25
Hi

i'm planning on getting Windows back on my laptop. (Need it for gaming)

Planning on using the "USB startup disk creator" on my lovely Ubuntu to boot it but a few questions before doing so.

When installing Windows 7 as dual boot would it partition my disk and erase all my ubuntu content?

Also do i need to specify how much hard drive i would like to give to Windows permanently or is that changeable later on?

thx

---

### Post by merlinus on 2009-07-25
You will have to create a primary partition into which to install win7, and probably format it as ntfs, since windows knows nothing about any other formats.

So if ubuntu is taking up your entire hdd, use gparted either on the live cd or gparted live to shrink its partition to make room.

You can always shrink and/or grow partitions down the line, but best to try and get it right the first time.

Also, win will overwrite grub, but it is easy to reinstall it afterwards.

---

### Post by razorboy5 on 2009-07-25
when making the space in the first place do i need to add the space the OS is going to be taking up? ex if i want to play games that'll take approx 5gb and windows OS will take about 30 then i should shrink about 35 or just 5?

thx

---

### Post by merlinus on 2009-07-25
Size for windows should include space for software you plan to install, and then some extra so you can defrag.

---

### Post by razorboy5 on 2009-07-25
thx Merlin :D
also never knew about gparted looks very useful in these situations

---

### Post by merlinus on 2009-07-25
Glad to be of assistance.  Let us know how it works out.

Also, you cannot do anything with mounted partitions, which is why I suggested using gparted live, or the one on the ubuntu live cd.  The former is a newer version, however.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

