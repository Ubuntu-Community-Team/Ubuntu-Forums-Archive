---
title: "Installer freezes on setup on Laditude CPx"
date: 2004-11-02
forum: Hardware &amp; Laptops
---

### Post by acray on 2004-11-02
I have an older dell laditude (PIII 500, 392mb) and when I try and install unbuntu it appears to be working correctly but right before the installer is going to partition the 12gig harddrive (I think that is where it happens)  it just "freezes".

It not really frozen since I can still type into the "console" but the screen is completely blank and it doesn't respond to any commands.

This is my first experience with unbuntu - and debian (other than using an already setup box) too for that matter - so I'm a newbie in that respect.

Any tips would be appreciated.

---

### Post by userX on 2004-11-02
I also had problems with my install, but mine happenend later in the process.

How are you partitioning? Are you using the automatic partitioning option or are you doing it manually, try switching it up. Or you could use another partitioning tool to prepare the partitions you will need, one root and one swap, and then try to run the install and use those. As far as tools go, you should be able to use any other linux boot disk with fdisk on it.

Let me know if that helps.

Will, more useful everyday

---

### Post by dread on 2004-12-22
I'm having the same problem... I did notice if i passed ide=nodma i get a little further into the installation before freezing. I don't have any trouble w/ non debian based installers. ](*,)

---

### Post by dave_euser on 2004-12-28
I used to have one of these....found that ACPI made it choke pretty hard (I think there was only a partial installation)....try booting with just APM support, no ACPI.

---

