---
title: "Installing XP while keeping files?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by cchase88 on 2009-01-10
I currently have Ubuntu 8.04 installed and have been wanting to install windows on one of my 3 hard drives. I read that it's easier to install XP, then Ubuntu, rather than the other way around. My question is whether or not  I can move all of my personal files to one hard drive while I install XP without it over writing them?

Heres what I would like to do:

I would like to take this:
80Gb [Ubuntu installation]
120Gb [extra space]
160Gb [extra space]

and turn it into this:

80Gb [XP]
120Gb [shared hard drive between both systems]
160Gb [Ubuntu installation]

Thanks for any feedback!8-)

---

### Post by maybeway36 on 2009-01-10
I'd say the Ubuntu installation might be better off where it is, and you could install Windows on the 120GB - it would be easier. After you install Windows, you need to 1. reinstall GRUB (search the forums and it tells you how) and 2. edit Ubuntu's /etc/fstab to let you see the new partitions.

---

### Post by cchase88 on 2009-01-10
I have already tried installing XP on the 160Gb drive and it comes up telling me that I need to install it on the 80Gb drive. I think it had something to do with Windows having to be on the first drive, but I'm not positive.

---

### Post by cchase88 on 2009-01-11
I've been thinking about this, and have come up with an idea:

If I format my 160Gb drive as NTFS, move all my files to it, and unplug it from inside my computer, I can then install XP on the 80Gb drive as well as use the 120Gb drive for extra XP space. Since the 160Gb drive is formatted as NTFS, I should be able to then plug it back in, have XP recognize it and transfer my files to the 120Gb drive. Then after that I can install Ubuntu on the 160Gb.

Anyone think this will work? Any other suggestions?

---

