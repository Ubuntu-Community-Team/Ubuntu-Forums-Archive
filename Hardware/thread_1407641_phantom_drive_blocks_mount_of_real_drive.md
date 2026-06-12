---
title: "phantom drive blocks mount of real drive"
date: 2010-02-15
forum: Hardware
---

### Post by jnwebster on 2010-02-15
I've recently reinstalled ubuntu 9.10 from scratch, and I reconfigured my drive layouts to provide some local backup ability.
Once I got the install completed, I noticed that my data drive was already listed in nautilus and on the places menu.
I don't want to have to manually mount it every time I boot, so I went into /etc/fstab and added an entry for it to automount, using the same settings that I used last time I installed.
However, now whenever I log in, I see **TWO** entries for this drive and neither of them will mount, the error says that the device is busy and that it's already mounted. I searched these forums and others in hopes that I could resolve this, but nothing I could find worked for me.
I looked in fstab, I looked in mtab, and I can't find any entry for it that I didn't put in there myself. Even when I manually delete entries for it from fstab, it still appears in nautilus and places, but it's listed nowhere in mount or mtab or fstab.

[SIZE=3]**Here is my question:**[/SIZE]
**Is there another place besides fstab that ubuntu checks to find which drives to mount?** I want to delete this phantom entry and use a real one.

Here is my setup:
/dev/sda1: root partition (20gb ext3)
/dev/sda2: swap partition (6gb swap)
/dev/sda3: home partition (20gb ext3)
/dev/sda4: backup partition (20gb ext3)

/dev/sdb1: data partition (500gb ext3)
This is the one that gets listed twice.

Thank you for your help.

---

